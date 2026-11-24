# WebXR Depth Demo

Tiefe aus der Handykamera, direkt im Browser: Abstand messen, Tiefenbild ansehen, Raum scannen und als Punktwolke oder einfachen Gaussian Splat speichern.

**Demo:** https://rdmueller.github.io/webxr-depth-demo/

## Voraussetzungen

- Chrome für Android auf einem ARCore-fähigen Handy (z. B. Galaxy S25)
- Aufruf über HTTPS

Am Desktop läuft kein AR. Dort zeigt die Beispiel-Punktwolke den Betrachter mit synthetischen Daten.

## Technik

Eine einzelne `index.html` ohne Abhängigkeiten. Sie nutzt die WebXR Depth Sensing API (`immersive-ar` mit `depth-sensing`) und WebGL.

## Export

- **Punktwolke** (`scan.ply`): Punkte mit Farbe, y zeigt nach oben, Einheit Meter.
- **Splat** (`scan-splat.ply`): 3DGS-PLY-Format, y zeigt nach unten. Der Splat ist nicht trainiert: Jeder Scanpunkt wird ein runder Gaussian in Kamerafarbe.

Die Kamerafarben brauchen die WebXR-Funktion `camera-access`. Ohne sie zeigt die Farbe die Höhe.

## Version

Die Seite zeigt ihre Version neben der Überschrift. Sie steht als `VERSION` in `index.html` und wird bei jeder Änderung von Hand erhöht.
