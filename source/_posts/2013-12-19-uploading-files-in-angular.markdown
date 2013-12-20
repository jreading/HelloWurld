---
layout: post
title: "Uploading Files in AngularJS"
date: 2013-12-19 20:45
comments: true
categories:  [angular, web dev, progressive enhancement] 
---

Of all the things that AngularJS makes easy, files uploads aren't one of them. You can grab some [OPC (other peoples' code)](https://github.com/danialfarid/angular-file-upload) or ignore IE9. 

<!-- more -->
```html template.html
<input 
	type="file" 
	onchange="angular.element(this).scope().myController.uploadFile(this.files[0]);"
/>

```


```js controller.js
var uploadFile = function(file) {
 
	var formData = new FormData();

	$scope.$digest();

	formData.append('file', file);

	$http({
		method: 'POST',
		url: 'url-to-accept-file',
		data: formData,
		headers: { 'Content-Type': undefined },
		transformRequest: function(data) { return data; }
	})
	.success(handleSuccess)
	.error(handleError);
}
```