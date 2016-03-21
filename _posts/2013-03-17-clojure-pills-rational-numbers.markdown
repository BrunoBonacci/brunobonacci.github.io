---
layout: post
title:  "Clojure Pills: rational numbers"
date:   2013-03-17 21:00:00
categories: [development]
tags: [Clojure]
---

A rather unique and interesting feature of Clojure (and Lisp derived languages) is the first class support for rational numbers.

``` Clojure
1/3
-5/3
(type 1/3)
;= clojure.lang.Ratio
```

Rational arithmetic is also supported:

``` Clojure
(- 3/5 (+ 1/3 4/5))
;= -8/15
```

And it does an automatic simplification when possible

``` Clojure
10/25
;= 2/5
```

Be careful when mixing rationals with floating point numbers as the result will default to Double (and lose precision).

``` Clojure
(+ 1/3 0.3)
;= 0.6333333333333333
(type (+ 1/3 0.3))
;= java.lang.Double
```

If you wish to preserve rationals when mixed with floating points in computations you can use the rationalize function.

``` Clojure
(rationalize 0.3)
;= 3/10
(+ 1/3 (rationalize 0.3))
;= 19/30
(type (+ 1/3 (rationalize 0.3)))
;= clojure.lang.Ratio
```

The caveats of using rational is that the performance drops drastically in favour of precision.
