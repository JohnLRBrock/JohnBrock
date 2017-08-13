---
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 3: References"
layout: post
permalink: "/john-brock-js/airbnb-styleguide-chapter-3"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. This post will cover chapter 3 on **objects**, creating, and using them.

> # What the heck is an object?
Simply put an object is a way to **encapsulate** something in a way that can be used or modified later. Objects can have variables and functions that act on them. The reason that objects are so useful is because you can create new objects that **inherit** properties from other objects. You could, for instance, make an object to represent a car which has variables to indicate it has an engine, four wheels, methods that let the user drive it. From there you can create other objects that inherit those properties from Car and add other ones like being able to drive itself. Programmers, being a lazy folk, do their best to follow something called the DRY principle ([Don't Repeat Yourself][DRY]). Objects are a useful way to package code for reuse in other places.


<br>
## Chapter 3: Objects
### [3.1][3.1]: Use the literal syntax for object creation. eslint: [`no-new-object`][no-new-object]

```javascript
// more error prone and verbose
const item = new Object();

// harder to mess up and easier to write 
const item = {};
```

Although the first method isn't harmful, it takes longer to write and can cause problems for you if you forget `new`. The second method is faster to write, easier to read, and harder to mess up. If you want to learn more about the why we tend to use the second version read the answers on this [stack overflow question.][SO object literal]

### [3.2][3.2]: Use computed property names when creating objects with dynamic property names.

JavaScript has a nifty feature that allows you to add or create properties for objects without knowing what the name of the property will be until the program is ran. This is helpful, for instance, when you want to create objects from data because you can create the names problematically instead of having to input them by hand. It's best to add the property name when you make the object so that you can keep all the properties in the same place.

```javascript
function getKey(k) {
  return `a key named ${k}`;
}

// bad
const obj = {
  id: 5,
  name: 'San Francisco',
};
obj[getKey('enabled')] = true;

// good
const obj = {
  id: 5,
  name: 'San Francisco',
  [getKey('enabled')]: true,
};
```

### [3.3][3.3]: Use object method shorthand. eslint: [`object-shorthand`][object-shorthand] jscs: [`requireEnhancedObjectLiterals`][requireEnhancedObjectLiterals]

Functions that belong to objects are called **methods**. These methods can be called on the object like `object.foo()`. This form of declaring functions is less verbose and easier to read.
```javascript
// bad
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};

// good
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```

### [3.4][3.4]: Use property value shorthand. eslint: [`object-shorthand`][object-shorthand] jscs: [`requireEnhancedObjectLiterals`][requireEnhancedObjectLiterals]

If the name of the property shares the name with the variable you're setting it to you can use property value shorthand which saves time and is more expressive.

```javascript
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
  lukeSkywalker: lukeSkywalker,
};

// good
const obj = {
  lukeSkywalker,
};
```

### [3.5][3.5]: Group your shorthand properties at the beginning of your object declaration.

This makes things clearer when you are assigning a large number of properties.

```javascript
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  lukeSkywalker,
  episodeThree: 3,
  mayTheFourth: 4,
  anakinSkywalker,
};

// good
const obj = {
  lukeSkywalker,
  anakinSkywalker,
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  episodeThree: 3,
  mayTheFourth: 4,
};
```

### [3.6][3.6]: Only quote properties that are invalid identifiers. eslint: [`quote-props`][quote-props] jscs: [`disallowQuotedKeysInObjects`][disallowQuotedKeysInObjects]

Some property names can be used but only when quoted. `'foo-bar'` would work but `foo-bar` (not quoted) will not. You could quote every name, for safety, but it's more verbose and it will probably rare where your property name will need the quotes.
```javascript
// bad
const bad = {
  'foo': 3,
  'bar': 4,
  'data-blah': 5,
};

// good
const good = {
  foo: 3,
  bar: 4,
  'data-blah': 5,
};
```

### [3.7][3.7]: Do not call `Object.prototype` methods directly, such as `hasOwnProperty`, `propertyIsEnumerable`, and `isPrototypeOf`.

There are some cases when calling `Object.prototype` methods directly (like `console.log(object.hasOwnProperty(key));`) can have unintended behavior, for instance if the object was null or if the method was **shadowed** by a property on the object.

```javascript
// bad
console.log(object.hasOwnProperty(key));

// good
console.log(Object.prototype.hasOwnProperty.call(object, key));

// best
const has = Object.prototype.hasOwnProperty; // cache the lookup once, in module scope.
/* or */
import has from 'has';
// ...
console.log(has.call(object, key));
```

> # What the heck is shadowing?
Shadowing is a concept related to scope. If you define a global variable and then a define a new variable in a more local scope, like in a function, then when you call the variable the local variable will be the one that gets used. In this instance it could look like this:
```javascript
myObject = {
  magic: true;
  hasOwnProperty: false;
}
myObject.hasOwnProperty(magic)                        #=> false
Object.prototype.hasOwnProperty.call(myObject, magic) #=> true
```


### [3.8][3.8]: Prefer the object spread operator over `Object.assign` to **shallow-copy** objects. Use the object rest operator to get a new object with certain properties omitted.

The spread operator is less verbose than `Object.assign`.

```javascript
// very bad
const original = { a: 1, b: 2 };
const copy = Object.assign(original, { c: 3 }); // this mutates `original` ಠ_ಠ
delete copy.a; // so does this

// bad
const original = { a: 1, b: 2 };
const copy = Object.assign({}, original, { c: 3 }); // copy => { a: 1, b: 2, c: 3 }

// good
const original = { a: 1, b: 2 };
const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }

const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
```

<br>
### Why Should I Care?
All JavaScript values except primitives are objects. You'll be working with objects all throughout your JavaScript career and it's important to know how to work with them. To learn more about JavaScript objects read this guide from [w3schools][W3S Objects Guide]


[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/
[3.1]: https://github.com/airbnb/javascript#objects--no-new
[3.2]: https://github.com/airbnb/javascript#es6-computed-properties
[3.3]: https://github.com/airbnb/javascript#es6-object-shorthand
[3.4]: https://github.com/airbnb/javascript#es6-object-concise
[3.5]: https://github.com/airbnb/javascript#objects--grouped-shorthand
[3.6]: https://github.com/airbnb/javascript#objects--quoted-props
[3.7]: https://github.com/airbnb/javascript#objects--prototype-builtins
[3.8]: https://github.com/airbnb/javascript#objects--rest-spread
[object-shorthand]: http://eslint.org/docs/rules/object-shorthand.html
[requireEnhancedObjectLiterals]: http://jscs.info/rule/requireEnhancedObjectLiterals
[no-new-object]: http://eslint.org/docs/rules/no-new-object.html
[quote-props]: http://eslint.org/docs/rules/quote-props.html
[disallowQuotedKeysInObjects]: http://jscs.info/rule/disallowQuotedKeysInObjects
[DRY]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
[SO object literal]: https://stackoverflow.com/questions/383402/is-javascripts-new-keyword-considered-harmful
[W3S Objects Guide]: https://www.w3schools.com/js/js_object_definition.asp