---
title: Relative Units
description: Relative units.
date: 2020-11-20
tags:
  - css
  - units
---

Relative units cover scalable unit (em, rem, vw, vh, etc.) and are relative to something else, maybe a parent element or the root font size of the HTML element.

**Both rem and em are scalable and relative units of size**, but with em, the unit is relative to the font size of its parent element, while the rem unit is only relative to the root font size of the HTML document. The “r” in rem stands for “root”. 

**em Unit:** The em unit allows setting the font size of an element relative to the font size of its parent. When the size of the parent element changes, the size of the child changes automatically.

```sh
<!DOCTYPE html>
<html>
<head>
    <title>Em vs Rem</title>
</head>
 
<style>
    .parent {
        font-size: 20px;
    }
 
    .child-em {
        font-size: 2em;
        margin: 1.5em;
    }
</style>
 
<body>
    <div class="parent">
        This is parent
        <div class="child-em">
            This is Child in em unit system
        </div>
    </div>
</body>
</html>
```

**rem Unit:** The rem is based upon the font-size value of the root element, which is the <html> element. And if the <html> element doesn’t have a specified font-size, the browser default value of 16px is used. So here only the value of the root is considered, and there is no relation with a parent element.

Unlike em, here size is relative for all declarations, not only the first. Let’s understand this with our previous example.

- The font-size of the .child element will be 60px (2*30px).
- The margin of .child will be 45px. That’s 1.5 times the font-size of the html element (1.5*30px).

```sh
<!DOCTYPE html>
<html>
<head>
    <title>Em vs Rem</title>
</head>
 
<style>
    html {
        font-size: 30px;
    }
 
    .parent {
        font-size: 20px;
    }
 
    .child-rem {
        font-size: 2rem;
        margin: 1.5rem;
    }
</style>
 
<body>
    <div class="parent">
        This is parent
        <div class="child-rem">
            This is Child in rem unit system
        </div>
    </div>
</body>
</html>
```