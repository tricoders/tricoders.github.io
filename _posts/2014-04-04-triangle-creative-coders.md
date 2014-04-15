---
layout: post
title: void setup()
cover: cover.png
date:   2014-04-14 12:00:00
categories: posts
---

## Introducing Triangle Creative Coders

Triangle Creative Coders is a group of creative coding enthusiasts based in Raleigh, Durham, and Chapel Hill, North Carolina. We focus on creative coding and hacking in the visual and audio arts, using tools such as 

* [Processing](http://www.processing.org)
* [openFrameworks](http://www.openframeworks.org)
* [Cinder](http://www.libcinder.org)
* [Polycode](http://polycode.org/)
* Javascript / [D3.js](http://d3js.org/) / [three.js](http://threejs.org/)
* [Nodebox](http://nodebox.net/)
* [vvvv](http://vvvv.org/)
* [Pure Data](http://puredata.info/)
* [MaxMSP/Jitter](http://cycling74.com/products/max/)
* [SuperCollider](http://supercollider.sourceforge.net/)
* [Overtone](http://overtone.github.io/)
* and more!

We are in the process or organizing our first meeting and will post details when they are available. The current target time is 7:30pm on the 20th of May, 2014, at the [James B. Hunt Library at North Carolina State University](http://www.lib.ncsu.edu/huntlibrary), either in the [Teaching and Visualization Lab](http://www.lib.ncsu.edu/spaces/teaching-and-visualization-lab) or in the [Creativity Studio](http://www.lib.ncsu.edu/spaces/creativity-studio-north).

**Banner Code in Processing**

{% highlight java %}
int w             = 750;
int h             = 150;
int numTrianglesW = 75;
float dim         = float(w)/numTrianglesW;
int numTrianglesH = int(h/dim);

void setup() {
  size(w + 10, h + 10);
  background(255);
}

void draw() {
  for (int i = 0; i < numTrianglesW; i++) {
    for (int j = 0; j < numTrianglesH; j++) {
      color c;
      float n = random(0, 1);
      if (n < 0.33) {
        c = color(37, 75, 102);
      } 
      else if (n < 0.66) {
        c = color(51, 105, 142);
      } 
      else if (n < 0.95) {
        c = color(74, 151, 204);
      } 
      else {
        c = color(255, 0, 0);
      }
      stroke(c);

      float xpos = i * dim;
      float ypos = j * dim;
      pushMatrix();
          translate(5 + xpos + dim/2, 5 + ypos + dim/2);
          float val = (i+1)* (j+1);
          rotate(radians(val));
          beginShape();
              vertex(-dim/2, dim/2);
              vertex(0, -dim/2);
              vertex(dim/2, dim/2);
              vertex(-dim/2, dim/2);
          endShape();
      popMatrix();
    }
  }
  noLoop();
}
{% endhighlight %}
