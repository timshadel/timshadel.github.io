---
title: Moving from WordPress 2 over to Typo 4
author: Tim
layout: post
redirect_from: /2006/08/19/moving-from-wordpress-2-over-to-typo-4/
categories:
  - News
tags:
  - typo wordpress apache2 rails mongrel
---
I&#8217;m in the middle of moving my blog from WordPress 2 to Typo 4. I&#8217;ve got the articles imported, and the migration script took care of that part. It also grabbed the categories I had and turned them into tags &#8212; too bad I wasn&#8217;t using WP categories; I was using Jerome&#8217;s Keywords. So now I&#8217;ve gotta go in and pull the keywords out of the metadata and connect them with my Typo posts. I also need to pull in the comments (for some reason they didn&#8217;t come in with the migration script). I probably messed something up there.

I did modify the `routes.rb` file to mimic the permalink structure I had with WordPress. It was important to keep my existing links workable (especially feed references), even if the new ones use a different format.

It also didn&#8217;t seem to pull in my podcast episodes. I&#8217;ve got a few simmering on the back burner right now, but I guess I need to figure out how to make the feed again before I put together another one.

I do like the personalization options this screen has, though the default font titles don&#8217;t handle non-Roman characters [like this one][1]. It&#8217;s not a big deal, though, since you can switch the font choice in the &#8220;personalization&#8221; section of the header to see the proper title.

So overall, it hasn&#8217;t been as smooth as I would have hoped, but it isn&#8217;t the end of the world either. I&#8217;m pretty happy, and I&#8217;m running Apache 2 + Mongrel now. That&#8217;s gotta be more fun. <img src="http://timshadel.com/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />

 [1]: http://timshadel.com/2004/08/18/a%25ce%25b8hna-2004
