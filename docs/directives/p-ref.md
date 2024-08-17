---
sidebar_position: 6
---

# p-ref

`p-ref` in combination with `refs` is a useful utility for easily accessing DOM elements directly.

It's most useful as a replacement for APIs like getElementById and querySelector.

```html
<input p-ref="counter" type="number" value="0">

<button @click="print(refs.counter.value)">Remove Text</button>
```

