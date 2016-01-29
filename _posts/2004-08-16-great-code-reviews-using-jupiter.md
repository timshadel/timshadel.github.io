---
title: Great Code Reviews using Jupiter
author: Tim
layout: post
redirect_from: /2004/08/16/great-code-reviews-using-jupiter/
category:  Craftsmanship
tags:
  - jupiter
  - Reviews
---
I just finished my first real code review cycle using [Jupiter][1], and I&#8217;m quite happy, to say the least. It&#8217;s quickly becoming something I don&#8217;t want to be without on any future project. Let me back up.

Everyone learns in Software Engineering 101 that code reviews are an excellent way to remove defects from your program. Many people are also introduced to the various types of software reviews, ranging from &#8220;Hey, can you look at this?&#8221; to a formalized code inspection. If you look at either Steve McConnell&#8217;s [Code Complete][2] or Shari Pfleeger&#8217;s [Software Engineering][3], you&#8217;ll find plenty of statistics on how many bizillion defects you can remove by doing code reviews and inspections.

The problem is, that the more formal-style inspections tend to have the biggest positive impact upon the code quality. But nobody has a great way of being formal about it. You don&#8217;t really want to have Author, Scribe, and Reviewer worprocessing templates that you print out and write on. That&#8217;s the technology that the experts suggest. That&#8217;s a pretty fair waste of time, and you don&#8217;t have that luxury on a faster moving small business project.

Enter Jupiter. It&#8217;s an excellent plugin for the Eclipse IDE that provides the more formal-style advantages with a very non-intrusive UI that allows you to conduct reviews that fit your company style. You get all of the record keeping with almost zero hassle.

The tools supports three simple steps, which you can do in any order.

  * Review code by yourself
  * Review code as a team
  * Follow up on identified defects

There&#8217;s really not a lot to this. You ask each of your team members to review your code on their own. They note defects and questions using Jupiter. Jupiter creates one XML file per person (per review session), and they commit that to your version control. Then you get together around one computer, pull the latest files from version control, and talk through the issues everyone found. You can double click on each issue to jump to the code where the suspected defect is. As you talk, you simply note down if the group thinks you should address it now, later, or never (among other choices). Once you finish, commit the files again, and return to your own computer. Pull down the files you updated during your team meeting, and then act on only those that the team thought you should change.

The critical elements are recorded. You can verify that issues were followed up on, and Jupiter is so smooth you never actually notice it during the process. During our experience, the group meeting was focused 100% on code and 15 seconds on the tool. It just worked. So well that no one even brought it up after their first experience. They just used it and we talked about the code.

Now that&#8217;s a well-written tool.

 [1]: http://csdl.ics.hawaii.edu/Tools/Jupiter/
 [2]: http://amazon.com/o/ASIN/0735619670/ref=ase_timshadelcom-20/
 [3]: http://amazon.com/o/ASIN/0130290491/ref=ase_timshadelcom-20/
