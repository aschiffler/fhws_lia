<!--
author:   Andreas Schiffler

email:    andreas.schiffler@fhws.de

version:  0.0.1

language: de

comment:  Infomatik und technische Mechanik. Ziel ist es neben den 
          klassischen Inhalten zur technischen Mechanik auch Grundlagen
          zur Programmierung und Informatik zu vermitteln.

script:   https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.10.2/p5.js

-->

# Mechanik und Informatik
## Einführung zu p5.js

Das folgende Javascript nutzt die Bibliothek [p5.js](https://p5js.org).

``` js
function setup() {
  createCanvas(300, 300);
}

function draw() {
  background(100);
  noFill()
  strokeWeight(10)
  circle(50,40,20)
  line(50,40,200,160)
  fill('red')
  circle(200,160,100)
  line(200,160,100,250)
  circle(100,250,20)
}
```
Das Ergebniss soll so aussehen

![images](https://github.com/aschiffler/fhws_lia/raw/master/assests/demo.png)

Man kann das auch [hier](https://editor.p5js.org/Schiffler/sketches/4T-0TFOv3) testen.

## Interaktive Inhalte
### JavaScript zum üben
Innerhalb dieses Kursbuchs kann man nun einfache Beispile ausführen und testen

```js
var name = "Andreas";
if (name == "Andreas"){
    console.log('Richtig');
}else{
    console.log('Nicht richtig');
}
```
<script>
    window.console.log = console.log;
    @input
</script>

### p5.js (JavaScript) zum üben
``` javascript +global.js
  let x = 100;
  let y = 100;
  let winkel = 0;
```
``` javascript +setup.js
    p.createCanvas(200, 200);
    //p.frameRate(10);
```
``` javascript +draw.js
    p.background(0);
    p.fill(255);
    p.circle(x+p.sin(winkel++/20)*20, y+p.cos(winkel++/20)*20, 50);
```
<script>
let sketch = function(p) {
    @input(0)
    p.setup = function() {
        @input(1)
    };
    p.draw = function() {
        @input(2)
    };
};
new p5(sketch, window.document.getElementById('p5-@0'));
</script>

<div id="p5-@0" class="persistent"></div>