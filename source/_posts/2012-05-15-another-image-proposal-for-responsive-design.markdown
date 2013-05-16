---
layout: post
title: "Another image proposal for responsive design"
date: 2012-05-15 10:17
comments: true
categories: [rwd, images, whatwg, w3c] 
---

There are a few ideas floating around now to deal with images and media queries. There are 
all [mostly](http://www.w3.org/community/respimg/2012/05/13/an-alternative-proposition-to-and-srcset-with-wider-scope/) [inefficient](https://github.com/Wilto/respimg) [ideas](https://gist.github.com/2701939), so I'm throwing my hat in the ring.

<!-- more -->

The `picture` element solution adds too much markup. The whatwg proposal is just ugly as heck and doesn't leverage any existing valid attributes. The meta tag/mediaquery technique seems close, but I think that can be improved.

Let look at the `link` element:

{% codeblock lang:html %}
<link 
	rel="stylesheet" 
	href="smartphone.css" 
	media="screen and (max-device-width: 480px)">
{% endcodeblock %}

What about other valid attributes we can add to that:

{% codeblock lang:html %}
<link
	rel="media"
	media="screen and (max-device-width: 480px)"
	type="low">
{% endcodeblock %}

The attribute `rel` associates a relationship to that mediaquery and is valid. `media` is a new value.

the `type` attribute is also valid, but the value is not implemented. 

This can be used in `img` elements as such:

{% codeblock lang:html %}
<img src="myimage.jpg" lowsrc="myimage-phone.jpg">
{% endcodeblock %}

`lowsrc`, remember that? Why not `highsrc` or `tabletsrc` or `tvsrc`? It would be up to browsers to only pull the correct src based on the alternate link. Browsers look for hooks for alternate now. This also has the benefit or not dealing with paths, unless you need to.

{% codeblock lang:html %}
<img src="myimage.jpg" lowsrc="" tvsrc="tvimage.jpg" highsrc="http://cdn.bigimages.org/myimage.jpg">
{% endcodeblock %}

With a path in the href attribute, maybe we can do this:

{% codeblock lang:html %}
<link
	rel="media"
	href="/phone-images/"
	media="screen and (max-device-width: 480px)"
	type="low">
<img src="myimage.jpg" lowsrc="myimage.jpg"> // `lowsrc` resolves to '/phone-images/myimage.jpg' 
{% endcodeblock %}

I believe that this method gives the greatest control, smallest footprint, provides backward compatibillity and the smoothest path to adoption of any techniques that have made the rounds lately. The picture element is just too much verbosity and I can't imagine what a page with 20 images would look like. The srcset syntax is a joke and not leveraging media queries at all. Thoughts?
