---
title: 'JSF: Spec vs. Implementation'
author: Tim
layout: post
permalink: /2006/02/07/jsf-spec-vs-implementation/
categories:
  - Impressions
tags:
  - feedback
  - java
  - jsf
  - specification
---
Michael Slattery makes [a good observation in a comment][1] on my last JSF podcast.

> I generally enjoy your podcasts. [&#8230;] I have some feedback. It seems like you are complaining mostly about an implementation of JSF rather than the spec itself.

Much of my chatter has centered around examples involving the actual implementation. Let me step back and summarize my podcast main points from the standpoint of the spec:

  1. The JSF spec indicates exclusive use of POST. That breaks all kinds of RESTful idioms and paradigms that good websites are based on. Strike one.

  2. The JSF spec itself attempts to create a component model with a lifecycle that obscures the underlying HTTP request-response cycle. It&#8217;s a Leaky Abstraction, and it does more harm than good. Strike two.

  3. The JSF spec defines the concept of a RenderKit; a concept that places HTML far away from page content and creates an abstraction that most people won&#8217;t need but everyone must deal with. Oh, and it turns the page definition into an XML config file, forcing my view logic back into the controller area. Strike three.

Many of the annoyances I listed are stated in an implementation specific way, but my philosophical differences truly lie with the spec. Perhaps it&#8217;s a forest vs trees thing. In any case, it evidently wasn&#8217;t clear that the spec was to blame for the issues discussed in my podcasts.

Oh. I almost forgot. One more:

  1. The JSF spec is a spec for a web framework(!?). So the rest of the problems I have with substandard implementations are indirectly caused because there&#8217;s a spec in the first place. If there was just a single, high-quality framework it would eliminate the chatter of choosing among several implementations and focus disucssion on the underlying merits of it&#8217;s approach to web development. Will the next web framework please step up to bat?

 [1]: http://timshadel.com/blog/2006/02/03/jsf-renderkit-blues/#comment-186
