---
title: '[Hibernate] How to setup a bidirectional relationship'
author: Tim
layout: post
permalink: /2005/10/17/hibernate-how-to-setup-a-bidirectional-relationship/
categories:
  - How-To
tags:
  - examples
  - hibernate
  - java
  - solutions
---
I got the following question from a friend the other day.

> I have a parent and a child object with a one-to-many relationship by the child&#8217;s table having a column that points to it&#8217;s parent. What are the correct settings for the mapping in this situation where I need to be able to remove children from the parent&#8217;s set, and save the updated parent. It seems like I&#8217;ve been through all sorts of combinations, and I was wondering if you could lend me your advice.

The same day I also had a similar question from a colleague at work. I figured I&#8217;d post my response here so I could easily find it in the future. I&#8217;ve tried to make the code reasonably generic, but watch out for dumb typos.

You should setup the parent mapping like this:

<pre class="textmate-source railscasts"><span class="source source_ruby"><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">&lt;</span>set name<span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>children<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span> lazy<span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>true<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span> inverse<span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>true<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">></span>
  <span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">&lt;</span>key column<span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>PARENT_ID<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">/</span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">></span>
  <span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">&lt;</span>one<span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">-</span>to<span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">-</span>many <span class="keyword keyword_control keyword_control_ruby">class</span><span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>my.child.ChildClass<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">/</span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">></span>
<span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">&lt;</span><span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">/</span>set<span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">></span></span></pre>

And then map the child like this:

<pre class="textmate-source railscasts"><span class="source source_ruby"><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">&lt;</span>many<span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">-</span>to<span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">-</span>one name<span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>parent<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span> column<span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>PARENT_ID<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span> <span class="keyword keyword_operator keyword_operator_logical keyword_operator_logical_ruby">not</span><span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">-</span>null<span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>false<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span> <span class="keyword keyword_control keyword_control_ruby">class</span><span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>my.parent.ParentClass<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">/</span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">></span></span></pre>

Notice that the column name in each refers to THE SAME COLUMN. You&#8217;re just connecting the link.

From the parent class:

<pre class="textmate-source railscasts"><span class="source source_java"><span class="comment comment_block comment_block_documentation comment_block_documentation_java"><span class="punctuation punctuation_definition punctuation_definition_comment punctuation_definition_comment_java">/**</span> The set of children of this object. <span class="punctuation punctuation_definition punctuation_definition_comment punctuation_definition_comment_java">*/
</span></span><span class="storage storage_modifier storage_modifier_access-control storage_modifier_access-control_java">private</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">Set</span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_java"><</span><span class="storage storage_type storage_type_java">ChildClass</span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_java">></span> children = <span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">new</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">HashSet</span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_java"><</span><span class="storage storage_type storage_type_java">ChildClass</span><span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_java">></span>();
<span class="meta meta_definition meta_definition_method meta_definition_method_java"><span class="storage storage_modifier storage_modifier_java">private </span><span class="storage storage_type storage_type_java">void</span> <span class="entity entity_name entity_name_function entity_name_function_java">setChildren</span><span class="meta meta_definition meta_definition_param-list meta_definition_param-list_java">(<span class="support support_type support_type_built-ins support_type_built-ins_java">Set</span><<span class="storage storage_type storage_type_java">ChildClass</span>> children</span>) </span>{
    <span class="variable variable_language variable_language_java">this</span>.children = children;
}</p>



<p>
  <span class="meta meta_definition meta_definition_method meta_definition_method_java"><span class="storage storage_modifier storage_modifier_java">public </span><span class="storage storage_type storage_type_java">void</span> <span class="entity entity_name entity_name_function entity_name_function_java">removeChild</span><span class="meta meta_definition meta_definition_param-list meta_definition_param-list_java">(<span class="storage storage_type storage_type_java">ChildClass</span> child</span>) </span>{
      children.remove(child);
      child.setParent(<span class="constant constant_language constant_language_java">null</span>);
  }
</p>



<p>
  <span class="meta meta_definition meta_definition_method meta_definition_method_java"><span class="storage storage_modifier storage_modifier_java">public </span><span class="storage storage_type storage_type_java">void</span> <span class="entity entity_name entity_name_function entity_name_function_java">addChild</span><span class="meta meta_definition meta_definition_param-list meta_definition_param-list_java">(<span class="storage storage_type storage_type_java">ChildClass</span> child</span>) <span class="meta meta_definition meta_definition_throws meta_definition_throws_java"><span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">throws</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">IllegalArgumentException</span> </span></span>{
      <span class="keyword keyword_control keyword_control_java">if</span> (child <span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_java">==</span> <span class="constant constant_language constant_language_java">null</span>) {
          <span class="keyword keyword_control keyword_control_catch-exception keyword_control_catch-exception_java">throw</span> <span class="keyword keyword_other keyword_other_class-fns keyword_other_class-fns_java">new</span> <span class="support support_type support_type_built-ins support_type_built-ins_java">IllegalArgumentException</span>(<span class="string string_quoted string_quoted_double string_quoted_double_java"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_java">"</span>Child may not be null<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_java">"</span></span>);
      }
      <span class="keyword keyword_control keyword_control_java">if</span> (child.getParent() <span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_java">!=</span> <span class="constant constant_language constant_language_java">null</span>) {
          child.getParent().removeChild(child);
      }
      child.setParent(<span class="variable variable_language variable_language_java">this</span>);
      children.add(child);
  }</span></pre>
  
</p>


<p>
  From the child class:
</p>


<p>
  <pre class="textmate-source railscasts"><span class="source source_java"><span class="comment comment_block comment_block_documentation comment_block_documentation_java"><span class="punctuation punctuation_definition punctuation_definition_comment punctuation_definition_comment_java">/**</span> The parent. <span class="punctuation punctuation_definition punctuation_definition_comment punctuation_definition_comment_java">*/
</span></span><span class="storage storage_modifier storage_modifier_access-control storage_modifier_access-control_java">private</span> <span class="storage storage_type storage_type_java">ParentClass</span> parent;</span></pre>
  
</p>


<p>
  This simple example seems to illustrate the basics.  My friend later pointed out that one of the things tripping him up was the <code>cascade</code> option.  Recognizing that it&#8217;s completely separate from the <code>inverse</code> property was a big step.  That&#8217;s an important point &#8211; the <code>inverse</code> just means that the child objects have a property that refers back to the parent.  It helps resolve object relationships on load, but the <code>cascade</code> and <code>lazy</code> attributes tell Hibernate when to save and load the objects to and from the database.
</p>
