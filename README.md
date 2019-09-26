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

## Usage
While this is relatively unopinionated, there are a few "opinions" to consider:

* `em` for for `font-size`
* a unitless `line-height`
* `rem` for left/right spacing
* text-spacing based on the golden ratio (.618 / 1.618)

### Fitting it into a CSS architecture
This would come after a reset / normalize and before you set baseline styles for forms or tables. If you're a fan of [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/), this is in the Elements layer.

### Modifying without Swearing or Heavy Drinking
One of the really annoying things about other CSS frameworks (cough cough <small>Bootstrap</small>) is that you mostly have to write new CSS to overwrite the existing styles. Often that means raising specificity, which is really stinking annoying. This is designed to avoid that by using [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)


The typography baseline sets all of the CSS variables on the `:root`. As CSS variables are subject to the cascade, you can override _any_ variable at any time by changing its value on the relevant selector. You can import this into your current CSS setup, and overwrite all the variables by setting new ones on the `html` element. 

So if you want the `--baseLinkColor` to be different, you can write the following in your own stylesheet:

```
html {
    --baseLinkColor: #c0ffee
}
```

No raising specificity. Just changing a variable. 

If you want to theme a special area of the site, or even a particular widget, it's just:

```
.theme {
    --baseLinkColor: #c0ffee
}
```


#### Color Palette
Colors are derivitives of a base value of 55. All of the neutral colors are multipliers of rgb(55,55,55). Even the non-neutral colors are close-ish to that. 

```
    --colorNeutralDarker: rgb(55,55,55);                  /* base       */
    --colorNeutralDark: rgb(110,110,110);                 /* base * 2:  */
    --colorNeutral: rgb(165,165,165);                     /* base * 3:  */
    --colorNeutralLight: rgb(192.5,192.5,192.5);          /* base * 3.5 */
    --colorNeutralLighter: rgb(220,220,220);              /* base * 4:  */
```
Color-naming convention follows a pattern established [here](https://codepen.io/paceaux/pen/XdxQza). A big huge and heavy thanks to Sarah Braumiller for suggesting that convention years ago. 

#### Colors
All of the colors variables are abstractions from the color palette. This is so you can change these colors without having to touch your neutral palette. 

```
    --baseTextColor: var(--colorNeutralDarker);
    --baseEditorialTextColor: var(--colorNeutralDark);
    --baseLinkColor: var(--colorCool);
    --baseLinkColorHover: var(--colorCoolDarker);
    --baseInlineBorderColor: var(--colorNeutralLight);
```

#### Line Heights
The `--baseLineHeight` is applied to body copy, and the `--smallLineHeight` is used on titles:

```    
    --baseLineHeight: 1.618;
    --smallLineHeight: 1.2;
```

#### Text Sizes
You have a minimum of 6 text sizes in two categories: `--<n>TextSize` and `--<n>TitleSize`. You have a "base" and then superlatives or diminutives to describe the deviation from that base. e.g.:


```
    --biggestTextSize:  1.3em;
    --biggerTextSize: 1.2em;
    --bigTextSize: 1.1em;
    --baseTextSize: 1em; /*What all ordinary body copy will be*/
    --smallTextSize: .8em;
    --smallerTextSize: .75em;
    --smallestTextSize: .618em;
```

For _titles_ you have only _six_ sizes, instead of seven. That's because each title size corresponds to an `<h/>` element. 

You may also notice that title sizes overlap with base text sizes. This is intentional! You have the flexibility to have your smaller headings be the same as larger text, or to create new title sizes for your headings that won't overlap with the text. 


```
    --biggestTitleSize: 2.617924em; /* (16 x 1.618) x 1.618 */
    --bigTitleSize: 1.618em;
    --baseTitleSize: 1.5em;
    --smallTitleSize: var(--biggestTextSize);
    --smallerTitleSize: var(--biggerTextSize);
    --smallestTitleSize: var(--bigTextSize);
```

#### Font families
You have three font families to choose from. `--baseFontFamily` is applied to the html element. 

```
    --baseFontFamily: Georgia, 'Times New Roman', serif;
    --titleFontFamily: Helvetica, Arial, sans-serif;
    --codeFontFamily: monospace;
```

## Conventions and Standards

### Style guide
The CSS follows the guidelines established [here](https://gist.github.com/paceaux/f31e278613ab29b74a412a7eb5046422).

### Naming Conventions
CSS Variable names follow a convention established [here](https://gist.github.com/paceaux/8638765e747f5bd6387b721cde99e066#sassscssstylus-naming).


[license-image]: http://img.shields.io/npm/l/typography-baseline.css.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/typography-baseline.css.svg
[downloads-url]: http://npm-stat.com/charts.html?package=typography-baseline.css

