---
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 3: References"
layout: post
permalink: "/john-brock-js/airbnb-styleguide-chapter-3"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. This post will cover chapter 3 on **objects**, creating, and using them.

> # What the heck is an object?
Simply put an object is a way to **encapsulate** something in a way that can be used or modified later. Objects can have variables and functions that act on them. Functions that belong to objects are called **methods**. The reason that objects are so useful is because you can create new objects that **inherit** properties from other objects. You could, for instance, make an object to represent a car which has variables to indicate it has an engine, four wheels, methods that let the user drive it. From there you can create other objects that inherit those properties from Car and add other ones like being able to drive itself. Programmers, being a lazy folk, do their best to follow something called the DRY principle ([Don't Repeat Yourself][DRY]). Objects are a useful way to package code for reuse in other places.


<br>
## Chapter 3: Objects
### [3.1][3.1]: Use the literal syntax for object creation. eslint: `[no-new-object][no-new-object]`




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
[no-new-object]: http://eslint.org/docs/rules/no-new-object.html
[DRY]: https://en.wikipedia.org/wiki/Don%27t_repeat_yourself