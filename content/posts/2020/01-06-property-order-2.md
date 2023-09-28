---
title: CSS Property Order
description: CSS Property Order notes
date: 2020-01-06
tags:
  - css
---
Suggested order of properties in a css selector

```sh
.selector {
    /* Positioning */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;

    /* Display & Box Model */
    display: block | inline | inline-block | 
      flex | inline-flex | grid | inline-grid;
    overflow: hidden;
    width: 100px;
    height: 100px;
    margin: 10px;
    padding: 10px;
    border: 10px solid #333;
    
    /* Color */
    background: #000;
    color: #fff;

    /* Text */
    font-family: sans-serif;
    font-size: 16px;
    line-height: 1.4;
    text-align: right;

    /* Other */
    cursor: pointer;    
}
```

