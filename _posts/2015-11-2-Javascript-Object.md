---
layout: post
title: Javascript Object
---

# Javascript

This artical is based on EMCScript5. There are more rich features, APIs in EMCScript6, especially Class, Inheritance like Java or C++. I seperate Javascript into three parts, Objects, Prototype, OOP. Firstly we must know javascript objects.

## Javascript Objects

Javascript has one complex data type, the Object data type, and five simple data types: Number, String, Null, Boolean and Undefined. Object data type is mutable, while the five data types is immutable.

### What's Object

And object is an unordered list of primitive data types that is stored as a series of key-value pairs.   

Consider this simple example:

```javascript
var mObject = { name:"name", age:23, 20:"zhang" };
```

Each item is called property. Properties name can be a string or a number. If the property name is number, it should be accessed with the bracket notation.

Consider the above example:

```javascript
mObject.name; mObject["name"]; mObject["20"];
```

### Reference data type and primitive data type

Object is stored as a referance, while primitive data type is stored directly on the variable.   

Consider this example:

```Javascript
var first = "first";
var second = first;
first = "first_1";
console.log(first); // "first_1"
console.log(second); // "first"
```

```Javascript
var first = { name:"Allen" };
var second = first;
first.name = "Kobe";
console.log(first.name); // "Kobe"
console.log(second.name); // "Kobe"
```
When we change first.name property to "Kebe", the second reflects the change becuase it only has a reference to it.

### Create Objects

There are two commom ways to create objects:

1. Object literals   

```Javascript
var mObject = { name:"zhang", age:23 };
```
2. Object constructor   

```Javascript
var mObject = new Object();
mObject.name = "zhang";
mObject.print = function(name){
    console.log(name);
}
```

### Practical patterns for creating objects

1. Construtor pattern

```Javascript
function Person(name, age){
	this.name = name;
	this.age = age;
	this.showName = function(){
		console.log(this.name);
	}
}
```

2. Prototype pattern

```Javascript
function Person(){
}
Person.prototype.name = "Zhang";
Person.prototype.age = 23;
Person.prototype.showName = function(){
	console.log(this.name);
}
var person = new Person();
person.showName();
```

### Deleting propertyies

```Javascript
delete person.name;
```

### Serilize and Deserilize objects

To transfer your objects via HTTP, you can use JSON.stringify to serilize your object.

```Javascript
var christmasList = {mike:"Book", jason:"sweater", chelsea:"iPad" }
JSON.stringify (christmasList);
​// Prints this string:​
​// "{"mike":"Book","jason":"sweater","chels":"iPad"}"  
​
​// To print a stringified object with formatting, add "null" and "4" as parameters:​
JSON.stringify (christmasList, null, 4);
// "{
    "mike": "Book",
    "jason": "sweater",
    "chels": "iPad"​
}
```
# Javascript Prototype

To undertand prototype you must understand objects in javascript.

There are two interrelated concepts with prototype in javascript

1. Every javascript function has a prototype property and you can attach properties and method to property when you want implement inheritance.

2. An object's prototype property points to it's parent

If an object is created with an literal object, it's prototype is Object.prototype. 

If an object is created from construtor

## OOP in javascript

Inheritance(objects inherit features from other objects), Polymorphism(object may share the same interface, however the implementaion of the interface may differ), Encapsulation(each object is responsible for specific task).

```javascript
function User(name,age){
	this.name = name;
	this.age = age;
	// private properties, can't be changed by instances
	var newDate = new Date();
	// CONSTANT variable, available to all instances, also private
	CONSTANT_STRING = "cettco";
	// This is the only way to access the private varaible.
	this.getConsString = function(){
		return CONSTANT_STRING;
	}
}
User.prototype.construtor = User;
User.prototype.save = function(score){
}
function Student(name, age){
	User.call(this, name, age);
}
```

* First write a parent object:User
* In the child's constructor, Call the Parent object's call method.
* fun.call(thisArg[, arg1[, arg2[, ...]]]). A different this object can be assigned when calling an existing function. this refers to the current object, the calling object. With call, you can write a method once and then inherit it in another object, without having to rewrite the method for the new object.