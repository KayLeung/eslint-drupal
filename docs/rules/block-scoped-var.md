---
title: Rule block-scoped-var
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Treat var as Block Scoped (block-scoped-var)

The `block-scoped-var` rule generates warnings when variables are used outside of the block in which they were defined. This emulates C-style block scope.

```js
function doSomething() {
    if (true) {
        var build = true;
    }

    console.log(build);
}
```

## Rule Details

This rule aims to reduce the usage of variables outside of their binding context and emulate traditional block scope from other languages. This is to help newcomers to the language avoid difficult bugs with variable hoisting.

The following patterns are considered warnings:

```js
function doSomething() {
    if (true) {
        var build = true;
    }

    console.log(build);
}
```

```js
function doAnother() {
    try {
        var build = 1;
    } catch (e) {
        var f = build;
    }
}
```

The following patterns are not warnings:

```js
function doSomething() {
    var build;

    if (true) {
        build = true;
    }

    console.log(build);
}
```

## Further Reading

* [JavaScript Scoping and Hoisting](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
* [var Hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting)

## Version

This rule was introduced in ESLint 0.1.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/block-scoped-var.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/block-scoped-var.md)
