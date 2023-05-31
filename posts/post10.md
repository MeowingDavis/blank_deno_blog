---
title: Strudel REPL
publish_date: 2023-05-16
disable_html_sanitization: true

---
## Strudel REPL !!

---
funny little techno loop i made in strudel repl.

[bleep bloop](https://strudel.tidalcycles.org/?D-n-0lNAODju).

ahhh I love strudel. The sequencing is amazing I would love if I could code my midi clips like that in ableton.. you probably can somehow.



Degrage is super cool it randomly drops notes or I guess I think of them as triggers in the sequence, breaking it up a little. 


I figured out that tempo is set by CPM (cycles per minute) I still havn't entirely worked out what that means in a musical context but 75 cycles per minute seemed to be sutiable for what I wanted.

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