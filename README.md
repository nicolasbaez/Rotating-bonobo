# Rotating-bonobo
Don't you ever get tired of setting limits?

![buh](https://github.com/nicolasbaez/Rotating-bonobo/blob/main/xp072.gif)
```javascript
k = 0;
setup = (_) => {
  createCanvas((w = 500), w, WEBGL);
};
draw = (_) => {
  c = 0;
  rotateX(1);
  h = w / 2;
  s = h / 5;
  for (i = -h; i < h; i += s) {
    for (j = -h; j < h; j += s) {
      if (c % 3 == 0) fill(99);
      if (c % 4 == 0) fill("#FF0");
      quad(
        i,
        j,
        noise(i, j, k) * s,
        i + s,
        j,
        noise(i + s, j, k) * s,
        i + s,
        j + s,
        noise(i + s, j + s, k) * s,
        i,
        j + s,
        noise(i, j + s, k) * s
      );
      c++;
    }
  }
  k += 0.01;
  if (frameCount == 1) saveGif("xp072.gif", 999, { delay: 0, units: "frames" });
};
