---
sidebar_position: 2
---

# Start Prune

Now that Pyscript is installed on your html page, we will run prune in your python file.

```python
# Import the Prune object, and the notify function
from prune import Prune, notify

# Create a class which will help you to represent your data
class User:
  def __init__(self, username):
    self.username = username

# Create an instance of this class
user = User("jojo")

# Create an instance of Prune, with keyword arguments
prune = Prune(user=user)
```

Now all the instance registered in prune are available in the html with the name `store`, via `p-*` attributes.

Imagine you want to show the username of your user you just have to write :

```html
<p p-text="store.user.username"></p>
```

`p-text` will replace the text of an element with a python expression value. (in this case the value of store.user.username : "jojo")

## Add Reactivity

Sometimes you want to udpate the dom when you run a method, to do that once again it's really simple :

```python
from prune import Prune, notify

class User:
  def __init__(self, username):
    self.username = username

  # By decorating the method with @notify
  # The dom will be updated at the end of the method
  @notify
  def change_username(self):
    self.username = "bob"

user = User("jojo")
prune = Prune(user=user)
```

```html
<p p-text="store.user.username"></p>
<button p-on:click="store.user.change_username()">Change Username</button>
```

Now when you click on the button, the dom will update the text of the p tag from 'jojo' to 'bob'.


