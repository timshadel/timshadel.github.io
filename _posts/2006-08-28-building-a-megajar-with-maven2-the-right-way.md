---
title: 'Building a Megajar with Maven2 &#8211; The Right Way'
author: Tim
layout: post
redirect_from: /2006/08/28/building-a-megajar-with-maven2-the-right-way/
categories:
  - How-To
tags:
  - assembly plugin
  - maven
  - subversion
  - Tools
  - version control
---
A *megajar* or *uberjar* is one jar file where all the contents of all dependent jars have been unpacked, and then everything has been re-`jar`ed up together again.

This is normally a very Bad Thing.

However, there are occasional one-off uses for such a thing. I&#8217;ve made a habit of following the advice given by the [Pragmatic Programmers][1] ([here][2] and [here][3]) by always creating a `tools` or `util` directory off the trunk of my project. I find that there are occasionally little things I do from the command-line to mass-update the source (for a package refactoring, perhaps), or there are small tools needed for one-time data conversions when a release is rolled out. I put those things in version control instead of losing them. I like to put the JIRA issue key in their name (e.g. `PRJ-12-migrate-start-times`), since this emphasizes the problem the tool is solving as well as its use only for the [nonce][4].

For one such tool we did lately, we needed only one dependency &#8212; the database driver jar file. Since we don&#8217;t run these things in production, it was important to make this thing as simple to use as possible. Hence, we decided that bundling the driver for this one-off tool was simpler than a lengthy set of instructions for the Release Team.

The command I used was

{% highlight sh %}
mvn assembly:assembly -DdescriptorId=jar-with-dependencies
{% endhighlight %}


You can find [more information][5] around the web. I found the [Maven2 Assembly Plugin docs][6] fairly helpful. I also added this snippet to my `pom.xml`:

{% highlight xml %}
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-assembly-plugin</artifactId>
  <configuration>
    <archive>
      <manifest>
        <mainClass>my.package.to.my.MainClass</mainClass>
      </manifest>
    </archive>
  </configuration>
</plugin>
{% endhighlight %}


So that the entire thing can be run with a simple Java command:

{% highlight sh %}
java -jar target/PRJ-12-migrate-start-times-1.0.0-jar-with-dependencies.jar
{% endhighlight %}

Got any tips for using the `tools` directory in your project?

 [1]: http://pragprog.com
 [2]: http://pragmaticprogrammer.com/titles/svn2/index.html
 [3]: http://pragmaticprogrammer.com/starter_kit/vc/index.html
 [4]: http://dictionary.reference.com/search?q=nonce&x=0&y=0
 [5]: http://www.synthesisstudios.com/whiteboard/tag/jar/
 [6]: http://maven.apache.org/plugins/maven-assembly-plugin/introduction.html
