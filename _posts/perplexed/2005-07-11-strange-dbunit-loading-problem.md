---
title: Strange DBUnit Loading Problem
author: Tim
layout: post
redirect_from: /2005/07/11/strange-dbunit-loading-problem/
category:  Perplexed
tags:
  - dbunit
  - solutions
  - testing
---
I use DBUnit to setup my database for test cases. Right now, I&#8217;m running HSQL in its &#8220;in memory&#8221; mode as the database. I&#8217;m using Hibernate mappings to connect my objects to the database, and I&#8217;ve got my Spring/Hibernate configuration setup to drop and create the tables at the beginning of my test run (and only once for all tests). I kept running into a problem with foreign keys, though. I couldn&#8217;t get past it, and no amount of wrestling with my mapping file eliminated my `"Integrity constraint violation"`.

I tracked it down eventually to my DBUnit file. I have a Composite pattern in one of my objects, so items in the Chart table have a parent that is also a Chart; but the root element has no parent. The first record in my XML file referred to a parent that was later in the file. I swapped the records around so that they were all created in the right order. No problem. Run the tests, no error, but my test fails. NullPointerException. Hmm.

Another while of head-banging and incantations leads nowhere. So I decided to swap from in-memory DB to an actual DB I can look at. Thankfully, that&#8217;s pretty easy. I fire up an HSQLDB server instance inside Eclipse, and swap the comment on this line in my Spring properties file&#8230; (More about my environment another time, this is a bug hunt!)

{% highlight sh %}
dataSource.url=jdbc:hsqldb:mem:account
#dataSource.url=jdbc:hsqldb:hsql://localhost:1701/
{% endhighlight %}

Now I can easily see that none of the <code>PARENT_ID</code> colums are being populated.  That&#8217;s really odd.  So I fiddle a bit, and decide to add a parent reference to my root node to point to itself, <span lang="fr"><em>et voilà</em></span>.  All of my parent references suddenly appear.  Make the root one null again; they&#8217;re all gone.  So I scratch my head for a bit, and then I make a guess.

DBUnit&#8217;s FlatXmlDataset requires you to <em>eliminate</em> a column if you want it left null.  But it appears that it uses the first record&#8217;s data to fully define the schema it&#8217;ll use when creating its eventual insert sequence.  I need that column to be null.  And I need that record to be first.  What to do?  I decided to embed a DTD right in my xml dataset.  I ran over to <a title=" How to generate a DTD representing my database schema" href="http://www.dbunit.org/faq.html#generatedtd">the right entry in the FAQ</a> and quickly got a DTD for my database schema.  Then I modified my xml dataset to look like this:

{% highlight xml %}
<?xml version='1.0' encoding='UTF-8'?>
<!DOCTYPE dataset
    [

<!ELEMENT dataset (
    CHART*)>
<!ELEMENT CHART EMPTY>
<!ATTLIST CHART
    ID CDATA #REQUIRED
    PARENT_ID CDATA #IMPLIED
    CHART_NUMBER CDATA #REQUIRED
    DESCRIPTION CDATA #REQUIRED
    OPEN_DATE CDATA #REQUIRED
    CLOSE_DATE CDATA #IMPLIED
>
    ]>

<dataset>
  <chart ID='12' CHART_NUMBER='12000' DESCRIPTION='Simple description' OPEN_DATE='2004-01-01 00:00:00.0'/>
  <chart ID='15' CHART_NUMBER='12100' PARENT_ID='12' DESCRIPTION='Sub chart' OPEN_DATE='2004-01-01 00:00:00.0'/>
  <chart ID='16' CHART_NUMBER='12110' PARENT_ID='15' DESCRIPTION='Sub sub chart' OPEN_DATE='2004-01-01 00:00:00.0'/>
  <chart ID='17' CHART_NUMBER='12200' PARENT_ID='12' DESCRIPTION='Sub chart 2' OPEN_DATE='2004-01-01 00:00:00.0'/>
  <chart ID='18' CHART_NUMBER='12210' PARENT_ID='17' DESCRIPTION='Sub sub chart 2' OPEN_DATE='2004-01-01 00:00:00.0'/>
</dataset>
{% endhighlight %}

I ran the tests, and bingo!  Green bar.  I love tests that run.
