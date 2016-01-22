---
title: Sweet Looking Headings with CSS
author: Tim
layout: post
permalink: /2007/06/22/text-shadows-with-safari/
categories:
  - How-To
tags:
  - css
  - design
  - drop shadow
  - html
  - readability
  - text
  - ui
  - usability
  - web
---
As I&#8217;ve been playing more with [Safari][1] lately, I&#8217;ve found that many good looking web sites add a bit of something extra for Safari. They use CSS to add a drop shadow to *certain* elements of the page. Take a look at this example from [LightHouse][2] (Firefox 2.0 on the left, Safari 3 on the right):

![Firefox vs. Safari rendering of the CSS 'text-shadow'][3]

From [Word Up! Creating Dynamic Visual Presentations][4]:

> A drop shadow on your text helps set apart your words from their background thus making them easier on the eyes.

And you can see that in the example above. Adding the slight, but dark drop shadow to the white text on the blue color makes it more readable. It&#8217;s a nice touch that makes the UI feel like it has an extra set of *polish*. The CSS is simple enough:

<pre class="textmate-source railscasts"><span class="source source_css"><span class="meta meta_property-list meta_property-list_css"><span class="meta meta_property-name meta_property-name_css"><span class="support support_type support_type_property-name support_type_property-name_css">text-shadow</span></span><span class="meta meta_property-value meta_property-value_css"><span class="punctuation punctuation_separator punctuation_separator_key-value punctuation_separator_key-value_css">:</span> <span class="constant constant_numeric constant_numeric_css">2</span><span class="keyword keyword_other keyword_other_unit keyword_other_unit_css">px</span><span class="constant constant_numeric constant_numeric_css"> 2</span><span class="keyword keyword_other keyword_other_unit keyword_other_unit_css">px</span> <span class="constant constant_other constant_other_color constant_other_color_rgb-value constant_other_color_rgb-value_css"><span class="punctuation punctuation_definition punctuation_definition_constant punctuation_definition_constant_css">#</span>055B98</span><span class="punctuation punctuation_terminator punctuation_terminator_rule punctuation_terminator_rule_css">;</span></span></span></span></pre>

While most mortals won&#8217;t get to enjoy the effect, you don&#8217;t develop just for mere mortals, do you? Kick your game up a notch.

 [1]: http://apple.com/safari
 [2]: http://lighthouseapp.com
 [3]: http://timshadel.com/wp-content/uploads/2007/06/583276709_b02c53bfe2.jpg?v=0
 [4]: http://www.youthspecialties.com/articles/topics/technology/word_up.php
