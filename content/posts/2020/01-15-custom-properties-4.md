---
title: CSS Custom Properties
description: CSS Custom Properties notes
date: 2020-01-15
tags:
  - css
---

CSS custom properties, also known as CSS variables, have an unusual declaration syntax: they allow almost any text at all in their declaration values. What’s more, those values are accessible to JavaScript, so any value might potentially be relevant to the user.

**Custom properties** (sometimes referred to as CSS variables or cascading variables) are entities defined by CSS authors that contain specific values to be reused throughout a document. They are set using custom property notation (e.g., `--main-color: black;`) and are accessed using the `var()` function (e.g., `color: var(--main-color);`).

Complex websites have very large amounts of CSS, often with a lot of repeated values. For example, the same color might be used in hundreds of different places, requiring global search and replace if that color needs to change. Custom properties allow a value to be stored in one place, then referenced in multiple other places. An additional benefit is semantic identifiers. For example, `--main-text-color` is easier to understand than `#00ff00`, especially if this same color is also used in other contexts.

https://www.sassmeister.com/

## Sass Custom Properties 
[Sass Custom Properties](https://sass-lang.com/documentation/style-rules/declarations/)

**CSS custom properties**, also known as CSS variables, have an unusual declaration syntax: they allow almost any text at all in their declaration values. What’s more, those values are accessible to JavaScript, so any value might potentially be relevant to the user. This includes values that would normally be parsed as SassScript.

Because of this, Sass parses custom property declarations differently than other property declarations. All tokens, including those that look like SassScript, are passed through to CSS as-is. The only exception is interpolation, which is the only way to inject dynamic values into a custom property.

```sh
$primary: #81899b;
$accent: #302e24;
$warn: #dfa612;

:root {
  --primary: #{$primary};
  --accent: #{$accent};
  --warn: #{$warn};
}
```

[CSS Custom Properties and Theming](https://css-tricks.com/css-custom-properties-theming/)

[CODEPEN: Theming a site with CSS Custom Properties](https://codepen.io/chriscoyier/pen/ybgNKP)

[Theming with Custom Properties](https://csswizardry.com/2016/10/pragmatic-practical-progressive-theming-with-custom-properties/)

> Theming, the vast majority of the time, is a complete nice-to-have. It is not business critical or usually even important. If you are asked to provide such theming, do not do so at the expense of performance or code quality.<br>
&nbsp;&nbsp;-&nbsp;Harry Roberts

[Lea Verou - CSS Variables](https://www.youtube.com/watch?v=2an6-WVPuJU)
