---
title: How to Setup Google Apps Chat SRV Records For iChat and xmpp4r-simple
author: Tim
layout: post
redirect_from: /2007/12/14/how-to-setup-google-apps-chat-srv-records-for-ichat-and-xmpp4r-simple/
category:  How-To
tags:
  - google
  - google apps
  - ichat
  - jabber
  - ruby
  - xmpp
  - xmpp4r
  - xmpp4r-simple
---
I&#8217;ve registered [several domains][1] using [Google Apps][2]. Lately I&#8217;ve been fiddling with using Jabber with those domains, and I wanted to have a program be able to interact on IM using an account like tim@example.com. Furthermore, I wanted to have everything Just Work.

The place to start was with DNS. [Google has a help page][3] about how to setup your DNS so that your Google Apps accounts can be federated with other non-Google Jabber communities. The problem is that neither `xmpp4r-simple` nor iChat simply work if I use `tim@example.com` as my [JID][4]. Then I stumbled across [this post][5] that connected the dots for me.

Here&#8217;s a screenshot of how I setup my SRV records over at [eNom][1]:

![DNS SRV records for XMPP federation and client setup.][6]

After that, my simple chat listener worked:

{% highlight ruby %}
require 'rubygems'
require 'xmpp4r-simple'

im = Jabber::Simple.new("tim@example.com", "secret-password")
puts im.connected?
im.accept_subscriptions = true

while true
  sleep(5) unless im.received_messages?
  im.received_messages { |msg| puts msg.body if msg.type == :chat }
end
{% endhighlight %}

My little &#8220;bot&#8221; silently accepted new buddy requests, and printed out recent messages every 5 seconds.

<b>UPDATE:</b> <del>Something&#8217;s amiss here, I think. I&#8217;ll update when I have more details.</del> Guess not.  I tried this out on another domain, and thought that things didn&#8217;t work right.  But I was mistaken.  Everything looks good.

 [1]: http://timshadel.com/2007/02/18/standing-up-against-the-sleaze/
 [2]: http://www.google.com/a/
 [3]: http://www.google.com/support/a/bin/answer.py?answer=60227&hl=en
 [4]: http://www.google.com/search?client=safari&rls=en-us&q=define:JID&ie=UTF-8&oe=UTF-8
 [5]: http://checksum.org/article/google_talk_for_google_apps_srv_records/
 [6]: http://timshadel.com/wp-content/uploads/2007/12/2110015204_17b478a06c_o.png
