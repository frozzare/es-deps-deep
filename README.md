# es-deps-deep

[![NPM version][npm-image]][npm-url]
[![Unix Build Status][travis-image]][travis-url]
[![Windows Build Status][appveyor-image]][appveyor-url]
[![Coveralls Status][coveralls-image]][coveralls-url]
[![Dependency Status][depstat-image]][depstat-url]

> ECMAScript 2015+/CommonJS module dependencies resolved in depth

## Install

    npm install --save es-deps-deep

## Usage

```js
import { esDepsDeep, esDepsDeepAsync } from 'es-deps-deep';

esDepsDeep('./fixtures/extended/index.js')
  .then(result => console.log(result)); /* [
  { requested: null,
    from: null,
    resolved: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/index.js' },
  { requested: './first/index.js',
    from: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/index.js',
    resolved: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/first/index.js' },
  { requested: './second/index.js',
    from: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/first/index.js',
    resolved: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/first/second/index.js' },
  { requested: '../third/index.js',
    from: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/first/index.js',
    resolved: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/third/index.js' },
  { requested: '../first/fourth/index.js',
    from: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/third/index.js',
    resolved: '/Users/iamstarkov/projects/es-deps-deep/fixtures/extended/first/fourth/index.js' } ] */
```

## API

### esDepsDeepAsync(file, excludeFn)

Return a promise that resolves to `Array[Object]`, where object is  [`es-dep-unit`][es-dep-unit].

[es-dep-unit]: https://github.com/iamstarkov/es-dep-unit

#### file

*Required*  
Type: `String`

Entry point of the for your app.

#### excludeFn

Type: `Function`  
Default: `() => false;`

`excludeFn` decides items to exclude from [`es-deps-resolved`][es-deps-resolved] each time when it's going to go deeper.

[es-deps-resolved]: https://github.com/iamstarkov/es-deps-resolved

## Related

* [es-deps][es-deps] — ECMAScript 2015+/CommonJS module dependencies array
* [es-deps-from-string][es-deps-from-string] — ECMAScript 2015+/CommonJS module dependencies array from string
* [es-deps-resolved][es-deps-resolved] — ECMAScript 2015+/CommonJS module dependencies resolved array
* [es-dep-unit][es-dep-unit] — Constructor for ECMAScript 2015+/CommonJS dependency unit `Object { requested, from, resolved }`

[es-deps]: https://github.com/iamstarkov/es-deps
[es-deps-from-string]: https://github.com/iamstarkov/es-deps-from-string
[es-deps-resolved]: https://github.com/iamstarkov/es-deps-resolved
[es-dep-unit]: https://github.com/iamstarkov/es-dep-unit

## License

MIT © [Vladimir Starkov](https://iamstarkov.com)

[npm-url]: https://npmjs.org/package/es-deps-deep
[npm-image]: https://img.shields.io/npm/v/es-deps-deep.svg?style=flat-square

[travis-url]: https://travis-ci.org/iamstarkov/es-deps-deep
[travis-image]: https://img.shields.io/travis/iamstarkov/es-deps-deep.svg?style=flat-square&label=unix

[appveyor-url]: https://ci.appveyor.com/project/iamstarkov/es-deps-deep
[appveyor-image]: https://img.shields.io/appveyor/ci/iamstarkov/es-deps-deep.svg?style=flat-square&label=windows

[coveralls-url]: https://coveralls.io/r/iamstarkov/es-deps-deep
[coveralls-image]: https://img.shields.io/coveralls/iamstarkov/es-deps-deep.svg?style=flat-square

[depstat-url]: https://david-dm.org/iamstarkov/es-deps-deep
[depstat-image]: https://david-dm.org/iamstarkov/es-deps-deep.svg?style=flat-square