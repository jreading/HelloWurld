---
layout: post
title: "Responsive Modules"
date: 2012-04-19 09:25
comments: true
categories: [js, rwd, amd] 
---
A lot has been said about Responsive Design lately (every time I type that and Ethan Marcotte gets shinny penny). It’s primary a design movement, but the real problem it tries to solve is making content “[flow like water]( http://www.slideshare.net/yiibu/reset-the-web).” To me it’s not about media queries, or 100% image widths, it’s about: one url, one codebase, and future-proofing new capabilities to maximize user experience.

Therefore, I give you: **Responsive Modules** (send your [pennies](https://twitter.com/#!/johnnyreading)).
<!-- more -->
Ok, I’m not reinventing anything; it’s just a way to leverage JavaScript’s prototypal inheritance, and future proof functionality through AMD dependency management.

**Backstory**: I liked Classes in JavaScript before it was [cool]( http://prototypejs.org/learn/class-inheritance) (wait, was that ever cool?). I’m bummed to see them [facing headwinds]( http://brendaneich.com/2011/10/jsconf-eu/) in ES6. They aren’t totally necessary in JS, but it’s nice to have a super() and init() built in to your modules. [There]( http://www.dustindiaz.com/klass) [are](http://jsclass.jcoglan.com/) [many]( http://coffeescript.org/#classes) [options]( http://ejohn.org/blog/simple-javascript-inheritance/). My personal favorite is John Resig’s, since it’s the easiest sell ("hey, that jQuery guy made it!"). There's a github of this setup [here](https://github.com/jreading/JsModuleBoilerplate) minus the responsive bit.


Enough chatter, the code...
---
Here's a carousel widget written in jQuery:
 
{% codeblock carousel.js lang:js %}
define([],function() {
	namespace.Carousel = namespace.Class.extend({
		options: {
			//options here
		},
		init: function() {
			this._super(opts, element);
			//instance vars live here
			this.intPos;
			this.attachEvents();
		},
		attachEvents: function() {
			$('.arrow-next',this.element).on('click',$.proxy(function(){
				this.scrollNext();
			},this));	
			
			$('.arrow-prev',this.element).on('click',$.proxy(function(){
				this.scrollPrev();
			},this));
		},
		scrollNext: function() {
			// calculate the intPos to move next here
			this.element.css({'left': this.intPos}); //css3 animation
		},
		scrollPrev: function () {
			//calculate the intPos to move previous here
			this.element.css({'left': this.intPos});
		}
	});
}
{% endcodeblock %}

Ok, so we have a little module that extends class, inits, bind itself to the 'this.element' data, attaches click events to arrows and scrolls the container. Cool... 

But what about touch devices? We don't even have the arrows on the mobile layout. We want an invisible gesture, like a swipe.

So, we write another module for touch devices that includes the same methods for scrolling, but has a different 'attachEvents' method. But now we aren't being [DRY](http://en.wikipedia.org/wiki/Don't_repeat_yourself). Or we can just add another method for swipe and conditionally call that, but now it's getting crufty...

AMD gives us a better way:

{% codeblock carousel.touch.js lang:js %}
define(['carousel'],function() {
	namespace.Carousel = namespace.Carousel.extend({
		attachEvents: function() {
			this.element.on('touchstart',$.proxy(function(e){
				this.startPos = e.originalEvent.touches[0].pageX;
			},this));	
			this.element.on('touchmove',$.proxy(functione(e){
				this.endPos = e.originalEvent.changedTouches[0].pageX;

				if (this.startPos < this.endPos) {
					this.scrollPrev();
				} else {
					this.scrollNext();
				}
			},this));
		},
	});
}
{% endcodeblock %}

Now we are only replacing the parts we need, staying DRY, and leveraging the prototype chain. This makes more sense when there are more shared methods, but you get the gist.

How's this work?
---

AMD allows for dependency management. The touch version of the script is dependent on the base carousel file and extends itself. Because we aren't including the _super method in there, it's overriding the entire method, giving us a version with touch events. 
Now it's just a matter of adding the right script for each device (this is where R+/RESS fits nicely).

One way to load this on the client would be:

{% codeblock head lang:js  %}
Modernizr.load({
	test: Modernizr.touch,
	yep: 'carousel.touch.js',
	nope: 'carousel.js'
});
{% endcodeblock  %}


Ways to improve
---

We could leave the 'attachEvents' method empty and have versions for each capability (carousel.touch.js, carousel.click.js, carousel.speech.js) that way if we had client-side dependency management happening (via require.js or curl.js for example, though [I hear that's bad](http://alexsexton.com/blog/2012/03/my-thoughts-on-amd/)) we wouldn't be carrying dead code around. We could also flip it around and have the touch events the default and make a carousel.click.js.

A better way would be to do AMD preprocessing and concatenate them all together (bonus points if your build script replaces the methods instead of just bundling the dependencies).

Regardless of execution, we are keeping the tenets of responsive design intact: keeping a common codebase, common url and future-proofing emerging capabilites without relying on loading more libraries or polyfills, or constraining the design.
