# @hishprorg/illum-animi-minus <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.findLast` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-array-find-from-last).

Because `Array.prototype.findLast` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @hishprorg/illum-animi-minus
```

## Usage/Examples

```js
var findLast = require('@hishprorg/illum-animi-minus');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];
var isNumber = function (x) { return typeof x === 'number' };

assert.deepEqual(findLast(arr, isNumber), 3);
```

```js
var findLast = require('@hishprorg/illum-animi-minus');
var assert = require('assert');
/* when Array#findLast is not present */
delete Array.prototype.findLast;
var shimmed = findLast.shim();

assert.equal(shimmed, findLast.getPolyfill());
assert.deepEqual(arr.findLast(isNumber), findLast(arr, isNumber));
```

```js
var findLast = require('@hishprorg/illum-animi-minus');
var assert = require('assert');
/* when Array#findLast is present */
var shimmed = findLast.shim();

assert.equal(shimmed, Array.prototype.findLast);
assert.deepEqual(arr.findLast(isNumber), findLast(arr, isNumber));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@hishprorg/illum-animi-minus
[npm-version-svg]: https://versionbadg.es/hishprorg/illum-animi-minus.svg
[deps-svg]: https://david-dm.org/hishprorg/illum-animi-minus.svg
[deps-url]: https://david-dm.org/hishprorg/illum-animi-minus
[dev-deps-svg]: https://david-dm.org/hishprorg/illum-animi-minus/dev-status.svg
[dev-deps-url]: https://david-dm.org/hishprorg/illum-animi-minus#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hishprorg/illum-animi-minus.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hishprorg/illum-animi-minus.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hishprorg/illum-animi-minus.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hishprorg/illum-animi-minus
[codecov-image]: https://codecov.io/gh/hishprorg/illum-animi-minus/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/hishprorg/illum-animi-minus/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/hishprorg/illum-animi-minus
[actions-url]: https://github.com/hishprorg/illum-animi-minus
