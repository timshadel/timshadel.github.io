---
title: Does your login page Yahoo?
author: Tim
layout: post
redirect_from: /2003/12/23/does-your-login-page-yahoo/
category:  Craftsmanship
---
[Yahoo! Mail &#8211; The best free web-based email!][1]

The Yahoo! mail login page uses some interesting ideas. They hash information on the client-side before attempting to login. They also store retries, and a challenge in hidden fields as well.

I should look into this a bit more. Some of this may be used to make it difficult for scripts to login. Some may be used to make it safer for users of public computers and prevent sensitive information from being cached on the client.

Does the `location.href` really instruct the browser to begin loading the URL while the current JavaScript continues execution? I find that hard to believe, but I&#8217;ll check it out.

 [1]: http://mail.yahoo.com/ "Yahoo! Mail - The best free web-based email!"
