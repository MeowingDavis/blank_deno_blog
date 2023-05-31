---
title: Hydra
publish_date: 2023-05-30
disable_html_sanitization: true

---
## Hydra



Hydra is live code-able video synth and coding environment that runs directly in the browser. It is free and open-source and made for beginners and experts alike.



### experimenting with different sources

[veronoi experiment](https://hydra.ojack.xyz/?code=dm9yb25vaSg1JTJDMC4zJTJDMC4zKSUwQSUyMC5jb2xvciglNUIxJTJDMCUyQzAlMkMxJTJDMCU1RCUyQyU1QjAlMkMxJTJDMCUyQzElMkMwJTVEJTJDJTVCMCUyQzAlMkMxJTJDMSUyQzAlNUQpJTBBJTIwJTIwLmNvbG9yYW1hKCU1QjAuMDA1JTJDMC4zMyUyQzAuNjYlMkMxLjAlNUQuZmFzdCgwLjEyNSkpJTBBJTA5LnBpeGVsYXRlKDUwJTJDJTIwNTApJTBBJTIwJTIwLm91dChvMCk%3D).

```javascript


voronoi(5,0.3,0.3)

voronoi(5,0.3,0.3)
.color([1,0,0,1,0],[0,1,0,1,0],[0,0,1,1,0])
.colorama([0.005,0.33,0.66,1.0].fast(0.125))
.pixelate(50, 50)
.out(o0)

```

[noise experiment](https://hydra.ojack.xyz/?code=bm9pc2UoNSUyQzAuMyUyQzAuMyklMEElMjAuY29sb3IoJTVCMSUyQzAlMkMwJTJDMSUyQyU1RCUyQyU1QjAlMkMxJTJDMCUyQzElMkMlNUQlMkMlNUIwJTJDMCUyQzElMkMxJTJDJTVEKSUwQSUyMCUyMC5jb2xvcmFtYSglNUIwLjAwNSUyQzAuMzMlMkMwLjY2JTJDMS4wJTVELmZhc3QoMC4xMjUpKSUwQS5yb3RhdGUoMzAlMkMlMjAwLjIpJTBBJTA5LnBpeGVsYXRlKDUwJTJDJTIwNTApJTBBJTIwJTIwLm91dChvMCk%3D).


```javascript
noise(5,0.3,0.3)
.color([1,0,0,1,],[0,1,0,1,],[0,0,1,1,])
.colorama([0.005,0.33,0.66,1.0].fast(0.125))
.rotate(30, 0.2)
.pixelate(50, 50)
.out(o0)
```