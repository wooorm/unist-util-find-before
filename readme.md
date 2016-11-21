# unist-util-find-before [![Build Status][travis-badge]][travis] [![Coverage Status][codecov-badge]][codecov]

[**Unist**][unist] utility to find a node before another node.

## Installation

[npm][]:

```bash
npm install unist-util-find-before
```

## Usage

```js
var remark = require('remark');
var findBefore = require('unist-util-find-before');

var tree = remark().parse('Some _emphasis_, **importance**, and `code`.');
var paragraph = tree.children[0];
var code = paragraph.children[paragraph.children.length - 1];

console.log(findBefore(paragraph, code, 'emphasis'));
```

Yields:

```js
{ type: 'emphasis',
  children: [ { type: 'text', value: 'emphasis' } ] }
```

## API

### `findBefore(parent, node|index[, test])`

Find the first child before `index` (or `node`) in `parent`, that passes `test`
(when given).

###### Parameters

*   `parent` ([`Node`][node]) — Context node;
*   `node` ([`Node`][node]) — Node in `parent`;
*   `index` (`number`, optional) — Position of a `node` in `parent`;
*   `test` (`Function`, `string`, or `Node`, optional)
    — See [`unist-util-is`][is].

###### Returns

[`Node?`][node] — Child node of `parent` passing `test`.

## License

[MIT][license] © [Titus Wormer][author]

<!-- Definitions -->

[travis-badge]: https://img.shields.io/travis/wooorm/unist-util-find-before.svg

[travis]: https://travis-ci.org/wooorm/unist-util-find-before

[codecov-badge]: https://img.shields.io/codecov/c/github/wooorm/unist-util-find-before.svg

[codecov]: https://codecov.io/github/wooorm/unist-util-find-before

[npm]: https://docs.npmjs.com/cli/install

[license]: LICENSE

[author]: http://wooorm.com

[unist]: https://github.com/wooorm/unist

[node]: https://github.com/wooorm/unist#node

[is]: https://github.com/wooorm/unist-util-is
