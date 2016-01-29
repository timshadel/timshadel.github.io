---
title: 'JSF: RenderKit Blues'
author: Tim
layout: post
redirect_from: /2006/02/03/jsf-renderkit-blues/
enclosure:
  - |
    |
        http://ia600400.us.archive.org/2/items/zdotpodcast/Zdot-20060203-JsfPart3.mp3
        14720566
        audio/mpeg

category:  podcast
tags:
  - accessibility
  - html
  - java
  - jsf
  - web standards
---
This is the final part of my three-part series on why JSF isn&#8217;t my personal choice for future development work. I focus on the woes of the doing HTML interfaces in JSF.

<a href="http://ia600400.us.archive.org/2/items/zdotpodcast/Zdot-20060203-JsfPart3.mp3" onClick="javascript:urchinTracker ('/podcasts/Zdot-20060203-JsfPart3.mp3'); "><img src="http://timshadel.com/wp-content/uploads/2006/02/podcast-logo.gif" /></a>

Download <a href="http://ia600400.us.archive.org/2/items/zdotpodcast/Zdot-20060203-JsfPart3.mp3" onClick="javascript:urchinTracker ('/podcasts/Zdot-20060203-JsfPart3.mp3'); ">JSF Part 3</a>.

The major problems I speak to:

  * The HTML put out by today&#8217;s JSF components is neither standards compliant or semantically meaningful. Take [a look][1] around [the web][2], and you&#8217;ll see [all sorts][3] of movements that require good, semantic, standards compliant HTML. JSF&#8217;s rederings are stuck in 1999.
  * The HTML for the components is very far away from the page layout (it&#8217;s in the RenderKit). To fix HTML problems, programmers will likely find workarounds instead of fixing the problem. That&#8217;s a set of Broken Windows waiting to happen (see [The Pragmatic Programmer][4]) . It doesn&#8217;t encourage the kind of clean programming that I think it ought to.
  * RenderKits are an artifact of the [Architecture Astronauts][5]. They are so unlikely to be used for the purpose for which they were designed that they create more pain than solution. (Will all seven of you using your JSF for HTML and WML please stand up?)
  * Finally, JSF turns JSP almost, if not entirely, into a data language (or [declarative language][6]) instead of an [imperative language][7]. The page layout is used to configure the component tree, and has no direct representation of executable statements like &#8220;if&#8221; and &#8220;for&#8221;. Some view this as a triumph; I think it&#8217;s a tragedy.

Again, I&#8217;d rather be solving the business problems than finding workarounds to these restrictions and annoyances of JSF. If you&#8217;re interested in reading and hearing more, please see my previous posts [here][8], [here][9] and [here][10].

**UPDATE:** The mp3 file should now be in the right spot. Serves me right for posting in a rush. Sorry. While I&#8217;m at it, I might as well claim [my Odeo channel][11] (odeo/0f55e88149deb27e). Enjoy.

 [1]: http://alistapart.com "A List Apart: For People Who Make Websites"
 [2]: http://webstandards.org/ "Web Standards Project"
 [3]: http://diveintoaccessibility.org/ "Dive Into Accessibility: 30 days to a more accessible web site"
 [4]: http://amazon.com/o/ASIN/020161622X/
 [5]: http://www.joelonsoftware.com/articles/fog0000000018.html "Don't Let Architecture Astronauts Scare You"
 [6]: http://en.wikipedia.org/wiki/Declarative_programming "Wikipedia: Declarative Language"
 [7]: http://en.wikipedia.org/wiki/Imperative_language "Wikipedia: Imperative Language"
 [8]: http://timshadel.com/blog/2006/01/19/jsf-the-7-layer-burrito-i-wont-eat-again/ "JSF: The 7-Layer Burrito I Won’t Eat Again"
 [9]: http://timshadel.com/blog/2006/01/20/jsf-burrito-more-complete-list/ "JSF Burrito: More Complete List"
 [10]: http://timshadel.com/blog/2006/01/24/jsf-leaky-abstractions-grab-a-mop/ "JSF: Leaky Abstractions (Grab a Mop)"
 [11]: http://odeo.com/claim/feed/0f55e88149deb27e
