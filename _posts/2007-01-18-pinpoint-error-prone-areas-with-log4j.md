---
title: Pinpoint error prone areas with log4j
author: Tim
layout: post
redirect_from: /2007/01/18/pinpoint-error-prone-areas-with-log4j/
categories:
  - How-To
tags:
  - chainsaw
  - error
  - grep
  - jboss
  - log4j
  - sed
  - sort
  - uniq
---
Building internal IT systems is as much about the data that passes through your application as it is about the logic that operates on it. I&#8217;ve scanned log files of web servers for years. I often use a combination of `grep`, `sed`, and other tools to look into specific problems. These are often one-off curiosities that don&#8217;t require a [GUI][1].

Since before taking over management of this team in July, our app has had some long-running cases where we see ERROR level items in our logs. Some I question whether they should be logged as errors, while some are disconcerting. The application works well overall, but in the spirit of No Broken Windows I&#8217;d like to clean up some of the sources of these errors.

Here&#8217;s a little snippet of the JBoss log file, showing some standard log output from Hibernate:

{% highlight sh %}
Jan 18 00:00:59 devserver local6:[00:00:59,182,SettingsFactory] INFO  Query cache factory: org.hibernate.cache.StandardQueryCacheFactory
Jan 18 00:00:59 devserver local6:[00:00:59,213,SettingsFactory] INFO  Statistics: disabled
Jan 18 00:00:59 devserver local6:[00:00:59,217,SettingsFactory] INFO  Deleted entity synthetic identifier rollback: disabled
Jan 18 00:00:59 devserver local6:[00:00:59,221,SettingsFactory] INFO  Default entity-mode: pojo
Jan 18 00:00:59 devserver local6:[00:00:59,331,SessionFactoryImpl] INFO  building session factory
Jan 18 00:01:00 devserver local6:[00:01:00,509,CacheFactory] WARN  read-only cache configured for mutable class: Address
Jan 18 00:01:00 devserver local6:[00:01:00,513,EhCacheProvider] WARN  Could not find configuration [Address]; using defaults.
Jan 18 00:01:02 devserver local6:[00:01:02,315,SessionFactoryObjectFactory] INFO  Not binding factory to JNDI, no JNDI name configured
Jan 18 00:01:02 devserver local6:[00:01:02,323,UpdateTimestampsCache] INFO  starting update timestamps cache at region: org.hibernate.cache.UpdateTimestampsCache
{% endhighlight %}

After a minute or two I formulated this little command-line string to give me a count of the classes that had the most errors:

{% highlight sh %}
grep ERROR jboss.log | sed -e "s/^.,(.)] .*$/\1/" | sort | uniq -c
{% endhighlight %}

This cuts through the log file, locates only errors, slices out the classname from the log message, sorts the remaining list, and then counts up the number of times each classname appears in the sorted list.

{% highlight sh %}
 4 LegacySkimmer
 4 PersistentRef
21 ProgramStateExclusionDaoImpl
 8 QualifyLeadsDelegate
28 RDBQualifyLeadsDAO
 2 SSOLogger
 1 ShowNextLeadAction
 3 [action]
{% endhighlight %}


Interpreting these results can be a bit tricky. I take it really informally. This doesn&#8217;t represent the number of bugs in the modules, or even the classes with the most software defects. For me, this is simply a list that shows from among the classes that do log errors, which classes have experienced conditions that trigger those error logs most frequently. For our setup, that usually means that there&#8217;s some data from another system coming in that doesn&#8217;t meet some assumptions. Other causes may include intermittent connection problems to other systems that just get noticed on one part of the code.

I&#8217;m not certain of the exact outcomes that will result from this little discovery exercise, but I&#8217;m betting that our code will be a bit cleaner and a bit more robust for it.

 [1]: http://logging.apache.org/log4j/docs/chainsaw.html
