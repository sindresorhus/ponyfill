<h1 align="center">
	<img src="media/header-min.svg" alt="Ponyfill">
</h1>
<h4 align="center">Like polyfill but with pony pureness</h4>
<br>
<br>
<br>

*Use [ponyfill.com](https://ponyfill.com) for linking here.*

## What’s a ponyfill?

A **ponyfill** is an implementation of a standard, but without pretending to be it.

Unlike [polyfills](https://en.wikipedia.org/wiki/Polyfill_%28programming%29), ponyfills don't pretend to be the native API. They offer the same functionality through explicit imports and usage, keeping your code predictable and side-effect free.

## The problem with polyfills

In JavaScript, a polyfill adds missing features by [monkey patching](https://en.wikipedia.org/wiki/Monkey_patch) the environment, typically by modifying globals like `Array.prototype`, `Object`, or `window`. This approach creates several problems:

- The polyfill is only partially spec-compliant (sometimes unavoidable)
- The spec changes
- Another library polyfills the same thing differently

In general, [you should not modify APIs you don’t own](https://www.nczonline.net/blog/2010/03/02/maintainable-javascript-dont-modify-objects-you-down-own/). Ponyfills avoid this entirely by staying pure.

## It’s not just for JavaScript

- **JavaScript** ponyfill: Exports functionality via a normal module, doesn’t patch anything
- **HTML** ponyfill: Uses custom elements or classes to emulate new features
- **CSS** ponyfill: Uses custom properties to simulate proposed syntax

## Polyfill vs Ponyfill

| Feature                     | Polyfill | Ponyfill           |
| --------------------------- | -------- | ------------------ |
| Patches global environment? | Yes      | No                 |
| Aims to match spec exactly? | Yes      | Often              |
| Meant to be removed later?  | Yes      | Not necessarily    |
| Causes global side effects? | Yes      | No                 |

**Ponyfills are clear. Explicit. Honest.** You use them directly and deliberately.

## Examples

### JavaScript

#### Polyfill

```js
Number.isNaN ??= function (value) {
	return value !== value;
};
```

```js
import 'is-nan-polyfill';

Number.isNaN(5);
```

#### Ponyfill

```js
export default function isNaN(value) {
	return value !== value;
};
```

```js
import isNanPonyfill from 'is-nan-ponyfill';

isNanPonyfill(5);
```

### HTML

```html
<!-- Instead of a future <card> element -->
<card-ponyfill>
	<h2 slot="title">Hello</h2>
</card-ponyfill>

<script>
	customElements.define('card-ponyfill', class extends HTMLElement {
		connectedCallback() {
			this.innerHTML = `<div class="card">${this.innerHTML}</div>`;
		}
	});
</script>
```

### CSS

```css
/* Instead of future syntax like @container */
:root {
	--container-sm: 480px;
	--container-lg: 768px;
}

.responsive-text[data-container='small'] {
	font-size: 0.875rem;
}

.responsive-text[data-container='large'] {
	font-size: 1.125rem;
}
```

```html
<div class="responsive-text" data-container="small">Responsive text</div>
```

### Why not use the native API in a ponyfill when available?

Ponyfills should avoid relying on native APIs unless unavoidable because:

- Native APIs may behave inconsistently
- Bugs or spec changes undermine confidence
- Reimplementing avoids dependency on the environment

Use native APIs **only** when:

- No alternative exists
- Reimplementation would hurt performance or bundle size

## How to create your own ponyfill

1. Read the spec or explainer
2. Implement the feature locally, without patching anything global
3. Avoid assuming native API correctness unless necessary
4. Write tests
5. Publish a module or package
6. Add `ponyfill` to the keywords field
7. Link to [ponyfill.com](https://ponyfill.com) in your readme

## Where can I find ponyfills?

[Search npm.](https://www.npmjs.com/search?q=keywords:ponyfill)

## Resources

- [Ponyfill definition - Silicon Valley Dictionary](http://svdictionary.com/words/ponyfill)
- [Polyfills or Ponyfills? - Pony Foo](https://ponyfoo.com/articles/polyfills-or-ponyfills)
- [Polyfill, Ponyfill and Prollyfill - Kikobeats](https://kikobeats.com/polyfill-ponyfill-and-prollyfill/)

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Sindre Sorhus](https://sindresorhus.com) has waived all copyright and related or neighboring rights to this work.

Header based on work by [Mary Winkler](https://www.vecteezy.com/members/acrylicana).
