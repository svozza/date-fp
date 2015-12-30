# date-fp

[![Circle CI](https://circleci.com/gh/cullophid/date-fp.svg?style=svg)](https://circleci.com/gh/cullophid/date-fp)
[![npm version](https://badge.fury.io/js/date-fp.svg)](https://badge.fury.io/js/date-fp)
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/cullophid/date-fp?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

**date-fp** is a utility library for working with JavaScript dates.

## Motivation
There are several excellent JavaScript libraries for managing dates in JavaScript but they are generally built to be used in the object-oriented programming paradigm. This makes them cumbersome to include in a functional context.

*If you are not familiar with functional programming in JavaScript read [Professor Frisby's Mostly Adequate Guide to  Functional Programming](https://drboolean.gitbooks.io/mostly-adequate-guide/content/)*

*Also check out [Ramda.js](http://ramdajs.com/0.17/index.html) (A great library for functional programming with JavaScript)*

## Key concepts
All functions in **date-fp** follow a set of functional programming principles.

### Generic Date objects
**date-fp** operates on normal JavaScript date objects. There are no wrapper objects and **date-fp** does not extend or mutate any native JavaScript objects. Among other things this means that you can still use normal comparison operators like `<` and `>`.

### Purity
All functions in **date-fp** are pure. For a function to be pure it must follow two basic rules.

1. Pure functions always produce the same output given the same input.
2. Pure functions have no side effects. This means that calling the function will not affect the world outside the function.

A consequence of this is that **date-fp** will never knowingly throw an error upon receiving invalid input but it will _return_ one. Inspect the
type signatures of **date-fp**'s functions to find out which functions behave in this manner.

### Immutability
Dates in **date-fp** are never mutated. All operations that modify a date return a copy with the given changes and leave the original date object intact.

### Currying
All functions in **date-fp** use automatic currying, which allows for easy partial application. For more information on currying read: [Why Curry Helps](https://web.archive.org/web/20140714014530/http://hughfdjackson.com/javascript/why-curry-helps)

### Composition
Functions in **date-fp** take the data (usually a date object) as the last parameter. This, combined with currying, allows for easy function composition.

```js
const tomorrowAsString = compose(D.format('YYY-MM-DD'), D.add('days', 1));

tomorrowAsString(new Date('2015-01-01')); // '2015-01-02';
```

## Documentation

Read the full [documentation](https://cullophid.github.io/date-fp)

## Contributing
Yes please!

Something to note is that automatically we release to NPM on every successful commit and we also strictly follow SemVer so please update the version number in `package.json` appropriately when submitting a Pull Request.
