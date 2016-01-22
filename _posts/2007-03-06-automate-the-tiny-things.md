---
title: Automate the Tiny Things
author: Tim
layout: post
permalink: /2007/03/06/automate-the-tiny-things/
categories:
  - Craftsmanship
tags:
  - alias
  - automation
  - bash
  - mac
  - pervasive
  - pragmatic
  - shell
  - subversion
---
I don&#8217;t know how many years I&#8217;ve used the following command chain to add all my unknown files to Subversion:

<pre class="textmate-source railscasts"><span class="source source_shell">svn st <span class="keyword keyword_operator keyword_operator_pipe keyword_operator_pipe_shell">|</span> grep ? <span class="keyword keyword_operator keyword_operator_pipe keyword_operator_pipe_shell">|</span> sed -e <span class="string string_quoted string_quoted_double string_quoted_double_shell"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_shell">"</span>s/? *//<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_shell">"</span></span> <span class="keyword keyword_operator keyword_operator_pipe keyword_operator_pipe_shell">|</span> xargs svn add</span></pre>

Inevitably I occasionally end up using that string on some directory where I have a space in the pathname, and everything bombs. So I finally got around to adding it to my `~/.bash_aliases` file today, with the additional `-e "s/^(.*)$/\"\1\"/"`. Simple, really (just make sure that something `source`s that file):

<pre class="textmate-source railscasts"><span class="source source_shell">alias svnaddall=<span class="string string_quoted string_quoted_single string_quoted_single_shell"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_shell">'</span>svn st | grep ? | sed -e "s/? <em>//" -e "s/^\(.</em>\)$/\"\1\"/" | xargs svn add<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_shell">'</span></span></span></pre>

I may still play with the actual alias name to see what sticks in my every day practice. Maybe I totally missed a way simpler way to do this. Seems like I&#8217;ve done something like this since back when I started using Subversion at release 0.18 or 0.19. Maybe I haven&#8217;t kept up, so I&#8217;d be happy to be enlightened.

Do you have anything tiny hanging around that should be [automated][1] right now?

 [1]: http://www.pragmaticprogrammer.com/articles/jan_04_3legs.pdf#page=2 "IEEE Software: Three Legs, No Wobble by the Pragmatic Programmers"
