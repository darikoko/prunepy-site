---
sidebar_position: 5
---

# p-bind

`p-bind` allows you to set HTML attributes on elements based on the result of Python expressions.

For example, here's a component where we will use p-bind to set the placeholder value of an input.

```html
<div>
    <input type="text" p-bind:placeholder="store.user.placeholder">
</div>
```

## Shorthand syntax

If `p-bind:` is too verbose for your liking, you can use the shorthand: `:`. For example, here is the same input element as above, but refactored to use the shorthand syntax.

```html
<div>
    <input type="text" :placeholder="store.user.placeholder">
</div>
```

## Binding classes

`p-bind` is most often useful for setting specific classes on an element based on your store.

Here's a simple example of a simple dropdown toggle, but instead of using p-show, we'll use a "hidden" class to toggle an element.

```html
<div>
    <button p-on:click="store.dropdown.open = not store.dropdown.open">Toggle Dropdown</button>
 
    <div :class="'hidden' if store.dropdown.open else ''">
        Dropdown Contents...
    </div>
</div>
```

Now, when open is false, the "hidden" class will be added to the dropdown.


## Special behavior

`p-bind:class` behaves differently than other attributes under the hood.

Consider the following case.

```html
<div class="opacity-50" :class="'hidden' if store.dropdown.open else ''">
```

If "class" were any other attribute, the `:class` binding would overwrite any existing class attribute, causing opacity-50 to be overwritten by either hidden or ''.

However, PrunePy treats class bindings differently. It's smart enough to preserve existing classes on an element.

For example, if hide is true, the above example will result in the following DOM element:

```html
<div class="opacity-50 hidden">
```

If hide is false, the DOM element will look like:

```html
<div class="opacity-50">
```

This behavior should be invisible and intuitive to most users, but it is worth mentioning explicitly for the inquiring developer or any special cases that might crop up.


