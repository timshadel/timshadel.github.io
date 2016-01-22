---
title: Converting Bloxsom entries to Pebble
author: Tim
layout: post
permalink: /2004/08/09/converting-bloxsom-entries-to-pebble/
categories:
  - News
tags:
  - bash
  - blosxom
  - pebble
---
Well, so far it&#8217;s been a bit of a slow process to bring over my old entries from [blosxom][1] to [Pebble][2]. Both use files to track blog entries, but blosxom uses plain text files (with implicit meaning attached to certain items) and Pebble uses <acronym title="eXtensible Markup Language">XML</acronym>.

#### Creating XML templates

I started by taking an existing entry and building a header and footer to wrap the contents of the blosxom files. Pebble uses `` sections to wrap the entry bodies — great for what I had to do. I copied each entry to it&#8217;s Pebble date folder. Then I wrote a script to run in each folder and add the <acronym title="eXtensible Markup Language">XML</acronym> template around the blosxom entry. This little shell script seemed to do a decent job.

<pre></p>



<h1>
  !/bin/bash
</h1>



<p>
  for i in *.txt; do
          cat /path/to/head.tmp > ${i%.txt}.xml;
          cat $i >> ${i%.txt}.xml;
          cat /path/to/foot.tmp >> ${i%.txt}.xml;
  done
  </pre>
  
</p>


<p>
  With that done, the next steps I had to do included moving the title line from the blosxom entry to the <code>&lt;title/></code> tag in the Pebble entry file, update the date to reflect the entry date, and rename the file using Pebble standards.
</p>


<h4>
  The Big Date Mess
</h4>


<p>
  Perhaps the biggest challenge has been to get the entry dates correct.  One of the biggest reasons I left blosxom was the way their dates were stored.  They simply used the last modified time of the file.  This didn&#8217;t provide me any flexibility to (easilty) make a punctuation change later and have the entry still hold the original date.  I used some tools that preserved the date, but I didn&#8217;t like them.  Pebble stores the date directly in the <acronym title="eXtensible Markup Language">XML</acronym> file.
</p>


<p>
  I didn&#8217;t want to write anything complicated, I just wanted to get my 15 or so entries converted, and was (unusually) willing to do it somewhat by hand.  So I needed a way to easily get the file times.  I dug around and found this:
</p>


<p>
  <pre>
   # ls --full-time
</pre>
  
</p>


<p>
  It shows a bit more than I needed, but gives me what I need to know.
</p>


<h4>
  Fixing Filenames
</h4>


<p>
  Next I needed to know how Pebble chose the filename.  I thought it was related to the date, and I found the code that was responsible for setting the <code>BlogEntry id</code> field.
</p>


<p>
  <pre>
    // blank out the milliseconds
    Calendar cal = dailyBlog.getRootBlog().getCalendar();
    cal.setTime(date);
    cal.set(Calendar.MILLISECOND, 0);</p>



<pre><code>this.date = cal.getTime();
this.id = "" + this.date.getTime();
</code></pre>
</p>


<p>
  With this information, I was ready to start editing the hastily templated files I created earlier.  In one sweep I would find the file's creation date, sweep the title to its rightful element, and then added the date into the required element.  Afterwards, I'd rename the file using the same date format I'd copied into the <acronym title="eXtensible Markup Language">XML</acronym> file.
</p>


<p>
  <pre>
    mv FileName.xml <code>date --date "23 Dec 2003 10:32:48 MST" +%s</code>000.xml
</pre>
  
</p>


<p>
  Because <a href="http://www.simongbrown.com/" title="Simon Brown's Weblog">Simon</a> eliminated the milliseconds from the filename, it works well with the <code>date</code> utility which can print seconds from 1970 to the given date.  I simply added three zeros to the end to make a compatible filename.
</p>


<p>
  After that point, I simply load up Pebble, and make sure that the entries appear correctly, and that all the permalinks work — the behavior makes me think that the permalink is calculated from the date in the entry file, and not the location that the file was loaded from for processing.  This means that if your date in the entry file doesn't match the location and name then you'll probably have a nice looking <code>404 File Not Found</code> message.
</p>


<p>
  This created an unusual question for me in one case.  I had an entry that was created in the wrong time zone.  When I figured out what time the entry was created in my timezone, I switched the time and the time zone recorded for that entry.  The UTC time was the same, so the filename did not change.  However, Pebble couldn't locate that particular file.  When I inspected the link, though, I noticed that the day had changed and that I needed to move the file from one day folder to the other for Pebble to find it.  In Pebble, entries are stored in the "day" folder according to the day indicated by their <code>&lt;date/></code> element, and not the UTC day.
</p>


<h4>
  Conclusion
</h4>


<p>
  Hopefully this quick description gives rise to efforts by people much smarter than me on using either tool.  I had glimpses of using Pebble's objects from a standalone application to construct the <code>BlogEntry</code> objects (and eliminate the tedious hand mangling of dates) and even use the Pebble objects to write the <acronym title="eXtensible Markup Language">XML</acronym> files.  Perhaps you could also write something in Java that would know how to read special tags in blosxom.  I never used many, so I'll do the one or two by hand.  I also chose not to deal with categories.  I can reconstruct those by hand as well, but a major conversion would benefit from automatically populating them into the new entry files.  A tool like this would definitely be needed to convert a sizeable history of a blog to the Pebble data format.  If you know of a tool that does, drop me a line or comment here.  Thanks!
</p>

 [1]: http://www.blosxom.com/ "Home page for the blosxom weblog tool"
 [2]: http://pebble.sourceforge.net "Home page for the Pebble weblog tool"
