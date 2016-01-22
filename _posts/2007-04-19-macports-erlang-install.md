---
title: Macports Erlang Install
author: Tim
layout: post
permalink: /2007/04/19/macports-erlang-install/
categories:
  - Perplexed
---
So I ran into a funny error today while trying to install `erlang` on my Mac.

<pre class="textmate-source railscasts"><span class="text text_plain"><span class="meta meta_paragraph meta_paragraph_text">Zdot-MBP:~ tim$ sudo port install erlang
Error: Unable to execute port: invalid command name "configure.cppflags"</span></span></pre>

It turns out (after running `port` using the `-d` option), that macports was trying to upgrade my `gettext` version. The `Portfile` seemed to be trying to set the `CPPFLAGS` option for the `configure` tool. I opened up `/opt/local/var/db/dports/sources/ rsync.rsync.darwinports.org_dpupdate_dports/devel/gettext/Portfile` and replaced:

<pre class="textmate-source railscasts"><span class="source source_shell">configure.cppflags \
    -no-cpp-precomp</span></pre>

with this:

<pre class="textmate-source railscasts"><span class="source source_shell">configure.env   CPPFLAGS=<span class="string string_quoted string_quoted_double string_quoted_double_shell"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_shell">"</span>-no-cpp-precomp<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_shell">"</span></span></span></pre>

That seemed to have fixed things. I was able to continue my install and fire up `erl`. Since I couldn&#8217;t find the answer on the big Google-Net I cast, I figured I&#8217;d write it up here in case some poor soul had the same bad luck I did.

Now it&#8217;s time to [try out some Amazon API][1] stuff.

 [1]: http://pragdave.pragprog.com/pragdave/2007/04/a_first_erlang_.html
