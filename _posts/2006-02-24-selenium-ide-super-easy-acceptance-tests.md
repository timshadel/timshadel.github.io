---
title: 'Selenium IDE: Super Easy Acceptance Tests'
author: Tim
layout: post
permalink: /2006/02/24/selenium-ide-super-easy-acceptance-tests/
categories:
  - How-To
tags:
  - firefox
  - screencasts
  - selenium
  - selenium-ide
  - testing
---
[Selenium][1] is an excellent open source tool to test your website automatically, right from your browser. The test scripts are written as plain HTML files, which makes them easy to read, edit, and understand. BUT, it&#8217;s even easier than that. There&#8217;s an IDE for developing these tests. 

We used to use [a different tool][2], but we found one that&#8217;s *MUCH* better. It&#8217;s called [Selenium IDE][3]. It&#8217;s a plugin to [Mozilla Firefox][4]. You can watch [this video][5] about how easy it is to record Selenium tests with Selenium IDE. 

#### Install Selenium IDE

Once you&#8217;re ready to start, you can [download Selenium IDE][6]. (When you click, you&#8217;ll see a yellow bar near the top of the page that says Firefox requires you to allow Extensions to be installed from openqa.org. Click the `Edit Options...` button to allow the installation.) 

#### Glimpse the Future

These automated tests are great, but sometimes we have trouble because they rely on specific data. [This video][7] shows an example of what is possible. The example is done in Ruby, so try to ignore that part if you&#8217;re not comfortable with Ruby. Watch, though, as it moves into automated acceptance tests that setup the database, click through the application, and do it in both Firefox and Internet Explorer. This is the vision that we have for automated acceptance testing. Enjoy.

 [1]: http://www.openqa.org/selenium/ "Selenium (by ThoughtWorks)"
 [2]: http://seleniumrecorder.mozdev.org/
 [3]: http://www.openqa.org/selenium-ide/
 [4]: http://getfirefox.com
 [5]: http://wiki.openqa.org/download/attachments/400/Selenium+IDE.swf?version=1 "Flash demo video for Selenium IDE"
 [6]: http://www.openqa.org/selenium-ide/download.action
 [7]: http://andthennothing.net/archives/2006/02/20/show-dont-tell "Show, don't tell"
