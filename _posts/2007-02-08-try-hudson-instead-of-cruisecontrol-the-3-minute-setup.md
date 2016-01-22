---
title: 'Try Hudson Instead of CruiseControl: The 3 Minute Setup'
author: Tim
layout: post
permalink: /2007/02/08/try-hudson-instead-of-cruisecontrol-the-3-minute-setup/
categories:
  - Craftsmanship
---
  1. Download [winstone][1] from it&#8217;s [Sourceforge Files page][2]
  2. Download the [Hudson][3] war file from its [Java.net Release page][4]
  3. Then run `java -jar winstone-0.9.6.jar --warfile=hudson.war --httpPort=8081`
  4. You should [see][5] something like the screenshot below.
  5. Play.

![Hudson screenshot][6]

One of my favorite features of Hudson is the ability to watch the console output of a build in progress, like this one:

![Hudson console output][7]

Other cool things include:

  * No more messing around with XML
  * I can setup a Hudson job and use it to run `mvn release:clean release:prepare` on my branch code. (Haven&#8217;t tried this beyond tinkering yet, though. Could possibly be manual or nightly job it seems.)
  * It&#8217;s easy to have several builds for different branches and see them all at once.
  * There&#8217;s a really cool build history graph that shows both the time it took to build each release, and whether it passed or failed &#8212; makes it easy to see your build trends on the team.

I&#8217;m looking forward to investigating it&#8217;s publishing of Javadoc and JUnit test results. I also want to see if it&#8217;ll do anything with Maven&#8217;s site generation. If so, that&#8217;d be a big win. I&#8217;ve fiddled with [Continuum][8], but this just feels like a better setup to me, and the author seems eager to add Maven2 integration to it.

After having it around for a couple weeks, I&#8217;ve tentatively switch our build to use it. It&#8217;s just so easy to turn on, that it seems like a no brainer. If it doesn&#8217;t pan out then we can always turn CruiseControl back on, but I don&#8217;t anticipate that outcome. Something else I might try is to drop Hudson into Tomcat if winstone seems to strain, but I don&#8217;t think we&#8217;ll need that either. It&#8217;s built our stuff plenty fast in that little servlet container for a few weeks now, so I&#8217;m not anticipating any load increase to it &#8212; simply more publicity for it among our team.

Try it out. Let me know if you think it&#8217;s worth the switch.

 [1]: http://winstone.sourceforge.net/
 [2]: http://sourceforge.net/project/showfiles.php?group_id=98922
 [3]: https://hudson.dev.java.net/
 [4]: https://hudson.dev.java.net/servlets/ProjectDocumentList?folderID=2761&expandFolder=2761&folderID=0
 [5]: http://localhost:8081
 [6]: http://timshadel.com/wp-content/uploads/2007/02/383688861_9230235159_d.jpg
 [7]: http://timshadel.com/wp-content/uploads/2007/02/383693600_5fd9106052_d.jpg
 [8]: http://maven.apache.org/continuum/
