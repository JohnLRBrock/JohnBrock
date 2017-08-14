---
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 4: Arrays"
layout: post
permalink: "/john-brock-js/airbnb-styleguide-chapter-4"
---

## Chapter 4: Arrays
### [4.1][4.1]: Use the literal syntax for array creation. eslint: [no-array-constructor][no-array-constructor]
### [4.2][4.2]: Use `Array#push` instead of direct assignment to add items to an array.
### [4.3][4.3]: Use array spreads ... to copy arrays.
### [4.4][4.4]: To convert an array-like object to an array, use `Array.from`.
### [4.5][4.5]: Use return statements in array method callbacks. It’s ok to omit the return if the function body consists of a single statement returning an expression without side effects, following [8.2][8.2]. eslint: [array-callback-return][array-callback-return]
### [4.6][4.6]: Use line breaks after open and before close array brackets if an array has multiple lines

<br>
### Next up: Destructuring
Next Saturday I'll explain what destructuring is and why it's useful.

[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/

[4.1]: https://github.com/airbnb/javascript#arrays--literals
[4.2]: https://github.com/airbnb/javascript#arrays--push
[4.3]: https://github.com/airbnb/javascript#es6-array-spreads
[4.4]: https://github.com/airbnb/javascript#arrays--from
[4.5]: https://github.com/airbnb/javascript#arrays--callback-return
[4.6]: https://github.com/airbnb/javascript#arrays--bracket-newline
[8.2]: https://github.com/airbnb/javascript#arrows--implicit-return

[no-array-constructor]: http://eslint.org/docs/rules/no-array-constructor.html
[array-callback-return]:http://eslint.org/docs/rules/array-callback-return