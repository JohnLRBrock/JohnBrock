---
layout: post
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Section 4: Arrays"
permalink: "/john-brock-js/airbnb-styleguide-section-4"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. [Airbnb][airbnb], the online marketplace for housing rentals, has a high quality and 'mostly reasonable' style guide for JavaScript, a programming language that adds dynamic behaviors to web browsers. Some of the topics in the guide are a bit advanced for beginners. This "Explain Like I'm 50" (ELI50) series will act as a plain English companion-guide to the [Airbnb style guide][style guide], because good design principles shouldn't be out of anyone's reach.

The topic of the fourth section of the style guide is **arrays** which are handy objects for containing collections of ordered data. To learn the basics of arrays you can read this guide from [w3schools][array basics] and to dive deeper you can read the documentation from [mozilla][array documentation].

## Section 4: Arrays
### [4.1][4.1]: Use the literal syntax for array creation. eslint: [no-array-constructor][no-array-constructor]
There are two main ways of creating arrays. Just like with object construction, using literals is faster and less prone to errors and is therefore the preferred method for creating arrays.

### [4.3][4.3]: Use array spreads ... to copy arrays.
Spreads are useful ways to copy many objects in JavaScript. For more information read the reference doc from [Mozilla][spread operator documentation]. In this case we use it because it is clearer and more succinct.

### [4.4][4.4]: To convert an array-like object to an array, use [`Array.from`][array from].
Once again, the preferred method is more expressive and easier to write.
```javascript
const foo = document.querySelectorAll('.foo');
const nodes = Array.from(foo);
```
### [4.6][4.6]: Use return statements in array method callbacks. It’s ok to omit the return if the function body consists of a single statement returning an expression without side effects, following [8.2][8.2]. eslint: [array-callback-return][array-callback-return]
There are certain methods that execute a block of code on each item in an array (Ex. reduce, map, filter, etc.). That block of code is referred to as a callback. If the callback is more than one line long, use a return statement. Otherwise skip it.

<br>
### Why Should I Care?
Arrays are one of the simplest, most intuitive, and most useful tools used by JavaScript programmers to create **data structures**. They are an essential tool for every programmer and if you're going to do work in JavaScript you need to know how to make and work with them.

<br>
### Next up: Destructuring
Next Saturday I'll explain what destructuring is and why it's useful.

[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/

[array basics]: https://www.w3schools.com/js/js_arrays.asp
[array documentation]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
[spread operator documentation]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator
[array from]: https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/from

[4.1]: https://github.com/airbnb/javascript#arrays--literals
[4.2]: https://github.com/airbnb/javascript#arrays--push
[4.3]: https://github.com/airbnb/javascript#es6-array-spreads
[4.4]: https://github.com/airbnb/javascript#arrays--from
[4.5]: https://github.com/airbnb/javascript#arrays--callback-return
[4.6]: https://github.com/airbnb/javascript#arrays--bracket-newline
[8.2]: https://github.com/airbnb/javascript#arrows--implicit-return

[no-array-constructor]: http://eslint.org/docs/rules/no-array-constructor.html
[array-callback-return]:http://eslint.org/docs/rules/array-callback-return