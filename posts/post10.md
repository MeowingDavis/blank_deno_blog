---
title: Strudel REPL
publish_date: 2023-05-16
disable_html_sanitization: true

---
## Strudel REPL !!

---
funny little techno loop i made in strudel repl.

[bleep bloop](https://strudel.tidalcycles.org/?ZrjgRsNqc7l6).

ahhh I love strudel. Still finding it a little confusing and I'm yet to try intergrate the midi out with any hardware synths but once im a little more comfortable with it I shall give it a go.



Degrage is super cool it randomly drops notes or I guess I think of them as triggers in the sequence, breaking it up a little. 

```javascript
stack(
  
 note("g3 g4, [c3 c4] [f4 g#4] b4 f3")
  //.arp("0 [0,2] 1 [0,2]")

  .decay(0.001)
  .cpm(75)
  .delay(0.2)
  .room(0.6)
  .s('gm_ocarina')
  .cutoff("200 400 300 [500 400]")
  .gain(0.7)
  ,
  
  note("C2 g1 [f2 g#2] c3").decay("0.001").cpm(75)
  .delay(0.07)
  .s("sine")
  .cutoff("200 400 [800 600] 500")
  ,
  
  s("bd ~ bd ~")
  .bank("RolandTR909")
  .cpm(75)
  ,

  s("hh*8").bank("RolandTR808")
  .room(0.8)
  .pan(0.5)
  .gain(0.1)
  .degrade()
  .cpm(75)
)

```