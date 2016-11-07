---
title: module pattern in nodejs
date: 2016-10-29 11:07:19
tags: nodejs, module pattern
comments: true
---
# CommonJS
* code example:
```javascript
	var lib = require("lib");
	function foo() {
		lib.log("Hello, the lib dependency is included successfully");
	}
	//Modules use exports to make things available, like function, object, prototype.
	exports.foobar = foo; // here we export a named function
```
<!-- more -->
* module.exports vs exports
	- :http://darrenderidder.github.io/talks/ModulePatterns/#/
	- Don't confuse it with ES6 Module:http://es6.ruanyifeng.com/#docs/module
* better suited for server side for its synchronous nature
* pros and cons
	- pros: it supports objects, functions, constructors, strings, JSON and many other types of modules
	- cons: no concept of File I/O

# RequireJS
* a script loader, AMD-compliant
* code example:
```javascript
	define(["lib"], function(lib) {
		function foo() {
			lib.log("Hello, the lib dependency is included successfully");
		}
		// export foo to other module as foobar
		return { foobar: foo };
	});
```
* better suited for client side (browser) for its asynchronous nature
* pros and cons
	- pros: 
		- covers concerns such as I/O, File system, Promises and more
		- supports unwrapped modules
	- cons: only support objects as modules.