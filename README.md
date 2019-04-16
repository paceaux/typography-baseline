# Typography-baseline.css
> A good start to your CSS typography that covers all the semantic nooks and crannies

[![License][license-image]][license-url] [![Downloads][downloads-image]][downloads-url]

**NPM**
```
npm install --save typography-baseline.css
```
**Download**
`https://raw.githubusercontent.com/paceaux/typography-baseline/master/src/baseline.css`

## What does it do?
### It gives you a good start
Before you start the layout of a web site or web application, and before you dive into applying to brand, you need something to which you should apply your brand. This is that thing. 

The easiest place to start in a design is with the typography. This makes it easy to do that. 

### It covers all your semantic markup
Driven by the [W3C spec](https://www.w3.org/TR/html5/) this addresses almost every semantic element that will wrap text and makes sure that everything looks like _something_. 

The <samp>test.html</samp> file  uses each and every element according to its semantic definition, too. So you have a miniature guide to semantics built in.

This saves you from a scare down the road when someone wants to output the `<kbd>` element, use `<dfn>`, or try some other obscure element. 

### Gives you a "no-design" design
For those times where you need just a bit more than a [Normalize](http://necolas.github.io/normalize.css/), but way less than [Bootstrap](https://getbootstrap.com/), this gets you there. 

This is a fairly unopinionated approach to making sure that the text has a decent font family, decent spacing, and decent visual appeal. 

## Browser Support
* Firefox
* Chrome
* Edge
* IE10*
* Safari
* Opera

 >*IE10 doesn't support CSS Variables, but nothing will break in IE10 if that's the case. 

## Extended Details
As this is typography-centric, it's meant to be very unopinionated. 

Being very unopinionated means:

* Focuses on text and text spacing so it doesn't massively disrupt layouts
* Styles elements with the lowest specificity possible so front-end devs don't have to rewrite stuff and back-end devs don't write loads of `!important`
* Uses a neutral color palette so that it fits well in any color scheme
* Progressively uses CSS Variables so that you have one single place to change properties. 

Unopinionated doesn't mean, "no opinions". There are a few things that would be harder to change (an hour or two for experienced devs):

* `em` for for `font-size`
* a unitless `line-height`
* `rem` for left/right spacing
* text-spacing based on the golden ratio (.618 / 1.618)
 

### Fitting it into a CSS architecture
This would come after a reset / normalize and before you set baseline styles for forms or tables. If you're a fan of [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/), this is in the Elements layer.

### Conventions and Standards

#### Style guide
The CSS follows the guidelines established [here](https://gist.github.com/paceaux/f31e278613ab29b74a412a7eb5046422).

#### Naming Conventions
CSS Variable names follow a convention established [here](https://gist.github.com/paceaux/8638765e747f5bd6387b721cde99e066#sassscssstylus-naming).

Color-naming convention follows a pattern established [here](https://codepen.io/paceaux/pen/XdxQza). A big huge and heavy thanks to Sarah Braumiller for suggesting that convention years ago. 

## Live Examples
There is a live version over on CodePen: [http://codepen.io/paceaux/pen/grKWWe](http://codepen.io/paceaux/pen/grKWWe)

You can also see it in action on [frankmtaylor.com](https://frankmtaylor.com) or [blog.frankmtaylor.com](https://blog.frankmtaylor.com). 


[license-image]: http://img.shields.io/npm/l/typography-baseline.css.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/typography-baseline.css.svg
[downloads-url]: http://npm-stat.com/charts.html?package=typography-baseline.css

