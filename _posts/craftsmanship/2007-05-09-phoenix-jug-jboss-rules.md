---
title: 'Phoenix JUG: JBoss Rules'
author: Tim
layout: post
redirect_from: /2007/05/09/phoenix-jug-jboss-rules/
category:  Craftsmanship
tags:
  - drools
  - java
  - jboss
  - jboss rules
  - jug
  - phoenix
  - presenting
  - rules
---
I gave a presentation tonight on [JBoss Rules][1] to the [Phoenix JUG][1]. There was a good group of people there, and we had a very lively discussion around some of the strengths and weaknesses of rules engines in general. It was fun to cover a topic that I don&#8217;t hear much of (outside of sales pitches), and to see so much interest. There were a log of thoughtful questions, and many people were interested in ideas of how to program using rules.

At work, we use JBoss Rules for a small portion of our code but that code handles an awful lot of our transactional complexity. Spring, Hibernate, and Struts handle most of the heavy lifting of our structure. But JBoss Rules helps keep our routing logic and call script questions fairly clean and maintainable.

While a lot of the value of a presentation is in the verbal exchange that goes on in the room, I figure there&#8217;s something to be gained by gazing through the slides and sample code after the fact. With any luck, I&#8217;ll take some time in the next couple weeks to put up some podcasts (gasp!) on JBoss Rules. Enjoy.

**Presentation:** [rules.pdf][2]
**Source Code:** [jboss-rules][3]

 [1]: http://phxjug.org/meetings.html
 [2]: https://github.com/timshadel/jboss-rules-presentation-may-2007/raw/master/rules.pdf
 [3]: https://github.com/timshadel/jboss-rules-presentation-may-2007/
