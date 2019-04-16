# Typography Baseline

Base typographical styles for all your  HTML elements.

[![License][license-image]][license-url] [![Downloads][downloads-image]][downloads-url]

## I have a normalize/reset, why do I need this?
This isn't meant to replace a normalize or a reset. Keep using that! This makes sure that even obscure elements (like `<del>` or `<samp>`) look like something nice.

## Where does this fit in my CSS architecture?
This would come after a reset / normalize and before you set baseline styles for forms tables. And definitely before you write a single ruleset with a class. If you're a fan of [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/), this is in the Elements layer.

## What should I change?
Anything and everything. It's a baseline. This thing's job is to make sure everything looks like something.
Look at the `:root` ruleset for some ideas. Most of the baseline has been consolidated into [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables).

## What's up with that HTML file?
The HTML file is an attempt to use all of the inline, content-flow, and otherwise odd/obscure semantic elements appropriately. Semantics are hard.

## Can I see it in action?
There is a live version over on CodePen: http://codepen.io/paceaux/pen/grKWWe

## Any other details I should know?
YES!

CSS Variable names follow a convention established [here](https://gist.github.com/paceaux/8638765e747f5bd6387b721cde99e066#sassscssstylus-naming).

There's a more robust example of a color palette [here](https://codepen.io/paceaux/pen/XdxQza).

[license-image]: http://img.shields.io/npm/l/typography-baseline.css.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/typography-baseline.css.svg
[downloads-url]: http://npm-stat.com/charts.html?package=typography-baseline.css

