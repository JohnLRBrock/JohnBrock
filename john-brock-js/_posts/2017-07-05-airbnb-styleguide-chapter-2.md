---
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 2: References"
layout: post
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. This post will cover chapter 2 on references, or why to avoid using `var`.

<br>
## Chapter 2: References

* ### [2.1][2.1]: Use const for all of your references; avoid using var. eslint: [`prefer-const`][prefer-const], [`no-const-assign`][no-const-assign]
* ### [2.2][2.2]: If you must reassign references, use let instead of var. eslint: [`no-var`][no-var] jscs: [`disallowVar`][disallowVar]
* ### [2.3][2.3]: Note that both let and const are block-scoped.

[style guide]: https://github.com/airbnb/javascript#types--primitives
[airbnb]: https://www.airbnb.com/
[2.1]: htps://github.com/airbnb/javascript#references--prefer-const
[2.2]: htps://github.com/airbnb/javascript#references--disallow-var
[2.3]: htps://github.com/airbnb/javascript#references--block-scope
[prefer-const]: http://eslint.org/docs/rules/prefer-const.html
[no-const-assign]: http://eslint.org/docs/rules/no-const-assign.html
[no-var]: http://eslint.org/docs/rules/no-var.html
[disallowVar]: http://jscs.info/rule/disallowVar
