---
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 1 'Types'"
layout: post
---
Airbnb, the online marketplace for housing rentals, has a high quality and 'mostly reasonable' style guide for JavaScript. Some of the topics in the guide are a bit advanced for beginners to the language. This series will act as a plain English guide to the [Airbnb style guide][style guide], because good design principles shouldn't be out of anyone's reach.

Each post will cover a chapter of the style guide, beginning with the rule, following with an explanation of terminology, then explaining the reasoning behind it when necessary.

## Types
<br>
### Primitives: When you access a primitive type you work directly on its value.

In JavaScript a data type is a way of storing information. A primitive type is the most basic form of this.
* **string:** Essentially text. Some other languages have a data type for individual characters and then another type for 'strings' of characters. JavaScript forgoes this and just has strings.
* **number:** Although some other languages have different data types for numbers JavaScript has but one.
* **boolean:** A boolean is a way of storing a value for True or False. 
* **null:** Information is stored in a computer's memory. To access the information the computer needs to know where in the memory it's located. For this purpose it uses an address. In computer science a 'pointer' is something which 'points' to an a place in memory. Null is used for when the pointer isn't pointing anywhere.
* **undefined:** Variables can be made without assigning them a value. When you **declare** a variable in this way the variable is given a value of undefined.

<br>
### Complex: When you access a complex type you work on a reference to its value.

* **object:** An object is a data type that contains information and methods for accessing that information.
* **array:** An array is a numbered list. In JavaScript, as well as most other languages, arrays are 0 indexed meaning that the first object in an array has the number 0 instead of the number 1. 
* **function:** A function is a way of storing instructions for the computer.

<br>
### What's the Rub?
Getting to the root of this section, what is the difference between working directly with a value and working with a reference?

Say I have two variables and I set one equal to the other. If they are both primitives and I later change one of them the other doesn't change. The two variables aren't linked in any way.

```javascript
const foo = 1;
let bar = foo;

bar = 9;

console.log(foo, bar); // => 1, 9
```

On the other hand if the first variable was, say, an array and I set my second variable equal to the first JavaScript doesn't make a copy of the array. Instead it uses a pointer as we discussed earlier to point to the place in memory that the array exists in. Now if I change the value in one of the variables, since they are both looking at the same place in memory, they both will have their values changed.

```javascript
const foo = [1, 2];
const bar = foo;

bar[0] = 9;

console.log(foo[0], bar[0]); // => 9, 9
```

This is an important concept to grasp because it's often the cause of strange behavior in complex programs.

<br>
### Next Up: References

In the next post I'll explain why you should avoid using `var` to declare variables.



[style guide]: https://github.com/airbnb/javascript#types--primitives