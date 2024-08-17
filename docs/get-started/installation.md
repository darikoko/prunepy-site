---
sidebar_position: 1
---

# Installation

To use python in the browser we will add Pyscript to our html page, it' very simple :

## 1. Import PyScript


```html
<head>
  ...
  <!-- PyScript CSS to show you errors in a beautifull way -->
  <link rel="stylesheet" href="https://pyscript.net/releases/2024.8.2/core.css">
  <!-- This script tag bootstraps PyScript -->
  <script type="module" src="https://pyscript.net/releases/2024.8.2/core.js"></script>
</head>
```


## 2. Then import your python code

```html
<body>
  ...
  <script type="mpy" src="/main.py" config="/package.json"></script>
</body>
```

This tag should be at the end of your body tag and has 3 attributes :
- `type` which should be `mpy`, it tells to pyscript to use micropython as backend.
- `src` : the url of your python file
- `config` : the url of your `package.json` file, this file allows you to declare the packages you want to use, thanks to it we will import PrunePy in the next step ;)

## 3. Include PrunePy in your config file

```html
<body>
  ...
  <script type="mpy" src="/main.py" config="/package.json"></script>
</body>
```

