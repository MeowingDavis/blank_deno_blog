---
title: RANDOM!!!
publish_date: 2023-03-13
disable_html_sanitization: true
---


Experimenting with random in p5js

[Random Sketch](https://editor.p5js.org/MeowingDavis/sketches/eA8brS7Vz "It sucks but i love it").





<iframe width="878" height="494" src="https://editor.p5js.org/MeowingDavis/full/eA8brS7Vz" allowfullscreen></iframe>



```javascript
let X, Y, R, G, B, S, A;
let slider;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(220);

  print(
    "HALLO! Double click to randomly change background colour/clear. The slider changes the framerate"
  );

  slider = createSlider(1, 60, 10);
}

function draw() {
  noStroke();
  X = random(windowWidth);
  Y = random(windowHeight);
  R = random(255);
  B = random(255);
  G = random(255);
  S = random(10, 50);
  A = random(1, 255);

  slider.position(10, 10);
  slider.style("width", "60px");

  let val = slider.value();
  frameRate(val);

  rectMode(CENTER);

  fill(R, G, B, A);
  rect(X, Y, S);

  circle(X + S, Y + S, S);
}
//i used double click cause using the slider counts as a mouse press
function doubleClicked() {
  clear();
  background(R, G, B);
}
```