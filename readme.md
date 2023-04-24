<h1 align="center">
	<img src="media/header-min.svg" alt="Ponyfill">
</h1>
<h4 align="center">Like polyfill but with pony pureness</h4>
<br>
<br>
<br>

*Use [ponyfill.com](https://ponyfill.com) for linking here.*

## Pony pureness, really?

While polyfills are naughty, ponyfills are pure, just like ponies.

## How are ponyfills better than polyfills?

A [polyfill](https://en.wikipedia.org/wiki/Polyfill_(programming)) is code that adds missing functionality by [monkey patching](https://en.wikipedia.org/wiki/Monkey_patch) an API. Unfortunately, it usually globally patches built-ins, which affects all code running in the environment. This is especially problematic when a polyfill is not fully spec compliant (which in some cases is impossible), as it could cause very hard to debug bugs and inconsistencies. Or when the spec for a new feature changes and your code depends on behavior that a module somewhere else in the dependency tree polyfills differently. In general, [you should not modify API's you don't own.](https://www.nczonline.net/blog/2010/03/02/maintainable-javascript-dont-modify-objects-you-down-own/)

A ponyfill, in contrast, doesn't monkey patch anything, but instead exports the functionality as a normal module, so you can use it locally without affecting other code.

*tl;dr:* Polyfills are naughty as they patch native APIs, while ponyfills are pure and doesn't affect the environment.

### Polyfill

```js
Number.isNaN ??= function (value) {
	return value !== value;
};
```

```js
import 'is-nan-polyfill';

Number.isNaN(5);
```

### Ponyfill

```js
export default function isNaN(value) {
	return value !== value;
};
```

```js
import isNanPonyfill from 'is-nan-ponyfill';

isNanPonyfill(5);
```

**Ponyfills should avoid using native APIs**, because potential bugs or differences in the native APIs will make such a ponyfill less robust (therefore defeating one of its main purposes). There are important exceptions, such as when:

- There is no way to implement some of the ponyfill without native APIs.
- Reimplementing native parts would have a large cost (e.g. performance or code size).

In such cases, it's still valuable for the ponyfill to minimize any assumptions about the underlying environment.

## Where can I find ponyfills?

[Search npm.](https://npms.io/search?q=keywords%3Aponyfill)

## How do I make a ponyfill?

- Read the specification or source code of the feature you want to ponyfill.
- Initialize an [npm package](https://github.com/sindresorhus/generator-nm).
- [Write some tests](https://avajs.dev) to ease writing the ponyfill logic.
- Link to documentation about the feature in your readme. [Example.](https://github.com/sindresorhus/buffer-includes#readme)
- Link to `https://ponyfill.com` in your readme. [Example.](https://github.com/sindresorhus/object-assign#readme)
- Add `ponyfill` to the `keywords` section in package.json.
- Publish!

## Resources

- [Ponyfill definition - Silicon Valley Dictionary](http://svdictionary.com/words/ponyfill)
- [Polyfills or Ponyfills? - Pony Foo](https://ponyfoo.com/articles/polyfills-or-ponyfills)
- [Polyfill, Ponyfill and Prollyfill - Kikobeats](https://kikobeats.com/polyfill-ponyfill-and-prollyfill/)

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Sindre Sorhus](https://sindresorhus.com) has waived all copyright and related or neighboring rights to this work.

Header based on work by [Mary Winkler](https://www.vecteezy.com/members/acrylicana).
