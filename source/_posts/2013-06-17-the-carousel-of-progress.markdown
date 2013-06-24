---
layout: post
title: "The Carousel of Progress"
date: 2013-06-17 16:29
comments: true
categories: [js, css, html, web dev, everything] 
---
After jsConf this year, I took the family to Disney World (what a guy, right?). One ride that I had never been on before was the [Carousel of Progress](http://en.wikipedia.org/wiki/Walt_Disney's_Carousel_of_Progress); a journey through time that celebrates change. Professionally, I felt like I've been on that ride without being allowed to get off for the last few years.

<!-- more -->
Calling yourself an expert these days says alot. You're probably not one, but that doesn't matter anyway... Progress marches on and if you're paying attention, you're in for a good ride.

The modern web is growing by leaps and bounds lately and it can seem hard to keep up. So, here's a list of some things that are on the horizon or in the mainstream that were essentially nonexistent a few months (or weeks) ago. I have no doubt this list will look completely different by the end of the year. I would expect nothing less.


HTML/Web APIs
-
*	Shadow DOM

Are you ready to start churning out web components? Are you psyched to see the imminent demise of the iframe? [Cool, me too](http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/).

* 	AppCache

It's alive and well. [Better get up to speed in all its quirks](http://blip.tv/jsconf/jsconf2012-jake-archibald-appcache-douchebag-6143723).

*	Web Storage

The days of the legacy Netscape "magic cookie" are behind us. [Hurray](https://developer.mozilla.org/en-US/docs/Web/Guide/DOM/Storage)!

*	WebRTC

So, so many cool things are going to come of webRTC. Realtime communication is going to be ubiquitious. [Check out all these demos](https://webrtc-experiment.appspot.com/). 

*	WebGL

It's 2013, I shouldn't have to hear "Flash could do that 10 years ago." Thanks [WebGL](http://learningwebgl.com/blog/)!

*	Canvas

[Canvas](http://css-tricks.com/learn-canvas-snake-game/) is one of the technologies that can build a career. My advice is to learn more than just canvas.

*	Semantics

Still waiting for a set of hard standards in terms of semantics. Doesn't mean this is extremely important to SEO, internationalization and plain, ole' good form. This is one of those "strong opinions weakly held" moments.

*	Sockets

Sockets are becoming indespensible. Yeah, flash "could do it years ago," but browsers [can do it today](http://www.html5rocks.com/en/tutorials/websockets/basics/).

* Proximity API

Damn, FireFox is really doing some cool stuff lately. Here's in glimpse into the future: the [proximity API](https://hacks.mozilla.org/2013/06/the-proximity-api/).

JS
-
*	Libraries: Backbone, Angular, et al.

You've clearly been under a rock if you don't have one of these under your belt. MV* is a narrow use case on the front-end, but gaining more and more ground (Angular looks to unseat Backbone recently). Take a look at [Google's Polymer](http://www.polymer-project.org/) (which is built on web components).

*	Modules, Require.js

Climb out from under there and get on board. [Js Modules](http://corner.squareup.com/2013/02/es6-module-transpiler.html) look to be native in ES6.

* 	Promises

Again, this is something that will be [native someday](http://domenic.me/2012/10/14/youre-missing-the-point-of-promises/) and in jQuery for ages. [Here's the standard](http://promises-aplus.github.io/promises-spec/). [Promises, promises](https://www.youtube.com/watch?feature=player_detailpage&v=H8Q83DPZy6E#t=30s).

*	Strict Mode

[Get used to it](http://edanhewitt.com/strict-javascript/). It's going to be a requirement soon enough.

*	Testing

Testing is the new normal. [Another great post by Ms. Murphey](http://alistapart.com/article/writing-testable-javascript).

*	Node/NPM

If I was writing a similar article for backend developers this would be at the top of the list. But for the front-end, it's just not cool to say you can't use the terminal, run `npm install` and push to a cloud-based repository or production server. [Learn node](http://net.tutsplus.com/tutorials/javascript-ajax/node-js-for-beginners/) and don't be a hater. It's just not acceptable and so, so [NOT cool](http://www.youtube.com/watch?v=1e1zzna-dNw).

*	Patterns

Everyone agrees on the best pattern, so I almost didn't include this very [thorough list of popular javascript patterns](http://shichuan.github.io/javascript-patterns/). There's hardly any dissent on the best way to code. ;P In seriousness, the [AOP pattern](http://cujojs.com/) presented in cujo.js looks great.

*	ES6/7

[So much hard work](http://tc39wiki.calculist.org/es6/) goes into the TC39 committee, if you ever see a member, give them a hug. Brendan Eich mentions es7 at jsConf recently... Wha?? Also, an [awesome chart](http://kangax.github.io/es5-compat-table/es6/).


CSS
-

*	UPDATE 6/24/13: [Blend modes in Canary](http://blogs.adobe.com/webplatform/2013/06/24/css-background-blend-modes-are-now-available-in-chrome-canary-and-webkit-nightly/).

*	Painting Optimization

Painting Optimization is the new `for` loop optimization. [Pay attention](https://developers.google.com/events/io/sessions/325933151).

*   Scoped stylesheets

Another thing to come out of chromium. [Take a look and learn](http://updates.html5rocks.com/2012/03/A-New-Experimental-Feature-style-scoped).

*	Preprocessors

Sass, Stylus, Rework.  LESS couldn't survive its tortured past. Regardless, [they're here to stay](http://blog.teamtreehouse.com/how-to-choose-the-right-css-preprocessor).

*	Flexible box model

Finally a solution to the float vs. inline-block problem. And the 100% height problem. And so many other ancient layout issues. [So much better](http://coding.smashingmagazine.com/2011/09/19/css3-flexible-box-layout-explained/)...

*   Native grids

Damn, [this will be nice](http://www.w3.org/TR/css3-grid-layout/).

*	Web Animations & the GPU

When css keyframe animation first came out in webkit, I found it to be unusable from a performance point of view. Browsers have come far enough now that [it's reliable](http://css-tricks.com/snippets/css/keyframe-animation-syntax/). 

*	Filters, Shaders, Masking, Gradients, Shadows...

So [many](http://html5-demos.appspot.com/static/css/filters/index.html) [cool](http://www.adobe.com/devnet/html5/articles/css-shaders.html) [things](http://www.html5rocks.com/en/tutorials/masking/adobe/) you can do in css now.

*	@supports

Capabilities testing in css you say? [Cool](http://davidwalsh.name/css-supports).



Networks & Devices
-
*	Latency

I'm all about custom builds for mobile networks (inline all the things). [Latency is a killer in mobile](http://www.igvita.com/2012/07/19/latency-the-new-web-performance-bottleneck/).


Deployment, Build Processes, and Monitoring Services
-
*   [Github](http://github.com), [bitbucket](https://bitbucket.org/), [heroku](https://www.heroku.com/), [nodejitsu](https://www.nodejitsu.com/) 

Don't tell me you still use SVN.

*	[Travis CI](https://travis-ci.org/), [David](https://david-dm.org/) (he kinda looks creepy), [Grunt](http://gruntjs.com/), [Yeoman](http://yeoman.io/). 

You need to know all of them.

