---
title: '[Spring] You create nothing.  All is given to you.'
author: Tim
layout: post
redirect_from: /2004/09/01/spring-you-create-nothing-all-is-given-to-you/
category:  Impressions
tags:
  - hivemind
  - ioc
  - solutions
  - spring
---
We&#8217;ve really loved our iniitial work with [Spring][1]. Yesterday we started tying it up with [Hibernate][2], and nothing I&#8217;ve seen has been a better solution to configuration and database access. It&#8217;s great. We seem to have run into a common misuse case though, and I wanted to jot it down for future reference.

We have existing Struts code that we&#8217;re adding some Spring and Hibernate stuff to. We&#8217;re using `HibernateDaoSupport` in creating our own `DAO`s, but sometimes they throw a `NullPointerException` when calling `getHibernateTemplate()`. We go &#8217;round and &#8217;round, but everything seems to be right. We check our `*.hbm.xml` files, we check our Spring config files, and find nothing. Then we find that our `Action` class looks something like this:

{% highlight java %}
public ActionForward execute( [...] ) {
   BusinessDelegate delegate = new BusinessDelegate();
   delegate.doSomethingGood();
}
{% endhighlight %}

I&#8217;m sure you&#8217;ve already spotted the problem. The whole principle behind the Spring implementation of [Inversion][3] [of][4] [Control][5] (or [Dependency Injection][6]) is that your `Action` class is *told* which `BusinessDelegate` to use. If you create your own, it simply isn&#8217;t assembled and configured using your Spring setup, and therefore it won&#8217;t have the dependencies set properly. And that&#8217;s why we&#8217;d find `NullPointerException`s.

Ahh. It&#8217;s written down. Now I&#8217;ll find it faster next time I forget&#8230;I hope.

 [1]: http://www.springframework.org/ "Spring Framework"
 [2]: http://www.hibernate.org/ "Hibernate: Relational Persistence For Idiomatic Java"
 [3]: http://docs.codehaus.org/display/PICO/Inversion+of+Control "Pico Container Docs: Inversion of Control"
 [4]: http://jakarta.apache.org/hivemind/ioc.html "HiveMind Docs: Inversion of Control"
 [5]: http://www.springframework.org/docs/reference/beans.html "Spring Docs: BeanFactory, the basis for Spring's Inversion of Control"
 [6]: http://www.martinfowler.com/articles/injection.html "Inversion of Control Containers and the Dependency Injection Pattern"
