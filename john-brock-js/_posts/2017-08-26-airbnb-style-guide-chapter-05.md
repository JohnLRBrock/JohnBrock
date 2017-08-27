---
layout: post
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 5: Destructuring"
permalink: "/john-brock-js/airbnb-styleguide-chapter-5"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. The topic of the 5th chapter of the style guide is **destructuring** which is a convenient way of extracting data from arrays, and objects. To learn the basics of destructuring you can read this simple guide from [Wes Bos][destructuring intro] and to get a deeper dive you can read this guide from [untangled.io][deeper dive].

## Chapter 5: Destructuring
># What does destructuring look like?
Destructuring looks backwards at first. With arrays, each variable on the left is being assigned, in order, to the elements in the array on the right.
```javascript
const beatles = ['John Lennon', 'Paul McCartney', 'George Harrison',
  'Ringo Starr', 'Brian Epstein'];
// Destructuring
const [rhythmGuitar, bass, leadGuitar, drums] = beatles;
```
Objects work similarly. In this case destructuring makes variables with the names of each of the attributes that you're pulling out of the object.
```javascript
// Object
const beatles = {
  rythmGuitar: 'John Lennon',
  bass: 'Paul McCartney',
  leadGuitar: 'George Harrison',
  drums: 'Ringo Starr'
  manager: 'Brian Epstein'
};
// destructuring
const { rhythmGuitar, bass, leadGuitar, drums } = beatles;
```
Both ways end up with a set of four variables (rhythmGuitar, bass, leadGuitar, and drums)
Each variable contains the name of their respective Beatle.

### [5.1][5.1]: Use object destructuring when accessing and using multiple properties of an object. jscs: [`requireObjectDestructuring`][requireObjectDestructuring]
This, and the following rule, should be followed because they are terser and allow you to avoid making temporary variables to hold the data.
```javascript
// bad
function getFullName(user) {
  const firstName = user.firstName;
  const lastName = user.lastName;

  return `${firstName} ${lastName}`;
}

// good
function getFullName(user) {
  const { firstName, lastName } = user;
  return `${firstName} ${lastName}`;
}

// best
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`;
}
```
### [5.2][5.2]: Use array destructuring. jscs: [`requireArrayDestructuring`][requireArrayDestructuring]
If you need non sequential values you can use something like `const [first, __, third] = arr;`.
```javascript
const arr = [1, 2, 3, 4];

// bad
const first = arr[0];
const second = arr[1];

// good
const [first, second] = arr;
```

### [5.3][5.3]: Use object destructuring for multiple return values, not array destructuring. jscs: [`disallowArrayDestructuringReturn`][disallowArrayDestructuringReturn]
When using destructuring to get data from an array you pull the data in order. Think back to the Beatles array in the first example. If you wanted the first and third value only you would need to do something like `const [rhythmGuitar, __, leadGuitar] = beatles;`. Using object destructuring allows us to ignore ordering and just get the things we want.
```javacript
// bad
function processInput(input) {
  // then a miracle occurs
  return [left, right, top, bottom];
}

// the caller needs to think about the order of return data
const [left, __, top] = processInput(input);

// good
function processInput(input) {
  // then a miracle occurs
  return { left, right, top, bottom };
}

// the caller selects only the data they need
const { left, top } = processInput(input);
```

<br>
### Why Should I Care?
The primary use case for destructuring is passing data around and is invaluable when creating complex programs with lots of moving parts.

<br>
### Next up: 
Next Saturday I'll explain what strings are and the best way to work with them.

[airbnb]: https://www.airbnb.com/
[style guide]: https://github.com/airbnb/javascript#types--primitives

[destructuring intro]: https://wesbos.com/destructuring-objects/
[deeper dive]: http://untangled.io/in-depth-es6-destructuring-with-assembled-avengers/

[5.1]: https://github.com/airbnb/javascript#destructuring--object
[5.2]: https://github.com/airbnb/javascript#destructuring--array
[5.3]: https://github.com/airbnb/javascript#destructuring--object-over-array

[requireObjectDestructuring]: http://jscs.info/rule/requireObjectDestructuring
[requireArrayDestructuring]: http://jscs.info/rule/requireArrayDestructuring
[disallowArrayDestructuringReturn]: http://jscs.info/rule/disallowArrayDestructuringReturn