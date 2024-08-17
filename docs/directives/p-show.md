---
sidebar_position: 3
---

# p-show

`p-show` provides an expressive way to show and hide DOM elements.

Here's an example of a simple dropdown component using `p-show`.

```python
from prune import Prune

class Dropdwon:

  def __init__(self) -> None:
    self.visible = False

dropdown = Dropdown()
prune = Prune(dropdown=dropdown)
```

```html
<div>
    <button p-on:click="store.dropdown.visible = not store.dropdown.visible">Toggle Dropdown</button>
    <div p-show="store.dropdown.visible">
        Dropdown Contents...
    </div>
</div>
```



