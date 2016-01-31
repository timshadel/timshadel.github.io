---
layout: post
title: Testing Stuff with Variability
---

One of the things I ran into when building [simple-secrets][1] was that I needed
to prove that the time it took the same amount of time to do two different
things. The problem was that there was enough variability in how long it took
to do one thing that it was hard to be sure that the other thing took just
as long. I wanted to run Thing A 1,000 times and then run Thing B 1,000 times
and then have _some_ way to tell if Thing A took just as long as Thing B.
_(Hint: you can't just compare the average time taken.)_

> How educated is my reader here? I feel like I'm insulting them.

<blockquote class="pullQuote">You've got something that has a decent amount of
variability to it, and you're trying to tell if it's better, worse, or the same
as the last run.</blockquote>

There's a million places that we need this skill in computing. Perhaps you're
trying to make a part of your API faster, or you're testing how well your app
uses battery life on an iPhone. These things have variation in them, so we
need to use the right tools know if we've made a dent or not.

 [1]: https://github.com/timshadel/simple-secrets

<!---more-->

I am not a statistician. But in statistics there's basically two answers: the
Skeptic's Answer, and the one that is so clear it must convince even the Skeptic.
When I wrote the [timing test][2] for simple-secrets, I needed to make sure that
the Skeptic always won—that there was no way to prove that Thing A took longer
than Thing B. I needed a tool to tell me how confident it was that my 1,000 runs
of Thing A had a different kind of variation than my 1,000 runs of Thing B, and
then I needed to test to fail whenever a difference could be detected.

The tool I used is called a [two-sided t-test][3]—don't freak out, all you do is
give it two arrays and it gives you back a number. So you need to ask yourself
how hard you need to work to convince the Skeptic. The Skeptic always believes
there's no real difference between the two arrays, just random noise. Will your
Skeptic believe if he sees there's a 60% chance there's a real difference, or
only if there's a 99% chance?

In my case the Skeptic was a hacker, and I figured he'd go with weak evidence,
so I made my test fail if there was anything more than a 90% chance that the
two timing arrays were different (remember, my test only passes if Thing A
takes just as long as as Thing B).

> I got to this point without talking about randomly failing unit tests when
> you simply use a threshold plucked out of the air.

So how do you get the 90% check? It's pretty easy. You take your Skeptic's
percentage-to-convince and you go to the [table in Wikipedia][4]. Your
percentage-to-convince picks the column. To choose the row you need to know how
many timing samples you'll collect from each thing—that's the row you use. For
1,000 samples you just use the ∞ row. Now, if the number you get from the
two-sided t-test is _less_ than the number from the table, then the Skeptic
wins. Otherwise the Skeptic is convinced there's a real difference between the
two groups.

> Zed's [rant][5] goes somewhere.

 [2]: https://github.com/timshadel/simple-secrets/blob/master/test/primitives.test.js#L212-L227
 [3]: http://www.ats.ucla.edu/stat/mult_pkg/faq/general/tail_tests.htm
 [4]: https://en.wikipedia.org/wiki/Student%27s_t-distribution#Table_of_selected_values
 [5]: http://zedshaw.com/archive/programmers-need-to-learn-statistics-or-i-will-kill-them-all/
