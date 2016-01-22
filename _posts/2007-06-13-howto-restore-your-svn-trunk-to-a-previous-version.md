---
title: HOWTO Restore Your SVN Trunk to a Previous Version
author: Tim
layout: post
permalink: /2007/06/13/howto-restore-your-svn-trunk-to-a-previous-version/
categories:
  - How-To
---
Sometimes you just need to admit that you&#8217;ve loused things up and you want to go back to the way you had them last Thursday. It takes courage to throw in the towel, but it also takes a reasonable understanding of how to do it quickly with your tool. Here&#8217;s the simple procedure I follow when I want my `trunk` restored to a previous version.

First, I have my repository laid out like this:

<pre>/myproject
   /tags
      /archive
   /branch
   /trunk
</pre>

-1. Know which revision of trunk you want to restore. If you don&#8217;t, then this is all a worthless waste of time.

  1. Also, make sure to talk to your team. You don&#8217;t want anyone trying to commit or update from trunk between steps 1 and 3. Also, they may have objections to your choice in step -1.

  2. Backup you work in the `/tags/archive` area. I use this area for snapshots of my project that I want to name, and don&#8217;t want to see very often (I want to see project releases occasionally, so they just go in `/tags`). Make sure you choose a good name (`good-name` in the url below) for your archive tag.

`
<pre>
svn cp http://url/for/my/trunk http://url/for/my/tags/archive/good-name -m "Save my messed up work."
</pre>
<p>`

  1. Delete your trunk. Now we could have simply used `mv` instead of `cp` in our last command, but we&#8217;re paranoid and want to make sure that everything worked first.

`
<pre>
svn rm http://url/for/my/trunk -m "Start over on trunk."
</pre>
<p>`

  1. Restore the version of trunk that you want to use. In this example, we&#8217;re using revision 437 as the source of our new trunk.

`
<pre>
svn cp -r 437 http://url/for/my/trunk http://url/for/my/trunk -m "Restore trunk to previous version."
</pre>
<p>`

There you have it, kids. Happy restoration.
