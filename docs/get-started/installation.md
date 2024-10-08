---
sidebar_position: 1
---

# Installation & First Project

In this project we will create a dynamic clock.

First, to use python in the browser we will add Pyscript to our html page, it' very simple :


## 0. Create a Html file

```html [index.html]
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- PyScript CSS to show you errors in a beautifull way -->
    <link rel="stylesheet" href="https://pyscript.net/releases/2024.8.2/core.css">
    <!-- This script tag bootstraps PyScript -->
    <script type="module" src="https://pyscript.net/releases/2024.8.2/core.js"></script>

    <title>Document</title>
</head>
<body>
 <div class="clock">
        <div class="hour" :style="f'rotate:{store.clock.hours_deg}deg;'">
            <div  class="hr" id="hr"></div>
        </div>
        <div class="min" :style="f'rotate:{store.clock.minutes_deg}deg;'">
            <div class="mn" id="mn"></div>
        </div>
        <div class="sec" :style="f'rotate:{store.clock.seconds_deg}deg;'">
            <div class="sc" id="sc"></div>
        </div>
    </div>

    <input type="range" min="0" max="24" step="1" placeholder="Heure" value="0" @input="store.clock.set_hour(event.target.value)">
    <input type="range" min="0" max="60" step="1" placeholder="Minute" value="0" @input="store.clock.set_minute(event.target.value)">
    <input type="range" min="0" max="60" step="1" placeholder="Seconde" value="0" @input="store.clock.set_second(event.target.value)">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-radius;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: #091921;
        }

        .clock {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 350px;
            height: 350px;
            background: url(../src/clock.png);
            background-size: cover;
            border: 4px solid #091921;
            border-radius: 50%;
            box-shadow: 0 -15px 15px rgba(255, 255, 255, 0.05),
                inset 0 -15px 15px rgba(255, 255, 255, 0.05), 0 15px 15px rgba(0, 0, 0, 0.3),
                inset 0 15px 15px rgba(0, 0, 0, 0.3);
        }

        .clock:before {
            content: "";
            position: absolute;
            width: 15px;
            height: 15px;
            background: #fff;
            border-radius: 50%;
            z-index: 10000;
        }

        .clock .hour,
        .clock .min,
        .clock .sec {
            position: absolute;
        }

        .clock .hour,
        .hr {
            width: 160px;
            height: 160px;
        }

        .clock .min,
        .mn {
            width: 190px;
            height: 190px;
        }

        .clock .sec,
        .sc {
            width: 230px;
            height: 230px;
        }

        .hr,
        .mn,
        .sc {
            display: flex;
            justify-content: center;
            /* align-items: center; */
            position: absolute;
            border-radius: 50%;
        }

        .hr:before {
            content: "";
            position: absolute;
            width: 8px;
            height: 80px;
            background: #ff105e;
            z-index: 10;
            border-radius: 6px 6px 0 0;
        }

        .mn:before {
            content: "";
            position: absolute;
            width: 4px;
            height: 90px;
            background: #fff;
            z-index: 11;
            border-radius: 6px 6px 0 0;
        }

        .sc:before {
            content: "";
            position: absolute;
            width: 2px;
            height: 150px;
            background: #fff;
            z-index: 11;
            border-radius: 6px 6px 0 0;
        }
    </style>

</body>
</html>
```
Now we can run some python in the browser !

## 1. Clone the PrunePy repo

To use PrunePy we need to clone the repo in the project, so just run the following command at the root of your project :

```bash
git clone https://github.com/darikoko/prunepy
```

## 2. Create the package.json file

We will now create a `package.json` file, it will indicates to pyscript where is located prune.py when we will import it in our python code.

```json
{
    "files":{
        "/prunepy/prune.py": "./prune.py"
    }
}
```

- On the left side whe have the relative URL path of the file.
- On the right side the desired file location when our code will be run by pyscript.

## 3. Create your Python file

Now we create a python file which will be the logic of our app, in this case it's a simple Clock App.

```python
from pyscript import window
from prune import Prune, notify

class Clock:
    def __init__(self) -> None:
        self.seconds_deg = 0
        self.minutes_deg = 0
        self.hours_deg = 0
        window.setInterval(self.refresh_clock, 1000)

    @notify
    def refresh_clock(self):
        self.seconds_deg += 360/60
        self.minutes_deg += 360/(60*60)
        self.hours_deg += 360/(60*60*12)

    @notify
    def set_hour(self, hour:str):
        self.hours_deg = 360/12 * int(hour)

    @notify
    def set_minute(self, minute:str):
        self.minutes_deg = 360/60 * int(minute)

    @notify
    def set_second(self, second:str):
        self.seconds_deg = 360/60 * int(second)

clock = Clock()
prune = Prune( clock=clock)
```


## 4. Include your Python file in your html

At the end of your body tag, just add this script tag :


```html
<body>
  ...
  <script type="mpy" src="/clock.py" config="/package.json"></script>
</body>
```
This tag should be at the end of your body tag and has 3 attributes :
- `type` which should be `mpy`, it tells to pyscript to use micropython as backend.
- `src` : the url of your python file
- `config` : the url of your `package.json` file 


## 5. Enjoy !

<iframe height="400px" src="/doc-examples/clock.html">
</iframe>

