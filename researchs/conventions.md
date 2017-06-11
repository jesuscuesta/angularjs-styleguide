# CSS conventions

## Sass and CSS features

#### Properties
CSS Variables are entities defined by CSS authors which contain specific values to be reused throughout a document.

##### [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_variables)
 They are set using custom property notation and are accessed using the var() function.

 ```css
   --font-stack:    Helvetica, sans-serif;
   --primary-color: #333;

   body {
     font: 100% var(--font-stack);
     color: var(--primary-color);
   }
 ```

##### [Sass](http://sass-lang.com/guide#topic-2)
```scss
  $font-stack:    Helvetica, sans-serif;
  $primary-color: #333;

  body {
    font: 100% $font-stack;
    color: $primary-color;
  }
```

#### Mixins
A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes.

##### [CSS](https://tabatkins.github.io/specs/css-apply-rule/)

```css
 --toolbar-theme: {
   background-color: hsl(120, 70%, 95%);
   border-radius: 4px;
   border: 1px solid var(--theme-color late);
 };

 @apply --toolbar-theme;
```

##### [SASS](http://sass-lang.com/guide#topic-6)

```scss
  @mixin border-radius($radius) {
   -webkit-border-radius: $radius;
      -moz-border-radius: $radius;
       -ms-border-radius: $radius;
           border-radius: $radius;
  }

  .box { @include border-radius(10px); }
```

#### Import
CSS has an import option that lets you split your CSS into smaller, more maintainable portions.

##### [SASS](http://sass-lang.com/guide#topic-5) and [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/@import)
```scss
// _reset.scss

html,
body,
ul,
ol {
  margin: 0;
  padding: 0;
}
```

```scss
// base.scss

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

#### [CSS Animations and Transitions]
[CSS animations] make it possible to animate transitions from one CSS style configuration to another. Animations consist of two components, a style describing the CSS animation and a set of keyframes that indicate the start and end states of the animation's style, as well as possible intermediate waypoints.
[CSS animations]:https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations
[CSS Animations and Transitions]:https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations

## Atomic Design

Atomic design is methodology for creating design systems. There are five distinct levels in atomic design:
- [Atoms]
- [Molecules]
- [Organisms]
- [Templates]
- [Pages]

[Atoms]: http://bradfrost.com/blog/post/atomic-web-design/#atoms
[Molecules]: http://bradfrost.com/blog/post/atomic-web-design/#molecules
[Organisms]: http://bradfrost.com/blog/post/atomic-web-design/#organisms
[Templates]: http://bradfrost.com/blog/post/atomic-web-design/#templates
[Pages]: http://bradfrost.com/blog/post/atomic-web-design/#pages

### Why Atomic Design

Atomic design provides a clear methodology for crafting design systems. Clients and team members are able to better appreciate the concept of design systems by actually seeing the steps laid out in front of them.

Atomic design gives us the ability to traverse from abstract to concrete. Because of this, we can create systems that promote consistency and scalability while simultaneously showing things in their final context. And by assembling rather than deconstructing, we’re crafting a system right out of the gate instead of cherry picking patterns after the fact.

Which makes a perfect pattern for using with web components.

## Guidelines

### Terminology

#### Rule declaration

A “rule declaration” is the name given to a selector (or a group of selectors) with an accompanying group of properties. Here's an example:

```css
.listing {
  font-size: 18px;
  line-height: 1.2;
}
```

#### Selectors

In a rule declaration, “selectors” are the bits that determine which elements in the DOM tree will be styled by the defined properties. Selectors can match HTML elements, as well as an element's class, ID, or any of its attributes. Here are some examples of selectors:

```css
.my-element-class {
  /* ... */
}

[aria-hidden] {
  /* ... */
}
```

#### Properties

Finally, properties are what give the selected elements of a rule declaration their style. Properties are key-value pairs, and a rule declaration can contain one or more property declarations. Property declarations look like this:

```css
/* some selector */ {
  background: #f1f1f1;
  color: #333;
}
```

### CSS

#### Formatting

* Use soft tabs (2 spaces) for indentation
* Prefer dashes over camelCasing in class names.
  - Underscores and PascalCasing are okay if you are using BEM (see [OOCSS and BEM](#oocss-and-bem) below).
* Do not use ID selectors
* When using multiple selectors in a rule declaration, give each selector its own line.
* Put a space before the opening brace `{` in rule declarations
* In properties, put a space after, but not before, the `:` character.
* Put closing braces `}` of rule declarations on a new line
* Put blank lines between rule declarations

<span style="color:red">**Bad**</span>

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```

<span style="color:green">**Good**</span>

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

#### Comments

* Prefer line comments (`//` in Sass-land) to block comments.
* Prefer comments on their own line. Avoid end-of-line comments.
* Write detailed comments for code that isn't self-documenting:
  - Uses of z-index
  - Compatibility or browser-specific hacks

**Example**

```jsx
// ListingCard.jsx
function ListingCard() {
  return (
    <article class="ListingCard ListingCard--featured">

      <h1 class="ListingCard__title">Adorable 2BR in the sunny Mission</h1>

      <div class="ListingCard__content">
        <p>Vestibulum id ligula porta felis euismod semper.</p>
      </div>

    </article>
  );
}
```

