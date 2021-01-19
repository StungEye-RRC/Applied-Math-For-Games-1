---
title: Objectives and History
parent: Introduction to Javascript
nav_order: 1
---

<!--prettier-ignore-start-->
# Objectives and History
{: .no_toc }

In this section we'll look at our learning goals for this module and take a quick look back at the history of the Javascript Language.

### Table of Contents
{: .no_toc }

1. TOC
{:toc}

<!--prettier-ignore-end-->

## Objectives

Upon completion of this module, you should be able to:

- Add executable Javascript to HTML files.
- Store data in variables and constants.
- Output strings to the debugging console.
- Interpolate variables in strings using template literals.
- Use comments in your Javascript code.
- Define your own named and anonymous functions.
- Store and retrieve single and multi-dimensional array data.
- Store and retrieve values in objects by key.
- Code various conditional and looping structures.
- Understand Javascript scoping rules.

## Conventions

All source code in the notes will be syntax highlighted like so:

```javascript
const ghost_quota = 37;
const caught_ghost = 12;

if (caughtGhosts > ghostQuota) {
  console.log("You are done for the day.");
} else {
  const ghostsRequired = ghostQuota - caughtGhosts;
  console.log(`You need to find ${ghostsRequired} more ghosts.`);
}
```

## History of Javascript

Javascript was created over 25 years ago as a way to add scripting to the Netscape web browser. Prior to this there was no way to add scripted behaviour to an HTML webpage. The first version of Javscript was created by Brendan Eich over a period of 10 days in 1995. The language was first known as Mocha, then Livescript, and finally Javascript. The final name was a marketing ploy, as Java had recently been released by Sun Microsystems.

The standardized version of the Javascript language is known as ECMAScript, which is why you'll sometimes hear people refer to particular version of the language as ES#, where # might be a version number or a year, like ES6 or ES2020.

### Further Reading

- [Brief History of Javascript](https://auth0.com/blog/a-brief-history-of-javascript/)
- [ECMAScript @ Wikipedia](https://en.wikipedia.org/wiki/ECMAScript)