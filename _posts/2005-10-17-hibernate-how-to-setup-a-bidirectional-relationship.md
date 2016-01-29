---
title: '[Hibernate] How to setup a bidirectional relationship'
author: Tim
layout: post
redirect_from: /2005/10/17/hibernate-how-to-setup-a-bidirectional-relationship/
categories:
  - How-To
tags:
  - examples
  - hibernate
  - java
  - solutions
---
I got the following question from a friend the other day.

> I have a parent and a child object with a one-to-many relationship by the child&#8217;s table having a column that points to it&#8217;s parent. What are the correct settings for the mapping in this situation where I need to be able to remove children from the parent&#8217;s set, and save the updated parent. It seems like I&#8217;ve been through all sorts of combinations, and I was wondering if you could lend me your advice.

The same day I also had a similar question from a colleague at work. I figured I&#8217;d post my response here so I could easily find it in the future. I&#8217;ve tried to make the code reasonably generic, but watch out for dumb typos.

You should setup the parent mapping like this:

{% highlight xml %}
<set name="children" lazy="true" inverse="true">
  <key column="PARENT_ID"/>
  <one-to-many class="my.child.ChildClass"/>
</set>
{% endhighlight %}

And then map the child like this:

{% highlight xml %}
<many-to-one name="parent" column="PARENT_ID" not-null="false" class="my.parent.ParentClass"/>
{% endhighlight %}


Notice that the column name in each refers to THE SAME COLUMN. You&#8217;re just connecting the link.

From the parent class:

{% highlight java %}
/** The set of children of this object. */
private Set<ChildClass> children = new HashSet<ChildClass>();
private void setChildren(Set<ChildClass> children) {
    this.children = children;
}

public void removeChild(ChildClass child) {
    children.remove(child);
    child.setParent(null);
}

public void addChild(ChildClass child) throws IllegalArgumentException {
    if (child == null) {
        throw new IllegalArgumentException("Child may not be null");
    }
    if (child.getParent() != null) {
        child.getParent().removeChild(child);
    }
    child.setParent(this);
    children.add(child);
}
{% endhighlight %}

<p>
  From the child class:
</p>

{% highlight java %}
/** The parent. */
private ParentClass parent;
{% endhighlight %}


<p>
  This simple example seems to illustrate the basics.  My friend later pointed out that one of the things tripping him up was the <code>cascade</code> option.  Recognizing that it&#8217;s completely separate from the <code>inverse</code> property was a big step.  That&#8217;s an important point &#8211; the <code>inverse</code> just means that the child objects have a property that refers back to the parent.  It helps resolve object relationships on load, but the <code>cascade</code> and <code>lazy</code> attributes tell Hibernate when to save and load the objects to and from the database.
</p>
