---
title: '[Ruby] GroupWise export to iCal'
author: Tim
layout: post
redirect_from: /2005/12/14/ruby-groupwise-export-to-ical/
category:  How-To
tags:
  - glue
  - groupwise
  - ical
  - integration
  - ole
  - ruby
  - win32
---
**UPDATE:** I&#8217;ve posted a more complete version of this code in [More Ruby Exporting of Groupwise to iCal][1].

I&#8217;ve wanted to export my Groupwise calendar to iCal format for a long time. Every time I try to do it, I ended up running into the [same][2] [few][3] pages. They sorta worked, but were clumsy.

So I threw this little beauty together in under 10 minutes and 2 google searches. It seems to be a start, though I expect to improve it. [Groupwise Object API Docs][4] (PDF format; the web version keeps blinking &#8212; arrrgh) from Novell were useful, as was [this Ruby gem][5].

{% highlight ruby %}
require 'win32ole'
require 'icalendar'

groupwise = WIN32OLE.new("NovellGroupWareSession")
# 2nd arg is not password, so leave blank
account = groupwise.Login("your-username", "")
path_to_host = account.PathToHost
cal = Icalendar::Calendar.new
account.Calendar.Messages.each do |message|
  next unless message.ClassName == "GW.MESSAGE.APPOINTMENT"
  event = cal.event  # This automatically adds the event to the calendar
  event.user_id = "tims@asrs.state.az.us"
  event.timestamp = DateTime.now
  event.summary = message.subject.PlainText
  event.description = message.BodyText.PlainText
  event.start = message.StartDate
  event.end = message.EndDate
end

puts cal.to_ical
{% endhighlight %}


Every day I find more reasons to love using Ruby.  Enjoy!

 [1]: http://timshadel.com/2007/01/19/more-ruby-exporting-of-groupwise-to-ical/
 [2]: http://helpdesk.doit.wisc.edu/page.php?cat=1003&id=2914 "WiscCal - Importing GroupWise Data into My Calendar"
 [3]: http://www1.umn.edu/umcal/support/GuideBook/Conversion-GW.html "GroupWise to UMCal Conversion"
 [4]: http://developer.novell.com/ndk/doc/gwobjapi/pdfdoc/gwobjenu/gwobjenu.pdf
 [5]: http://icalendar.rubyforge.org/ "iCalendar"
