---
title: DB connection problems? Try a logging datasource!
author: Tim
layout: post
permalink: /2007/02/20/db-connection-problems-try-a-logging-datasource/
categories:
  - How-To
tags:
  - datasource
  - debugging
  - hibernate
  - java
  - jdbc
  - log4j
  - logging
  - spring
---
We&#8217;ve been grappling with a number of different problems with our app over the last week. We&#8217;ve made many improvements, including several changes to our Spring configs (which I may touch on another day), but we still had a problem where occasionally we ran out of database connections momentarily &#8212; no matter how many we had in the pool to start with.

So the other morning I got an itch to start coding while I was waiting for my carpool ride to show up. By the time I got to work, I had a rough draft of something I wanted to try out. It&#8217;s a simple [logging DataSource][1]. We converted our datasource to one driven by Spring a couple months ago, but we still have a combination of straight JDBC, an old custom in-house ORM tool, and Hibernate. Somewhere among them, we&#8217;ve got something occasionally misbehaving.

It&#8217;s a pretty simple concept. I decided to extend Spring&#8217;s [DelegatingDatasourceProxy][2] to make my [LoggingDataSource][3]. Configuration is just as simple as changing this:

{% highlight xml %}
<jee:jndi-lookup id="dataSourceTarget" jndi-name="java:/MyJbossDS"/>
{% endhighlight %}

to this:

{% highlight xml %}
<bean id="dataSource" class="com.timshadel.util.LoggingDataSource">
    <property name="targetDataSource" ref="dataSourceTarget"/>
    <property name="filterPattern" value="^(com.timshadel|com.example).*"/>
</bean>

<jee:jndi-lookup id="dataSourceTarget" jndi-name="java:/MyJbossDS"/>
{% endhighlight %}

When you turn it on, you might see something like this:

{% highlight sh %}
[main] INFO  com.timshadel.util.LoggingDataSource  - Connection request stack trace, filtered by '^(com.timshadel|com.example).'
        com.example.myapp.model.MyClass.determineSomethingImportant(MyClass.java:770)
        com.example.myapp.model.MyClass.updateStatusString(MyClass.java:674)
        com.example.myapp.model.MyClass.loadStatusInfo(MyClass.java:643)
        com.example.myapp.model.MyClass.reloadStatusInfo(MyClass.java:332)
        com.example.myapp.util.helper.LegacyHelper.run(LegacyHelper.java:440)
[main] ERROR com.timshadel.util.LoggingDataSource  - Connection request stack trace, filtered by '^(com.timshadel|com.example).'
        CAUGHT EXCEPTION (java.sql.SQLException): Pretend there's no more connections.
        com.example.myapp.model.MyClass.determineSomethingImportant(MyClass.java:770)
        com.example.myapp.model.MyClass.updateStatusString(MyClass.java:674)
        com.example.myapp.model.MyClass.loadStatusInfo(MyClass.java:643)
        com.example.myapp.model.MyClass.reloadStatusInfo(MyClass.java:332)
        com.example.myapp.util.helper.LegacyHelper.run(LegacyHelper.java:440)
{% endhighlight %}

All of the stacktrace lines have been removed except those that match your pattern.  This is helpful to make sure you cut through <a href="http://ptrthomas.wordpress.com/2006/06/06/java-call-stack-from-http-upto-jdbc-as-a-picture/">a typical enterprise Java call stack</a> to only show the calls your code is making.  For us that was helpful as a poor man&#8217;s way to determine which pieces of our code were using connections frequently.  One simple run turned up a few hotspots.  If we need to dig in a bit more, perhaps we&#8217;ll throw together a simple Ruby script to count how often a given call stack shows up in the log.

Also note, that since this puts the info out to Log4j, you can obviously pull this logging out to a completely separate file, set a different threshold, or use any of the other standard Log4j features to capture this information in a way that&#8217;s useful to you.

Finally, please remember that I pulled lots of this together while riding to work.  It&#8217;s not really meant to be used for anything serious.  Please expect warts and problems, but hopefully it&#8217;s enough to help get you goin&#8217;.

 [1]: http://timshadel.com/code/small/logging-datastore/
 [2]: http://static.springframework.org/spring/docs/2.0.x/api/index.html?org/springframework/jdbc/datasource/DelegatingDataSource.html
 [3]: http://timshadel.com/code/small/logging-datastore/src/main/java/com/timshadel/util/LoggingDataSource.java
