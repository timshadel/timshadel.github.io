---
title: DHH On Stateful Web Applications
author: Tim
layout: post
redirect_from: /2007/04/13/dhh-on-stateful-web-applications/
categories:
  - Impressions
---
In last year&#8217;s [JSF Burrito podcasts][1], I argued that I didn&#8217;t see the point of using a strong component model for [JSF][2] and that throwing away nice HTTP RESTful URIs is a Bad Thing. In an interview with InfoQ, DHH takes up a similar (though probably more polite) stance.

[InfoQ: DHH Responds to Stateful Web Applications Row][3]

> [There is an] assumption that all web developers really want to be desktop developers and that all web applications would be better if only they were more like their desktop counterparts. I don&#8217;t accept that assumption. I love working with the web as it is. I love the architectural patterns offered by HTTP and REST.
>
> So in many ways, I see chasing a desktop-like view of the web as chasing the past, not the future.

I&#8217;ve written about my reactions to JSF one year after the burrito entries. I find myself clearly in the camp that DHH is in: making desktop-like web apps is chasing the past, using RESTful style development is an approach I prefer.

A number of months ago we held an internal debate over XUL, and its place in our development. For the most part, we debated *many* sides of the issue and came out with &#8220;let&#8217;s wait and see.&#8221; Basically the core of the debate was whether a desktop-like UI is better *for our apps* or if a web model was more appropriate. Some of us leaned toward the web app side, some just thought the timing was too soon to tell for XUL. Personally, I prefer to keep all the MVC issues on the controller side, and limit JavaScript on the client to handle issues of rapid user feedback (check out the code behind Google&#8217;s &#8220;star&#8221; in GMail), and leave the control flow and rendering decisions to the server-side.

But that&#8217;s just me.

 [1]: http://timshadel.com/2006/01/19/jsf-the-7-layer-burrito-i-wont-eat-again/
 [2]: http://timshadel.com/tag/jsf
 [3]: http://www.infoq.com/news/2007/04/no-compromise-stateful-row
