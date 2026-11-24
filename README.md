# WebXR Depth Demo

Tiefe aus der Handykamera, direkt im Browser: Abstand messen, Tiefenbild ansehen, Raum als Punktwolke scannen und als PLY speichern.

**Demo:** https://rdmueller.github.io/webxr-depth-demo/

## Voraussetzungen

- Chrome für Android auf einem ARCore-fähigen Handy (z. B. Galaxy S25)
- Aufruf über HTTPS

Am Desktop läuft kein AR. Dort zeigt die Beispiel-Punktwolke den Betrachter mit synthetischen Daten.

## Technik

Eine einzelne `index.html` ohne Abhängigkeiten. Sie nutzt die WebXR Depth Sensing API (`immersive-ar` mit `depth-sensing`) und WebGL.
