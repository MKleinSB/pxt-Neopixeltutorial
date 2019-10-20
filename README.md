# Neopixel am @boardname@

## Willkommen!

Dieses geführte Tutorial zeigt dir, wie du ein Skript programmierst mit dem Du RGB-LEDs (Neopixel) mit Deinem @boardname@ ansteuern kannst.
![Neopixelbild](https://github.com/MKleinSB/pxt-Neopixeltutorial/blob/master/1.jfif)
Fangen wir an!

## Neopixel anschließen @fullscreen
Neopixel lassen sich ganz leicht am @boardname@ anschließen:
Verbinde DIN mit P0, +5V mit dem + des @boardname@ und GND mit - des @boardname@
Gut geeignet sind RGB-Streifen die es sehr günstig gibt. Mehr als 8 LEDs sollten es ohne zusätzliche Stromversorgung nicht sein.
![Neopixelanschluss](https://github.com/MKleinSB/pxt-Neopixeltutorial/blob/master/2.jfif)

## Neopixelstreifen einer Variablen zuweisen @fullscreen

Dieses Projekt verwendet die **neopixel** Erweiterung. Du musst sie zu deinem Projekt hinzufügen.
* klicke auf das Zahnrad-Menü und wähle **Erweiterungen**
* wähle die **neopixel** Erweiterung
![Neopixelextension](https://github.com/MKleinSB/pxt-Neopixeltutorial/blob/master/0.png)
Nun musst Du dem @boardname@ sagen wie dein Neopixelstreifen heißen soll und aus wie vielen LEDs er besteht.
Wir gehen mal von 8 LEDs aus die an P0 angeschlossen sind.

```blocks
let strip = neopixel.create(DigitalPin.P0, 8, NeoPixelMode.RGB)
```

## Helligkeit der LEDs festlegen @fullscreen

Dein @boardname@ kann die Helligkeit der LEDs mit dem Befehl ``||neopixel.setze Helligkeit||`` festlegen.

```blocks
let strip = neopixel.create(DigitalPin.P0, 8, NeoPixelMode.RGB)
strip.setBrightness(150)
```

## Neopixelfarbe festlegen

Du kannst alle Neopixel auf einmal einfärben mit ``||neopixel.zeige Farbe||`` oder jedem Neopixel eine eigene Farbe zuweisen. Dies geschieht mit ``||neopixel.Setze Farbe von Neopixel  auf||``
Die **8 Neopixel** sind dabei **von 0 bis 7 nummeriert!**
Die Änderungen müssen mit ``||neopixel.strip anzeigen||`` sichtbar gemacht werden.
```blocks
let strip = neopixel.create(DigitalPin.P0, 8, NeoPixelMode.RGB)
strip.setBrightness(150)
strip.showColor(neopixel.colors(NeoPixelColors.Blue))
strip.setPixelColor(0, neopixel.colors(NeoPixelColors.Red))
strip.setPixelColor(7, neopixel.colors(NeoPixelColors.Orange))
strip.show()
```

## Neopixel in Regenbogenfarben

Schön ist es auch, die Neopixel mit der Funktion ``||neopixel.strip zeige Regenbogen von bis||`` in `Regenbogenfarben` leuchten zu lassen.
Teste es selbst!

```blocks
let strip = neopixel.create(DigitalPin.P0, 8, NeoPixelMode.RGB)
strip.showRainbow(1, 8)
strip.show()
```

## Farben rotieren lassen

Mit ``||neopixel.rotiere Neopixel um||`` `1` bewegen sich die Farben der Neopixel vorwärts, mit dem Wert `-1` rückwärts.
Um die Bewegung zu verlangsamen in die Dauerhaftschleife ``||basic.pausiere||`` einbauen.


```blocks
let strip = neopixel.create(DigitalPin.P0, 8, NeoPixelMode.RGB)
strip.showRainbow(1, 256)
strip.show()
basic.forever(function () {
    strip.rotate(1)
    strip.show()
    basic.pause(100)
})
```

## Balkendiagramm

Zeige doch mit dem @boardname@ analoge Werte wie die Helligkeit als Balkendiagramm an!
Verwende dazu den Block ``||neopixel.zeige Balkendiagramm von Wert||``, ``||input.lichtstärke||`` und den analogen Maximalwert für Licht `255`.
Platziere die Blöcke in der Endlosschleife. 

```blocks
let strip = neopixel.create(DigitalPin.P0, 8, NeoPixelMode.RGB)
basic.forever(function () {
    strip.showBarGraph(input.lightLevel(), 255)
})
```

## Ausblick

Was könntest Du jetzt noch mit deinem @boardname@ und Neopixeln tun? 
* Lasse eine farbige LED hin- und herlaufen
* Erstelle eine Ampelschaltung
* lasse Deiner Fantasie freien Lauf!

```package
neopixel=github:microsoft/pxt-neopixel#v0.6.12
```
