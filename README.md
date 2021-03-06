# GA Communication SCSS/CSS Code Standards

These standards were cobbled together by the fine folks at GA from the following sources:

* http://css-tricks.com/sass-style-guide/
* https://github.com/styleguide/css
* http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml
* https://smacss.com/

## Spacing/Structure

* Use spaces (NOT tabs) with a two space indent. Spaces are the only way to guarantee code renders the same in any person's environment.
* Put 1 space after : in property declarations.
* Put 1 space before { in rule declarations.
* When grouping selectors, keep individual selectors to a single line if IDE allows.

**Correct:**
```css
#selector-1,
#selector-2,
#selector-3 {
  background: #fff;
  color: #000;
}
```

**Incorrect:**
```css
#selector-1, #selector-2, #selector-3 {
  background: #FFF;
}

#selector-1 { background: #FFF; color: #000; }
```

* Place closing braces of declaration blocks on a new line.
* Each declaration should appear on its own line for more accurate error reporting.

## Formatting
* Use hex color codes #000  and short-hand if possible unless using rgba()
* Avoid specifying units for zero values, e.g., margin: 0; instead of margin: 0px;

## Misc
* As a rule of thumb, avoid unnecessary nesting in SCSS. Don't nest more than 3 or 4 levels deep as this creates bloated CSS and is too specific. If you cannot help it, step back and rethink your overall strategy (either the specificity needed, or the layout of the nesting)

## Font-Size Unit
* Use rem for font-size

## Specificity (classes vs. ids)

Elements that occur exactly once inside a page should use IDs, otherwise, use classes. When in doubt, use a class name.

* **Good** candidates for ids: header, footer, modal popups.
* **Bad** candidates for ids: navigation, item listings, item view pages (ex: issue view).

When styling a component, start with an element + class namespace (prefer class names over ids), prefer direct descendant selectors by default, and use as little specificity as possible. Here is a good example:

## Class Naming Conventions

* Use hyphens (-) NOT underscores (_) in class names
* All lowercase

## Global Include SCSS Files are Your Table of Contents

List Vendor Dependencies First, Then Global Dependencies, Then Components, Then Sections. Breakup stylesheets into logical SMACSS like areas of concern

```css
/* Vendor Dependencies */
@import “compass”;
@import “susy”;

/* Global Base Dependencies */
@import “base/colors”;
@import “base/mixins”;

/* Components */
@import “components/tabs”;
@import “components/modals”;

/* Sections */
@import “layout/header”;
@import “layout/footer”;
```

## Property Ordering

```css
.overlay {
    background: #fff;
    color: #777;
    padding: 10px;
    position: absolute;
    z-index: 1;
}
```

## SCSS Nesting Order

* List @extends(s) First
* List  “Regular Styles” Next
* List @include(s) Next
* List Nested Selectors Last

```css
.weather {
  @extends %module;
  background: #fff;
  @include transition(all 0.3s ease);
  > h3 {
    border-bottom: 1px solid #FFF;
    @include transform(rotate(90deg));
  }
}
```

## Media Query Structure

* Nest media queries within selector
* Use breakpoints mixin
* Use variables for breakpoints
* Use mobile first approach to ordering breakpoints

**Correct**

```css
.sidebar {
    float: right;
    width: 33.3333%
    @include breakpoint($phablet) {
      width: 50%;
    }
    @include breakpoint($tablet) {
      width: 33.333%;
    }
    @include breakpoint($desktop) {
      width: 25%;
    }
}
```

**Incorrect**

```css
.sidebar {
  width: 50%;
}
@include breakpoint($phablet) {
  .sidebar {
    width: 33.333%
  }
}
@include breakpoint($tablet) {
  .sidebar {
    width: 33.333%;
  }
}
@include breakpoint($desktop) {
  .sidebar {
    width: 25%;
  }
}
```

## Specificity Guidelines

* If you must use an id selector (#selector) make sure that you have no more than *one* in your rule declaration. A rule like `#header .search #quicksearch { ... }` is considered harmful.
* When modifying an existing element for a specific use, try to use specific class names. Instead of `.listings-layout.bigger` use rules like `.listings-layout.listings-bigger`. Think about ack/greping your code in the future.
* The class names `.disabled`, `.mousedown`, `.danger`, `.hover`, `.selected`, and `.active` should always be namespaced by an element (`button.selected` is a good example).

## Partials are named _partial.scss

This is a common naming convention that indicates this file isn't meant to be compiled by itself. It likely has dependencies that would make it impossible to compile by itself.

## Variablize All Colors

Except perhaps white and black. Chances are a color isn't one-off, and even if you think it is, once it's in a variable you might see uses for it elsewhere. Variations on that color can often be handled by the Sass color functions like `lighten()` and `darken()` - which make updating colors easier (change in one place, whole color scheme updates).

## Override File

Use on a case by case basis for stuff like plugins where the author used `!important` _overrides.scss

## Shame Last

In your global stylesheet, @import a _shame.scss file last. This file should only contain temporary quick fixes that are meant to be incorporated later into their proper place. Ideally this file should be empty however it's better to make the hack public and shame it rather than add these styles to the end of random stylesheets where they may never get fixed.

For more on the benefits of the _shame.scss see http://csswizardry.com/2013/04/shame-css/


