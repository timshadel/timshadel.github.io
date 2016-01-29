---
title: Clean builds are possible
author: Tim
layout: post
redirect_from: /2005/12/19/clean-builds-are-possible/
categories:
  - Craftsmanship
---
This was a wonderous site to see, and one a long time coming. After long months of working to build a sense of importance for the build, we finally got every one of our 199 projects in CruiseControl to build successfully. Good work team.

![CruiseControl build tool summary showing 199 projects building successfully][1]

One obstacle we faced along the way was knowing exactly how many of our projects were failing. That&#8217;s what lead me to submit [this patch][2] to CruiseControl. It was accepted and has since been improved upon by others, I believe. It&#8217;s finally nice to see the &#8220;Failed&#8221; count down to 0. <img src="http://timshadel.com/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />

 [1]: http://timshadel.com/wp-content/uploads/2005/12/clean-build.gif
 [2]: http://jira.public.thoughtworks.org/browse/CC-203 "[#CC-203] Show number of projects on status page"
