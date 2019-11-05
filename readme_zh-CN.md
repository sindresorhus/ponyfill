<h1 align="center">
	<img src="media/header-min.svg" alt="Ponyfill">
</h1>

<h4 align="center">像 polyfill 却带着小马的纯洁</h4><br><br><br>

*使用 [ponyfill.com](https://ponyfill.com) 链接到这里*

[en_US](readme.md)

## 小马的纯粹, 真的?

尽管 polyfills 很顽皮，ponyfill 却很纯真，就像小马.

## ponyfill 比 polyfill 好？

[polyfill](https://en.wikipedia.org/wiki/Polyfill_(programming)) 是[mokey patching](https://en.wikipedia.org/wiki/Monkey_patch)一个不存在的功能的 API 添加的那些代码。不幸的是，它通常是全局的修补，这会影响所有运行在这个环境的代码。当一个 polyfill 没有完全符合规范的时候（在某些情况下这是不可能的），这非常有问题，因为这会导致调试 bug 非常困难并且产生不一致性。或者当新功能的规格改变，你的代码取决于模块的依赖树某处的 polyfill 不同的行为，通常[你不应该修改不是你自己的 API](https://www.nczonline.net/blog/2010/03/02/maintainable-javascript-dont-modify-objects-you-down-own/)

ponyfill 则相反，它不 monkey patch 任何东西，作为替代，将功能作为普通的模块导出，所以你可以在本地使用，而不影响其他代码。

*tl;dr;* polyfill 淘气是因为他们修补原生 API，而 ponyfill 是纯净的并且不影响环境。

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
module.exports = function (value) {
	return value !== value;
};
```

```js
var isNanPonyfill = require('is-nan-ponyfill');

isNanPonyfill(5);
```

**ponyfill 应该永远不使用原生 API，即使可以**，因为它在不同环境有稍微不同的表现，这可以导致 bug。

## 我可以在哪里找到 ponyfill？

[搜索 npm。](https://npms.io/search?q=keywords%3Aponyfill)

## 我该如何创建一个 ponyfill？

- 阅读你要 ponyfill 的规格或者功能源代码。
- 初始化一个 [npm 包](https://github.com/sindresorhus/generator-nm)。
- [编写一些测试](https://ava.li) 去简单编写 ponyfill 逻辑
- 在你的 readme 链接功能的文档。[例子🌰。](https://github.com/sindresorhus/buffer-includes#readme)
- 在你的 readme 链接`https://ponyfill.com`。[例子🌰。](https://github.com/sindresorhus/object-assign#readme)
- 在你的 package.json 的`keywords`章节添加`ponyfill`。
- 发布！

## 资源

- [Ponyfill 定义 - Sillicon Valley Dictionary](http://svdictionary.com/words/ponyfill)
- [Polyfills 或者 Ponyfills？ - Pony Foo](https://ponyfoo.com/articles/polyfills-or-ponyfills)
- [Polyfill，Ponyfill 和 Prollyfill - Kikobeats](https://kikobeats.com/polyfill-ponyfill-and-prollyfill/)

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Sindre Sorhus](https://sindresorhus.com) has waived all copyright and related or neighboring rights to this work.

Header based on work by [Mary Winkler](https://www.vecteezy.com/members/acrylicana).
