# it-reduce <!-- omit in toc -->

[![codecov](https://img.shields.io/codecov/c/github/achingbrain/it.svg?style=flat-square)](https://codecov.io/gh/achingbrain/it)
[![CI](https://img.shields.io/github/actions/workflow/status/achingbrain/it/js-test-and-release.yml?branch=master\&style=flat-square)](https://github.com/achingbrain/it/actions/workflows/js-test-and-release.yml?query=branch%3Amaster)

> Reduces the values yielded from an async iterator

## Table of contents <!-- omit in toc -->

- [Install](#install)
  - [Browser `<script>` tag](#browser-script-tag)
- [Usage](#usage)
- [License](#license)
- [Contribution](#contribution)

## Install

```console
$ npm i it-reduce
```

### Browser `<script>` tag

Loading this module through a script tag will make it's exports available as `ItReduce` in the global namespace.

```html
<script src="https://unpkg.com/it-reduce/dist/index.min.js"></script>
```

Mostly useful for tests or when you want to be explicit about consuming an iterable without doing anything with any yielded values.

## Usage

```javascript
import reduce from 'it-reduce'

// This can also be an iterator, generator, etc
const values = [0, 1, 2, 3, 4]

const result = reduce(values, (acc, curr) => acc + curr, 0)

console.info(result) // 10
```

Async sources must be awaited:

```javascript
import reduce from 'it-reduce'

const values = async function * () {
  yield * [0, 1, 2, 3, 4]
}

const result = await reduce(values(), (acc, curr) => acc + curr, 0)

console.info(result) // 10
```

## License

Licensed under either of

- Apache 2.0, ([LICENSE-APACHE](LICENSE-APACHE) / <http://www.apache.org/licenses/LICENSE-2.0>)
- MIT ([LICENSE-MIT](LICENSE-MIT) / <http://opensource.org/licenses/MIT>)

## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.
