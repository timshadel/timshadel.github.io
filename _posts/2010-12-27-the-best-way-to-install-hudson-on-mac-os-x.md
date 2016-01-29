---
title: The Best Way to Install Hudson on Mac OS X
author: Tim
layout: post
redirect_from: /2010/12/27/the-best-way-to-install-hudson-on-mac-os-x/
categories:
  - How-To
tags:
  - build
  - ci
  - continuous integration
  - homebrew
  - hudson
  - install
  - iphone
  - mac
  - osx
---
For the short-attention spans (like mine):

    brew install hudson


OK. <ins datetime="2010-12-28T03:10:36+00:00">That should work now.</ins> <del datetime="2010-12-28T03:10:36+00:00">That may not work&#8230;yet. There are details after the jump for those who don&#8217;t want to wait for <a href="https://github.com/mxcl/homebrew/pull/3706">the pull request</a> to go through.</del> Oh, and read the directions after running that command to get it to launch automatically.

<ins datetime="2010-12-28T03:10:36+00:00"><strong>UPDATE:</strong> <a href="http://github.com/mikemcquaid">mikemcquaid</a> was super fast and the changes are merged. Read the details below for more info both on what happens, the basic approach, and how you can <code>brew install</code> your own version.</ins>

<!--more-->

For some reason I&#8217;ve had a thing for making [Hudson][1] easier to install. Several years ago I wrote the [3-minute setup guide][2] which the fantastic maintainer [Kohsuke Kawaguchi][3] turned around and [rolled directly into Hudson][4]. I don&#8217;t think I&#8217;ve touched any other CI system since (for anything beyond a quick test drive). The configuration management group at my current workplace uses that very direct self-executing hudson version to run a couple dozen production build servers; I didn&#8217;t have anything to do with that decision, it was just simple.

So, nearly 4 years later, I&#8217;ve been looking around at how to automate iPhone builds. My [Waterlogged app][5] has been in the AppStore for almost a year, and has covered quite a bit of ground in feature growth in that time. It&#8217;s reasonably mature, while still fairly small as far as the code goes. I finally picked up a mid-2009 Mac mini with the intent of making it into a build server. I&#8217;ve found a number of ideas about [how to automate][6] [iPhone app builds][7] and [over-the-air beta deployments][8], as well as how to add [automatic][9] [testing][10] [to][11] that build. The first thing obviously seemed to be to install Hudson on my Mac mini.

So, all the cool tool installation on Mac these days is done with [Homebrew][12]. But `brew info hudson` left me with nothing. So I rolled up my sleeves in the evening on this Christmas Day (with kids not quite in bed yet) and started to take a crack at it. I wanted Hudson installed in a default location; no thinking required. And I wanted it so that when the mini rebooted, Hudson came up automatically. That meant I needed a LaunchDaemon. After finding a few really bad ideas out there, I came across Jérôme Renard&#8217;s simple plist file. I combined that with the basics from the mongodb Homebrew Formula, and the conventions I saw in the results from the grails install, and cobbled together a first draft of the Hudson install.

It&#8217;s probably less-than-ideal, but I figured I&#8217;d ship the first version, request a pull, and then let the magic of git and crowds perfect it over time. I created the Formula on my Air, pushed to GitHub, then with a few commands on my mini,



I was ready to install my own Formula.



and it launches now, and is setup to launch any time my user logs in. I hit it in the browser, and it came back just fine.

<img src="http://timshadel.com/wp-content/uploads/2010/12/hudson.png" alt="" title="hudson" width="550" height="359" class="aligncenter size-full wp-image-342" />

Notice that if my pull request gets merged in soon, the first part just drops off and you get left with just 3 commands:



and the bottom two are given to you when you run the first one. So in the end, all you need is

    brew install hudson


Which is where we started&#8230; Merry Christmas, and Happy Building on your Mac!

 [1]: http://hudson-ci.org
 [2]: http://timshadel.com/2007/02/08/try-hudson-instead-of-cruisecontrol-the-3-minute-setup/
 [3]: http://www.hudson-labs.org/content/about-hudson-labs
 [4]: http://weblogs.java.net/blog/kohsuke/archive/2007/02/hudson_became_s.html
 [5]: http://bit.ly/a4qn3x
 [6]: http://nachbaur.com/blog/how-to-automate-your-iphone-app-builds-with-hudson
 [7]: http://blog.octo.com/en/automating-over-the-air-deployment-for-iphone/
 [8]: http://stackoverflow.com/questions/2415161/over-the-air-deployment-of-iphone-app
 [9]: http://pivotallabs.com/users/amilligan/blog/articles/1321-iphone-ui-automation-tests-with-jasmine
 [10]: https://github.com/pivotal/cedar
 [11]: http://alexvollmer.com/posts/2010/07/03/working-with-uiautomation/
 [12]: http://mxcl.github.com/homebrew/
