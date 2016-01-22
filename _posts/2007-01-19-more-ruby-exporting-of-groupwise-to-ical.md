---
title: More Ruby Exporting of Groupwise to iCal
author: Tim
layout: post
permalink: /2007/01/19/more-ruby-exporting-of-groupwise-to-ical/
categories:
  - How-To
---
One of my most frequently requested posts is [my initial exploration][1] into using Ruby to export my Groupwise calendar to iCal format. The code I posted there was simple, and it *almost* worked. I figured that&#8217;d be the jumping off point for a lot of people to dive in and explore the options Ruby has from there. In retrospect, though, I should also have posted my final version that I worked out a few weeks later.

So now I&#8217;d like to introduce [timshadel.com/code][2]. It&#8217;s the start of a simple public Subversion repository where I can share my half-baked code ideas, and where you could watch some of my ideas evolve over time. I&#8217;ve run across several small scripts and even medium-sized projects that I figured might be worth sharing, not because they&#8217;re stellar code showing the best kind of professional attention to detail, but because there was some aspect about them that I thought was fun to play with and I always like to see examples to start with when I&#8217;m investigating a new topic.

So, without further ado, proceed to the [full version of my script][3] that turns Groupwise calendars into *working* iCal files. Please note that I no longer use Groupwise, so I&#8217;m not likely to make any more improvements to it, but as it stands it should be able to dump not only your appointments, but the attendees and their email addresses into a format that even [Google Calendar][4] can read. Also note that Google Calendar may send reminders to your invitees; so watch out.

If you&#8217;ve got comments or improvements, feel free to share them in the comments.

 [1]: http://timshadel.com/2005/12/14/ruby-groupwise-export-to-ical/
 [2]: http://timshadel.com/code "Tim Shadel's Public Code Repository"
 [3]: http://timshadel.com/code/tidbits/gw2ical.rb
 [4]: http://google.com/calendar
