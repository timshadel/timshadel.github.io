---
title: How to Setup Google Apps Chat SRV Records For iChat and xmpp4r-simple
author: Tim
layout: post
permalink: /2007/12/14/how-to-setup-google-apps-chat-srv-records-for-ichat-and-xmpp4r-simple/
categories:
  - How-To
tags:
  - google
  - google apps
  - ichat
  - jabber
  - ruby
  - xmpp
  - xmpp4r
  - xmpp4r-simple
---
I&#8217;ve registered [several domains][1] using [Google Apps][2]. Lately I&#8217;ve been fiddling with using Jabber with those domains, and I wanted to have a program be able to interact on IM using an account like tim@example.com. Furthermore, I wanted to have everything Just Work.

The place to start was with DNS. [Google has a help page][3] about how to setup your DNS so that your Google Apps accounts can be federated with other non-Google Jabber communities. The problem is that neither `xmpp4r-simple` nor iChat simply work if I use `tim@example.com` as my [JID][4]. Then I stumbled across [this post][5] that connected the dots for me.

Here&#8217;s a screenshot of how I setup my SRV records over at [eNom][1]:

![DNS SRV records for XMPP federation and client setup.][6]

After that, my simple chat listener worked:

<pre class="textmate-source railscasts"><span class="source source_ruby"><span class="meta meta_require meta_require_ruby"><span class="keyword keyword_other keyword_other_special-method keyword_other_special-method_ruby">require</span> <span class="string string_quoted string_quoted_single string_quoted_single_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">'</span>rubygems<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">'</span></span></span>
<span class="meta meta_require meta_require_ruby"><span class="keyword keyword_other keyword_other_special-method keyword_other_special-method_ruby">require</span> <span class="string string_quoted string_quoted_single string_quoted_single_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">'</span>xmpp4r-simple<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">'</span></span></span></p>



<p>
  im <span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span> <span class="support support_class support_class_ruby">Jabber</span><span class="punctuation punctuation_separator punctuation_separator_other punctuation_separator_other_ruby">::</span><span class="support support_class support_class_ruby">Simple</span><span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span><span class="keyword keyword_other keyword_other_special-method keyword_other_special-method_ruby">new</span><span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">(</span><span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>tim@example.com<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="punctuation punctuation_separator punctuation_separator_object punctuation_separator_object_ruby">,</span> <span class="string string_quoted string_quoted_double string_quoted_double_ruby"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_ruby">"</span>secret-password<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_ruby">"</span></span><span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">)</span>
  puts im<span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>connected?
  im<span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>accept_subscriptions <span class="keyword keyword_operator keyword_operator_assignment keyword_operator_assignment_ruby">=</span> <span class="constant constant_language constant_language_ruby">true</span>
</p>



<p>
  <span class="keyword keyword_control keyword_control_ruby">while</span> <span class="constant constant_language constant_language_ruby">true</span>
    sleep<span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">(</span><span class="constant constant_numeric constant_numeric_ruby">5</span><span class="punctuation punctuation_section punctuation_section_function punctuation_section_function_ruby">)</span> <span class="keyword keyword_control keyword_control_ruby">unless</span> im<span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>received_messages?
</p>



<p>
  im<span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>received_messages <span class="punctuation punctuation_section punctuation_section_scope punctuation_section_scope_ruby">{</span><span class="meta meta_syntax meta_syntax_ruby meta_syntax_ruby_start-block"> </span><span class="punctuation punctuation_separator punctuation_separator_variable punctuation_separator_variable_ruby">|</span><span class="variable variable_other variable_other_block variable_other_block_ruby">msg</span><span class="punctuation punctuation_separator punctuation_separator_variable punctuation_separator_variable_ruby">|</span> puts msg<span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>body <span class="keyword keyword_control keyword_control_ruby">if</span> msg<span class="punctuation punctuation_separator punctuation_separator_method punctuation_separator_method_ruby">.</span>type <span class="keyword keyword_operator keyword_operator_comparison keyword_operator_comparison_ruby">==</span> <span class="constant constant_other constant_other_symbol constant_other_symbol_ruby"><span class="punctuation punctuation_definition punctuation_definition_constant punctuation_definition_constant_ruby">:</span>chat</span> <span class="punctuation punctuation_section punctuation_section_scope punctuation_section_scope_ruby">}</span>
  <span class="keyword keyword_control keyword_control_ruby">end</span></span></pre>
  
</p>


<p>
  My little &#8220;bot&#8221; silently accepted new buddy requests, and printed out recent messages every 5 seconds.
</p>


<p>
  <b>UPDATE:</b> <del>Something&#8217;s amiss here, I think. I&#8217;ll update when I have more details.</del> Guess not.  I tried this out on another domain, and thought that things didn&#8217;t work right.  But I was mistaken.  Everything looks good.
</p>

 [1]: http://timshadel.com/2007/02/18/standing-up-against-the-sleaze/
 [2]: http://www.google.com/a/
 [3]: http://www.google.com/support/a/bin/answer.py?answer=60227&hl=en
 [4]: http://www.google.com/search?client=safari&rls=en-us&q=define:JID&ie=UTF-8&oe=UTF-8
 [5]: http://checksum.org/article/google_talk_for_google_apps_srv_records/
 [6]: http://timshadel.com/wp-content/uploads/2007/12/2110015204_17b478a06c_o.png
