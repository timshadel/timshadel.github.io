---
title: Using POST for Search Considered Harmful
author: Tim
layout: post
redirect_from: /2006/11/09/using-post-for-search-considered-harmful/
categories:
  - Craftsmanship
tags:
  - harry potter
  - http
  - jsf
  - search
  - usability
---
This is why JSF&#8217;s &#8220;everything-is-a-POST&#8221; approach is bad, but first let me give a bit of background information. I&#8217;m a Harry Potter fan. I like the books. I like the occasional conversation. I ususally keep my enthusiasm centered around new arrivals of a book or movie. A while back, my mom and I were talking Harry Potter. She tried to send me a few links. Here&#8217;s what I got:

> Hi guys,
>
> Here are a couple of links you might like:
>
> Video stream of Radio City Music Hall reading:
>
> http://www.the-leaky-cauldron.org/#article:8956
>
> Here&#8217;s a quick rundown of the above interview. You have to scroll down to &#8220;Coverage:Harry Carrie and Garp&#8221; There are some additional links to fan reaction toward the end of the article.
>
> http://www.mugglenet.com/search/index.php
>
> transcript of Richard and Judy interview:
>
> http://www.mugglenet.com/search/index.php
>
> Have fun,
> loveya,
> mom

Notice the last two links. They&#8217;re identical, and they clearly have no information about which particular search results should appear in them. They&#8217;re entirely dependent upon the state of the current session of the user. Yet they have interesting content that my mom wants to share with me.

With most other sites (including the first link in the email), you can simply cut-n-paste the URL and send something meaninful to a friend. Lots of people know this. But when you hide your search behind a POST, you break that tacit understanding between the user and the Big Web World. You violate a social [moré][1]. This isn&#8217;t just a problem with JSF (though their assertion that everything&#8217;s a POST is darn annoying) &#8212; even my example is from a PHP site.

Please stop breaking the web. Always use GET for your search options, and reserve POST for what it should be for: operations with such side effects that the user agent should prevent accidental replay of the request.

 [1]: http://en.wikipedia.org/wiki/Mores
