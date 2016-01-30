---
title: The JSF Burrito, One Year Later
author: Tim
layout: post
redirect_from: /2007/02/16/the-jsf-burrito-one-year-later/
category:  Impressions
tags:
  - ajax
  - burrito
  - ejb
  - facelets
  - followup
  - hibernate
  - java
  - jboss
  - jpa
  - jsf
  - retrospective
  - rules
---
It&#8217;s hard to believe that it&#8217;s been a year since my &#8220;burrito&#8221; [podcasts][1] [on][2] [JSF][3]. So what have I done in this last year with JSF? What is my opinion now and how has it changed?

Have you ever skipped out on a movie that was popular? Decided not to see it because it either didn&#8217;t fit your taste or didn&#8217;t mesh with your life in some other way? I have. I usually look back later on without regret. That&#8217;s the way I feel looking back at JSF a year later, but let give you some details.

 [1]: http://timshadel.com/2006/01/19/jsf-the-7-layer-burrito-i-wont-eat-again/
 [2]: http://timshadel.com/2006/01/24/jsf-leaky-abstractions-grab-a-mop/
 [3]: http://timshadel.com/2006/02/03/jsf-renderkit-blues/

<!--more-->

I&#8217;ve changed organizations and roles in this last year. At my old place, we continued to use JSF through the time I left. For a couple months at this new place I worked as a Senior Developer on different team, before being asked to step in as the Manager for my current team. During that time, the team was just starting a new project. They had decided to use JSF, and so I had a bit more than a month where I continued using JSF, again pretty much every day (some days were more Hibernate/JPA-focused). We used Facelets, and looked at Seam (decided &#8220;No&#8221;). The newer JSF stuff was a bit nicer to use, and Facelets made it feel like I was programming with JSP tags again, so I could do layouts easier. I added some stuff from various popular JavaScript libraries (before AjaxFaces), and it seemed to work pretty well with what we had.

Overall, I just found that it only seemed to add complexity without taking a substantial load off my plate. Another issue arose in testing JSF. Again, it&#8217;s always been a challenge, since early on. While it&#8217;s gotten better, I&#8217;ve [watched Ed Gibbs&#8217;s team][4] struggle with testing JSF. In some ways, he says [it&#8217;s been a hurdle in adopting TDD][5] in his team:

> The core issue comes down to having to use JSF for the GUI layer and dealing with its’ many mock objects using Shale’s mocking package for JSF. Thus many tests cannot simply test a single method without making sure FacesContext and many other stubs are setup. This tends to make the tests harder and more tedious to write especially for developers who haven’t quite caught the whole TDD bug anyway.

As I&#8217;ve moved into my position as a Manager, I took on direct responsibilities for not only the technical work of my team, but also for working day in and day out with our main client (internal), the deadlines for our product, and meeting the overall company initiatives started from the upper management (I&#8217;m in a weekly meeting with several VP&#8217;s and others about [an initiative directly affecting my product][6]). In all the work we have to do on our project, very little of it has centered around a need for reusable UI components. We work in an enterprise environment. I work for a Fortune 500 company, with IT sprawled as far as the eye can see. We have standardization efforts, we have a heterogeneous environment. For all intents and purposes, one would predict that we&#8217;d really need JSF. And yet I look back over a dozen release cycles that we&#8217;ve been through since I took this position, and so few of them have required anything close to the features JSF offers above other web frameworks. There are a couple, sure. But for those few we&#8217;ve used some standard solutions that are common to our organization and they&#8217;ve been good enough.

Where has the work been? We&#8217;ve eliminated EJBs. We&#8217;ve implemented Spring. We dumped Ant and moved to Maven 2. We&#8217;ve thrown out an older, commercial rules engine and setup JBoss Rules (formerly Drools). We&#8217;ve made major shifts in our application functionality to accommodate some fairly significant business changes. We&#8217;ve expanded our user base, and improved our turn around time for small items. We&#8217;ve started some in-depth User Centered Design work with our HCI group that&#8217;s focused on bringing some existing business processes into our app for the first time, and reworking some existing stuff. We&#8217;ve made quite a few changes, and done a lot of work over the last seven months. I&#8217;ve focused mainly on the technical changes here, but the main thrust of our work has been support for business needs. Those, in turn, drove the technical needs.

In conclusion, I stand by my [previous][2] [opinions][3] that I feel that solving business problems is both more interesting and more important. For me, the vast majority of that is done *outside* the UI layer.

 [4]: http://edgibbs.com/category/jsf/
 [5]: http://edgibbs.com/2006/12/03/excessive-setup-anti-pattern/
 [6]: http://timshadel.com/2007/01/17/calm-before-the-storm/
