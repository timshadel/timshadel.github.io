---
title: 'JMS Error &#8216;ctor&#8217;'
author: Tim
layout: post
permalink: /2004/08/25/jms-error-ctor/
categories:
  - Perplexed
tags:
  - jms
  - solutions
  - spring
---
I&#8217;m trying out the [Spring JMS support in the 1.1 RC2 release][1]. So far I&#8217;m pretty impressed, but that&#8217;s something I&#8217;ll delve into another time. While I was running my tests from the Eclipse JUnit test runner, I got the following exception: 

<pre>org.springframework.jms.UncategorizedJmsException: 
Uncategorized exception occured during JMS processing; nested exception is javax.jms.JMSException: ctor
javax.jms.JMSException: ctor
    at com.evermind.server.jms.JMSUtils.makeJMSException(JMSUtils.java:1829)
    at com.evermind.server.jms.JMSUtils.toJMSException(JMSUtils.java:1845)
    at com.evermind.server.jms.EvermindObjectMessage.&lt;init>(EvermindObjectMessage.java:64)
    at com.evermind.server.jms.EvermindSession.makeMessage(EvermindSession.java:1405)
    at com.evermind.server.jms.EvermindSession.createObjectMessage(EvermindSession.java:276)
    at com.example.myproject.JmsSender$1.createMessage(JmsSender.java:59)
    at org.springframework.jms.core.JmsTemplate.doSend(JmsTemplate.java:566)
    at org.springframework.jms.core.JmsTemplate$2.doInJms(JmsTemplate.java:547)
    at org.springframework.jms.core.JmsTemplate.execute(JmsTemplate.java:512)
    at org.springframework.jms.core.JmsTemplate.execute(JmsTemplate.java:524)
    at org.springframework.jms.core.JmsTemplate.send(JmsTemplate.java:545)
        [...]
&lt;/init></pre>

The original message (not from Spring) `ctor` was incredibly vague, so I decided to follow a hunch. I applied the [serialization testing advice][2] from one of my recent posts to this new project, <span lang="fr"><em>et voilà</em></span>, my error was immediately uncovered. One of the two items in my `Message` object was not `Serializable`. A quick update and I was happily sending JMS messages using the Spring template.

 [1]: http://www.springframework.org/news.html#1.1RC2 "ANNOUNCEMENT: Spring Framework 1.1 Release Candidate 2 is available"
 [2]: http://timshadel.com/blog/2004/08/18/1092869770000.html "Testing Out Serialization Gotchas"
