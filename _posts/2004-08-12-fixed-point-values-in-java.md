---
title: Fixed point values in Java
author: Tim
layout: post
redirect_from: /2004/08/12/fixed-point-values-in-java/
categories:
  - How-To
tags:
  - accounting
  - java
---
I mentioned in one of my [latest entries][1] that I&#8217;ve done a bunch of fixed point stuff in Java lately. I work for a company that does many financial calculations, and much of the legacy code is in other languages. There&#8217;s always been a problem with rounding and consistency in these calculations. They&#8217;ve all been addressed, but there&#8217;s always pain to get it through testing when a change to calculation code arises.

[Martin Fowler][2] has discussed in [several][3] [venues ][4]the idea of having a class that represents Money. This ensures semantic consistency, rounding precision, and especially it provides an `allocate` method to distribute Money among various individuals or accounts without losing any fractions. Everything is accounted for correctly.

We not only deal with Money, but other values which we must treat as always having exactly `n` number of decimals. Martin Fowler&#8217;s examples have often included code, and [this guy][5] wrote [a Money class][6] in the same spirit. But I didn&#8217;t want to rely on my own fixed point caculations to do the job right (you know, losing precision, increasing scale based on the arithmetic function performed, and all that stuff that&#8217;s real easy to ignore — even though you know it&#8217;s gonna come back and bite). I poked around and found out that IBM [has done a great job of it already][7]. They [submitted a JSR long ago][8], and you can see that their work has been [incorporated into J2SE 1.5][9] (or 5.0 — silly Sun marketing droids).

If you need to do reliable fixed point or decimal floating point calculations in Java, and you aren&#8217;t moving to J2SE 5.0 immediately, check out the small decimal.jar in [this ZIP file][10] (there&#8217;s even decimal1.jar for the 0.004% of Java users stuck on JDK 1.1) from IBM. It just may save the day.

 [1]: http://timshadel.com/blog/2004/08/10/1092190000000.html
 [2]: http://www.martinfowler.com
 [3]: http://www.martinfowler.com/eaaCatalog/money.html "Patterns of Enterprise Architecture Catalog: Money"
 [4]: http://www.martinfowler.com/ieeeSoftware/whenType.pdf "IEEE Software Jan/Feb 2003: When to Make a Type"
 [5]: http://members.shaw.ca/jagarnett/
 [6]: http://members.shaw.ca/jagarnett/Files/Money_java.html
 [7]: http://www2.hursley.ibm.com/decimalj/ "Decimal arithmetic for Java"
 [8]: http://www.jcp.org/en/jsr/detail?id=13 "JSR 13: Decimal Arithmetic Enhancement"
 [9]: http://java.sun.com/j2se/1.5.0/docs/api/java/math/BigDecimal.html "Class BigDecimal"
 [10]: http://timshadel.com/wp-content/uploads/2004/08/decimal.zip "Decimal package (decimal.zip)"
