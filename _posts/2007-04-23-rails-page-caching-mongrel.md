---
title: Rails Page Caching + Mongrel
author: Tim
layout: post
permalink: /2007/04/23/rails-page-caching-mongrel/
categories:
  - Perplexed
tags:
  - mongrel
  - open source
  - patch
  - path_info
  - rails
  - ruby
  - testing
  - url
---
So you&#8217;ve got a great Rails app. You&#8217;re setting up page caching for those publicly accessible pages shared by everyone. One of your pages is the `:index`. It seems like the caching isn&#8217;t working when you&#8217;re testing it, but the output constantly says:

<pre class="textmate-source railscasts"><span class="text text_plain"><span class="meta meta_paragraph meta_paragraph_text">Cached page: /tag.html (0.00044)</span></span></pre>

What gives? Try seeing if &#8220;/tag&#8221; seems to use the cache, but &#8220;/tag/&#8221; doesn&#8217;t.

The mechanism behind the Rails page caching takes your action output and stuffs it all into an HTML file that *can easily be found by the **web server***. Ah! So there&#8217;s no voodoo in Rails itself that tries to check for that page. In fact, it&#8217;s banking on not being called by pushing that burden off to the web server. In our case, this is Mongrel.

So how does Mongrel decide? Well, the `mongrel_rails` fires up a `RailsHandler` which uses the `PATH_INFO` to check for the existence of a cached file. When you&#8217;re requesting &#8220;/tag/&#8221; it&#8217;s looking for tag/.html, but not finding it.

I put together a patch [here][1] to address it. Seems to work in my limited testing, but I don&#8217;t know what I may have broken. Yeah, usually I make sure to write a test for my patches. This time I didn&#8217;t. Perhaps it won&#8217;t make it in until I do, but at least I&#8217;ve got it written down here to remind me when my cache doesn&#8217;t seem to work quite right.

 [1]: http://rubyforge.org/tracker/index.php?func=detail&aid=10330&group_id=1306&atid=5147
