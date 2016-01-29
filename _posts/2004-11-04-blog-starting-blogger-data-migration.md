---
title: '[Blog] Starting Blogger data migration'
author: Tim
layout: post
redirect_from: /2004/11/04/blog-starting-blogger-data-migration/
categories:
  - News
tags:
  - apache
  - blogger
  - blogging
---
Ok. I&#8217;ve got [my most popular article][1] ported over to Blogger. I now have my domain registrar pointing my domain name at a server I own running Apache. I use [URL rewriting][2] to ensure old article permalinks still work. I also use the [mod_proxy][3] to send all requests to Blogger. I host my own images, since Blogger doesn&#8217;t host any.

I&#8217;ll be backporting my entries for a while, then tweaking my templates. After that, I&#8217;ve got some great stuff to write on my recent work with using [Spring][4], JMS, and threads to process hundreds of thousands of messages.

 [1]: http://timshadel.com/blog/2004/08/28/eclipse-standardizing-plugins-across-your-team/ "[Eclipse] Standardizing plugins across your team"
 [2]: http://httpd.apache.org/docs-2.0/misc/rewriteguide.html "URL Rewriting Guide - Apache HTTP Server"
 [3]: http://httpd.apache.org/docs-2.0/mod/mod_proxy.html "mod_proxy - Apache HTTP Server"
 [4]: http://www.springframework.org/ "Spring Framework"
