---
title: Extracting CAS configuration into YAML, like database.yml
author: Tim
layout: post
permalink: /2008/05/31/extracting-cas-configuration-into-yaml-like-databaseyml/
categories:
  - How-To
tags:
  - authentication
  - cas
  - rails
  - ruby
  - rubycas-client
  - yaml
---
If you&#8217;ve done any enterprise work with Rails, and your shop is using [CAS][1] for authentication, chances are you&#8217;ve seen [rubycas-client][2]. Chances are you&#8217;ve also loved how easy it was to get working. There&#8217;s usually only one hitch &#8212; you&#8217;ve got to change the config based on which environment you&#8217;re deploying into.

Here&#8217;s the standard advice you get from the RDoc:

<pre class="textmate-source railscasts"><span class="source source_ruby source_ruby_rails"><span class="comment comment_line comment_line_number-sign comment_line_number-sign_ruby"><span class="punctuation punctuation_definition punctuation_definition_comment punctuation_definition_comment_ruby">#</span> in your config/environment.rb
</span><span class="support support_class support_class_ruby">CASClient</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span><span class="support support_class support_class_ruby">Frameworks</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span><span class="support support_class support_class_ruby">Rails</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span><span class="support support_class support_class_ruby">Filter</span><span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>configure<span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">(</span>
  <span class="constant constant_other constant_other_symbol constant_other_symbol_ruby"><span class="punctuation punctuation_definition punctuation_definition_constant punctuation_definition_constant_ruby">:</span>cas_base_url</span> <span class="punctuation punctuation_separator punctuation_separator_key-value">=></span> <span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>https://cas.example.foo/<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="punctuation punctuation_separator punctuation_separator_object punctuation_separator_object_ruby">,</span>
  <span class="constant constant_other constant_other_symbol constant_other_symbol_ruby"><span class="punctuation punctuation_definition punctuation_definition_constant punctuation_definition_constant_ruby">:</span>proxy_retrieval_url</span> <span class="punctuation punctuation_separator punctuation_separator_key-value">=></span> <span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>https://cas-proxy-callback.example.foo/cas_proxy_callback/retrieve_pgt<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="punctuation punctuation_separator punctuation_separator_object punctuation_separator_object_ruby">,</span>
  <span class="constant constant_other constant_other_symbol constant_other_symbol_ruby"><span class="punctuation punctuation_definition punctuation_definition_constant punctuation_definition_constant_ruby">:</span>proxy_callback_url</span> <span class="punctuation punctuation_separator punctuation_separator_key-value">=></span> <span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>https://cas-proxy-callback.example.foo/cas_proxy_callback/receive_pgt<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="punctuation punctuation_separator punctuation_separator_object punctuation_separator_object_ruby">,</span>
  <span class="constant constant_other constant_other_symbol constant_other_symbol_ruby"><span class="punctuation punctuation_definition punctuation_definition_constant punctuation_definition_constant_ruby">:</span>logger</span> <span class="punctuation punctuation_separator punctuation_separator_key-value">=></span> cas_logger
<span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">)</span></span></pre>

<!--more-->

But with a tiny change, you can give your CAS setup all the flexibility and auto-magical environmental savvy of `database.yml`. Goodbye last minute edits for a production deployment. Check this out:

<pre class="textmate-source railscasts"><span class="source source_ruby source_ruby_rails"><span class="comment comment_line comment_line_number-sign comment_line_number-sign_ruby"><span class="punctuation punctuation_definition punctuation_definition_comment punctuation_definition_comment_ruby">#</span> in your config/environment.rb
</span>cas_options <span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span> <span class="support support_class support_class_ruby">YAML</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span>load_file<span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">(</span><span class="variable variable_other variable_other_constant variable_other_constant_ruby">RAILS_ROOT</span><span class="keyword keyword_operator keyword_operator_arithmetic keyword_operator_arithmetic_ruby">+</span><span class="string string_quoted string_quoted_single string_quoted_single_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">'</span>/config/cas.yml<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">'</span></span><span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">)</span>
<span class="support support_class support_class_ruby">CASClient</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span><span class="support support_class support_class_ruby">Frameworks</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span><span class="support support_class support_class_ruby">Rails</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span><span class="support support_class support_class_ruby">Filter</span><span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>configure<span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">(</span>cas_options<span class="punctuation punctuation_section punctuation_section_array punctuation_section_array_ruby">[</span><span class="variable variable_other variable_other_constant variable_other_constant_ruby">RAILS_ENV</span><span class="punctuation punctuation_section punctuation_section_array punctuation_section_array_ruby">]</span><span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">)</span>
</span></pre>

Now make a simple YAML file, `cas.yml`:

<pre class="textmate-source railscasts"><span class="source source_yaml"><span class="comment comment_line comment_line_number-sign comment_line_number-sign_yaml"><span class="punctuation punctuation_definition punctuation_definition_comment punctuation_definition_comment_yaml">#</span> config/cas.yml
</span><span class="meta meta_tag meta_tag_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">development</span><span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span>
</span>    :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">cas_base_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.qaexample.tld/cas/</span></span>
    :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">validate_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.qaexample.tld/cas/validate</span></span>
    :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">logout_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.qaexample.tld/cas/logout</span></span></p>



<p>
  <span class="meta meta_tag meta_tag_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">test</span><span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span>
  </span>    :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">cas_base_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.qaexample.tld/cas/</span></span>
      :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">validate_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.qaexample.tld/cas/validate</span></span>
      :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">logout_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.qaexample.tld/cas/logout</span></span>
</p>



<p>
  <span class="meta meta_tag meta_tag_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">production</span><span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span>
  </span>    :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">cas_base_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.example.tld/cas/</span></span>
      :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">validate_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.example.tld/cas/validate</span></span>
      :<span class="string string_unquoted string_unquoted_yaml"><span class="entity entity_name entity_name_tag entity_name_tag_yaml">logout_url<span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_yaml">:</span></span> <span class="string string_unquoted string_unquoted_yaml">https://cas.example.tld/cas/logout</span></span>
  </span></pre>
  
</p>


<p>
  It&#8217;s worth noting that the colons in front of the YAML keys indicate that those keys are Ruby symbols, not strings.  All the rubycas-client docs use symbols in their examples, so I&#8217;d follow their lead if I were you.
</p>


<p>
  Got an opinion about using CAS with Rails?  Leave a comment and let us hear it!
</p>

 [1]: http://www.ja-sig.org/products/cas/
 [2]: http://rubycas-client.rubyforge.org/
