---
sidebar_position: 1
---

# p-text

`p-text` sets the text content of an element to the result of a given expression.

Here's a basic example of using `p-text` to display a user's username.

```python
from prune import Prune

class User:

  def __init__(self, username:str) -> None:
    self.usernarme = username

user = User("jojo")
prune = Prune(user=user)
```

And here is the html to show the username of the user :

```html
<p>Username: <span p-text="store.user.username"></span></p>
```

Username: jojo


<p>Salut</p>