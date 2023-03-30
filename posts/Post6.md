---
title: map
publish_date: 2023-03-27
disable_html_sanitization: true

---
# playing around with the map setting


`map()` is a function that takes a value within one range of numbers and maps it to a corresponding value in a different range of numbers.

The map() function takes five arguments:

    value: the value to be mapped, which can be any number
    start1: the lower bound of the original range of numbers to map from
    stop1: the upper bound of the original range of numbers to map from
    start2: the lower bound of the target range of numbers to map to
    stop2: the upper bound of the target range of numbers to map to

The map() function then returns a new value that is proportionally mapped from the original range to the target range.

<iframe width="400" height="442" src="https://editor.p5js.org/MeowingDavis/full/mdrgHxsn8"></iframe>

```javascript
let r = 0;
let b = 255;


function setup() {
  createCanvas(600, 400);
}

function draw() {

  r = map(mouseX, 0, 600, 0, 255);
  g = map(mouseY, 0, 400, 0, 255);
  b = map(mouseX, 0, 600, 255, 0);
  background(r, g, b);
 
}
```