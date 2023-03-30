---
title: Assignment 1
publish_date: 2023-03-29
disable_html_sanitization: true

---
# Assignment 1



Click to randomise the colour of the text and the speed of the bouncing square.

move mouse on the X and Y to change the background colour.

<iframe width="576" height="366" src="https://editor.p5js.org/MeowingDavis/full/QM6ICBQuE"></iframe>


```javascript
let museo, helvetica;


//col_2 is no longer being used.
// let col_2;
let col_1, col_3;

//uppercase R G B for random colours lowercase to be used in map 
let R, G, B, r, g, b;

// I called this bounce to remember what I was doing its for the speed of the jumping square 
let bounce;

function preload () {
  museo = loadFont ('fonts/Museo 700.otf');
  helvetica = loadFont ('fonts/Helvetica Neue.ttf');
}

function setup () {
  createCanvas (576, 324);
  //RGB and bounce are just randomly generated
  R = random(255);
  G = random(255);
  B = random(255);
  bounce = random(20, 120);

  col_1 = color (0, 0, 84);
  col_2 = color (230, 30, 42);
  col_3 = color (250, 200, 0);
  noStroke ();
}

function draw() {
  
  //using map because it 
  r = map(mouseX, 0, 576, 0, 255);
  g = map(mouseY, 0, 324, 0, 255);
  b = map(mouseX, 0, 324, 255, 0);
  background(r, g, b);
   

  for (let i = 0; i < 128; i++) {
    let p = (frameCount + i) / bounce;
    let y_off = abs(sin(p * PI * 2) * 120);
    const c = lerpColor(col_1, col_3, i / 128);
    fill(c);
    square(50 + ((i / 128) * 100), 160 - y_off, 100);
  }

  // Add movement to the y-coordinate of the text
  let Y = sin(frameCount * 0.05) * 10;
  fill(R, G, B);
  textFont(museo);
  textSize(100);
  text(`RMIT`, width / 2, 130 + Y);

  fill(R, G, B);
  textFont(helvetica);
  textSize(42);
  text(`Creative Coding`, width / 2, 190);
  text(`Specialisation`, width / 2, 240);
}
// i added this mouse press function because I didnt want to have to refresh the page every time i wanted to randomise the colour of the text and speed of the bounce.
function mousePressed() {
  // Generate new random RGB/bounce values
  R = random(255);
  G = random(255);
  B = random(255);
  bounce = random(20, 120);

}
```