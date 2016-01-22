---
title: What to use instead of JSF
author: Tim
layout: post
permalink: /2006/02/15/what-to-use-instead-of-jsf/
categories:
  - Impressions
tags:
  - choices
  - java
  - jsf
  - web frameworks
---
I&#8217;ve had lots of feedback from listeners of my JSF podcasts. Many of them have asked what I&#8217;d recommend instead of JSF. I think the best answer is no answer here. Matt Raible&#8217;s [latest post][1] is a great example of the process I&#8217;d actually recommend to make your own decision.

Look at your project, your people, and your skills. Look at the industry directions, and contrast the approaches each framework takes. Look at your existing tools, your budget, tool documentation, forum support, and a growing collective knowledge of how to solve hard problems with a framework. From there, take your best guess and try it out on something small, then add a bit of complexity in difficult areas like using complex objects to drive your UI or reusing chunks of UI and controller logic. See how well your framework front-runner does.

Have a junior developer try to complete a maintenance task on your prototype. Evaluate the options enough to get a feel for it, but take the plunge at some point. Recognize that you can change it later, and that will cost something, but you need a longer term experience to know the bumps, bruises and bright spots. Blog about your experiences on the way to clarify and catalog the evolution of your thinking.

Finally, don&#8217;t choose simply one framework and always use that. Matt&#8217;s a great example in this area as well. If you look back, he&#8217;s done several comparisons of various web frameworks; often the same frameworks are in all of the comparisons. He&#8217;s made different recommendations over time depending on the goals of his comparison. He&#8217;s also looked at fringe frameworks and disected them to understand what they offered, even if he decided not to use them. These are the kinds of things you want to do or see others do when making a choice about most technical recommendations.

 [1]: http://raibledesigns.com/page/rd?entry=large_sites_powered_by_java
