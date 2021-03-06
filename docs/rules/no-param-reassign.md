---
title: Rule no-param-reassign
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Disallow Reassignment of Function Parameters (no-param-reassign)

Assignment to variables declared as function parameters can be misleading and lead to confusing behavior, as modifying function parameters will also mutate the `arguments` object. Often, assignment to function parameters is unintended and indicative of a mistake or programmer error.

## Rule Details

This rule aims to prevent unintended behavior caused by overwriting function parameters.

The following patterns are considered warnings:

```js
function foo(bar) {
    bar = 13;
}
```

```js
function foo(bar) {
    bar++;
}
```

The following patterns are not warnings:

```js
function foo(a) {
    var b = a;
}
```

```js
function foo(a) {
    a.prop = 'value';
}
```

## When Not To Use It

If you want to allow assignment to function parameters, then you can safely disable this rule.

## Further Reading

* [JavaScript: Don’t Reassign Your Function Arguments](http://spin.atomicobject.com/2011/04/10/javascript-don-t-reassign-your-function-arguments/)

## Version

This rule was introduced in ESLint 0.18.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-param-reassign.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-param-reassign.md)
