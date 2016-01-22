---
title: Unit Testing Your Database Code with Hibernate and Spring
author: Tim
layout: post
permalink: /2005/07/21/unit-testing-your-database-code-with-hibernate-and-spring/
enclosure:
  - |
    |
        http://timshadel.com/podcasts/Zdot-20050721-UnitTestingDatabaseCode.mp3
        24858506
        audio/mpeg
        
categories:
  - '*-casts'
tags:
  - dbunit
  - hibernate
  - hsqldb
  - spring
  - testing
---
You&#8217;ve got database code that uses both [Hibernate][1] and [Spring][2]. You need to test it. In this podcast I talk about how you can use DBUnit and HSQLDB along with some Spring test classes to create a setup that will let you test database code fast, and in isolation. Just what good unit tests should do.

Check out some great references on database testing, including the ones I mentioned in this show.

[DBUnit][3] and thier [best practices for database testing][4].  
The [HSQLDB home page][5].  
Scott Ambler&#8217;s excellent discussion of [database refactoring][6].  
An article from TheServerSide.com about [unit testing with HSQLDB][7].  
Spring&#8217;s [AbstractTransactionalDataSourceSpringContextTests][8] class that helps make some of your database testing easier. Check the other classes in the hierarchy for specifics on what they do as well.

I decided to try out adding a GarageBand.com song today, like the [SlashdotReview][9] podcast does. The song is [Calendar][10] by [Eugenia and The Boys][11]. Let me know if you like it. Also feel free to revolt and tell me to pull the music and keep it to tech stuff. <img src="http://timshadel.com/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />

Listen now with the Flash player.  


Download [Unit Testing Database Code][12].

 [1]: http://hibernate.org
 [2]: http://springframework.org/
 [3]: http://www.dbunit.org/
 [4]: http://www.dbunit.org/bestpractices.html "The DBUnit Framework - Best Practices"
 [5]: http://hsqldb.org/
 [6]: http://www.agiledata.org/essays/databaseRefactoring.html "The Process of Database Refactoring"
 [7]: http://www.theserverside.com/articles/article.tss?l=UnitTesting "Unit-Testing Hibernate with HSQLDB"
 [8]: http://static.springframework.org/spring/docs/1.2.x/api/org/springframework/test/AbstractTransactionalDataSourceSpringContextTests.html
 [9]: http://slashdotreview.com/
 [10]: http://www.garageband.com/artist/eugeniaandtheboys
 [11]: http://www.eugeniaandtheboys.com/
 [12]: http://timshadel.com/podcasts/Zdot-20050721-UnitTestingDatabaseCode.mp3
