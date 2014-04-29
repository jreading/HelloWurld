---
layout: post
title: "On Angular $resource"
date: 2014-04-29 17:12
comments: true
categories: [angular, web dev, rest]
---

It is said that your services should always be heavier than your controllers. That's a generally a good architectural metric, but not at the expense of simplicity; particularily for REST services. 

Here's a super simple approach in Angular that I've found that keeps some cruft from your controllers.

<!-- more -->
There's alot of FUD about angular providers, services, and factories [(see this)](http://codeofrob.com/entries/you-have-ruined-javascript.html), but the reality is that Angular $resource is super convienent for REST services [(here's a good review)](http://www.bennadel.com/blog/2433-using-restful-controllers-in-an-angularjs-resource.htm). It seems to lack some heft at times and my REST services do often look as skinny as a Williamsburg hipster. This leads people to use the more raw $http service and write a ton of code. There's a niftier way.

Often you will need to massage data in and massage data out to get the it match your model-view. Remember the single greatest thing about Angular is the MVVM, two-way binding. It's too much to ask of your REST model to match completely with your view, so you need to tweak it first.

Thankfully, angular gives us `transformRequest` and `transformResponse`.


```javascript services.js
app.factory('ThatThing', function($resource) {
	return $resource('/REST/ThatThing/:id', {
		id: '@id'
	},
	{
		get: {
			method: 'GET',
			transformResponse: function(data) {
				var newData = {'sup': 'playa', 'data': angular.fromJson(data)};
				return newData;
			}
		}
	});
});

```

```javascript controllers.js
ThatThing.get(function(data){
	console.log(data);	// {'sup':'playa', 'data': {...}}
});
```

You can munge the day away in that transformResponse function and pass it back to your view.

POSTS and PUTS can tweak data as well:

```javascript services.js
app.factory('ThatThing', function($resource) {
	return $resource('/REST/ThatThing/:id', {
		id: '@id'
	},
	{
		get: {
			method: 'GET',
			transformResponse: function(data) {
				var newData = {'sup': 'playa', 'data': angular.fromJson(data)};
				return newData;
			}
		},
		update: {
			method: 'PUT',
			transformRequest: function(data, headers) {
				var newData = {'hey': 'girl', 'data': data};
				return angular.toJson(newData);
			}
		}
	});
});
```

```javascript controllers.js
ThatThing.update({id:5},{'foo':'bar'},function(data){ 
	// Request Payload: {"hey":"girl","data":{"foo":"bar"}}
});
```
Now, you can get crazy in your services and let your controllers do what they are supposed to: *very little*.