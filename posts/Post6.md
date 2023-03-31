---
title: Assignment 1
publish_date: 2023-03-29
disable_html_sanitization: true

---
# Assignment 1



Click to randomise the colour of the text and the speed of the bouncing square.

Move mouse on the X and Y to change the background colour.

using functions and variables.

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
  
  //map() is a function that takes a value within one range of numbers and maps it to a corresponding value in a different range of numbers.
  r = map(mouseX, 0, 576, 0, 255);
  g = map(mouseY, 0, 324, 0, 255);
  b = map(mouseX, 0, 324, 255, 0);
  background(r, g, b);
   

  for (let i = 0; i < 128; i++) {
    // deviding frameCount by the randomised bounce number.
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



this is another sketch for the rmit thing its pretty basic I was trying to experiment with rotating the text it was kind of weird and im not sure id be able to do it without the p5 reference but its i think it was a fun attempt anyway.

using an array and boolean.


<iframe  width="400" height="442" src="https://editor.p5js.org/MeowingDavis/full/bgYx1tUAn"></iframe>

```javascript
let angle = 0;
let angle2 = 2;
let rewind = false;

// define an array of colors
let colors = ["pink", "blue", "red", "yellow"];
let currentColor = colors[0];

function setup() {
  createCanvas(400, 400);
  textAlign(CENTER);
  textSize(32);
}

function draw() {
  background(currentColor);
  
  translate(width/2, height/2);
  if (!rewind) {
    rotate(angle);
  } else {
    rotate(-angle);
  }
  text("RMIT", 0, 50);
  
  angle += 0.02;
  
  translate(width/4, height/4);
  if (!rewind) {
    rotate(angle2);
  } else {
    rotate(-angle2);
  }
  text("Creative Coding", 0 ,50)
  
  angle2 += 0.03;
}

function mouseClicked() {
  rewind = !rewind;
  
  // select a random color from the array and set it as the current background color
  currentColor = colors[Math.floor(Math.random() * colors.length)];
}
```