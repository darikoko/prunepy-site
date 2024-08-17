---
sidebar_position: 7
---
# p-on

`p-on` allows you to easily run code on dispatched DOM events.

Here's an example of simple button that print the username of your user when clicked (by calling the print_username method from your `User` class).


```html
<button p-on:click="store.user.print_username()"></button>
```


## Shorthand syntax

If `p-on`: is too verbose for your tastes, you can use the shorthand syntax: `@`.

Here's the same component as above, but using the shorthand syntax instead:

```html
<button @click="print('Hello World!')">Print Hello World</button>
```

## Passing events

You can pass the js events object to a python function and use it like you would do in JS.

```html
<button @click="store.user.say_hi(event)">Add task</button>
```


