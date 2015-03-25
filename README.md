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
