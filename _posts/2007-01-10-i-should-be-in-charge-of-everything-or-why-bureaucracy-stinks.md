---
title: I should be in charge of everything, or why bureaucracy stinks
author: Tim
layout: post
redirect_from: /2007/01/10/i-should-be-in-charge-of-everything-or-why-bureaucracy-stinks/
category:  Impressions
tags:
  - big company culture
  - bureaucracy
  - inefficiency
  - non-agile
  - software development
  - waste
---
Today:

  * Release team took 3 hours to respond to the build request I spent all early-morning working on. That made it very late for the QA guy.
  * When we sent an updated release, they asked for us to re-email something we had sent just 1 hour before.
  * I can&#8217;t get a login to my dev machines without going through the generic HelpDesk ticket system. I can&#8217;t select the appropriate party to assign the ticket to. I&#8217;m stuck with no access.
  * I can&#8217;t have more than 100 MB of email space. Today I had to dump all my archived mail to mbox for the 2nd time in one month.
  * I can&#8217;t get access to the hardware load balancer configs without going through the generic HelpDesk ticket system either. I just guessed about where to assign it. It&#8217;s now lost in neverland.
  * The release team doesn&#8217;t own the boxes they build on, so 90 minutes after my second request they were still trying to build but running out of disk space on some partition they had no rights to. They are now planning to build on another machine, and aren&#8217;t interested in my local automated build system&#8217;s binary output. (It&#8217;s all done and even automated on our side, but \_they\_ haven&#8217;t done it yet.)

Other days:

  * I can&#8217;t connect via POP to pull mail from a common mailbox to streamline turning customer requests into JIRA issues.
  * Virus scanners eat gigantic portions of my team&#8217;s CPU cycles, to do nothing useful, effectively reducing the speed of the CPU purchased by the company.
  * They&#8217;re recently installed [BlueCoat][1] and have institutionalized the [Man-In-The-Middle][2] SSL attack for all outgoing SSL traffic.
  * I must write English instructions of how to deploy my application, and then have them executed by a person that has access to the boxes, but very little knowledge of the application. I cannot run any automated commands to accomplish this process.

So today I&#8217;m grumbling because I have a different set of priorities that others in the company. That&#8217;s life, but today I&#8217;m grumbling.

 [1]: http://www.bluecoat.com/
 [2]: http://en.wikipedia.org/wiki/Man_in_the_middle_attack
