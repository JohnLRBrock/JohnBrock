---
layout: post
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Section 2: References"
permalink: "/john-brock-js/airbnb-styleguide-section-2"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. This post will cover section 2 on references, or why to avoid using `var`.

<br>
## Section 2: References
### [2.1][2.1]: Use const for all of your references; avoid using var.
There are three **reserved words** you can use to create variables with JavaScript. They are `var`, `const`, and `let`. When you are defining a variable that won't change, like Pi, use `const` which stands for constant.
```javascript
const pi = 3.1415926535;
```

This practice helps prevent bugs and makes your intent clearer, increasing readability.
> # What the heck is a reserved word?
Reserved words are the words of power that make up JavaScript like `if`, `new`, and `for`. These words have fixed meanings and aren't allowed to be redefined by the programmer (which means you can't make a variable called 'if', for instance.) The three reserved words we're talking about in this post are `let`, `const`, and `var`.

### [2.2][2.2]: If you must reassign references, use let instead of var.
Using `const` for variables that won't change makes sense, but why use `let` over `var`? At the risk of oversimplifying, `let` can do almost everything that `var` can, while also avoiding unintentional bizarre behavior as described in this article from [Vegibit][let vs var vs const vegibit].

### [2.3][2.3]: Note that both let and const are block-scoped.

This is one of the most important differences between the preferred reserved words, `let` and `const`, and the less preferred reserved word, `var`. Scope refers to what something can see. If I define a variable with `let` outside a function and then define a variable with the same name inside the function the variable outside the function won't change.
```javascript
let myName = 'John'; // => 'John'
function() {
  let myName = 'Khanthulhu'; // => 'Khanthulhu'
}
myName; // => 'John'
```
However, if we changed `let` to `var` then myName can be changed from inside the function.
```javascript
var myName = 'John'; // => 'John'
function() {
  var myName = 'Khanthulhu'; // => 'Khanthulhu'
}
myName; // => 'Khanthulhu'
```
Although there are other reasons to avoid `var`, how it handles scope is probably the biggest one.

<br>
### Why Should I Care?
The changes recommended in this section are easy to implement, especially with the use of a linter, make your code more expressive, and can save you loads of headaches in the future.

<br>
### Next Up: Objects
Next Saturday I'll explain what objects are, how you should be making them, and how you should be working with them.

If you learned something from this post, have some constructive criticism or just want to say hi, leave a comment below.


[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/

[2.1]: htps://github.com/airbnb/javascript#references--prefer-const
[2.2]: htps://github.com/airbnb/javascript#references--disallow-var
[2.3]: htps://github.com/airbnb/javascript#references--block-scope

[let vs var vs const vegibit]: http://vegibit.com/es6-let-vs-var-vs-const/