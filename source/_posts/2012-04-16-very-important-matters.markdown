---
layout: post
title: "Very Important Matters"
date: 2012-04-16 17:07
comments: true
categories: [ux, ui, js] 
---

I was recently asked to put together a list of the most important issues in UI development on the web today and here's what I came up with:
<!-- more -->

	Modules: AMD, CommonJs & ES.next Patterns & Structure.
	Responsive Design & RESS: Device Agnostic UI vs. Server Side Sniffing
	Less, Sass & Stylus: Why not?
	HTML5 beyond the ‘section’ tag: AppCache, WebWorkers, LocalStorage, & DnD
	ES.next & Harmony: the next JS
	JavaScript MVC: when, where & how?
	Testing & Development best practices: TDD vs. CI vs. throwing it at wall 

Let's dig in...

Modules: AMD, CommonJs & ES.next Patterns & Structure.
--

There was a recent dust-up about [AMD](http://tomdale.net/2012/01/amd-is-not-the-answer/) [lately](http://alexsexton.com/blog/2012/03/my-thoughts-on-amd/) and I was heartened to see (from my own annecdotal research at jsconf) that AMD is a good thing and pre-processing (or not preprocessing) isn't a dealbreaker. There's still a ton of use cases for client-side dependency management and the module pattern is a no-brainer, particularly in a CMS. AMD seems to be dominating now mainly due to require.js and Dojo. [Real modules in es harmony](http://addyosmani.com/writing-modular-js/) will end the debate (not likely).

Responsive Design & RESS: Device Agnostic UI vs. Server Side Sniffing
--
What's responsive design? Never heard of it...

Ok, I don't live in a treehouse. This is obviously the next sliced bread in the web dev world and still in the early stages. There are [problems](http://www.vannavada.com/?p=35) and ingenious solutions, so what does this all mean for the future. And how do we do our best from a technical perspective, but also from a user expereince perspective. Apparently, there's [still](http://www.useit.com/alertbox/mobile-vs-full-sites.html) [some](http://www.netmagazine.com/opinions/nielsen-wrong-mobile) [debate](http://www.netmagazine.com/interviews/nielsen-responds-mobile-criticism). (Nielsen's MOSTLY wrong).

Less, Sass & Stylus: Why not?
--

More interweb dustups lately, this time with [LESS.js](https://github.com/cloudhead/less.js/issues/49#issuecomment-4628059). I've been hearing alot of people sticking with SASS for this very reason (and the bigger issue of less.js looking like abandonware). I've also been hearing about Stylus, but to me, it looks a bit like a [scrHipster motivational exercise](https://github.com/twitter/bootstrap/issues/3057).

HTML5 beyond the ‘section’ tag: AppCache, WebWorkers, LocalStorage, & DnD
--
Remy Sharp's jsConf talk was truly one of the best and the stuff he said just made sense. [Look for yourself](http://speakerdeck.com/u/rem/p/build-anything).

ES.next & Harmony: the next JS
--
Brenden Eich is still the man. I'm not counting on Douglas Crockford's "CoffeeScript: The Good Parts" to hit bookstores soon, but looks like [ES Harmony will do it for us](http://blip.tv/jsconf/jsconf2011-jeremy-ashkenas-5258082). Don't be left behind. It'll be interesting to see native classes in js and all that [sugar](http://edtsech.github.com/).

JavaScript MVC: when, where & how?
--

Backbone.js, 'nuff said; that's the how... The problem is sometimes people forget the "when and where?" Js MVC use case is narrower than people realize, but when done right it's a pretty little thing. And Ember? It falls into the same place as jQMobile does for me. Too much sacrifice given for rapid development.

Testing & Development best practices: TDD vs. CI vs. throwing it at the wall
--

I admit I dont do enough testing. There I said it... I really do want to use [Grunt](https://github.com/cowboy/grunt) though. And I was floored by the idea that [Jacob Thornton](https://github.com/fat) put forward at jsConf about just releasing test suites and specs and letting the libraries write themselves. Kudos to anyone who does that on github first.

----
This is the conference I'd like to see. What'd I forget?

