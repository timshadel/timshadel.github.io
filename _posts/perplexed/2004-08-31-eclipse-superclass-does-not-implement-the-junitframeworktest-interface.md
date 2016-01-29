---
title: '[Eclipse] Superclass does not implement the &#8216;junit.framework.Test&#8217; interface'
author: Tim
layout: post
redirect_from: /2004/08/31/eclipse-superclass-does-not-implement-the-junitframeworktest-interface/
category:  Perplexed
tags:
  - eclipse
  - junit
  - solutions
---
I ran into this really strange error the other day while using Eclipse. I had been creating some JUnit tests, and everything was going just fine. Then I tried to create another one, and I saw the dialog below with the error message, *Superclass does not implement the &#8216;junit.framework.Test&#8217; interface*.

![Eclipse 'Create JUnit Test Case' error screenshot][1]

The JUnit JAR file was in my classpath, so I was befuddled for a minute or two. After searching around I discovered that I had accidentally deleted the JRE System Library from my project Java Build Path. After I restored that, everything worked fine.

 [1]: http://timshadel.com/wp-content/uploads/2004/08/eclipse-junit-error.gif
