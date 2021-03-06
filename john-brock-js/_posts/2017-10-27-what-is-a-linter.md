---
blog: john-brock-js
title: "What's a Linter and Why Should I Be Using One?"
layout: post
permalink: "/john-brock-js/what-is-a-linter"
---
Each programmer has their own coding style, conscious or otherwise. Some people are verbose, others are terse, and some are slapdash. Style covers everything from whitespace, to how you name variables, to how common problems are solved. Having good style can not only make your code easier to read, but also less error prone. Often companies will put together a list of guidelines for style, aptly called a **style guide**.

One of the most popular style guides for JavaScript is [Airbnb's][airbnb styleguide]. It's a fantastic guide, but because of both the breadth of the topics covered and the advanced nature of some of the rules, it can be hard for a developer, especially a novice one, to *remember* all the rules, let along follow them.

That's where linters can be helpful. A **linter** is a program which looks for both stylistic and syntactic errors in your code. It acts as a guide for writing clean code and can also check your code while you write it. There are linters for most programming languages, such as the fantastic [RubuCop][rubocop] for Ruby, but this being a JavaScript blog, let's talk about linters for JavaScript.

There are several JavaScript linters. For a long time the two main linters were ESLint and JSCS. Recently, JSCS [merged][eslint jscs] into ESLint which is now the dominant JavaScript linter and the one that I recommend. To learn more about it, check out the [ESLint][eslint] homepage.

Linters are incredibly useful programs, especially for novices. If you haven't tried using one before, I highly recommend it. You'll wonder how you ever coded without one.

If you enjoyed learning about linters, have a criticism, or just want to say hi, leave a comment below.

[airbnb styleguide]: https://github.com/airbnb/javascript
[eslint jscs]: http://eslint.org/blog/2016/04/welcoming-jscs-to-eslint
[rubocop]: https://github.com/bbatsov/rubocop
[eslint]: https://eslint.org/