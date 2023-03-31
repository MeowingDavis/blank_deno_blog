---
title: Assignment 1
publish_date: 2023-03-29
disable_html_sanitization: true

---
# Assignment 1



Click to randomise the colour of the text, the speed of the bouncing square plus change the direction inwhich the text is moving.
p5 reference allll the waay
Move mouse on the X and Y to change the background colour.

I had this script working better without an array but i wanted to jam one in there.



<iframe width="576" height="366" src="https://editor.p5js.org/MeowingDavis/full/O5mzXVR3x"></iframe>

```javascript
let museo, helvetica;

// an array for col_1 and col_2
let colors = [];

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

  // an array of colors
  colors[0] = color(0, 0, 84);
  colors[1] = color(250, 200, 0);

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
    //uncommeting line 51 and commenting 49 will randomise thae jump height.
    // let y_off = abs(sin(p * PI * 2) * bounce);
    const c = lerpColor(colors[0], colors[1], i / 128);
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



this is sketch hurts my eyes...its pretty much all written within a class. 
I wanted to use a class but idk i didn't feel it was necessary in the previous sketch. so i made this 



<iframe  width="576" height="366" src="https://editor.p5js.org/MeowingDavis/full/MMzp_K21K"></iframe>

```javascript
class Sketch {
  constructor() {
    this.angle = 0;
    this.angle2 = 2;
    this.rewind = false;
    this.colors = ["pink", "blue", "red", "yellow"];
    this.currentColor = this.colors[0];
  }

  setup() {
    createCanvas(576, 324);
    
    textAlign(CENTER);
    textSize(32);
  }

  draw() {
    background(this.currentColor);
  
    translate(width/2, height/2);
    if (!this.rewind) {
      rotate(this.angle);
    } else {
      rotate(-this.angle);
    }
    text("RMIT", 0, 50);
  
    this.angle += 0.02;
  
    translate(width/4, height/4);
    if (!this.rewind) {
      rotate(this.angle2);
    } else {
      rotate(-this.angle2);
    }
    text("Creative Coding", 0 ,50)
  
    this.angle2 += 0.03;
  }

  mouseClicked() {
    this.rewind = !this.rewind;
  
    this.currentColor = this.colors[Math.floor(Math.random() * this.colors.length)];
  }
}

const sketch = new Sketch();

function setup() {
  sketch.setup();
  print("LAAAG")
}

function draw() {
  sketch.draw();
 
 
  
}

function mouseClicked() {
  sketch.mouseClicked();
}


```