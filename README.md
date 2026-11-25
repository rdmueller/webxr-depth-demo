# WebXR Depth Demo

Tiefe aus der Handykamera, direkt im Browser: Abstand messen, Tiefenbild ansehen, Raum scannen und als Punktwolke oder einfachen Gaussian Splat speichern.

**Demo:** https://rdmueller.github.io/webxr-depth-demo/

## Bug Hunt Cam

Ein zweites Experiment im Unterordner `bug-hunt-cam/`: ein Webcam-Spiel im Pixel-Art-Stil. Die Seite erkennt Hände, Gesicht und Gegenstände mit MediaPipe direkt im Browser.

**Demo:** https://rdmueller.github.io/webxr-depth-demo/bug-hunt-cam/

- Kneifen mit Daumen und Zeigefinger zerquetscht Bugs, Mund auf frisst Dokumente.
- Eine Tasse vor der Kamera bremst die Bugs, ein Buch gibt ein Herz zurück.
- „Scanner" schaltet auf die Rückkamera und startet eine Schnitzeljagd nach Gegenständen.

Eine einzelne `index.html`. Bibliothek und Modelle lädt sie beim Start von jsDelivr und Google Storage, das Kamerabild bleibt im Browser.

Unten links steht eine Diagnosezeile, zum Beispiel `H12 F18 OC140 28FPS`: Millisekunden pro Durchlauf für Hand-, Gesichts- und Bilderkennung, `C` heißt CPU statt Grafikchip, `-` heißt abgeschaltet. Friert die Seite in einer Erkennung ein, merkt sie sich das: Beim nächsten Start läuft diese Erkennung auf der CPU, beim zweiten Mal bleibt sie aus. `?gpu` an der Adresse setzt das zurück, `?cpu` erzwingt die CPU für alle. Wirft eine Erkennung auf dem Grafikchip Fehler, wird sie auf der CPU neu aufgebaut. Der Knopf „Info" zeigt Version, Gerät, Zeiten und die vollständigen Fehlermeldungen zum Kopieren. Die folgenden Abschnitte beschreiben die WebXR-Demo.

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
