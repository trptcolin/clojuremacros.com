---
layout: post
title: timebomb-comment
date: 2014-09-03
summary: Don't let your comments get out of date.
---

<a
href="https://github.com/runa-dev/kits/blob/d14d1853c238e758049d98c4558244f15aa17faa/src/kits/homeless.clj#L803-L809">`timebomb-comment`</a>,
from Runa (now <a href="http://www.stapleslabs.com/innovation-lab.html">Staples
Innovation Lab</a>), makes sure that comments stay up-to-date. This is pretty
serious business!

{% highlight clojure %}
(defmacro timebomb-comment
  "Used to comment things out that we want to force ourselves to come
   back to by a certain point in time in order to resolve later."
  [timestamp-long & body]
  `(if (<= ~timestamp-long (System/currentTimeMillis))
     (throw (Exception. "Timebomb comment has passed its due date."))
     (comment ~@body)))
{% endhighlight %}

I've definitely felt pain from old &amp; busted comments, and this kind of
thing would sure motivate me to keep anything remotely old out of the codebase.

