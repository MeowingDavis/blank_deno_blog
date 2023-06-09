---
title: testing web audio outside of p5js
publish_date: 2023-05-02
disable_html_sanitization: true

---
# web audio


The Web Audio API involves handling audio operations inside an audio context, and has been designed to allow modular routing. Basic audio operations are performed with audio nodes, which are linked together to form an audio routing graph. Several sources — with different types of channel layout — are supported even within a single context. This modular design provides the flexibility to create complex audio functions with dynamic effects.

### This was my first experiment using web audio 

[Click for acid](https://netart-davis.deno.dev/).

---
```javascript

document.body.style.margin = 0;
document.body.style.overflow = `hidden`;

const audio_context = new AudioContext();
audio_context.suspend();

let acid_buffers = [];
let current_buffer_index = 0;
// let wave = 0;

get_acid_buffers();

function get_acid_buffers() {
  const filenames = ['acid_note_1.wav', 'acid_note_2.wav', 'acid_note_3.wav', 'acid_note_4.wav', 'acid_note_5.wav'];
  Promise.all(filenames.map(fetchAndDecode)).then(buffers => {
    acid_buffers = buffers;
  });
}

async function fetchAndDecode(filename) {
  const response = await fetch(filename);
  const buffer = await response.arrayBuffer();
  return await audio_context.decodeAudioData(buffer);
}

document.onclick = click_handler;

function click_handler(mouse_event) {
  if (audio_context.state == 'suspended') {
    audio_context.resume();
  } else {
    const buffer = acid_buffers[current_buffer_index];
    // const playback_rate = (mouse_event.clientX / windowWidth) * 2 + 0.5;
    play_acid(buffer,  0.6);
    current_buffer_index = (current_buffer_index + 1) % acid_buffers.length;
  }
}

function play_acid(buffer, rate) {
  const buf_node = audio_context.createBufferSource();
  const gainNode = audio_context.createGain(); // add gain node
  buf_node.buffer = buffer;
  // buf_node.playbackRate.value = rate;
  buf_node.connect(gainNode); // connect to gain node
  gainNode.gain.value = 0.3; // set gain value
  gainNode.connect(audio_context.destination);
  buf_node.start();
}

let r, circleColor;

function setup() {
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB);
  circleColor = rand_colour();
  r = new RecursiveCircle(width/2, height/2, min(width, height), circleColor);
  noStroke();
  
  // add event listener to window to call resizeCanvas() on window resize
  window.addEventListener('resize', () => {
    resizeCanvas(windowWidth, windowHeight);
    r = new RecursiveCircle(width/2, height/2, min(width, windowHeight), circleColor);
  });

  // add event listener to canvas to randomize color on click
  // canvas.addEventListener('click', () => {
  //   circleColor = rand_colour();
  //   r.updateColor(circleColor);
  // });
}

function draw() {
  background(220);
  r.draw(frameCount);
  // wave = sin(frameCount * 0.1) * 50;
  
}

class RecursiveCircle {
  constructor(x, y, d, c) {
    this.x = x;
    this.y = y;
    this.d = d;
    this.c = c;
    this.has_child = false;
    this.n_x = random() * 20;
    this.n_y = random() * 20;
    this.x_offset = 0; // initialize x_offset to 0
    if (d > 10) {
      const c = rand_colour();
      this.child = new RecursiveCircle(x, y, d * 0.75, c);
      this.has_child = true;
    }
  }

  draw(f) {
    fill(this.c);
    this.x_offset = sin(f / 60) * 20; // update x_offset based on frame count
    const offset = noise(this.n_x + (f / 60), this.n_y) * 60 - 30;
    ellipse(this.x + this.x_offset, this.y, this.d + offset, this.d + offset); // add x_offset to x position of ellipse
    if (this.has_child) {
      this.child.draw(f);
    }
  }

  updateColor(c) {
    this.c = c;
    if (this.has_child) {
      this.child.updateColor(rand_colour());
    }
  }
}



function rand_colour() {
  const h = random(360);
  return color(h, 100, h);
}


```





