---
title: '[Subclipse] 0.9.7 &#8211; Not ready'
author: Tim
layout: post
permalink: /2004/07/06/subclipse-097-not-ready/
categories:
  - Impressions
tags:
  - eclipse
  - subclipse
  - subversion
---
I&#8217;ve been excited about the idea of an Eclipse plugin for Subversion ever since I saw the initial announcements about Subclipse. I recently installed version 0.9.7 via the update site (http://www.loonsoft.com/updates), but was not impressed.

Subclipse seems slow! I&#8217;m not sure if it&#8217;s just the JNI component, or if there&#8217;s something else affecting it, but it&#8217;s slow to load when Eclipse opens a Subversion project. It&#8217;s also incredibly slow the first you right click on a project and choose Team -> Share, and choose SVN. It takes forever for the Finish button to be enabled!

What I want is a clean replacement for the CVS plugin, including Team Synchronizing. I suppose I should just shutup and code some help for the project, but I&#8217;m becoming increasingly discouraged by the difficulty of having patches accepted for the code I use frequently (Note: I&#8217;ve never submitted a patch to the Subclipse project), and so I&#8217;m becoming more content to wait for the updates to be done by those closer to the project, even if it takes a bit longer.
