---
layout: post
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Section 7: Functions "
permalink: "/john-brock-js/airbnb-styleguide-section-7"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. The topic of the 7th section of the style guide is **functions** which are ways to package up code for re-use. Functions are enormously important topic in programming. With proper use they make your code DRYer, more secure, easier to test and maintain, and less prone to bugs. Using functions properly is tied to many concepts in computer science and the topic is therefore to wide for a single article to cover in depth. That being said, if you want a refresher on functions or their syntax, I recommend this [w3schools][function basics] article and if you want a more detailed reference on functions check out this page from [mozilla][function reference].

Note that there are many rules in this section and some of them I will skip either because they are self explanatory or are thoroughly explained by Airbnb.  

## Section 7: Functions
### [7.1][7.1]: Use named function expressions instead of function declarations.
> # What's hoisting?
Generally with JavaScript your code is executed in the order that it's written. There are some instances, like with function declarations, where JavaScript moves something to the top of the order. This is called hoisting. It's sometimes the cause of bugs and confusion so it's often best to just avoid it. To learn more about hoisting read this [w3schools][hoisting basics] article.

> # What's an Error Call Stack?
A [call stack][https://en.wikipedia.org/wiki/Call_stack] allows you to trace errors through your program. It will show you the path your program took through its code that led to the error. This makes finding complex bugs that involve code in several locations easier to fix.

### [7.5][7.5]: Never name a parameter arguments. This will take precedence over the arguments object that is given to every function scope.
According to [Mozilla][arguments object]
>"The arguments object is a local variable available within all (non-arrow) functions. You can refer to a function's arguments within the function by using the arguments object. This object contains an entry for each argument passed to the function, the first entry's index starting at 0."

Making one of your function's parameters `arguments` will overwrite the default `arguments` and you won't be able to use it.

### [7.7][7.7]: Use default parameter syntax rather than mutating function arguments.
JavaScript has this fun feature where if you don't supply a function the arguments it was expecting, it tries to run it anyways without giving you an error. You *could* use this feature, as shown in Airbnb's example to create a default value in case no argument was given, but that requires changing, or **mutating** the argument and that's bad practice. Instead, use the assignment operator (=) inside the parenthesis of a function and JavaScript will know to set the parameter equal to that if no value is given when the function is called. 
### [7.8][7.8]: Avoid side effects with default parameters.
A **side effect** is when a function modifies something outside of its scope. In Airbnb's example the function is modifying the variable b which is defined outside the function. This goes against the rule of encapsulation and can make your programs have strange behaviors and even stranger bugs.
### [7.10][7.10]: Never use the Function constructor to create a new function.
I talked about why eval() is bad in the [strings]({% post_url 2017-09-02-airbnb-style-guide-section-6 %}) section. Just like with eval(), if you're not careful, this could allow malicious users to insert and run their own code in your program. It's best not use it at all so you don't have to worry about this vulnerability.
### [7.12][7.12]: Never mutate parameters.
### [7.13][7.13]: Never reassign parameters. 
### [7.14][7.14]: Prefer the use of the spread operator ... to call variadic functions.
### [7.15][7.15]: Functions with multiline signatures, or invocations, should be indented just like every other multiline list in this guide: with each item on a line by itself, with a trailing comma on the last item.

> #What the heck is ?
<br>
### Why Should I Care?

<br>
### Next up: 
Next Saturday I'll explain 

[airbnb]: https://www.airbnb.com/
[style guide]: https://github.com/airbnb/javascript#types--primitives

[function basics]: https://www.w3schools.com/js/js_functions.asp
[function reference]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions

[7.1]: https://github.com/airbnb/javascript#functions--declarations
[7.5]: https://github.com/airbnb/javascript#functions--arguments-shadow
[7.7]: https://github.com/airbnb/javascript#es6-default-parameters
[7.8]: https://github.com/airbnb/javascript#functions--default-side-effects
[7.]:
[7.]:
[7.]:
[7.]:
[7.]:
[7.]:
[7.]:
[7.]:

[hoisting basics]: https://www.w3schools.com/js/js_hoisting.asp

[arguments object]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments

