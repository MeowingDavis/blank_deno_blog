---
title: Assignment 1
publish_date: 2023-03-29
disable_html_sanitization: true

---
# Assignment 1



Click to randomise the colour of the text, the speed of the bouncing square plus change the direction inwhich the text is moving.

Move mouse on the X and Y to change the background colour.




<iframe width="576" height="366" src="https://editor.p5js.org/MeowingDavis/full/O5mzXVR3x"></iframe>

```javascript
let museo, helvetica;

//col_2 is no longer in use
let col_1, col_3;

//I just like rgb as a way off thinking about colour and it works well when randomising imo. the lowercase rgb is more for map and randomising within the draw function not startup
let R, G, B, r, g, b;
//this will be to randomise the bounce speed of the square
let bounce;

//boolean variable to keep track of whether the letters should move on the x-axis or y-axis
let moveXY = false;

function preload() {
  museo = loadFont("fonts/Museo 700.otf");
  helvetica = loadFont("fonts/Helvetica Neue.ttf");
}

function setup() {
  createCanvas(576, 324);

  // uncommenting this and commenting out the background in the draw function and clicking has some interesting results.

  // background(r, g, b);

  //Randomise !!
  R = random(255);
  G = random(255);
  B = random(255);
  bounce = random(20, 120);

  col_1 = color(0, 0, 84);
  col_3 = color(250, 200, 0);
  // who even likes having a stroke
  noStroke();
}

function draw() {
  r = map(mouseX, 0, 576, 0, 255);
  g = map(mouseY, 0, 324, 0, 255);
  b = map(mouseX, 0, 324, 255, 0);

  background(r, g, b);

  for (let i = 0; i < 128; i++) {
    let p = (frameCount + i) / bounce;
    let y_off = abs(sin(p * PI * 2) * 120);
    // uncommenting line 49 and commenting out line 47 randomises the height the square bounces at.
    // let y_off = abs(sin(p * PI * 2) * bounce);
    const c = lerpColor(col_1, col_3, i / 128);
    fill(c);
    square(50 + (i / 128) * 100, 160 - y_off, 100);
  }

  let Y = sin(frameCount * 0.05) * 10;

  //conditional to flip from x to y movement.
  if (moveXY) {
    let X = sin(frameCount * 0.05) * 10;
    translate(X, 0);
  } else {
    Y = sin(frameCount * 0.05) * 10;
    translate(0, Y);
  }

  fill(R, G, B);
  textFont(museo);
  textSize(100);
  text(`RMIT`, width / 2, 130);

  fill(R, G, B);
  textFont(helvetica);
  textSize(42);
  text(`Creative Coding`, width / 2, 190);
  text(`Specialisation`, width / 2, 240);
}

// mousePressed() function to randomise colours, bounce speed and Toggle the moveXY variable
function mousePressed() {
  R = random(255);
  G = random(255);
  B = random(255);
  bounce = random(20, 120);

  moveXY = !moveXY;
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