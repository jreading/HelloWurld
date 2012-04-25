---
layout: post
title: "The Importance of Optimizing JavaScript for Responsive Design"
date: 2012-04-25 13:17
comments: true
categories: [js, rwd] 
---

So many responsive design solutions involve client-side detection, polyfills, data-attrs and event remapping. This all works fine, but as more and more sites begin to move toward a responsive design the importance of JavaScript optimization is more relevant than ever. More often than not, implementing a responsive design means more JavaScript and more logic. The Kb size debate for responsive sites is important, but often overlooked is the computational impact. 

I’m not a micro-optimization troll (there’s plenty of that out there), but it’s shocking how some devices perform with the simple things we all take for granted. I would argue that for most devices, processing and latency are more important than Kb size.

So let’s take a look…
<!-- more -->
One of my favorite talks from JsConf 2012 was [JDalton’s](https://twitter.com/#!/jdalton) “The Hidden Cost of Javascript Natives.” While admitting that some stuff was getting into unnecessary micro-optimization, the tests he showed were quite interesting. 

I thought I would look at some of these things from a mobile/RWD perspective. It’s important to remember that I’m not really looking at how the tests perform against each other, but how the devices perform against Chrome, Firefox and Safari. Often there’s not going to be an appreciable difference for most things, these tests illustrate that Mobile Safari isn’t going to process js as fast as Chrome 18.

[For..In loops](http://jsperf.com/touch-events-exists) 
--

These are often called out as being hogs (the “for” loop still kills everything else), but they are necessary for doing capabilities tests.

![Alt text](http://content.screencast.com/users/JReading/folders/Jing/media/da63f2fc-d53c-4d27-96e9-285212f0adcb/00000065.png)

It’s amazing how poorly some devices perform. I’m not saying that Modernzr is going to kill your Android 2.0 phone, but these things add up.

[Data Attributes](http://jsperf.com/jquery-data-vs-html-data-reading/3)
--

The staple of any responsive images implementation performs horribly. Interesting that only mobile Safari and Webkit prefer the native dataset implementation.

![Alt text](http://content.screencast.com/users/JReading/folders/Jing/media/73c69e5f-6184-4ee6-ba25-0d8449b8fda5/00000064.png)

[Here’s another look at it](http://jsperf.com/data-vs-attr-data/4).

[jQuery Prepend/Append](http://jsperf.com/prepend-append)
--

Optimization zealot’s favorite pariah ([and rightfully so](http://jsperf.com/jquery-vs-native-appendchild)), this is a biggie on mobile.

![Alt text](http://content.screencast.com/users/JReading/folders/Jing/media/509a5f42-73b7-4d48-a213-ebc33a712c63/00000066.png)

2000 op/sec is ghastly, but how many items are you appending really? In a client-side MVC, it could get into the hundreds. It's all cumulative after all...

[DOM access](http://jsperf.com/optimising-dom-access)
--

Going to the DOM is always expensive and on mobile, it’s going to cost an arm and a leg.

![Alt text](http://content.screencast.com/users/JReading/folders/Jing/media/9409fc16-7f32-4f7c-ad10-33fa637703b2/00000067.png)

This is a good example of optimizing code in general for performance.

Chrome Timeline Panel
--

A great [post](http://gent.ilcore.com/2012/04/optimizing-with-timeline-panel.html) on debugging optimizations popped up recently and it’s definitely something to do on your sites now. Just know that whatever you see there in Chrome is probably amplified by a hundred on mobile devices.

Conclusion
--
Optimizing for performance is important regardless of the final client’s processing power, but it’s so much more important for a responsive design site. Piling on more and more JavaScript seems misguided and we should keep that in mind when trying to future-proof sites. I’d love to see how these tests stack up on other devices, so if you have web access on your toaster; please run them!




