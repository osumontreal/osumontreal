# Coding Guideline: CSS

## General CSS coding style

### Use flexible/relative units

For maximum flexibility over the widest possible range of devices, it is a good
idea to size containers, padding, etc. using relative units like ems and rems, or
percentages and viewport units if you want them to vary depending on viewport
width. You can read some more about this in our Responsive design building blocks
article.

### Don't use resets

For maximum control over CSS across platforms, a lot of people used to use CSS
resets to remove every style, before then building things back up themselves.
This certainly has its merits, but especially in the modern world CSS resets can
be overkill, resulting in lots of extra time spent reimplementing things that
weren't completely broken in the first place, like default margins, list styles,
etc.

If you really feel like you need to use a reset, consider using normalize.css by
Nicolas Gallagher, which aims to just make things more consistent across browsers,
get rid of some default annoyances that we always remove (the margins on <body>,
for example) and fix a few bugs.

### Plan your CSS — avoid overriding

Before diving in and writing huge chunks of CSS, plan your styles carefully. What
general styles are going to be needed, what different layouts do you need to
create, what specific overrides need to be created, and are they reusable? Above
all, you need to try to avoid too much overriding. If you keep finding yourself
writing styles and then cancelling them again a few rulesets down, you probably
need to rethink your strategy.

### Use expanded syntax

There are a variety of CSS writing styles you can use, but we prefer the expanded
style, with the selector/opening brace, close brace, and each declaration on a
separate line. This maximizes readability, and again, promotes consistency on MDN.

Use this:

```
p {
  color: white;
  background-color: black;
  padding: 1rem;
}
```

Not this:

```
p { color: white; background-color: black; padding: 1rem; }
```

In addition, keep these specifics in mind:

* Include a space between the selector(s) and the opening curly brace.
* Always include a semi-colon at the end of the last declaration, even though it
  isn't strictly necessary.
* Put the closing curly brace on a new line.
* In each declaration, put a space after the separating colon, but not before.
* Use 2 spaces for code indentation.

### Favor longhand rules over terse shorthand

Usually when teaching the specifics of CSS syntax, it is clearer and more obvious
to use longhand properties, rather than terse shorthand (unless of course
teaching the shorthand is the point of the example). Remember that the point of
MDN examples is to teach people, not to be clever or efficient.

To start with, it is often harder to understand what the shorthand is doing. It
takes a while to pick apart exactly what font syntax is doing, for example:

```
font: small-caps bold 2rem/1.5 sans-serif;
```

Whereas this is more immediate in terms of understanding:

```
font-variant: small-caps;
font-weight: bold;
font-size: 2rem;
line-height: 1.5;
font-family: sans-serif;
```

Second, CSS shorthand comes with potential added pitfalls — default values are
set for parts of the syntax that you don't explicitly set, which can produce
unexpected resets of values you've set earlier in the cascade, or other expected
effects. The grid property for example sets all of the following default values
for items that are not specified:

```
grid-template-rows: none
grid-template-columns: none
grid-template-areas: none
grid-auto-rows: auto
grid-auto-columns: auto
grid-auto-flow: row
grid-column-gap: 0
grid-row-gap: 0
column-gap: normal
row-gap: normal
```

In addition, some shorthands only work as expected if you include the different
value components in a certain order. In CSS animations for example:

```
/* duration | timing-function | delay | iteration-count
   direction | fill-mode | play-state | name */
animation: 3s ease-in 1s 2 reverse both paused slidein;
```

As an example, the first value that can be parsed as a `<time>` is assigned to
the animation-duration, and the second one is assigned to animation-delay. For
more details, read the full animation syntax details.

### Use double quotes around values

Where quotes can or should be included, use them, and use double quotes. For
example:

```
[data-vegetable="liquid"] {
  background-color: goldenrod;
  background-image: url("../../media/examples/lizard.png");
}
```

### Spacing around function parameters

Function parameters should have spaces after their separating commas, but not
before:

```
color: rgb(255, 0, 0);
background-image: linear-gradient(to bottom, red, black);
```

### CSS comments

Use CSS-style comments to comment code that isn't self-documenting:

```
/* This is a CSS-style comment */
```

Put your comments on separate lines preceeding the code they are referring to:

```
h3 {
  /* Creates a red drop shadow, offset 1px right and down, w/2px blur radius */
  text-shadow: 1px 1px 2px red;
  /* Sets the font-size to double the default document font size */
  font-size: 2rem;
}
```

Also note that you should leave a space between the asterisks and the comment,
in each case.

### Don't use !important

!important is a last resort generally only used when you need to override
something and there is no other way. It is a bad practice and you should avoid it
wherever possible.

Bad:

```
.bad-code {
  font-size: 4rem !important;
}
```

## Specific CSS syntax points

### Turning off borders and other properties

When turning off borders (and any other properties that can take 0 or none as
values), use 0 rather than none:

```
border: 0;
```

### Use "mobile first" media queries

When including different sets of styles for different target viewport sizes using
media queries inside the same stylesheet, it is a good idea to make the default
styling before any media queries have been applied to the document the narrow
screen/mobile styling, and then override this for wider viewports inside
successive media queries.

```
/*Default CSS layout for narrow screens*/

@media (min-width: 480px) {
  /*CSS for medium width screens*/
}

@media (min-width: 800px) {
  /*CSS for wide screens*/
}

@media (min-width: 1100px) {
  /*CSS for really wide screens*/
}
```

## Selectors

### Don't use ID selectors

There is really no need to use ID selectors — they are less flexible (you can't
add more if you discover you need more than one), and are harder to override if
needed, being of a higher specificity than classes.

Good:

```
.editorial-summary {
  ...
}
```

Bad:

```
#editorial-summary {
  ...
}
```

### Put multiple selectors on separate lines

When a rule has multiple selectors, put each selector on a new line. This makes
the selector list easier to read, and can help to make code lines shorter.

Do this:

```
h1,
h2,
h3 {
  font-family: sans-serif;
  text-align: center;
}
```

Not this:

```
h1, h2, h3 {
  font-family: sans-serif;
  text-align: center;
}
```
