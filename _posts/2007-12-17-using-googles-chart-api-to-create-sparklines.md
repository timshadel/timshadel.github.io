---
title: 'Using Google&#8217;s Chart API to Create Sparklines'
author: Tim
layout: post
permalink: /2007/12/17/using-googles-chart-api-to-create-sparklines/
categories:
  - How-To
tags:
  - analytics
  - api
  - chart
  - colt
  - google
  - metrics
  - sparkline
  - statistics
---
Just a couple weeks ago [I was wondering][1] how Google made its [sparklines for Google Analytics][2]. I was creating a Health Page of sorts for my application (a rudimentary listing of recent performance statistics, like how long it took to get a DB connection). I had designed my stats collection piece to keep track of data over the last 15 minutes or so, hoping to show a chart of recent activity when I hit my health page. I had plugged in the [Colt statistics library][3] to perform some calculations on the set of measurements in each minute. I had a lot of data points ready to display.

But I didn&#8217;t like how the [Java Sparklines library][4] worked, and I couldn&#8217;t see an easy way to mimic Google. Then just a short time later, they released their [Chart API][5]. So this morning I put my data into their API and the charts came out pretty decent (ignoring the fonts, decimal formatting, and alignment of my other stuff):

![Sparklines using Google's Chart API][6]

I can&#8217;t figure out how to get rid of the x and y axes entirely. I mimicked the [Analytics][7] chart size of 75&#215;18 (or thereabouts), and it&#8217;s close. The Analytics charts also seem to have a minimum 2px buffer of fill along the bottom, so even 0 has some fill below it. They also seem to auto-size so the max measurement it at the top. There are several ways to refine what I&#8217;ve started with, but for an admin page that&#8217;s full of 80-150 charts, and only viewed by a few people, it&#8217;s a decent start.

Please leave a comment if you&#8217;ve got any tips on how you use Google&#8217;s Chart API to create [sparklines][8].

 [1]: http://twitter.com/timshadel/statuses/411633902
 [2]: http://www.flickr.com/photos/timshadel/2003400791/
 [3]: http://dsd.lbl.gov/~hoschek/colt/
 [4]: http://www.representqueens.com/spark/
 [5]: http://code.google.com/apis/chart/
 [6]: http://timshadel.com/wp-content/uploads/2007/12/2110517181_1e7c88c4f1.jpg?v=0
 [7]: http://analytics.google.com
 [8]: http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0001OR
