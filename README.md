<!--
author:   Andreas Schiffler

email:    andreas.schiffler@fhws.de

version:  0.0.1

language: de

comment:  Infomatik und technische Mechanik. Ziel ist es neben den
          klassischen Inhalten zur technischen Mechanik auch Grundlagen
          zur Programmierung und Informatik zu vermitteln.

script:   https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.10.2/p5.js
          https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.10.2/addons/p5.sound.min.js


@@ uid erzeugt einmalig einen Wert und wird, als erster Wert an das versteckte
   Macro übergeben, so können mehrere Elemente mit eindeutigen IDs erzeugt
   werden...

@P5.eval: @P5.eval_(@uid)

@@ das eigentliche Macro...

@P5.eval_
<script>

let div = window.document.getElementById('p5-@0')

div.innerHTML = ""

let sketch = function(p5) {
    // sieht etwas komisch aus, sorgt aber nur dafür, dass im input-macro auch
    // backtics verwendet werden können
    eval(`@'input`)
    
    // reagiert auf Konsolen-Eingaben, wzb. `p5.line(0,0,500,500)`, so kann
    // man noch während das Programm läuft, zeichnen
    send.handle("input", input => {
      try{
        let rslt = eval(input)

        if (rslt != undefined)
          console.log(rslt)
      } catch (e) {
        console.error(e);
      }
    })
};

let env = new p5(sketch, div);

// falls der Stop-Button geklickt wird, dann wird der Prozess beendet
send.handle("stop", e => { env.remove() })

// Sagt LiaScript, dass das Terminal geöffnet werden soll, Alternativen sind:
//"LIA: wait"
//"LIA: stop"
"LIA: terminal"
</script>

<div id="p5-@0"></div>

@end

-->

[Hier als LiaScript anschauen](https://liascript.github.io/course/?https://raw.githubusercontent.com/aschiffler/fhws_lia/master/README.md)

# Mechanik und Informatik


## Einführung zu p5.js

Das folgende Javascript nutzt die Bibliothek [p5.js](https://p5js.org).

``` js
p5.setup = function() {
  p5.createCanvas(300, 300);
}

p5.draw = function() {
  p5.background(100);
  p5.noFill()
  p5.strokeWeight(10)
  p5.circle(50,40,20)
  p5.line(50,40,200,160)
  p5.fill('red')
  p5.circle(200,160,100)
  p5.line(200,160,100,250)
  p5.circle(100,250,20)
}
```
@P5.eval

Das Ergebniss soll so aussehen

![images](https://github.com/aschiffler/fhws_lia/raw/master/assests/demo.png)

Man kann das auch [hier](https://editor.p5js.org/Schiffler/sketches/4T-0TFOv3) testen.


## Interaktive Inhalte


### JavaScript zum üben

Innerhalb dieses Kursbuchs kann man nun einfache Beispiele ausführen und testen

```js
var name = "Andreas";
if (name == "Andreas"){
    console.log('Richtig');
} else {
    console.log('Nicht richtig');
}
```
<script>
@input

"LIA: stop"
</script>