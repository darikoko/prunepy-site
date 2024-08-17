---
sidebar_position: 7
---
# p-for



PrunePy's `p-for` directive allows you to create DOM elements by iterating through a list.

Here's a simple example of using it to create a list of colors based on an array.

:::warning[Take care]


`p-for` MUST be declared on a `<template>` element.

That `<template>` element MUST contain **only one root** element

:::


```html
<ul>
    <template p-for="color in ['red', 'blue', 'black']">
        <li p-text="color"></li>
    </template>
</ul>
```

## Iterate on a range

You can iterate on any iterable, for example a range :
```html
<ul>
    <template p-for="i in range(10)">
        <li p-text="i"></li>
    </template>
</ul>
```

## Iterate on dict

You can iterate on any iterable, so a dict works too
```html
<ul>
    <template p-for="key,value in {'taste':'peperonni', 'size': 'XL'}.items()">
        <li p-text="i">
            <span p-text="key"></span>
            <span> - </span>
            <span p-text="value"></span>
        </li>
    </template>
</ul>
```