---
layout: post
title: "Bootstrapping AngularJS in Existing Application Frameworks"
date: 2013-11-19 20:05
comments: true
categories: [angular, web dev] 
---
Lately, I've been spending alot of time in coding in AngularJS, in my case; porting existing functionality from an existing application. One challenge has been keeping the bulk of the application intact, while introducing an Angular architecture on top. Sometimes, it's just not feasbile to rewrite everything and one must take a modular approach. 

Thankfully, the Angular team provides us [angular.bootstrap.js](http://docs.angularjs.org/api/angular.bootstrap) ( which has nothing to do with that twitter boilerplate thing)...

<!-- more -->

It's always important to start with a good modular setup regardless of existing architecture. It's just easier to develop, collaborate, and version control your app when the files are broken out. By following [Brian Ford's advice](http://briantford.com/blog/huuuuuge-angular-apps.html) on structuring Angular apps, we have a basic setup that looks like this:

{% codeblock directory structure %}
angular-apps
├── js
│   ├── common
│   │   ├── controllers
│   │   ├── directives
│   │   │   └── datepicker.js
│   │   ├── filters
│   │   │   └── strings.js
│   │   └── services
│   ├── ourapp
│   │   ├── controllers.js
│   │   ├── directives.js
│   │   ├── bootstrap.js
│   │   ├── filters.js
│   │   └── services.js
{% endcodeblock %}

The files that are in `common` will be bundled with all of our Angular libraries (including [angular.bootstrap.js](http://docs.angularjs.org/api/angular.bootstrap)) and will be included on every page in our existing application via a Grunt build process.

For each module/app in Angular, the important file here is `bootstrap.js`, which will handle dependencies, and bind the Angular module/app to an element.  

{% codeblock ng-module-bootstrap.js lang:js %}
/*
	Angular Module
	@desc An AngularJS app in module form
*/

//define the angular app; include dependencies from angular & common
angular.module('ourApp', ['ngResource', 'common.directives.datepicker', 'common.filters.strings']);

//load dependencies with requireJS
require(['apps/ourapp/directives','apps/ourapp/controllers','apps/ourapp/services','apps/ourapp/filters'], function(directives, controllers, services, filters) {
	angular.bootstrap(angular.element($('#ourApp')), ['ourApp']);
});
{% endcodeblock %}

The app is bound to the element in the bootstrap method `angular.bootstrap(angular.element($('#ourApp')), ['ourApp']);`. 

You can see we are using require.js to handle the dependencies. A Grunt task to flatten the require dependencies is a clear choice. Now you'll be able to manage all your dependencies for that app outside of your existing application framework; quite useful if you need to build the backend for each change.

Now it's simply a matter of injecting the element and script tag with the bootstrap file from your existing application when needed. A Java/Scala/PHP Class to do this automagically is a good idea. 

{% codeblock backend injection on demand lang:html %}
<div id="#ourApp"><ourAppEl/></div>
<script src="angular-apps/ourapp/bootstrap.js" type="text/javascript"></script>
{% endcodeblock %}

Create a directive to load an HTML template can be the basis for all declarations, `<ourAppEL>` in this case. All of the directives, controllers, services, and filters for this app will refer to the Angular module we created in the bootstrap file:

{% codeblock ourapp/views/directives.js lang:js %}
//get the existing angular module; must be written this way for the ngminifier
angular.module('outApp').directive('ourAppEl', function(){
	return {
		restrict: 'E',
		replace: true,
		templateUrl: '../js/angular-apps/ourapp/views/main.html',
		controller: function($scope, $element, $attrs) {
			//stuff
		}
	};
});
{% endcodeblock %}

If you need another instance of your Angular app, your backend Classes should know this and you will only need the bootstrap code and element.
{% codeblock backend injection on demand lang:html %}
<div id="#ourApp"><ourAppEl/></div>
<script type="text/javascript">
	angular.bootstrap(angular.element($('#ourApp2')), ['ourApp']);
</script>
{% endcodeblock %}

Now the downside: *App Teardown*

There is still no great solution for this when using this approach (I'm working on it). I'm also confident the Angular core team will come up with something.

You can see more about that [here](https://github.com/angular/angular.js/issues/1537#issuecomment-10164971).


