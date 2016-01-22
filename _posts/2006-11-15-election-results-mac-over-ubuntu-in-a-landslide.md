---
title: 'Election Results: Mac over Ubuntu in a landslide'
author: Tim
layout: post
permalink: /2006/11/15/election-results-mac-over-ubuntu-in-a-landslide/
categories:
  - Impressions
tags:
  - bluetooth
  - email
  - entourage
  - evolution
  - gtd
  - linux
  - mac
  - macbook pro
  - mail
  - quicksilver
  - ubuntu
---
Just before election day in the US I bought another Mac (a MacBook Pro, Core 2 Duo to be precise) after ditching my Ubuntu laptop. This goes against some of the recent migrations that smart people have been making. Mark Pilgrim [moved][1] from Mac to Ubuntu, as have a few [others][2].

I&#8217;ve read why they switched, and in my experience I&#8217;m voting 100% in the other direction. Why? Well, first some background.

I&#8217;ve been using Linux frequently for 6+ years. I&#8217;ve used Caldera, RedHat, SuSE, Gentoo (extensively), and Ubuntu. Almost all of them were installed on more than one machine, some were desktops and some were servers. Linux has served as my primary all-day-programming desktop for over 18 months. I&#8217;ve been around the block with Linux. I&#8217;m no stranger to compiling, configuring, and kernel stuff. They don&#8217;t intimidate me me.

I&#8217;ve also owned a Mac for two years. In that time I&#8217;ve used it to do some development and some home stuff. I&#8217;ve used it a fair amount. I&#8217;ve used it enough to have problems with it (corrupt disk), and I&#8217;ve used it enough to know that there are some quirks I&#8217;m not fond of (I can&#8217;t hit Tab in the browser and give focus to a checkbox).

Recently, very early this year I installed Ubuntu on multiple machines &#8212; a couple laptops, a desktop, and a remote server. I&#8217;ve used these machines as my primary work and home environments for close to 6 months now. And I&#8217;m ready to move on (at least in my home environment).

Why?

Because things in Ubuntu *almost* work, and on a Mac things Just Work. Ubuntu&#8217;s close enough to working that the &#8220;almost&#8221; takes a few months to fully manifest itself, but in the end I&#8217;m sick of fiddling and I&#8217;d rather move on to just Getting Things Done.

### Hands Down Mac Victories

**Search.** Spotlight nails it. Beagle&#8217;s cool, but it&#8217;s not there. It&#8217;s a wannabe, and it shows. The presentation isn&#8217;t as good. The integration into the &#8220;chrome&#8221; of the operating system isn&#8217;t as smooth. In short, the little barriers to invoking it as well as the slightly less useful results it gave made me abandon it after a couple weeks. On a Mac, I live by Spotlight. And it rarely fails me. On Ubuntu, it *almost* works.

**Mail.** Mail.app is great. Evolution *almost* works. I have to use exchange at work (I have Ubuntu installed there, too). Evolution has a module to integrate with Exchange, and it sorta thinks about working. It&#8217;s slow, and frequently it hangs. So much so that I got sick of typing

`ps -ef | grep evolu | grep -v grep | awk '{ print $2 }' | xargs kill`

that I put it in a <del datetime="2006-11-15T06:09:22+00:00">batch file</del> shell script. I ran it no less than twice a day, sometimes more. Calendaring *almost* worked, except when it didn&#8217;t. Frequently I&#8217;d send out an appointment only to figure out that my colleagues version of the appointment didn&#8217;t repeat over the right interval. I don&#8217;t blame anyone for having trouble integrating with a Microsoft product. But at the end of the day, it was still annoyingly brittle. On Mac, there&#8217;s Entourage &#8212; an M$ product to work with the M$ server. As it is, Mail.app rocks for [processing my personal email really efficiently][3]. Oh, and it *can* export your mail to mbox. Duh. On Ubuntu, mail *almost* works.

