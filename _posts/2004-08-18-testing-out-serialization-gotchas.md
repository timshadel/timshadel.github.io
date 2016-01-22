---
title: Testing Out Serialization Gotchas
author: Tim
layout: post
permalink: /2004/08/18/testing-out-serialization-gotchas/
categories:
  - How-To
tags:
  - enums
  - java
  - serialization
  - testing
---
Have you ever encounterd a `<a title="Javadoc for NotSerializableException" href="http://java.sun.com/j2se/1.4.2/docs/api/java/io/NotSerializableException.html">NotSerializableException</a>` in staging, or worse, production? Perhaps you&#8217;ve run your application for months or years, but then you decided to cluster your web tier and you realize that your container is actually trying to write out your `<a title="Javadoc for HttpSession" href="http://java.sun.com/j2ee/sdk_1.3/techdocs/api/javax/servlet/http/HttpSession.html">HttpSession</a>`s to some place hither or yon. Perhaps you&#8217;re testing after adding that last little feature, only to eventually realize that your brilliant new feature inserts something into the session that prevents serialization. 

I&#8217;ve encountered such unpleasent experience as those in past projects. Today I wanted to make sure that my `Message` for a JMS queue was serializable. More than that, I wanted to make sure that the attribute that&#8217;s a Typesafe Enum class I&#8217;ve used (yeah, I know they&#8217;ve added enums in 1.5/5.0) properly deserializes — it shouldn&#8217;t create a new object. Here&#8217;s the test I used on the enum: 

<pre class="textmate-source railscasts"><span class="source source_java"><span class="meta meta_definition meta_definition_method meta_definition_method_java"><span class="storage storage_modifier storage_modifier_java">public </span><span class="storage storage_type storage_type_java">void</span> <span class="entity entity_name entity_name_function entity_name_function_java">testSerialize</span><span class="meta meta_definition meta_definition_param-list meta_definition_param-list_java">(</span>) <span class="meta meta_definition meta_definition_throws meta_definition_throws_java"><span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">throws</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">Exception</span> </span></span>{
    <span class="support support_type support_type_built-ins support_type_built-ins_java">ByteArrayOutputStream</span> bout = <span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">new</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">ByteArrayOutputStream</span>();
    <span class="support support_type support_type_built-ins support_type_built-ins_java">ObjectOutputStream</span> out = <span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">new</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">ObjectOutputStream</span>(bout);
    out.writeObject(<span class="storage storage_type storage_type_java">MyEnum</span>.<span class="constant constant_other constant_other_java">ENUM_CHOICE</span>);
    out.flush();
    <span class="storage storage_type storage_type_java">byte</span>[] bytes = bout.toByteArray();
    <span class="support support_type support_type_built-ins support_type_built-ins_java">ObjectInputStream</span> in = <span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">new</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">ObjectInputStream</span>(<span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">new</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">ByteArrayInputStream</span>(bytes));
    <span class="storage storage_type storage_type_java">MyEnum</span> enum = (<span class="storage storage_type storage_type_java">MyEnum</span>) in.readObject();
    assertTrue(<span class="string string_quoted string_quoted_double string_quoted_double_java"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_java">"</span>Deserialized constant should be exactly the same object as the constant itself.<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_java">"</span></span>, enum <span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_java">==</span> <span class="storage storage_type storage_type_java">MyEnum</span>.<span class="constant constant_other constant_other_java">ENUM_CHOICE</span>);
}</span></pre>

For more nuances of writing Typesafe Enums, why they&#8217;re really needed, and how to use them well, you should really checkout *Item 21* of [Josh&#8217;s book][1]. In the meantime, think about testing your serialization assumptions. Got any suggestions for other serialization areas to watch?

 [1]: http://amazon.com/o/ASIN/0201310058/ref=ase_timshadelcom-20/ "Effective Java: Programming Language Guide"
