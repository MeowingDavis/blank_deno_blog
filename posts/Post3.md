---
title: RANDOM!!!
publish_date: 2023-03-13
disable_html_sanitization: true
---


Experimenting with random in p5js.

I absolutly love randomness. I cant quite explain why but I love seeing what happens. I think im just drawn to the idea of a human giving parameters and allowing the machine to generate what it wants within those parameters. It stems from my fasination with Music thing modulars' turing machine based off a step register. 

[Random Sketch](https://editor.p5js.org/MeowingDavis/sketches/eA8brS7Vz "It sucks but i love it").





<iframe width="878" height="494" src="https://editor.p5js.org/MeowingDavis/full/eA8brS7Vz" allowfullscreen></iframe>



```javascript
//sketch for random squares and circles

let X, X2, Y, Y2, R, G, B, S, A;
let slider;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(R, G, B);

  print(
    "HALLO! Double click to randomly change background colour/clear. The slider changes the framerate"
  );
//slider min, max, starting pos
  slider = createSlider(1, 60, 10);
}

function draw() {
  noStroke();
  //randomise!!
  X = random(windowWidth);
  Y2 = random(windowHeight);
  X2 = random(windowWidth);
  Y = random(windowHeight);
  R = random(255);
  B = random(255);
  G = random(255);
  S = random(10, 50);
  A = random(1, 255);

  //slider position and size
  slider.position(10, 10);
  slider.style("width", "60px");

  
  
  let val = slider.value();
  frameRate(val);

  rectMode(CENTER);

  fill(R, G, B, A);
  rect(X, Y, S);

  circle(X2, Y2, S);
}
//i used double click cause using the slider counts as a mouse press
function doubleClicked() {
  clear();
  background(R, G, B);
  print("background reset");
}
```