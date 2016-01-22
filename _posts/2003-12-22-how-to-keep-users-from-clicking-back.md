---
title: 'How to Keep Users from Clicking &#8220;Back&#8221;'
author: Tim
layout: post
permalink: /2003/12/22/how-to-keep-users-from-clicking-back/
categories:
  - How-To
tags:
  - struts
  - web development
---
You really can&#8217;t. There are Struts discussions [here][1] with recommended settings [here][2]. And [this][3] discussion refers to the WebObjects docs [here][4].

You also can&#8217;t reliably display a &#8220;Warning: Page has Expired&#8221; IE message, as discussed [here][5].

Overall it seems like [transaction tokens][6] are a [recommended][7] solution, but I was surprised that no one mentioned [Struts Workflow][8].

 [1]: http://marc.theaimsgroup.com/?l=struts-user&m=106252599627745&w=2
 [2]: http://marc.theaimsgroup.com/?l=struts-user&m=106266317031122&w=2
 [3]: http://marc.theaimsgroup.com/?l=struts-user&m=106256120130642&w=2
 [4]: http://developer.apple.com/documentation/WebObjects/Web_Applications/BacktrackingAndCache/chapter_6_section_5.html
 [5]: http://marc.theaimsgroup.com/?l=struts-user&m=103173031229537&w=2
 [6]: http://jakarta.apache.org/struts/api/org/apache/struts/action/Action.html#isTokenValid(javax.servlet.http.HttpServletRequest)
 [7]: http://marc.theaimsgroup.com/?l=struts-user&m=106270396515315&w=2
 [8]: http://www.livinglogic.de/Struts/
