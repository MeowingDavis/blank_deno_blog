---
title: recursion
publish_date: 2023-05-06
disable_html_sanitization: true

---
# recursion 

Recursion in coding refers to the process in which a function calls itself as a part of its execution.
---
<iframe width="400" height="442" src="https://editor.p5js.org/MeowingDavis/full/n0R9MZ-cI"></iframe>

```javascript
function setup() {
  createCanvas(400, 400);
  frameRate (2)
}

function draw() {
  recursive_rect (0, 0, width, height, 7)
}

function recursive_rect (x, y, w, h, g) {
  fill (rand_colour ())
  rect (x, y, w, h)
  
  if (w > 0 && h > 0) {
    recursive_rect (x + 5, y + 5, w - 10, h - 10)    
  }
  
  // if (g > 0) {
  //   recursive_rect (x + 5, y + 5, w - 10, h - 10, g - 1)    
  // }
  
}

function rand_colour () {
  const h = random (360)
  const s = 100
  const b = 100
  colorMode (HSB)
  return color (h, s, b)
}
```
---

<iframe width="400" height="442" src="https://editor.p5js.org/MeowingDavis/full/jbPYzDhd_"></iframe>

```javascript
// let randyMarsh;

function setup() {
  createCanvas(400, 400);
  
  // randyMarsh = random(1, 100);
}

function draw() {
  background(`black`);
  noFill ()

  
  stroke (`deeppink`)
  
  recursive_ellipse (width / 2, height / 2, 200, 200)
  
  
  stroke (`yellow`)
  // fill (`green`)
  recursive_rect (width / 2, height / 2, 200, 200)
}

function recursive_rect (x, y, w, h) {
  rect (x, y, w, h)
  
  if (w < 1) return
  recursive_rect (x * (w / 20), x, w /3, h / 20)
  recursive_rect (y - (h / 2), y, w / 2, h / 3)
  
  
}



function recursive_ellipse (x, y, w, h) {
  ellipse (x, y, w, h)
  
  if (w < 1) return
  recursive_ellipse (x - (w / 2), y, w /3, h / 5)
  recursive_ellipse (y + (h / 3), x, w / 2, h / 3)
  
  
}
```




