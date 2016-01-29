---
title: Why Hibernate is absolutely better than SQL
author: Tim
layout: post
redirect_from: /2004/08/04/why-hibernate-is-absolutely-better-than-sql/
category:  Impressions
tags:
  - hibernate
  - jdbc
  - sql
---
<pre>Handcoded time: 9 min
Hibernate time: 103 sec
</pre>

That&#8217;s the time we saved on an internal operation by switching it from hand-coded JDBC to Hibernate. These measurements tell a bigger story than SQL, though. They really tell about how Hibernate makes it easy to write understandable, fast code.

Let me back up. This application retrieved thousands of database rows and processed them. Part of the processing was to take a column containing XML data, grab the XSL transform from another table, and store the result to the file system. A bit messy. The orginal programmer used JDBC code and a database view to get the needed information to accomplish his task. When the test database had 120K+ rows, the performance problem became obvious. Another of our programmers worked with him to make it use Hibernate. Not only did we get a more understandable object model, we got great caching, relationship managment, and tuned SQL for free.

Bottom line: Hibernate encourages understandable object models, and makes it really fast to use them well.
