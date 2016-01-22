---
title: Query Your Filesystem
author: Tim
layout: post
permalink: /2010/12/03/query-your-filesystem/
categories:
  - Leftovers
---
Queries are a way of asking a computer system questions. (I heard you say &#8216;duh!&#8217;) You&#8217;ve probably done this lots in SQL to ask your database questions. How many members have this condition? How much money was sent to these people in August? But how about this one: Which file has the bean named &#8216;myCrazyService&#8217; in it? Or, How many projects refer to the old version of &#8216;projectFastMoving&#8217;? For these questions you should turn to the *nix-like file utilities.

Standard *nix tools can be used to create queries that your filesystem can answer. Let&#8217;s start with `find`.

### The `find` utility

The `find` command lets you locate files that are named in a specific way, and that have certain file attributes. Let&#8217;s look at an example:

{% highlight shell %}
find . -iname SpriNg.xml
{% endhighlight %}

This query searches the current directory, and looks for files with names like: spring.xml, Spring.xml, or sprinG.xml. The `i` in `iname` means that the pattern will use a case-insensitive comparison when matching against existing files. Let&#8217;s try another:

{% highlight shell %}
find . -name proj*.xml -maxdepth 2
{% endhighlight %}

This code searches the current directory, and will go down only 2 folders below this one in search of matches. It will look for files named like: projector.xml, project.xml, and proj2.xml. Limiting the depth can greatly speed your search. So can starting at a lower level of the directory structure.

<!--more-->

### Add `grep` to your bucket

Now that you&#8217;ve located the set of files under suscpicion, it&#8217;s time to execute your unwarrented search. For example, if you&#8217;re looking for which projects depend on my-shared-code then your query might look something like this:

{% highlight shell %}
find . -name project.xml -maxdepth 2 -exec grep -l my-shared-code {} ;
{% endhighlight %}

There&#8217;s a lot going on here. The first half of the find command should be fairly familiar. The last half invokes a program for each result found, using the `-exec` parameter. Everything from that point until the semicolon is considered part of the executed command. The `{}`&#8216;s indicate where the filename should be substituted at execution time. So the resulting command runs **as if** it were something like this:

{% highlight shell %}
grep -l my-shared-code \work\my-products\myproduct\trunk\myproject\project.xml
{% endhighlight %}

The option used in grep is a lowercase `L`. It tells grep to list only the filename whose contents match, and not the line contents that triggered the match.

### Stuck on Windows?

Try [Console 2][1] or [Cygwin][2]. I&#8217;ve been [exclusively on Mac for over 4 years][3], so I can&#8217;t help you much more than that. <img src="http://timshadel.com/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />

### Go try it

Now go try it. See what kinds of queries you can write. See which take a long time, and how you can focus them to get the info you need in a reasonable time frame. Enjoy!

 [1]: http://sourceforge.net/projects/console/
 [2]: http://www.cygwin.com/
 [3]: http://timshadel.com/2006/11/15/election-results-mac-over-ubuntu-in-a-landslide
