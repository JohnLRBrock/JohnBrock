---
layout: post
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Section 3: Objects"
permalink: "/john-brock-js/airbnb-styleguide-section-3"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. [Airbnb][airbnb], the online marketplace for housing rentals, has a high quality and 'mostly reasonable' style guide for JavaScript, a programming language that adds dynamic behaviors to web browsers. Some of the topics in the guide are a bit advanced for beginners. This "Explain Like I'm 50" (ELI50) series will act as a plain English companion-guide to the [Airbnb style guide][style guide], because good design principles shouldn't be out of anyone's reach.

This post will cover section 3 on **objects**, creating, and using them.

> # What the heck is an object?
Simply put an object is a way to **encapsulate** something in a way that can be used or modified later. Objects can have variables and functions (called **methods**) that act on them. The reason that objects are so useful is because you can create new objects that **inherit** properties from other objects. You could, for instance, make an object to represent a car which has variables to indicate it has an engine, four wheels, methods that let the user drive it. From there you can create other objects that inherit those properties from Car and add other ones like being able to drive itself. Programmers, being a lazy folk, do their best to follow something called the DRY principle ([Don't Repeat Yourself][DRY]). Objects are a useful way to package code for reuse in other places.


<br>
## Section 3: Objects
### [3.1][3.1]: Use the literal syntax for object creation. eslint: [`no-new-object`][no-new-object]

Although the new object syntax, `const myObj = new Object();`, isn't harmful it takes longer to write and can cause problems for you if you forget the `new`. Object literal syntax, `const myObj = {};`, is faster to write, easier to read, and harder to mess up. If you want to learn more about why we tend to use the second version, read the answers on this [stack overflow question.][SO object literal]

### [3.2][3.2]: Use computed property names when creating objects with dynamic property names.

JavaScript has a nifty feature that allows you to add or create properties for objects without knowing what the name of the property will be until the program is executed. This is helpful, for instance, when you want to create objects from data because you can create the names **programmatically**, instead of having to input them by hand. It's best to add the property name when you make the object so that you can keep all the properties in the same place. To learn more about computed properties or to see examples check out this [guide][computed properties] from Mozilla.

### [3.7][3.7]: Do not call `Object.prototype` methods directly, such as `hasOwnProperty`, `propertyIsEnumerable`, and `isPrototypeOf`.

There are some cases when calling `Object.prototype` methods directly, like `console.log(object.hasOwnProperty(key));`, can have unintended behavior. For instance if the object was null or if the method was **shadowed** by a property on the object.

> # What the heck is shadowing?
Shadowing is a concept related to scope. If you define a global variable and then a define a new variable in a more local scope, like in a function, then when you call the variable, the local variable will be the one that gets used. In this instance it could look like this:
```javascript
myObject = {
  magic: true;
  hasOwnProperty: false;
}
myObject.hasOwnProperty(magic)                        #=> false
Object.prototype.hasOwnProperty.call(myObject, magic) #=> true
```

<br>
### Why Should I Care?
All JavaScript values except primitives are objects. You'll be working with objects all throughout your JavaScript career and it's important to know how to work with them. To learn more about JavaScript objects read this guide from [w3schools][W3S Objects Guide].

<br>
### Next Up: Arrays
Next Saturday I'll explain what Arrays are and how to use them.

If you did or did not like this article, let me know how you feel in the comments below.

[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/

[3.1]: https://github.com/airbnb/javascript#objects--no-new
[3.2]: https://github.com/airbnb/javascript#es6-computed-properties
[3.3]: https://github.com/airbnb/javascript#es6-object-shorthand
[3.4]: https://github.com/airbnb/javascript#es6-object-concise
[3.5]: https://github.com/airbnb/javascript#objects--grouped-shorthand
[3.6]: https://github.com/airbnb/javascript#objects--quoted-props
[3.7]: https://github.com/airbnb/javascript#objects--prototype-builtins

[no-new-object]: http://eslint.org/docs/rules/no-new-object.html

[DRY]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
[SO object literal]: https://stackoverflow.com/questions/383402/is-javascripts-new-keyword-considered-harmful
[W3S Objects Guide]: https://www.w3schools.com/js/js_object_definition.asp
[computed properties]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer