---
sidebar_position: 2
---

# p-html

`p-html` sets the "innerHTML" property of an element to the result of a given expression.


:::warning[Take care]

⚠️ Only use on trusted content and never on user-provided content. ⚠️

Dynamically rendering HTML from third parties can easily lead to XSS vulnerabilities.

:::

Here's a basic example of using `p-html` to display a user's username.

```python
from prune import Prune

class User:

  def __init__(self, username:str) -> None:
    self.usernarme = username

  def html_username(self):
    return f"<strong>{self.username}</strong>"

user = User("<strong>calebporzio</strong>")
prune = Prune(user=user)
```

And here is the html to show the username of the user :

```html
<p>Username: <span p-text="store.user.html_username()"></span></p>
```

Username: **jojo**

