---
title: What are good ways to get file contents to an EJB?
author: Tim
layout: post
redirect_from: /2003/12/18/what-are-good-ways-to-get-file-contents-to-an-ejb/
category:  Perplexed
tags:
  - ejb
  - file upload
---
I can think of a few:

  * From a webserver, use the Commons FileUpload library and provide a custom class that sends bytes to the EJB instead of the file system.
  * From a console program, loop through buffers of the file, and send chunks of the file to the EJB

Does this mean that you have to create a TCP-like idea for your EJB, to
make sure everything got there and is in order?

How well does it handle failures?

What kinds of failures could occur?

Is it really worth it?

[Links][1] [I&#8217;ve][2] [found][3] [here][4].

 [1]: http://forum.java.sun.com/thread.jsp?thread=437124&forum=31&message=1963860
 [2]: http://www.mail-archive.com/orion-interest@orionserver.com/msg15141.html
 [3]: http://forum.java.sun.com/thread.jsp?thread=298620&forum=13&message=1183186
 [4]: http://forum.java.sun.com/thread.jsp?forum=13&thread=297320
