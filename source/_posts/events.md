---
title: Events in Javascript
date: 2016-10-18 22:23:17
tags: Javascript
---
# Register Events

## **1. inline**
* on + eventType 
```html
<select onchange="alert('changed')">
</select>
```
* Don't use it. separating behavior and structure

<!-- more -->

## **2. traditional**
```javascript
element.onclick = doSomething;
```
* Drawback
	* onclick property can contain only one function
	* what if i want to register multiple event handlers for one event?
		* **flexible resgistration**
		```javascript
		var old = (element.onclick) ? element.onclick : function() {};
		element.onclick = function() {old(); secondHandler()}
		```
## **3. W3C**
* addEventListener
```javascript
element.addEventListener('change', doSomething, false)
// false argument means this handler should be executed in the bubbling phase
// else means in the capturing phase
```
* Advantage 
	* add as many event listeners as we want. no order for handlers' firing
	* feel free to remove specific handler

## **4. Microsoft**
* attachEvent
```javascript
element.attachEvent('onclick', doSomething);
```
* Drawback
	* this keyword in the handler refers to window.
	* why not refer to event's target?
		* because the event handling function is referenced, not copied.

# Register Events in JQuery
* namespace of event
```javascript
$(document).bind('click.handler1', function() {console.log('1')});
$(document).bind('click.handler2', function() {console.log('2')});

$(document).unbind('click.handler1'); //unbind specific event handler
$(document).unbind('click'); //unbind all click events
$(document).unbind(); //unbind all events attached to document
//$._data(document, "events") get all the events
```
* compatibility issue has already been solved



