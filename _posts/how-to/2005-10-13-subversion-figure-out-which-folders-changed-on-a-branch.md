---
title: '[Subversion] Figure out which folders changed on a branch'
author: Tim
layout: post
redirect_from: /2005/10/13/subversion-figure-out-which-folders-changed-on-a-branch/
category:  How-To
tags:
  - recipe
  - solutions
  - subversion
---
Just wanted to jot down a quick Subversion recipe. I&#8217;m doing a merge today, and I wanted to know which of the 25 folders on my branch actually changed. Here&#8217;s what I used to figure it out.

{% highlight sh %}
svn diff -r 4649:HEAD http://myserver/svn/branches/mybranch | grep "Index:" | sed -e "s/Index: ([^\/])\/./\1/" | sort -u
{% endhighlight %}

Downsides: If I&#8217;ve got a folder that has only directory structure changes, I won&#8217;t see them there.
