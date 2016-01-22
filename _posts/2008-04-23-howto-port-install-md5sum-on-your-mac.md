---
title: HOWTO port install md5sum on your Mac
author: Tim
layout: post
permalink: /2008/04/23/howto-port-install-md5sum-on-your-mac/
categories:
  - How-To
tags:
  - hash
  - linux
  - mac
  - md5
  - md5sum
---
I&#8217;ve been using Linux [for a long time][1]. While it lost the battle for my desktop, it still reigns supreme in my server world. I have this very occasional habit of wanting to check if two files are really, honestly, undoubtedly the same.

I had that need again today.

I&#8217;ve always used `md5sum` on Linux. `sudo port search md5sum` was a bust. I Googled around. I figured I&#8217;d just have to find the package that contains `md5sum` and `sudo port install [package]`. No dice. Nothing promising for miles around, or at least through page 5 of the Google results.

<!--more-->

Eventually I landed on [Wikipedia&#8217;s md5sum page][2]. Then a flood of vague memories hit me. Macs have a similar program, but it&#8217;s named `md5` and its output formatting is slightly different (but the calculated hash is the same). It had been ages since I had discovered this, and I had totally forgotten.

So, instead of `sudo port install md5sum`, I&#8217;ve edited my `~/.bash_aliases` file to contain this:

{% highlight sh %}
alias md5sum='man md5'
{% endhighlight %}

Maybe there really is a fabled `md5sum` for Mac, but this is good enough for me. This will remind the more frozen part of my brain that I really want to type `md5 [filename]` instead. And then I won&#8217;t go a-Googling for it any more. And perhaps, neither will you.

P.S. the `md5` man page on my Mac shows it to be part of `openssl`, just in case you wondered.

 [1]: http://timshadel.com/2006/11/15/election-results-mac-over-ubuntu-in-a-landslide/
 [2]: http://en.wikipedia.org/wiki/Md5sum
