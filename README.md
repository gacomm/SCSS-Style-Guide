# GA Communication SCSS/CSS Code Standards

These standards were cobbled together by the fine folks at GA from the following resources:

* http://css-tricks.com/sass-style-guide/
* https://github.com/styleguide/css
* http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml
* https://smacss.com/

## Spacing/Structure

* Use spaces (NOT tabs) with a two space indent. Spaces are the only way to guarantee code renders the same in any person's environment.
* Put 1 space after : in property declarations.
* Put 1 space before { in rule declarations.
* When grouping selectors, keep individual selectors to a single line if IDE allows.

Correct:
```css
#selector-1,
#selector-2,
#selector-3 {
  background: #fff;
  color: #000;
}
```

Incorrect:
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
* As a rule of thumb, avoid unnecessary nesting in SASS. At most, aim for three levels max four. If you cannot help it, step back and rethink your overall strategy (either the specificity needed, or the layout of the nesting)

## Font-Size Unit
* Use rem for font-size

## Specificity (classes vs. ids)

Elements that occur exactly once inside a page should use IDs, otherwise, use classes. When in doubt, use a class name.

* **Good** candidates for ids: header, footer, modal popups.
* **Bad** candidates for ids: navigation, item listings, item view pages (ex: issue view).

When styling a component, start with an element + class namespace (prefer class names over ids), prefer direct descendant selectors by default, and use as little specificity as possible. Here is a good example:
