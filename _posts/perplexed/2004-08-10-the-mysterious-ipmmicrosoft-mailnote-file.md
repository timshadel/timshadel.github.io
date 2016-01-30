---
title: 'The Mysterious &#8220;IPM.Microsoft Mail.Note&#8221; File'
author: Tim
layout: post
redirect_from: /2004/08/10/the-mysterious-ipmmicrosoft-mailnote-file/
category:  Perplexed
tags:
  - google
  - microsoft
  - solutions
---
My wife has been doing some work for a friend, which has involved some mailing lists and merging. This friend isn&#8217;t very computer savvy, and has obtained these lists from other people lacking in computer knowledge. We have received files in various formats, all with poor field design for this type of work, but tonight was the one that topped them all.

We received a disk with a file named something like `mailing_list.dat`. All attempts to open the file failed. Opening the file in Notepad showed that the file began with this information, including non-printable chars not listed here.

<pre>xŸ>"

ä  è
€ IPM.Microsoft Mail.Note
</pre>

When I got back from work I did some Google digging, and came up with a few potential sites, including one where [Eudora claimed][1]:

> This TNEF information [winmail.dat] is unopenable and irrelevant outside of Outlook.

But I persisted, annoyed again at Microsoft&#8217;s snub of standards, this time causing my wife&#8217;s confused friend to be unable to open her list file.

Then I hit the jackpot. [A post at Google Answers][2] pointed out that while the file was an annoying side effect of the MS Outlook, it could be decoded using a shareware time-limited program available for [free download][3].

I ran the program and out popped a Microsoft Excel spreadsheet, which I happily opened with OpenOffice.

Google really does have all the answers to the messes Microsoft creates. <img src="http://timshadel.com/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />

 [1]: http://www.eudora.com/techsupport/kb/1552hq.html
 [2]: http://answers.google.com/answers/threadview?id=370297
 [3]: http://www.biblet.freeserve.co.uk/
