---
title: 'HttpUnit, HtmlUnit, jWebUnit, DbUnit, and JMeter &#8211; wow!'
author: Tim
layout: post
redirect_from: /2005/02/02/httpunit-htmlunit-jwebunit-dbunit-and-jmeter-wow/
category:  Impressions
tags:
  - dbunit
  - httpunit
  - jmeter
  - jwebunit
  - testing
---
About a year ago, we were using [jWebUnit][1], which is an API built on [HttpUnit][2] — which in turn is very similar to [HtmlUnit][3]. We used it in conjunction with [DbUnit][4] to load the database tables before the test and verify them after. It worked really well. We had tests that could verify the operation properly manipulated the database, and could check the structure of the HTML returned.

We went away from it mainly because functional tests could only be written by programmers with that method, and with [JMeter][5] we could have someone a systems analyst or a tester write the functional tests. Using the proxy recorder available in JMeter let a user click through the test and replay it. JMeter could load the DB and check it based on CSV files, instead of XML. In the end I think the flexibility is a little less, but the number of people who can help get the work done has increased.

 [1]: http://jwebunit.sourceforge.net/
 [2]: http://httpunit.sourceforge.net/
 [3]: http://htmlunit.sourceforge.net/
 [4]: http://www.dbunit.org/
 [5]: http://jakarta.apache.org/jmeter/
