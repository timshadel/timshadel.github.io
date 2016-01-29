---
title: 'URLs as Identity: Time Does Matter'
author: Tim
layout: post
redirect_from: /2005/12/01/urls-as-identity-time-does-matter/
category:  Impressions
tags:
  - digital identity
---
[Phil Windley][1] has some interesting pointers on URLs as identities over in [this post][2]. This isn&#8217;t the first time I&#8217;ve heard of this, and I expect it won&#8217;t be the last. While I think the idea is good, and I hope to see it continue to grow. I am concerned that I don&#8217;t readily see a consensus on how to handle URLs changing hands over time.

Certificates have CRLs, and expiration dates. You have to get new ones, and no one can get your old certificate.

I, like many of you, have purchased several domain names over time. Some I held for a time and have let go. How can you assert who owned a URL at a point in time in the past? For example, this comment will still be visible for times to come. If I need to let my domain die, and someone else picks it up, do they now inherit the credit for all my deeds scattered across the internet? Does everyone simultaneously stop asserting that my identity is good, or can they still assert that the identity was good at the time the action was taken?

Time is something I&#8217;ve continually wrestled while developing internal systems at many companies. Most things have a period of validity. Many things require an occasional check that something was valid at a particular point in the past. Most software I&#8217;ve seen that deals with certificates doesn&#8217;t quite act this way. For example, if a person&#8217;s email certificate expires most S/MIME clients I&#8217;ve used will refuse to certify that the email was properly signed and sent and the certificate was valid *as of the date it was sent*. That&#8217;s what I care about when reading signed email. I don&#8217;t care that the person uses a different certificate today.

Similarly, if I leave a comment on a site, author an article that&#8217;s signed, or use a digital identity in some other way. I want my use of that identity, at that point in history, to be considered valid for all time.

Perhaps the real breakdown in this structure falls to locating a trusted time source. Perhaps it doesn&#8217;t matter so much if you&#8217;re willing to trust your own site&#8217;s time source, and some authoritative source&#8217;s answer to &#8220;what range of time is this identity good for.&#8221;

URLs as identity are useful. I used one at the beginning of this post to casually identify Phil Windley. I think that straightforward ideas like this have big potential to do good and be widely adopted. But, while I&#8217;m no expert on digital identity, in my opinion time does matter. Ignoring it will exhibit pain in the future. But right now, just about everything that deals with time in the [OpenID Spec][3] is crossed out.

Hopefully I&#8217;m clueless about a big piece of the pie.

 [1]: http://www.windley.com/
 [2]: http://www.windley.com/archives/2005/11/urls_as_identit.shtml "Phil Windley's Technometria | URLs as Identity"
 [3]: http://openid.net/specs.bml
