<h1 align="center">
	<img src="https://cdn.rawgit.com/sindresorhus/ponyfill/bf5b4d09f669c690b359b66bb7c82f4759bee6b6/media/header-min.svg" alt="Ponyfill">
</h1>

<h4 align="center">Like polyfill but with pony pureness</h4><br><br><br>


## Pony pureness, really?

While polyfills are naughty, ponyfills are pure, just like ponies.


## How are ponyfills better than polyfills?

A [polyfill](https://en.wikipedia.org/wiki/Polyfill) is code that adds missing functionality by [monkey patching](https://en.wikipedia.org/wiki/Monkey_patch) an API. Unfortunately, it usually globally patches built-ins, which affects all code running in the environment. This is especially problematic when a polyfill is not fully spec compliant (which in some cases is impossible), as it could cause very hard to debug bugs and inconsistencies. Or when the spec for a new feature changes and your code depends on behavior that a module somewhere else in the dependency tree polyfills differently. In general, [you should not modify API's you don't own.](https://www.nczonline.net/blog/2010/03/02/maintainable-javascript-dont-modify-objects-you-down-own/)

A ponyfill, in contrast, doesn't monkey patch anything, but instead exports the functionality as a normal module, so you can use it locally without affecting other code.

*tl;dr;* Polyfills are naughty as they patch native APIs, while ponyfills are pure and don't affect the environment.

### Polyfill

```js
Number.isNaN = Number.isNaN || function (value) {
	return value !== value;
};
```

```js
require('is-nan-polyfill');

Number.isNaN(5);
```

### Ponyfill

```js
module.exports = Number.isNaN || function (value) {
	return value !== value;
};
```

```js
var isNanPonyfill = require('is-nan-ponyfill');

isNanPonyfill(5);
```

*Only use the native API in your ponyfill (the `Number.isNaN || ` part) when the spec is stable, to ensure it doesn't have differing behavior depending on the environment.*


## Where can I find ponyfills?

[Search npm.](https://npms.io/search?q=keywords%3Aponyfill)


## Resources

- [Ponyfill definition - Sillicon Valley Dictionary](http://svdictionary.com/words/ponyfill)
- [Polyfills or Ponyfills? - Pony Foo](https://ponyfoo.com/articles/polyfills-or-ponyfills)


## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Sindre Sorhus](https://sindresorhus.com) has waived all copyright and related or neighboring rights to this work.

Header based on work by [Mary Winkler](https://www.vecteezy.com/members/acrylicana).
