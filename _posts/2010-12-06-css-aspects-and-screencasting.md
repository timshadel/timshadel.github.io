---
title: CSS, Aspects, and Screencasting
author: Tim
layout: post
permalink: /2010/12/06/css-aspects-and-screencasting/
categories:
  - Leftovers
---
I recently came across an old draft post from 2007 that I never published. It looks finished enough to simply push it out as-is. While it was obviously written before the explosion of CSS frameworks and tools like Blueprint and Compass, those don&#8217;t really have much impact on the core of what I was saying. I hope you find it useful&#8230;

&#8211;Tim

* * *

This morning I read a post by Jon Udell that ignited a series of latent thoughts I&#8217;ve had, mostly centered around CSS, aspects, and screencasting.

In his post, [Matthew Levine’s holy grail][1], Jon praises the theory of CSS but bemoans the drudgery that so many of us not-a-designer-but-geek-enough-to-try types face at some point or other:

> To be honest, although I’m hugely fond of CSS styling, I’ve always struggled with CSS layouts, and I know I’m not the only one in that boat. When you read the explanation in Matthew’s article, you can see why. CSS layout is like one of those games where you slide 15 tiles around in a 16-square matrix. In principle it is a declarative language, but in practice the techniques are highly procedural: Step 1, Step 2, etc.

Jon goes on to request a pattern library for CSS layouts, and while I think it&#8217;s a great idea I don&#8217;t think it&#8217;s enough. In my many years of web programming experience few things been more intriguing and challenging as deconstructing a complex web design from someone else and distilling it to the essentials. In the end, we muddle through, leaving unnecessary HTML and CSS constructs littered throughout our new site. Data needs evolve for the site, invoking the corresponding evolutionary change in the HTML and CSS constructs. The ebb and flow of change ultimately builds up enough sediment in our design that, like your old water heater, you simply throw it out and start afresh.

<!--more-->

Why is it so complicated? Isn&#8217;t it just colors and a bit of structure? To get good at evolutionary web design takes several things. I believe that first it takes time to understand how web designers approach the process of building a particular template. On top of that it takes a clear understanding of the unbreakable link between HTML structure and CSS &#8212; a coupling so tight and so loose at the same time.

For starters, the design process is sufficiently opaque to obscure the reasoning for certain elements. (Is this HTML construct here only to achieve a certain feature? Is that CSS construct there for the same reason, or does it play multiple roles?) Learning more of the tacit knowledge of the evolutionary web design is helpful.

One piece of the puzzle is to understand the design process more in depth. Jon&#8217;s been the major proponent of screencasts for a long time. He&#8217;s said in his article [Screencasting of tacit knowledge][2]:

> One of the things that I&#8217;ve known tacitly, but never articulated, is that screencasting can be an excellent way to transmit tacit knowledge.

But one of the challenges is transmitting the kind of tacit knowledge involved in CSS design work is that it takes place over a long period of time &#8212; *way* to long to merit a screencast. I recently stumbled across another form of transmitting that kind of tacit knowledge, though. It seems like the time-lapse cousin to the screencast. [Dylan Bennett created][3] what he calls a *designline*:

> To create this designline, I took a screenshot basically every time I saved my HTML file. I&#8217;m one of those people who impulsively hits Ctrl-S after every tiny little change, so you end up seeing every little change made to the file as it goes. I started out with a blank text file and I go all the way to a completed site design. Check it out.
> 
> ![Time-lapse evolution of a web site design][4]

While CSS has a declarative format, as Jon mentions above, to me it also has the feel of an aspect-oriented language in that a single declaration may cut across a multitude of unrelated elements. One single element may have [multiple CSS classes][5] associated with it.

 [1]: http://blog.jonudell.net/2007/01/22/matthew-levines-holy-grail/
 [2]: http://weblog.infoworld.com/udell/2006/09/19.html
 [3]: http://mboffin.com/post.aspx?id=1619 "MBoffin.com - Designline - A Design Timeline"
 [4]: http://timshadel.com/wp-content/uploads/2010/12/designline-openair.gif
 [5]: http://weblog.infoworld.com/udell/2004/02/09.html#a913 "Multivalued CSS class attributes"
