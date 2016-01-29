---
title: 'Ant: Available task for multiple files'
author: Tim
layout: post
redirect_from: /2004/06/30/ant-available-task-for-multiple-files/
categories:
  - How-To
tags:
  - ant
  - maven
---
Today I wanted to find out, using [Ant][1], if any of a set of files existed. Based on that information, I would conditionally execute a target. Well, really I needed to solve a problem in [Maven][2], but an Ant solution would plug in just fine. Here&#8217;s what I came up with:

<pre>&lt;project name="test" default="test" basedir=".">
    &lt;target name="test">
        &lt;delete file="target\dir\status.file"/>
        &lt;copy todir="target\dir">
            &lt;fileset dir="target\dir" includes="*.xml"/>
            &lt;mapper type="merge" to="status.file"/>
        &lt;/copy>
        &lt;available property="test.any" value="true" file="target\dir\status.file"/>
        &lt;property name="test.any" value="false"/>
        &lt;echo>any.xml: ${test.any}&lt;/echo>
    &lt;/target>
&lt;/project>
</pre>

That seems to work. The side effect is that one file is duplicated exactly, but only one.

 [1]: http://ant.apache.org
 [2]: http://maven.apache.org