**Wireless.** Wireless Just Works on a Mac (providing your router isn&#8217;t ancient). On Ubuntu, it&#8217;s the opposite. If you buy a great machine, your wireless may take months to work. On my work machine, I couldn&#8217;t use the regular Broadcom driver setup, and so I had to resort to `ndiswrapper`. The funny thing is, that once I got it setup, it started the habit of dropping the connection randomly. Sometimes it&#8217;d go 20 minutes, or an hour and a half, or 30 seconds. It was unpredictable. Come to find out, there&#8217;s an IRQ conflict between ndiswrapper and nvidia. A conflict that only the BIOS manufacturer (Dell) can resolve. So if I want to use wireless when working from home, I have to turn off nvidia. If I want the eye candy of Beryl (more on that later) at work, then I have to switch my `xorg.conf` every time my laptop migrates.

**Visual Effects.** Ok. So I love that twirling cube on the Mac. The login box shakes its head at you when you put the wrong password in. The system preferences menu highlights areas that may have what you&#8217;re looking for as you search. Beyond being &#8220;cute&#8221;, these kinds of user interface indications provide [street signs and affordances][4] that anchor the user in a useful mental model of how the system is treating their actions. It reduces both the Gulf of Evaluation and the Gulf of Execution by radiating system state in a creative, intuitive, meaningful way. There seem to be several different combinations of programs and libraries that you can install on Ubuntu to try to bring some of this UI goodness to your Linux desktop. Beryl has been my most recent favorite. But the maze of configuration settings and the massive number of things that can go wrong if you don&#8217;t get something setup quite right are annoying. I had XGL and Compiz setup great on my laptop. Then I did an update one day and everything broke. I had no chrome (close, max, min buttons; resize arrows, etc.) on any of my windows. I dropped back to my normal window manager. I waited. 2 days. 5 days. 3 weeks. Nothing. Meanwhile, my work laptop continued to like Compiz. But then I added an external monitor and then nothing worked. Then Beryl came out. It worked. It fixed both problems, but added others. Configuration still was an intermediate level task. On Ubuntu, the visual effects are mainly eye candy, unstable, and hard to configure. On a Mac, the visual effects are subtle, elegant UI design that Just Works.

**Audio Effects.** Chat doesn&#8217;t blare at you, and the Power On sound is impressive. The sound design shows the same kind of polish as [the Tokyo subway][4]. On Ubuntu, some of the sounds are great but some are lame. The inconsistency an lack of harmony among the components is reminiscent of the PC fragmentation. On Ubuntu, it&#8217;s *almost* sorta there, but not quite. A Mac feels more integrated and unified, in my opinion, and the design standard is clearly on a higher Zen plane.

**Bluetooth.** Bluetooth on the Mac just works. I&#8217;ve had an iMac with a bluetooth keyboard and mouse for over 2 years now. I&#8217;ve used that same iMac to connect to my cell phone and my bluetooth headset. I&#8217;ve pulled pictures off my cellphone, dropped MP3 ringtones onto it, and browsed it&#8217;s directories. Ubuntu&#8217;s support of bluetooth is nothing short of disastrous. There are half baked projects scattered across both Gnome and KDE. Some work, some don&#8217;t. None could connect to my cell phone. Only one could browse part of it. Ubuntu simply gets a failing grade in this area, for sucking the life out of me while I fell down this rabbit hole into the Pit of Despair. On Mac bluetooth Just Works.

### Bonus Points for the Mac

Sadly, I don&#8217;t have time to elaborate on why this things are so cool. You should just buy a Mac, and then you&#8217;d know.

  * [QuickSilver][5]. You can&#8217;t understand how cool this is by simply reading.
  * Magnetic battery connection. It&#8217;s like moving to a mouse with a scroll wheel &#8212; you have to experience it.
  * [Scriptability][6].
  * I can boot off another device. Like, say, another Mac in Firewire-mode.
  * Movie editing. No, real movie editing.
  * iPod+iTunes. (amaroK is lame, iTunes is QuickSilver enabled)
  * Open formats. Most things speak the open formats I care about.
  * Two finger right click + horizontal scroll. Yup, experience required to feel the cool factor.

### Stuck on Windows

**Visio.** There&#8217;s nothing on Ubuntu that lets me read files written by Visio. Oh, and VMWare <ins datetime="2006-11-21T05:21:53+00:00">on Linux</ins> *almost* works. Except their website process for downloading the free server edition requires me to re-register every time I need to download. And it requires strange root access. At it can&#8217;t boot the physical partition where my real Windows data is. And I&#8217;d have to ask support to register my virtual instance with the domain controller so they could conceivably remotely install Visio on my virtual instance. Nope, gotta keep the dual boot. In fact, this has actually pushed me more toward staying in Windows on the work machine.

### Conclusion

My reasons for choosing to dump Ubuntu for a Mac are almost entirely about the experience. After years of Linux work, I&#8217;m tired of fiddling. I&#8217;m tired of things that almost *work*. I&#8217;m ready for a change. I&#8217;m sick of the war to get things to work. I&#8217;m ready to simply Get Things Done.

Cast your vote.

 [1]: http://diveintomark.org/archives/2006/06/02/when-the-bough-breaks
 [2]: http://www.intertwingly.net/blog/2006/06/27/Nonconformity
 [3]: http://www.43folders.com/topics/mail.app/
 [4]: http://www.boxesandarrows.com/view/ambient_signifi
 [5]: http://www.43folders.com/topics/quicksilver/
 [6]: http://clarkware.com/cgi/blosxom/2006/10/24#RubyOSA
