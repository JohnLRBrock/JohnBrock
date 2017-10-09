---
layout: post
blog: john-brock-js
title: "ELI50: Airbnb JavaScript Style Guide Chapter 6: Strings"
permalink: "/john-brock-js/airbnb-styleguide-chapter-6"
---

Welcome back to my weekly [Airbnb][airbnb] JavaScript [style guide][style guide] explainer. The topic of the 6th chapter of the style guide is **strings** which are a primitive data-type which represents a  string of characters. Strings can be used to represent a wide variety of data, from text, to keys in objects.

## Chapter 6: Strings
### [6.1][6.1]: Use single quotes '' for strings.
Double and single quotes are functionally the same except that strings made with single quotes can be used in double quote strings and vice versa.
```'When I use single quotes my string can contain "double quotes".'```
```"And when I use double quotes my string can contain 'single quotes'."```
It's generally considered bad practice to swap between double and single quotes willy nilly. It's less that you need to use single quotes and more that you need to pick either one or the other and stick to it. The exception to this rule is when when breaking this style rule allows you to adhere to other ones. For example, I default to single quotes but if my string contains a single quote then for that one I'll use double quotes.

### [6.2][6.2]: Strings that cause the line to go over 100 characters should not be written across multiple lines using string concatenation.
There are good reasons to that people go either way on this rule so it's another one that amounts to personal choice. It's generally best practice to keep the length of your codes of line short but this rule is saying that it's more important to keep strings together, so you can search for any combination of words in them, than it is to have them be as readable as possible. Personally I loathe having to side scroll and would rather break the text up, but the author raises a valid point.

> # What the heck is a ruler?
Some text editors, like [Sublime Text][sublime text], have a feature called a ruler which displays a line on your screen showing you when your lines reach a certain character limit. When I'm writing JavaScript I have mine set to 100 characters and which acts as a great guide for keeping my lines terse.

### [6.3][6.3] When programmatically building up strings, use template strings instead of concatenation.
When you want to create a block of code which constructs a string, you should use template strings, which use back ticks ``` ` ``` instead of concatenating them, which is when you literally add strings together like `"I'm a string " + "and I'm a string also"`.

> # What the heck is string interpolation?
This is a feature that I first discovered in Ruby and I'm glad to have it was added in the most recent update to JavaScript, ES6. In short, string interpolation is a way of inserting JavaScript code directly into a string. The code can be a function, a variable, or just about anything else so long as it can be converted into a string, which is done automatically. Note that, as of this writing, templating and, by extension, string interpolation, doesn't work perfectly in all web browsers. Before you use it I recommend you check to see if it will affect your [user base][caniuse templates].

### [6.4][6.4] Never use eval() on a string, it opens too many vulnerabilities.
the eval() function takes a string and then executes it (RIP). This can be a powerful metaprogramming tool but with great power comes great security vulnerabilities. If you ever decide to use eval() you have to be absolutely sure that there's no way for malicious code to be executed. The simplest way to do that is to not use eval() at all. It removes one possible vector for attack and precludes careless programming. If you want to learn more about eval() read this article by [Angus Croll][eval()].

># What the heck is metaprogramming
When you create a program that can alter other programs, or even itself, then you're doing metaprogramming. Metaprogramming is usually a more advanced technique because it tends to have more moving parts, but it can be consequently also either make for faster, more powerful programs, or simply allow the programmer to save themselves some time.

### [6.5][6.5] Do not unnecessarily escape characters in strings.
Escape characters allow you do things like have single quotes in strings that are created using single quotes and they're usually created with the backspace `\`. There's a special escape character you should know about called the new line which looks like `\n`. Although it looks like two characters, computers treat it like a single character. If you want to learn more about escape character read this [wikipedia article][escape characters].

<br>
### Next up: Functions
Next Saturday I'll cover the rules related to functions.

If you enjoyed this post, or especially if you didn't enjoy it, leave me a post in the comments telling me why.

[airbnb]: https://www.airbnb.com/
[style guide]: https://github.com/airbnb/javascript#types--primitives

[6.1]: https://github.com/airbnb/javascript#strings--quotes
[6.2]: https://github.com/airbnb/javascript#strings--line-length
[6.3]: https://github.com/airbnb/javascript#es6-template-literals
[6.4]: https://github.com/airbnb/javascript#strings--eval
[6.5]: https://github.com/airbnb/javascript#strings--escaping

[sublime text]: https://www.sublimetext.com/
[caniuse templates]: https://caniuse.com/#feat=template-literals
[eval()]: https://javascriptweblog.wordpress.com/2010/04/19/how-evil-is-eval/
[escape character]: https://en.wikipedia.org/wiki/Escape_character