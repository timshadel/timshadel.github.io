---
title: 'JSF: Leaky Abstractions (Grab a Mop)'
author: Tim
layout: post
redirect_from: /2006/01/24/jsf-leaky-abstractions-grab-a-mop/
enclosure:
  - |
    |
        http://ia600400.us.archive.org/2/items/zdotpodcast/Zdot-20060124-JsfPart2.mp3
        17670103
        audio/mpeg

category:  podcast
tags:
  - java
  - jsf
  - leaky abstraction
---
In part two of my series of podcasts on why I&#8217;m not interested in using JSF in the future, I focus on the Leaky Abstraction that it provides. I feel like the leaks get in the way of getting actual work done; they confuse new developers, and cause headaches for everyone. Users even see the results of the leaking.

<a href="http://ia600400.us.archive.org/2/items/zdotpodcast/Zdot-20060124-JsfPart2.mp3" onClick="javascript:urchinTracker ('/podcasts/Zdot-20060124-JsfPart2.mp3'); "><img src="http://timshadel.com/wp-content/uploads/2006/01/podcast-logo.gif" /></a>

Download <a href="http://ia600400.us.archive.org/2/items/zdotpodcast/Zdot-20060124-JsfPart2.mp3" onClick="javascript:urchinTracker ('/podcasts/Zdot-20060124-JsfPart2.mp3'); ">JSF Part 2</a>.

Some of the leaks I discuss include:

  * Ultimately, JSF provides a [Leaky Abstraction][1] that (in spite of its promise) still requires all developers to understand Request-Response in addition to the 6 lifecycle phases.
  * Security in the web.xml is based around URL, and by definition you don&#8217;t know the URL for many JSF actions. This makes it MUCH harder to get the fine-grained security right, but also expose the basic servlet (think Request-Response) nature of the application.
  * Users may refresh a page, like the Search Results, and be whirled away to the search entry page &#8211; their results having been scattered to the wind.

My point isn&#8217;t that these items can&#8217;t be dealt with, but that the core abstraction leaks somewhat and I prefer to do without it. I have *many* choices of Java web frameworks. I&#8217;d rather be solving the business problems &#8211; those are by far more important. Please see previous posts [here][2] and [here][3].

**UPDATE:**[The third and final part][4] of the series is now posted.

 [1]: http://www.joelonsoftware.com/articles/LeakyAbstractions.html "The Law of Leaky Abstractions"
 [2]: http://timshadel.com/blog/2006/01/19/jsf-the-7-layer-burrito-i-wont-eat-again/ "JSF: The 7-Layer Burrito I Won’t Eat Again"
 [3]: http://timshadel.com/blog/2006/01/20/jsf-burrito-more-complete-list/ "JSF Burrito: More Complete List"
 [4]: http://timshadel.com/blog/2006/02/03/jsf-renderkit-blues/ "JSF: RenderKit Blues"
