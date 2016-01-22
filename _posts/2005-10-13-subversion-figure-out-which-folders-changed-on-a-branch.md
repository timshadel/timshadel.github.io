---
title: '[Subversion] Figure out which folders changed on a branch'
author: Tim
layout: post
permalink: /2005/10/13/subversion-figure-out-which-folders-changed-on-a-branch/
categories:
  - How-To
tags:
  - recipe
  - solutions
  - subversion
---
Just wanted to jot down a quick Subversion recipe. I&#8217;m doing a merge today, and I wanted to know which of the 25 folders on my branch actually changed. Here&#8217;s what I used to figure it out.

<pre class="textmate-source railscasts"><span class="source source_shell">svn diff -r 4649:HEAD http://myserver/svn/branches/mybranch <span class="keyword keyword_operator keyword_operator_pipe keyword_operator_pipe_shell">|</span> grep <span class="string string_quoted string_quoted_double string_quoted_double_shell"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_shell">"</span>Index:<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_shell">"</span></span> <span class="keyword keyword_operator keyword_operator_pipe keyword_operator_pipe_shell">|</span> sed -e <span class="string string_quoted string_quoted_double string_quoted_double_shell"><span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_begin punctuation_definition_string_begin_shell">"</span>s/Index: ([^\/]<em>)\/.</em>/\1/<span class="punctuation punctuation_definition punctuation_definition_string punctuation_definition_string_end punctuation_definition_string_end_shell">"</span></span> <span class="keyword keyword_operator keyword_operator_pipe keyword_operator_pipe_shell">|</span> sort -u</span></pre>

Downsides: If I&#8217;ve got a folder that has only directory structure changes, I won&#8217;t see them there.
