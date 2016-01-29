---
title: 'Making Rails use Google&#8217;s AuthSub'
author: Tim
layout: post
redirect_from: /2006/10/14/making-rails-use-googles-authsub/
category:  How-To
tags:
  - authentication
  - google
  - rails
  - web services
  - yahoo
---
I&#8217;ve managed to patch together several 10-minute sessions of playtime with Rails over the past few weeks, and the subject I&#8217;ve been pursuing is how to make Rails use Google for authentication.

I first played with this idea back in February, after reading Phil Windley&#8217;s article on [GTalk using XMPP][1]. I grabbed the source of [XMPP4R][2], and hacked it to use [the X-GOOGLE-TOKEN][3] in its SASL protocol. It worked, and I was able to issue the XMPP message to Google&#8217;s servers to grab my mail &#8212; just like GTalk does on Windows. There were a few drawbacks to this, though. First, I had to convince people to type their Google username and password into *my form*. I wouldn&#8217;t want to do that. Bad idea. Number 2, there was no way to kill a token once it was requested. If a user left my site and never came back, I&#8217;d be able to read his mail forever. Bad idea #2. You can read more on this [here][4] and [here][5].

So I waited. I still hoped to use Google&#8217;s authentication. With all the security breaches these days, who wants to store passwords, much less credit card info.

Then Google came out with [AuthSub][6]. I now had a way to have users type their username and password into a Google web page, and then have Google simply give me a token. It wasn&#8217;t too hard to get working. You can see the beginnings of it on [gotdone.com][7]. Right now, there&#8217;s nothing there but the login, the welcome, and the logout. Eventually I want to offer login either via Google or via [Yahoo! BBAuth][8].

This is cool, since I no longer have to write a silly register form with every app that will ask for your name, email, username, and password. I simply glean it from Google when you give me access. Once you logout, I can tell Google that the token is revoked, and then it can&#8217;t be used by anyone else again &#8212; including me. Nice.

One of the next steps available via Google is to register my domain with them, and then you won&#8217;t see the warning message &#8220;Don&#8217;t even think of doing this unless you trust gotdone.com&#8221; (or whatever it is they actually say).

Yahoo! takes a different approach. You must register your endpoint with them *before* you can use their authentication method. As far as I can tell, this makes it difficult to have your app redirect to localhost during development and your true domain during production. Perhaps they have a developer sandbox I haven&#8217;t seen in my 30 second perusal.

Either way, there&#8217;s a handicap that you hit with taking either of these roads: you can&#8217;t develop on an airplane. Well, more accurately, you can&#8217;t login during development unless you have Internet access. If you wireless goes down, if you&#8217;re commuting to work in your carpool (not driving I hope), or if you&#8217;re stuck at a conference without the $15 it takes to get access, you can&#8217;t use your app. Now, that doesn&#8217;t mean there aren&#8217;t workarounds. You could write your own trivial Rails app that acts as a bogus auth mechanism, you could swap out code so you use one piece of code for prod and one for dev (yikes!), or you could simply sit back and enjoy your plane ride&#8230; Yeah. Like that&#8217;s gonna happen. In any case, let me know if you&#8217;ve got grand ideas about how to adapt your app to offline development with this new authentication paradigm.

So, in conclusion, I think that Google and Yahoo! are on the right track by offering their auth services. Are they perfect? Nope. Are they foolproof? Nah. Are there still security concerns? Absolutely. But I like it better than having your password. And I certainly like it better than having to write &#8220;Forgot My Password&#8221; code for the zillionth time.

You decide.

 [1]: http://www.windley.com/archives/2006/03/trusting_google.shtml
 [2]: http://home.gna.org/xmpp4r/
 [3]: http://dystopics.dump.be/2006/02/04/the-mysteries-of-x-google-token-and-why-it-matters/
 [4]: http://www.windley.com/archives/2006/02/using_googles_u.shtml
 [5]: http://dystopics.dump.be/2006/02/04/the-mysteries-of-x-google-token-and-why-it-matters#comments
 [6]: http://code.google.com/apis/accounts/AuthForWebApps.html
 [7]: http://gotdone.com
 [8]: http://developer.yahoo.com/auth/
