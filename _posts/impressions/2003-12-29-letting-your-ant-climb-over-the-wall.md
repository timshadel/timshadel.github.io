---
title: Letting your Ant climb over the wall
author: Tim
layout: post
redirect_from: /2003/12/29/letting-your-ant-climb-over-the-wall/
category:  Impressions
---
It&#8217;s been quite interesting to play with [Ant][1] 1.6. I&#8217;ve trying to figure out the best way to share `macrodef` snippets between projects, and I think I found my preferred way for now. There are two ways I see for sharing Ant macros:

  1. Placing a common project in a well-known directory (typically up the directory hierarchy a bit), and then having all build files `import` that file
  2. Using the new `antlib` to define the macros, and then bringing those definitions into the current build file

I think that the metaphor I&#8217;ll use is that common build files are a part of a separate, deployable project. This approach should support:

  * One central place to change the shared macros
  * Easy inclusion of local common macros and targets alongside third party macros and targets
  * Sharing local macros with others external to this organization
  * Consistent use of the shared macros in each project without requiring per-machine or per-login configuration

To meet those needs, I&#8217;ll do the following:

  * Create a separated, versioned project for common build tasks, macros, etc. whose deliverable product is a JAR file
  * From the project perspective, treat the common build JAR like any other Java library, and check the JAR into that project&#8217;s version control tree
  * Use a standard directory in each project to hold all `antlib`s
  * Invoke Ant using the new `ant -lib [commonAntlibDir] [target]` method
  * Define namespaces at the beginning of each project file, using the `xmlns:myTasks="antlib:my.domain.ant"` syntax to automagically grab the shared task from the Ant classpath that includes the local project `commonAntlibDir` directory

One challenge is that always using `ant -lib ...` is bound to become tedious. Perhaps the local environment could be set to use this automatically, but that violates one of the goals. I&#8217;d prefer setting up the Ant libraries per-project rather than cluttering my local Ant installation, and hoping that everyone else has the needed libraries. This approach comes closest to doing that consistently than any other I&#8217;ve seen so far. We&#8217;ll have to see. YMMV.

 [1]: http://ant.apache.org
