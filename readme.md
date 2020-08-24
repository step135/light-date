# Light Date :alarm_clock:

> Blazing fast & lightweight date formatting for Node.js and the browser.

[![Build Status](https://travis-ci.org/xxczaki/light-date.svg?branch=master)](https://travis-ci.org/xxczaki/light-date)
[![Coverage Status](https://coveralls.io/repos/github/xxczaki/light-date/badge.svg?branch=master)](https://coveralls.io/github/xxczaki/light-date?branch=master)
[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/xojs/xo)
![minified size](https://img.shields.io/bundlephobia/minzip/light-date)

Inspired by [`tinydate`](https://github.com/lukeed/tinydate), [`tinytime`](https://github.com/aweary/tinytime), [`date-fns`](https://github.com/date-fns/date-fns) and more, this module aims to provide super fast and easy way to format dates, while also staying lightweight.

Note that only a [limited subset of Date methods](#patterns) is provided.

---

## Highlights

* **Small.** 191 bytes (minified and gzipped). No dependencies. [Size Limit](https://github.com/ai/size-limit) controls the size.
* **Fast.** See the [benchmarks](#benchmarks).
* **Compliant.** Follows [Unicode Technical Standard #35](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table).
* **Well tested.** To make sure it handles various use cases correctly.
* **Portable.** Works pretty much everywhere.
* **Written in TypeScript.**

## Install

```
$ npm install light-date
```

## Usage

```js
import {format} from 'light-date';

const date = new Date('5/1/2020, 4:30:09 PM');

format(date, 'The date is {MM}/{dd}/{yyyy}!'); //=> 'The date is 05/01/2020!'
```

## API

### format(date, exp)

Returns a string with formatted date.

##### date

Type: `Date`

Date object, which should be used.

##### exp

Type: `string`

String, which you want to format, for example: `{yyyy}-{MM}-{dd}` or `Current time: {hh}:{mm}:{ss}`.

## Patterns

Format of the string is based on [Unicode Technical Standard #35](https://www.unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table).

| **Unit**      | **Pattern** | **Result examples**    |
| ------------- | ----------- | ---------------------- |
| Calendar year | {yy}        | 44, 01, 00, 17         |
|               | {yyyy}      | 0044, 0001, 1900, 2020 |
| Month         | {MM}        | 01, 02, ..., 12        |
| Day           | {dd}        | 01, 02, ..., 31        |
| Hour          | {HH}        | 00, 01, 02, ..., 23    |
| Minute        | {mm}        | 00, 01, ..., 59        |
| Second        | {ss}        | 00, 01, ..., 59        |
| Millisecond   | {SSS}       | 000, 0001, ..., 999    |

## Benchmarks

```
# Node.js v12.18.3

light-date             x   7,382,656 ops/sec ±0.94% (90 runs sampled)
tinytime               x   5,283,247 ops/sec ±0.57% (94 runs sampled)
tinydate               x   4,002,904 ops/sec ±0.43% (92 runs sampled)
date-format            x   830,962 ops/sec ±0.14% (97 runs sampled)
moment                 x   674,096 ops/sec ±0.47% (94 runs sampled)
date-fns lightFormat   x   462,305 ops/sec ±0.19% (97 runs sampled)
date-fns format        x   345,092 ops/sec ±0.19% (98 runs sampled)
dayjs                  x   262,442 ops/sec ±0.28% (94 runs sampled)
```

## License

MIT © [Antoni Kepinski](https://kepinski.me)