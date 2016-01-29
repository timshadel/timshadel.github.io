---
title: 'My Philosophy for Choosing git &#038; GitHub over Mercurial &#038; BitBucket'
author: Tim
layout: post
redirect_from: /2010/10/11/my-philosophy-for-choosing-git-github-over-mercurial-bitbucket/
category:  Craftsmanship
  - Featured
  - Impressions
tags:
  - git
  - opinion
  - Tools
  - version control
---
This is taken from an argument I made back in November for why our entire company should adopt git. There may be errors in it, and it&#8217;s fairly out of date. Given those caveats, I hope it&#8217;s useful.

* * *

In short, I choose git and github based on my beliefs about software development at the organizational and individual levels.

## As a software craftsman, I believe in sharp tools

> Tools amplify your talent. The better your tools, and the better you know how to use them, the more productive you can be. [&#8230;]

> Many new programmers make the mistake of adopting a single power tool, such as a particular integrated development environment (IDE), and never leave its cozy interface. This really is a mistake. We need to be comfortable beyond the limits imposed by an IDE. The only way to do this is to keep the basic tool set sharp and ready to use.
> &#8211; The Pragmatic Programmer, Chapter 3

<!--more-->

While Mercurial provides a command-line tool, it&#8217;s interface is limited. Git provides a more rich set of tools for me to poke through my versioned set of source code. Doing so gives me powerful ways to solve unanticipated problems that will be of great importance at some point in the future. Choosing git now lets us prepare for those moments when performance of a difficult operation will be required.

> We need to let our craftsmen work with sharp tools, rather than protect them from themselves.
> &#8211; Bruce Tate, author and programmer

## I believe in people over process

> &#8220;Individuals and interactions over processes and tools&#8221; &#8211; The Agile Manifesto

Given a choice of two tools, one of which favors interactions and empowers individuals more than the other, I will choose the one that empowers nearly every time since I believe that trusting my peers and coaching each other in the use of a powerful concept or tool will lead to a better result overall.

> &#8220;There is nothing that motivates, or inspires, people like having trust extended to them. When it is, people don&#8217;t need to be managed or supervised; they manage themselves.&#8221; &#8211; Stephen R. M. Covey, [The SPEED of Trust][1], p. 227

Git makes it fast to switch between local forks of code. Doing so it shortens the process of forking, empowering people by reducing the process around keeping track of all of the forks they use. It makes the personal pain less, so that they fork more often and when needed instead of when the benefit outweighs the noticeable cost.

## I believe in optimizing the common cases of individual use

Git makes it very fast to switch between local forks of code. It is very fast to clone a remote repo over the git protocol. It is harder to setup a central server using the git protocol. The common cases are clones and switches. The less common case is setting up server infrastructure for use among teams of individuals. GitHub innovates around this space.

## I believe in making broad work across an organization globally visible

Discovery and discoverability are the hallmarks of communication, serendipitous invention, and spontaneous collaboration. They are the heart of tools in the agile movement such as Continuous Integration, Big Visible Charts, and Collective Code Ownership. These principles are built on the idea that we must trust everyone involved in building our software to both see the code, see the progress we&#8217;re making in building our software, and make changes to any code that they need to to push the software forward. I believe extending that trust is absolutely required if we are to develop software at industry speed.

If we are to develop software at that speed, we need a way for people not only to extend that trust, but to do so in ways that are discoverable by others in the sea of changes that occur when a large organization undertakes writing software. Collaborative community-based tools, like GitHub, built on solid distributed software tools are required to make the host of conceptual development streams visible and discoverable to individual front-line developers.

By using innovations such as following fellow developers, following specific forks, and reading peer comments about specific commits we empower developers to discover community knowledge around our massively changing source base in powerful ways that they cannot simply by interacting with the source control tool.

By choosing a community tool built on an infrastructure and core tool community that prods individual developers to craft the ways they publish their changes to others, we then get individual developers communicating meaningful semantic changes to their peers in ways discoverable chunks sized to the optimal granularity of the discovery scope and mechanism.

## I believe in Programming on Purpose, and Not By Coincidence

Part of that belief is that developers should make informed, conscious choices about their actions at every step of the way. They should choose indexes wisely in their database, choose their abstractions correctly given the realities of their software and its environment, and craft their source code history consciously to give those that follow a clear picture of the conceptual evolution of their code.

I believe that using a tool born out of a culture that believes in communicating intent over preserving immutability will shape a developer&#8217;s thinking more correctly for harnessing that powerful communication possibility than using a tool from a community that is generally opposed to it. Freezing the code in its coincidental flow of changes by making history immutable disallows a logical communication of changes in favor of a physical communication. A culture that promotes historical immutability will always promote to the developer that the preservation of coincidental timelines above conceptual change communication.

This is a powerful, principled, and irreconcilable difference in the philosophical underpinnings among the tool communities. The blogs and manuals of Mercurial heavily favor immutability over communicating intent.

## As a minimalist and computer science advocate, I believe in very clean data structures

> &#8220;The programmer at wit&#8217;s end for lack of space can often do best by disentangling himself from his code, rearing back, and contemplating his data. Representation *is* the essence of programming&#8221; &#8211; Fred Brooks, [The Mythical Man-Month][2]

In Chapter 3 of the classic book [Programming Pearls][3], Jon Bentley covers data structures and illustrates both in striking detail and in beautiful simplicity how the underlying data structures impact the performance of a program. I would add that it is also clear how that structure alters the possibilities of new code that can use that data and the minds of the programmers approaching it.

Git&#8217;s simplistic data structure allowed its initial approach to version a source tree to grow in unexpected ways:

  * Its compression algorithm is better than any other tool because it is not compressing data structured around a filename.
  * It was trivial to take advantage of the OS filesystem cache by allowing an in-place switch of a working copy from one branch to another by realizing that each local branch is a pointer to into its blob graph.
  * The above makes it trivial to add on the concepts of remote references, making it possible for developers to see locally (without a network) the evolution of a remote repository. Such is not available in Mercurial. The core data structure of Git made this evolutionary functionality possible.
  * By focusing around a specific data structure and following the UNIX tradition of composable programs, git evolved a structure allowing for custom pluggable merge and difference drivers. This, combined with the simple data structure giving a list of parents instead of exactly two, produced the octopus merge tool that can take many separate branches and merge them all. This tool seems most often used in larger projects, and I anticipate it may prove useful for us.

Overall, we will be more likely to see innovative features out of a community around a product with a clean data structure than with communities around tools with less powerful data structures. These innovations may seem small at a cursory glance (like taking advantage of OS filesystem caching on fork switches); in the end they will empower our developers in deeper ways than can be seen at first (making new ways of working cheap).

## I believe that community matters when adopting tools &#8211; especially open source

Community affects how well you can get your job done because community directly influences:

### When the Tool is Truly Revolutionary

  * Truly novel principles will attract thought leaders who will then provide both a strong and prominent voice in favor of a tool, and contribute mind-blowing innovative products and ideas around the core tool.

### When the Community Includes Thought Leaders

  * Innovation will follow the thought leaders.
  * Imitation will follow the innovation.
  * Innovation around a core feature is more valuable than innovation around a glossy feature.
  * Thought leaders and Innovation will attract Early Adopters

### Community Includes The Masses

  * The number of free articles published on your topic, because that&#8217;s driven by the number of users
  * The number of paid resources (like books and screencasts) on your tool, because that&#8217;s driven by what the market will pay for
  * The probability that a new developer we hire will be familiar with a tool, because that&#8217;s driven by market share
  * The number and stability of paid support options for your tool, because that&#8217;s again driven by what the market will pay for

 [1]: http://amzn.to/cRCuZY
 [2]: http://amzn.to/cxk698
 [3]: http://amzn.to/9bR8Zv
