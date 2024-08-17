---
sidebar_position: 4
---
# p-if

`p-if` is used for toggling elements on the page, similarly to `p-show`, however it completely adds and removes the element it's applied to rather than just changing its CSS display property to "none".

Because of this difference in behavior, p-if should not be applied directly to the element, but instead to a `<template>` tag that encloses the element. This way, Prune can keep a record of the element once it's removed from the page.

```html
<template p-if="store.dropdown.is_open">
    <div>Contents...</div>
</template>
```


:::warning[Take care]

Remember: `<template>` tags can only contain one root level element.

:::