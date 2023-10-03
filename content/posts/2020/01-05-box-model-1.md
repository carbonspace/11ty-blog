---
title: CSS Box Model
description: CSS Box Model notes
date: 2020-01-05
tags:
  - css
---

The CSS box model as a whole applies to block boxes and defines how the different parts of a box — margin, border, padding, and content — work together to create a box that you can see on a page. Inline boxes use just some of the behavior defined in the box model. To add complexity, there is a standard and an alternate box model. By default, browsers use the standard box model.


**The standard CSS box model**

<img src="/images/2020-box-model.png" width="100%" alt="Standard CSS Box Model" />

In the standard box model, if you give a box an `inline-size` and a `block-size` (or `width` and a `height`) attributes, this defines the inline-size and block-size (width and height in horizontal languages) of the *content* box. Any padding and border is then added to those dimensions to get the total size taken up by the box (see image below).

If we assume that a box has the following CSS:

```sh
.box {
  width: 350px;
  height: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

The *actual* space taken up by the box will be 410px wide (350 + 25 + 25 + 5 + 5) and 210px high (150 + 25 + 25 + 5 + 5).

<img src="/images/2020-box-model-2.png" width="100%" alt="Standard CSS Box Model" />

> The margin is not counted towards the actual size of the box — sure, it affects the total space that the box will take up on the page, but only the space outside the box. The box's area stops at the border — it does not extend into the margin.

## The alternative CSS box model

In the alternative box model, any width is the width of the visible box on the page. The content area width is that width minus the width for the padding and border (see image below). No need to add up the border and padding to get the real size of the box.

To turn on the alternative model for an element, set `box-sizing: border-box` on it:

```sh
.box {
  box-sizing: border-box;
}
```

If we assume the box has the same CSS as above:

```sh
.box {
  width: 350px;
  inline-size: 350px;
  height: 150px;
  block-size: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

Now, the *actual* space taken up by the box will be 350px in the inline direction and 150px in the block direction.

<img src="/images/2020-alt-box-model.png" width="100%" alt="Alternative CSS Box Model" />

To use the alternative box model for all of your elements (**which is a common choice among developers**), set the `box-sizing property` on the `<html>` element and set all other elements to inherit that value:

```sh
html {
  box-sizing: border-box;
}
*,
*::before,
*::after {
  box-sizing: inherit;
}
```

[CSS Tricks: Box-sizing Article](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)