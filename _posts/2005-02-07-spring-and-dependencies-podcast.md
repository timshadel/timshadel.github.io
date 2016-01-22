---
title: Spring and Dependencies Podcast
author: Tim
layout: post
permalink: /2005/02/07/spring-and-dependencies-podcast/
enclosure:
  - |
    |
        http://timshadel.com/podcasts/20050207-SpringAndDependencies.mp3
        15989699
        audio/mpeg
        
        
categories:
  - '*-casts'
tags:
  - dependencies
  - spring
---
This podcast focuses on a quick intro to Spring and how it affects your code dependencies.



If don&#8217;t want to listen to it with the player above, you can download [Spring and Dependencies][1] podcast.

#### Show Notes

Here&#8217;s the outline I worked from while recording the podcast. It&#8217;s sketchy, so don&#8217;t take it for hard information. I&#8217;ve woven in a couple links, though.

  * Who I am 
      * Java developer since 90&#8217;s 
      * J2EE since Struts 0.5 
      * Worked as programmer for university, .com, government 
  * What the show format is 
      * Cover interesting topics, many of them as they&#8217;re emerging 
      * Mainly my own experience and my reading: get what I think is a decent overview 
      * I wanted something substantive to listen to on the way to work or somewhere else 
          * 10-20 minutes 
          * Split topics across shows often 
          * Perhaps have a basic theme for week 
  * EJ classes 
      * 90 minutes, 3 times per week 

  * Spring IoC: Basic bean factory 
      * Allows for creation and wiring up 
      * Gives you home theater components instead of an all-in-one 
      * Encourages interface programming 
      * Can/should replace config file 
      * Eliminates creation and relationship code, allows object to focus on its reall purpose 
      * Moves dependency definitions to configuration 

  * Dependencies 
      * Variable type (Comcast comcast) 
      * Constructor choice (new Comcast()) 
      * Variable methods used (comcast.connect(), comcast.sendSpam()) 

  * Getting rid of dependencies 
      * Change variable type from concrete class to interface (Isp isp) 
          * That eliminates dependency on variable type 
          * That also standardizes the methods used &#8212; (isp.connect(), isp doesn&#8217;t have sendSpam() call). This may require changes to your code. You see this recommendation when using Map vs. Hasmap. 
      * Remove constructor call and replace with set method. 
          * Lets object creation be someone else&#8217;s problem 
          * Your object is now dealing simply with how to get its work done and collaborate with other objects. 
          * This has a really cool side effect: you&#8217;ve now made it really easy to use mocks of your Isp during testing instead of a real implementation. 
          * Check out the [sample chapter][2] of [Pragmatic Unit Testing][3]. 

  * Back to Spring 
      * Read the configuration file 
      * Instantiate the objects 
      * Resolve all the dependencies and relationships 
      * Call the correct set methods 
      * Left with all your business objects created, initialized, and connected 

  * Benefits 
      * All creation and relationship info is in one spot, instead of scattered in classes 
      * When something must be changed, there&#8217;s just one place to go to 
      * If your code relies on the interface, then you can choose which implementation in the config, and no code changes are needed.

 [1]: http://timshadel.com/podcasts/20050207-SpringAndDependencies.mp3
 [2]: http://www.pragmaticprogrammer.com/starter_kit/utj/mockobjects.pdf "Using Mock Objects"
 [3]: http://www.pragmaticprogrammer.com/starter_kit/utj/index.html