```css
/* ListingCard.css */
.ListingCard { }
.ListingCard--featured { }
.ListingCard__title { }
.ListingCard__content { }
```

  * `.ListingCard` is the “block” and represents the higher-level component
  * `.ListingCard__title` is an “element” and represents a descendant of `.ListingCard` that helps compose the block as a whole.
  * `.ListingCard--featured` is a “modifier” and represents a different state or variation on the `.ListingCard` block.

### ID selectors

While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) to your rule declarations, and they are not reusable.

For more on this subject, read [CSS Wizardry's article](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) on dealing with specificity.

#### JavaScript hooks

Avoid binding to the same class in both your CSS and JavaScript. Conflating the two often leads to, at a minimum, time wasted during refactoring when a developer must cross-reference each class they are changing, and at its worst, developers being afraid to make changes for fear of breaking functionality.

We recommend creating JavaScript-specific classes to bind to, prefixed with `.js-`:

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

#### Border

Use `0` instead of `none` to specify that a style has no border.

<span style="color:red">**Bad**</span>

```css
.foo {
  border: none;
}
```

<span style="color:green">**Good**</span>

```css
.foo {
  border: 0;
}
```

### Sass

#### Syntax

* Use the `.scss` syntax, never the original `.sass` syntax
* Order your regular CSS and `@include` declarations logically (see below)

#### Ordering of property declarations

1. Property declarations

    List all standard property declarations, anything that isn't an `@include` or a nested selector.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      // ...
    }
    ```

2. `@include` declarations

    Grouping `@include`s at the end makes it easier to read the entire selector.

    ```scss
    .btn-green {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);
      // ...
    }
    ```

3. Nested selectors

    Nested selectors, _if necessary_, go last, and nothing goes after them. Add whitespace between your rule declarations and nested selectors, as well as between adjacent nested selectors. Apply the same guidelines as above to your nested selectors.

    ```scss
    .btn {
      background: green;
      font-weight: bold;
      @include transition(background 0.5s ease);

      .icon {
        margin-right: 10px;
      }
    }
    ```

#### Variables

Prefer dash-cased variable names (e.g. `$my-variable`) over camelCased or snake_cased variable names. It is acceptable to prefix variable names that are intended to be used only within the same file with an underscore (e.g. `$_my-variable`).

#### Mixins

Mixins should be used to DRY up your code, add clarity, or abstract complexity--in much the same way as well-named functions. Mixins that accept no arguments can be useful for this, but note that if you are not compressing your payload (e.g. gzip), this may contribute to unnecessary code duplication in the resulting styles.

#### Extend directive

`@extend` should be avoided because it has unintuitive and potentially dangerous behavior, especially when used with nested selectors. Even extending top-level placeholder selectors can cause problems if the order of selectors ends up changing later (e.g. if they are in other files and the order the files are loaded shifts). Gzipping should handle most of the savings you would have gained by using `@extend`, and you can DRY up your stylesheets nicely with mixins.

#### Nested selectors

**Do not nest selectors more than three levels deep!**

```scss
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}
```

When selectors become this long, you're likely writing CSS that is:

* Strongly coupled to the HTML (fragile) *—OR—*
* Overly specific (powerful) *—OR—*
* Not reusable


Again: **never nest ID selectors!**

If you must use an ID selector in the first place (and you should really try not to), they should never be nested. If you find yourself doing this, you need to revisit your markup, or figure out why such strong specificity is needed. If you are writing well formed HTML and CSS, you should **never** need to do this.


## Natural language
Literally every element in nowadays web interfaces already have it's own name (or even several names). We as web developers are using them in every day life talking to other developers and designers. So why should we make up some fancy class names with prefixes or suffixes, abbreviate words or concatenate several words to make selector more unique?

Just use natural language for naming classes. These words are mostly unique already, and they make your code a lot more readable and understandable. Using this names as CSS selector gives us most descriptive and understandable language to build web pages and communicate with other developers.

## BEM
The BEM approach ensures that everyone who participates in the development of a website works with a single codebase and speaks the same language. Using proper naming will prepare you for the changes in design of the website.

In BEM there are three pieces:

### Block
Encapsulates a standalone entity that is meaningful on its own. While blocks can be nested and interact with each other, semantically they remain equal; there is no precedence or hierarchy. Holistic entities without DOM representation (such as controllers or models) can be blocks as well.

```html
HTML:

<div class="block">...</div>
```
```css
CSS:

.block { color: #042; }
```

### Element
Parts of a block and have no standalone meaning. Any element is semantically tied to its block.

```html
HTML:

<div class="block">
  ...
  <span class="block__elem">...</span>
</div>
```
```css
CSS:

.block__elem { color: #042; }
```

### Modifier
Flags on blocks or elements. Use them to change appearance, behavior or state.

```html
HTML:

<div class="block block--mod">
  ...
	<div class="block__element--mod">...</div>
</div>
```
```css
CSS:

.block__elem--mod { }
```
