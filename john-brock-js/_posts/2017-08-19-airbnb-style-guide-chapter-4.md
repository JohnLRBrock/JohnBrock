---
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 4: Arrays"
layout: post
permalink: "/john-brock-js/airbnb-styleguide-chapter-4"
---

The fourth chapter of the style guide covers arrays and are handy for containing collections of ordered data.

## Chapter 4: Arrays
### [4.1][4.1]: Use the literal syntax for array creation. eslint: [no-array-constructor][no-array-constructor]
There are two main ways of creating arrays. Just like with object construction, using literals is faster and less prone to errors and is therefore the preferred method for creating arrays.
```javascript
// using new, bad
const items = new Array();

// using a literal, good
const items = [];
```
### [4.2][4.2]: Use `Array#push` instead of direct assignment to add items to an array.
Using push is clearer and more succinct.
```javascript
const someStack = [];

// bad
someStack[someStack.length] = 'abracadabra';

// good
someStack.push('abracadabra');
```
### [4.3][4.3]: Use array spreads ... to copy arrays.
Spreads are useful ways to copy many objects in JavaScript. For more information read the reference doc from [Mozilla][spread operator documentation]. In this case we use it because is is clearer and more succinct than the alternative.
```javascript
// bad
const len = items.length;
const itemsCopy = [];
let i;

for (i = 0; i < len; i += 1) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```
### [4.4][4.4]: To convert an array-like object to an array, use [`Array.from`][array from].
```javascript
const foo = document.querySelectorAll('.foo');
const nodes = Array.from(foo);
```
### [4.5][4.5]: Use return statements in array method callbacks. It’s ok to omit the return if the function body consists of a single statement returning an expression without side effects, following [8.2][8.2]. eslint: [array-callback-return][array-callback-return]
There are certain methods that execute a block of code on each item in an array (Ex. reduce, map, filter, etc.). That block of code is referred to as a callback. If the callback is more than one line long, use a return statement. Otherwise skip it.
### [4.6][4.6]: Use line breaks after open and before close array brackets if an array has multiple lines
This simply makes the array more readable.
```javascript
// bad
const arr = [
  [0, 1], [2, 3], [4, 5],
];

const objectInArray = [{
  id: 1,
}, {
  id: 2,
}];

const numberInArray = [
  1, 2,
];

// good
const arr = [[0, 1], [2, 3], [4, 5]];

const objectInArray = [
  {
    id: 1,
  },
  {
    id: 2,
  },
];

const numberInArray = [
  1,
  2,
];
```
<br>
### Next up: Destructuring
Next Saturday I'll explain what destructuring is and why it's useful.

[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/
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