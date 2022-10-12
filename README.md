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
    - import into your project with NPM  `@import typography-baseline.css`
    - <kbd>copy</kbd> + <kbd>paste</kbd> this project's `baseline.css`
2. Add your own `typography.css` file that comes after the baseline, but before you style anything else.
3. Add something like `html {}` or `body {}`.
4. Modify the variables _in those rulesets_.
5. Then add your own element styles. 

**Don't modify the typography-baseline directly. Modify the variables it sets with new rulesets.**

### Modifying without Swearing or Heavy Drinking
One of the really annoying things about other CSS frameworks (cough cough <small>Bootstrap</small>) is that you mostly have to write new CSS to overwrite the existing styles. Often that means raising specificity, which is really stinking annoying. This is designed to avoid that by using [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)


The typography baseline sets all of the CSS variables on the `:root`. As CSS variables are subject to the cascade, you can override _any_ variable at any time by changing its value &mdash; on the same selector *or* a more specific one.

You can import this into your current CSS setup, and overwrite all the variables by setting new ones on the `html` element. 

So if you want the `--baseLinkColor` to be different, you can write the following in your own stylesheet:

```
html {
    --baseLinkColor: #c0ffee
}
```

**No raising specificity. Just changing a variable.**

If you want to theme a special area of the site, or even a particular widget, it's just:

```
.theme {
    --baseLinkColor: #c0ffee
}
```


#### Color Palette
Colors are derivatives of a base value of 55. All of the neutral colors are multipliers of rgb(55,55,55). Even the non-neutral colors are close-ish to that. 

```
    --colorNeutralDarker: rgb(55,55,55);                  /* base       */
    --colorNeutralDark: rgb(110,110,110);                 /* base * 2:  */
    --colorNeutral: rgb(165,165,165);                     /* base * 3:  */
    --colorNeutralLight: rgb(192.5,192.5,192.5);          /* base * 3.5 */
    --colorNeutralLighter: rgb(220,220,220);              /* base * 4:  */
```
Color-naming convention follows a pattern established [here](https://codepen.io/paceaux/pen/XdxQza). A big huge and heavy thanks to Sarah Braumiller for suggesting that convention years ago. 

[The great big idea](https://blog.frankmtaylor.com/2021/10/21/a-small-guide-for-naming-stuff-in-front-end-code/#css-pre-processor-naming-scss-sass-less-stylus) is that these color name tells you a meaningful aspect of the value, not the value itself. That way it feels safer changing it. 

#### Colors
All of the color variables are abstractions from the color palette. This is so you can change these colors without having to touch your neutral palette. 

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

You may notice that all of the font-sizes are in `em`. This is _intentional_ so that your headlines can scale easily relative to the font-size of their containers. That means **you should be careful about how many times you change `font-size`**. 

If you think you'll be changing `font-size` _a lot_, you may want to set these in `rem` instead, to avoid FOUC (Flash Of Unstyled Content). 

#### Spacing
Spacing is done with the golden ratio (.618 / 1.618)
`rem` is used for horizontal spacing so that text remains aligned, regardless of size. `em` is used for vertical spacing so that bigger text gets more room to breathe. 
You have two spacings to start with. 

```
    --bigSpacingHorizontal: 1.618rem;
    --baseSpacingHorizontal: .618rem;

    --bigSpacingVertical: 1.618em;
    --baseSpacingVertical: .618em;
```

#### Font Modifications

##### Font families
You have three font families to choose from. `--baseFontFamily` is applied to the html element. 

```
    --baseFontFamily: Georgia, 'Times New Roman', serif;
    --titleFontFamily: Helvetica, Arial, sans-serif;
    --codeFontFamily: monospace;
```

##### Font Weights
You have three font weights to choose from.

```
    --lightestFontWeight: 100;
    --baseFontWeight: 400;
    --heaviestFontWeight: 700;
```

 While the browser technically has nine font-weights, you're only able to add another four (for a total of seven) by following the pattern of adding "er" or "est". If you *really* need nine font-weights, consider naming the ones at the heavy end `--ultraHeavy` and `--ultraHeaviest`. 
 
 *Just make sure you've added those typefaces!*

 ```
    --lightFontWeight: 300;
    --lighterFontWeight: 200;
    --heavyFontWeight: 500;
    --heavierFontWeight: 600
 ```

If you add more font-weights, remember that [the browser will synthesize the font weights unless proper font-families with those weights are provided](https://w3c.github.io/csswg-drafts/css-fonts-4/#missing-weights)&mdash; unless you are using a [variable font ](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight#variable_fonts). **Add more font-weights carefully**. 

##### Font Styles
You have three font styles to use. These are called `fontVoice` because it's important for you to imagine how a person might read the text _out loud_. If you think someone might enunciate or pronounce it differently, that's "italic" (what you might use for `<em>` or `<i>`). The browser will actually look for an italic font. 

If you just want to show slanted text, that's "oblique". The browser is just going to angle the font. 

```
    --shiftedFontVoice: oblique 15deg;
    --baseFontVoice: normal;
    --alternateFontVoice: italic;
```

#### Quote Styles
One of the very few strong opinions in this baseline is the look and feel of a blockquote. However, you can set the  quotes that come before and after the `<blockquote>` and `<q>` elements. This is useful for internationalization; you have one place to make sure all quote symbols are updated!

```
    --baseTextQuotes: "\201C""\201D""\2018""\2019"; 
```

`<blockquote>` and `<samp>` both share a thick left "quote border":

```
    --baseQuoteBorder: 10px solid var(--colorNeutralLighter);
    --smallQuoteBorder: 5px solid var(--colorNeutralLight);
```

## Conventions and Standards

### Style guide
The CSS follows the guidelines established [here](https://gist.github.com/paceaux/f31e278613ab29b74a412a7eb5046422).

### Naming Conventions
CSS Variable names follow a convention established [here](https://blog.frankmtaylor.com/2021/10/21/a-small-guide-for-naming-stuff-in-front-end-code/).


[license-image]: http://img.shields.io/npm/l/typography-baseline.css.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/typography-baseline.css.svg
[downloads-url]: http://npm-stat.com/charts.html?package=typography-baseline.css

