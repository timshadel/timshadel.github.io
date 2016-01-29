---
title: '[Eclipse] More success with standardizing team plugins'
author: Tim
layout: post
redirect_from: /2004/08/30/eclipse-more-success-with-standardizing-team-plugins/
categories:
  - How-To
tags:
  - eclipse
  - plugins
  - subclipse
---
I recently wrote about [standardizing Eclipse plugins across your team][1] by using a shared Eclipse product extension. We had to do a few things this morning that we hadn&#8217;t yet tried since we set this up about a week and a half ago, and it worked out great.

We upgraded our common [Subclipse plugin][2] from 0.9.13 to 0.9.16. This turned out to be a [really][3] [bad][4] [idea][5] (not to mention the [maintainters are losing my respect][6]), so we backed it out and reverted to 0.9.13. The only thing we had to do was re-enable that plugin on some developers&#8217; Manage Configuration screen (watch out — disabled plugins aren&#8217;t shown by default, but you just need to click a button on the toolbar to make them show up again).

We also promoted a plugin from my personal plugin area up to the unstable area. Within 2 or 3 minutes, the move was complete and everyone had the new plugin that wanted to use it. Piece of cake.

We even had a guy move to Eclipse 3.1 M1 last week by simply copying the `links` folder to his new Eclipse directory as discussed in my other entry. It worked like a charm, and all he was up on 3.1.

So continued experience with this plugin setup seems to be quite favorable. Let me know how you&#8217;ve shared or standardized Eclipse plugins in your group.

 [1]: http://timshadel.com/blog/2004/08/28/1093715447000.html
 [2]: subclipse.tigris.org/
 [3]: http://subclipse.tigris.org/servlets/ReadMsg?list=users&msgNo=1014 "Subclipse Mailing List: Subclipse 0.9.15 update breaks my eclipse"
 [4]: http://subclipse.tigris.org/servlets/ReadMsg?list=users&msgNo=1021 "Subclipse Mailing List: 0.9.15 Disaster"
 [5]: http://subclipse.tigris.org/servlets/ReadMsg?list=users&msgNo=1031 "Subclipse Mailing List: 0.9.16 still broken"
 [6]: http://subclipse.tigris.org/servlets/ReadMsg?list=users&msgNo=1041 "Subclipse Mailing List Paraphrase: We don't need no stinking Release Notes"
