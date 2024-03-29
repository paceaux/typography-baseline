# Typography-baseline.css

> A good start to your CSS typography that covers all the semantic nooks and crannies

[![License][license-image]][license-url] [![Downloads][downloads-image]][downloads-url]

**NPM**

```bash
npm install --save typography-baseline.css
```

**Download**
`https://raw.githubusercontent.com/paceaux/typography-baseline/master/src/baseline.css`

## What does it do?

### It gives you a good start

Before you start the layout of a web site or web application, and before you dive into applying to brand, you need something to which you should apply your brand. This is that thing.

The easiest place to start in a design is with the typography.

This makes it easy to do that.

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
* Safari
* Opera


## Usage

While this is relatively unopinionated, there are a few "opinions" to consider:

* [`em` for for `font-size`](https://css-tricks.com/rems-ems/)
* [a unitless `line-height`](https://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/)
* `rem` for left/right spacing
* [text-spacing based on the golden ratio ](https://pearsonified.com/golden-ratio-typography-intro/)(.618 / 1.618)

### Fitting it into a CSS architecture

This would come after a reset / [normalize](https://necolas.github.io/normalize.css/) and before you set baseline styles for forms or tables. If you're a fan of [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/), this is in the Elements layer.

If you were to load this into a [CSS Layer](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer), you would want it to come very early so that you could over ride it.

Wherever you place it, place it _early_ in the cascade so that other things can use and/or  re-declare the variables.

#### Using it in a project

1. Add the baseline
    * import into your project with NPM  `@import typography-baseline.css`
    * <kbd>copy</kbd> + <kbd>paste</kbd> this project's `src/baseline.css`
2. Add your own `typography.css` file that comes after the baseline, but before you style anything else.
3. Add something like `html {}` or `body {}`.
4. Modify the variables _in those rulesets_.
5. Then add your own element styles.

**Don't modify the typography-baseline directly. Modify the variables it sets with new rulesets.**

### Modifying without Swearing or Heavy Drinking

One of the really annoying things about other CSS frameworks (cough cough <small>Bootstrap</small>) is that you mostly have to write new CSS to overwrite the existing styles. Often that means raising specificity, which is really stinking annoying. This is designed to avoid that by using [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)

See [Standards and Conventions](#standards-and-conventions) for understanding why variables are named the way they are.

#### Override close to (or at) the root

The typography baseline sets all of the CSS variables on the `:root`. As CSS variables are subject to the cascade, you can override _any_ variable at any time by changing its value &mdash; on the same selector *or* a more specific one.

You can import this into your current CSS setup, and overwrite all the variables by setting new ones on the `html` element.

So if you want the `--baseLinkColor` to be different, you can write the following in your own stylesheet:

```css
html {
    --baseLinkColor: #c0ffee
}
```

#### No raising specificity; just changing a variable

If you want to theme a special area of the site, or even a particular widget, it's just:

```css
.theme {
    --baseLinkColor: #c0ffee
}
```

#### Color Palette(s)

The color palette contains predominantly neutral colors.

Neutral colors are derivatives of a base value of 31. All of the neutral colors are multipliers of rgb(31,31,31).

```css
    --colorNeutralDarker: rgb(31,31,31);     /* base  */
    --colorNeutralDark: rgb(62,62,62);       /* base * 2 */
    --colorNeutral: rgb(155,155,155);        /* base * 5 */
    --colorNeutralLight: rgb(186,186,186);   /* base * 6 */
    --colorNeutralLighter: rgb(217,217,217); /* base * 7 */
```

The color-naming convention follows a pattern established [here](https://codepen.io/paceaux/pen/XdxQza). A big huge and heavy thanks to Sarah Braumiller for suggesting that convention years ago.

#### Applying Colors

All of the color variables are abstractions from the color palette. This is so you can change these colors without having to touch your neutral palette &mdash; and you can add new palettes if you want.

```css
    --baseTextColor: var(--colorNeutralDarker);
    --baseEditorialTextColor: var(--colorNeutralDark);
    --baseLinkColor: var(--colorCool);
    --baseLinkColorHover: var(--colorCoolDarker);
    --baseInlineBorderColor: var(--colorNeutralLight);
```

#### Line Heights

The `--baseLineHeight` is applied to body copy, and the `--smallLineHeight` is used on titles:

```css
    --baseLineHeight: 1.618;
    --smallLineHeight: 1.2;
```

#### Text and Title Sizes

You have a minimum of 6 text sizes in two categories: `--<n>TextSize` and `--<n>TitleSize`. You have a "base" and then superlatives or diminutives to describe the deviation from that base. e.g.:

```css
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

```css
    --biggestTitleSize: 2.617924em; /* (16 x 1.618) x 1.618 */
    --bigTitleSize: 1.618em;
    --baseTitleSize: 1.5em;
    --smallTitleSize: var(--biggestTextSize);
    --smallerTitleSize: var(--biggerTextSize);
    --smallestTitleSize: var(--bigTextSize);
```

You may notice that all of the font-sizes are in `em`. This is _intentional_ so that your headlines can scale easily relative to the font-size of their containers. That means **you should be careful about how many times you change `font-size`**.

If you think you'll be changing `font-size` _a lot_, you may want to set these in `rem` instead, to avoid FOUC (Flash Of Unstyled Content).

#### Spacing

Spacing is done with the golden ratio (.618 / 1.618)
`rem` is used for horizontal spacing so that text remains aligned, regardless of size. `em` is used for vertical spacing so that bigger text gets more room to breathe.

You have two spacings to start with.

```css
    --bigSpacingHorizontal: 1.618rem;
    --baseSpacingHorizontal: .618rem;

    --bigSpacingVertical: 1.618em;
    --baseSpacingVertical: .618em;
```

#### Font Modifications

##### Font families

You have three font families to choose from. `--baseFontFamily` is applied to the html element.

```css
    --baseFontFamily: Georgia, 'Times New Roman', serif;
    --titleFontFamily: Helvetica, Arial, sans-serif;
    --codeFontFamily: monospace;
```

##### Font Weights

You have three font weights to choose from.

```css
    --lightestFontWeight: 100;
    --baseFontWeight: 400;
    --heaviestFontWeight: 700;
```

 While the browser technically has nine font-weights, you're only able to add another four (for a total of seven) by following the pattern of adding "er" or "est". If you *really* need nine font-weights, consider naming the ones at the heavy end `--ultraHeavy` and `--ultraHeaviest`.

 *Just make sure you've added those typefaces!*

 ```css
    --lightFontWeight: 300;
    --lighterFontWeight: 200;
    --heavyFontWeight: 500;
    --heavierFontWeight: 600
 ```

If you add more font-weights, remember that [the browser will synthesize the font weights unless proper font-families with those weights are provided](https://w3c.github.io/csswg-drafts/css-fonts-4/#missing-weights)&mdash; unless you are using a [variable font ](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight#variable_fonts). **Add more font-weights carefully**. 

##### Font Styles

You have three font styles to use. These are called `fontVoice` because it's important for you to imagine how a person might read the text _out loud_. If you think someone might enunciate or pronounce it differently, that's "italic" (what you might use for `<em>` or `<i>`). The browser will actually look for an italic font.

If you just want to show slanted text, that's "oblique". The browser is just going to angle the font. 

```css
    --shiftedFontVoice: oblique 15deg;
    --baseFontVoice: normal;
    --alternateFontVoice: italic;
```

#### Quote Styles

One of the very few strong opinions in this baseline is the look and feel of a blockquote. However, you can set the  quotes that come before and after the `<blockquote>` and `<q>` elements. This is useful for internationalization; you have one place to make sure all quote symbols are updated!

```css
    --baseTextQuotes: "\201C""\201D""\2018""\2019"; 
```

`<blockquote>` and `<samp>` both share a thick left "quote border":

```css
    --baseQuoteBorder: 10px solid var(--colorNeutralLighter);
    --smallQuoteBorder: 5px solid var(--colorNeutralLight);
```

#### Links

One of the only strong opinions here is how links are presented. Instead of using using `text-decoration`, they use a bottom border. This is because I like just a little more space between text and line than what `text-decoration` offers.

Your core link-related styles are:

```css
    --baseLinkColor: var(--colorCool);
    --baseLinkColorHover: var(--colorCoolDarker);

    --idleTextLineStyle: dotted; /* default */
    --interestTextLineStyle: solid; /* :hover and :focus*/
    --activeTextLineStyle: solid; /* :active */
    --idleTextDecoration: var(--idleTextLineStyle) underline 2px;
```

Since we indicate interaction with color and border, if you wanted to change how links behave, you would need to target `:hover`, `:focus`, and `:active` states. e.g.:

```css
a {
    border-bottom: 1px var(--idleTextLineStyle);
}

a:hover,
a:focus {
    border-bottom-style: var(--interestTextLineStyle);
}

a:active {
    border-bottom-style: var(--activeTextLineStyle);
}
```

## Standards and Conventions

### Accessibility (A11Y)

The <samp>test.html</samp> file passes [WCAG 2.1](https://www.w3.org/TR/WCAG21/) level AA guidelines. It is tested _manually_ using the [Axe dev tools](https://chrome.google.com/webstore/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd) Chrome extension.

The text and link colors were determined by testing how they contrast each other and a white background using [WebAIM's Contrast Checker](https://webaim.org/resources/contrastchecker/).

### Style guide

The CSS is linted against [stylelint](https://stylelint.io/). The rules are in the `.stylelintrc` file. There is a specific order for CSS properties (content, position, font, inside-out box sizing, effects).

### Naming Conventions

CSS Variable names follow a convention established [here](https://blog.frankmtaylor.com/2021/10/21/a-small-guide-for-naming-stuff-in-front-end-code/).

The guiding principles for the variable names are:

* camelCased
* Describe usage or purpose
* Favor descriptors (adjectives) that can use common comparatives and superlatives (e.g <samp>er</samp> and <samp>est</samp>) to indicate how variations of a common value are related.
* Start by indicating if it's a base or a derivative with a modifier(adjective): <samp>base</samp>, <samp>small</samp>, <samp>big</samp>, <samp>shifted</samp>, <samp>alternate</samp>
* Then indicate the domain of the user experience  the variable affects with a noun: <samp>color</samp>, <samp>font</samp>, <samp>lineHeight</samp>, <samp>spacing</samp>, <samp>text</samp>, <samp>title</samp>, <samp>voice</samp>
* If necessary, narrow the domain with another noun:
  * Subdomain of the affected value: <samp>LineStyle</samp>, <samp>Size</samp>, <samp>Weight</samp>
  * A specific state where the value might change: <samp>Hover</samp>, <samp>interest</samp>

[license-image]: http://img.shields.io/npm/l/typography-baseline.css.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/typography-baseline.css.svg
[downloads-url]: http://npm-stat.com/charts.html?package=typography-baseline.css
