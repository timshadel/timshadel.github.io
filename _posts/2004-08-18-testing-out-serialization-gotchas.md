---
title: Testing Out Serialization Gotchas
author: Tim
layout: post
permalink: /2004/08/18/testing-out-serialization-gotchas/
categories:
  - How-To
tags:
  - enums
  - java
  - serialization
  - testing
---
Have you ever encounterd a `<a title="Javadoc for NotSerializableException" href="http://java.sun.com/j2se/1.4.2/docs/api/java/io/NotSerializableException.html">NotSerializableException</a>` in staging, or worse, production? Perhaps you&#8217;ve run your application for months or years, but then you decided to cluster your web tier and you realize that your container is actually trying to write out your `<a title="Javadoc for HttpSession" href="http://java.sun.com/j2ee/sdk_1.3/techdocs/api/javax/servlet/http/HttpSession.html">HttpSession</a>`s to some place hither or yon. Perhaps you&#8217;re testing after adding that last little feature, only to eventually realize that your brilliant new feature inserts something into the session that prevents serialization.

I&#8217;ve encountered such unpleasent experience as those in past projects. Today I wanted to make sure that my `Message` for a JMS queue was serializable. More than that, I wanted to make sure that the attribute that&#8217;s a Typesafe Enum class I&#8217;ve used (yeah, I know they&#8217;ve added enums in 1.5/5.0) properly deserializes — it shouldn&#8217;t create a new object. Here&#8217;s the test I used on the enum:

{% highlight java %}
public void testSerialize() throws Exception {
    ByteArrayOutputStream bout = new ByteArrayOutputStream();
    ObjectOutputStream out = new ObjectOutputStream(bout);
    out.writeObject(MyEnum.ENUM_CHOICE);
    out.flush();
    byte[] bytes = bout.toByteArray();
    ObjectInputStream in = new ObjectInputStream(new ByteArrayInputStream(bytes));
    MyEnum enum = (MyEnum) in.readObject();
    assertTrue("Deserialized constant should be exactly the same object as the constant itself.", enum == MyEnum.ENUM_CHOICE);
}
{% endhighlight %}

For more nuances of writing Typesafe Enums, why they&#8217;re really needed, and how to use them well, you should really checkout *Item 21* of [Josh&#8217;s book][1]. In the meantime, think about testing your serialization assumptions. Got any suggestions for other serialization areas to watch?

 [1]: http://amazon.com/o/ASIN/0201310058/ref=ase_timshadelcom-20/ "Effective Java: Programming Language Guide"
