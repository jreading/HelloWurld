---
layout: post
title: "Desktop First: A Reverse Do-Nothing, Responsive Anti-Pattern"
date: 2012-03-22 09:33
comments: true
categories: 
---
Well now that I got your attention...


When looking for a good strategy for implementing a responsive design, web devs are bombarded with tons of techniques, libraries, polyfills, and workarounds. Most of the time, we don't need them. <!--more-->

The "mobile-first" approach towards building a site can necessitate the use of polyfills for legacy desktop browsers or just [an awful looking desktop experience](http://starbucks.com). 

Looking at [this comment from a smashing mag post on responsive techniques](http://coding.smashingmagazine.com/2011/08/10/techniques-for-gracefully-degrading-media-queries/#comment-545128), this seems like the simpliest approach considering there's no need to worry about fallbacks, polyfills, and other workarounds. Why do we have respond.js, Modernzr.mq, jQueryMobile CSS hacks and the like...?

{% codeblock desktop-first.css lang:css %}
#main {
	width: 960px; /*oh so fixed width*/
}

header nav li {
	float: left;
}

@media only screen and (max-width: 400px) {
	#main {
		width: 100%;
		max-width: 400px;
	}
	header nav li {
		float: none;
	}
}
{% endcodeblock %}

Combine a few (read: keep it simple) of these with [aggressive](http://www.leemunroe.com/ie-rounded-corners-css3/) [enhancement](https://twitter.com/#!/zeldman/statuses/170930936718950400), and a few [fully responsive techniques](http://www.leemunroe.com/adaptive-responsive/) and it seems like everything else is just cruft. 

What if you want to have access to that media query capability in your js? Well, then [you're doing it wrong](http://www.nczonline.net/blog/2012/01/03/css-media-queries-in-javascript-part-1/). Styles shouldn't ever be bound to so tightly to your app or widget, or even content for that matter.

Large images in CSS? Don't do it. Use fluid images or data-attrs to lazy load the right size from the markup.

One last thing, if we take a trending approach [such as this by Thierry Koblentz (who's a genuine hero)] (http://coding.smashingmagazine.com/2012/03/22/device-agnostic-approach-to-responsive-web-design/) of "device agnostic," there's still a presumption that it's oldIE or media-query capable. Not a totally unsafe assumption, but when we talk about the "internet of things," who knows...
