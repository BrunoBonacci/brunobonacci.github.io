---
layout: post
title:  "Clojure Pills: rational numbers"
date:   2013-03-17 21:00:00
categories: Clojure
---

A rather unique and interesting feature of Clojure (and Lisp derived languages) is the first class support for rational numbers.

{% highlight Clojure %}
1/3
-5/3
(type 1/3)
;= clojure.lang.Ratio
{% endhighlight %}

Rational arithmetic is also supported:

{% highlight Clojure %}
(- 3/5 (+ 1/3 4/5))
;= -8/15
{% endhighlight %}

And it does an automatic simplification when possible

{% highlight Clojure %}
10/25
;= 2/5
{% endhighlight %}

Be careful when mixing rationals with floating point numbers as the result will default to Double (and lose precision).

{% highlight Clojure %}
(+ 1/3 0.3)
;= 0.6333333333333333
(type (+ 1/3 0.3))
;= java.lang.Double
{% endhighlight %}

If you wish to preserve rationals when mixed with floating points in computations you can use the rationalize function.

{% highlight Clojure %}
(rationalize 0.3)
;= 3/10
(+ 1/3 (rationalize 0.3))
;= 19/30
(type (+ 1/3 (rationalize 0.3)))
;= clojure.lang.Ratio
{% endhighlight %}

The caveats of using rational is that the performance drops drastically in favour of precision.


