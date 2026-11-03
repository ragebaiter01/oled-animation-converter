# Pixel to OLED

Ein kleiner Browser-Konverter für Bilder und GIFs auf SSD1306-OLEDs mit einem Wemos D1 mini (ESP8266). Die Seite wandelt Bilddateien in monochrome Frames um und erstellt daraus einen Arduino-Sketch.

## Online mit GitHub Pages

1. Erstelle ein GitHub-Repository.
2. Wähle **Add file → Upload files** und lade die Dateien aus diesem Ordner hoch. `index.html` muss direkt im Stammverzeichnis des Repositories liegen.
3. Committe die Dateien auf den Branch `main`.
4. Öffne **Settings → Pages**.
5. Wähle **Deploy from a branch**, den Branch `main` und den Ordner `/ (root)`, dann klicke **Save**.
6. Öffne nach der Veröffentlichung die angezeigte GitHub-Pages-Adresse.

Die Seite braucht keinen Build-Schritt und keine externen Pakete. Bild- und GIF-Dateien werden direkt im Browser verarbeitet und nicht hochgeladen.

## Lokal starten

Mit installiertem Node.js im Projektordner ausführen:

```sh
node server.js
```

Dann im Browser <http://127.0.0.1:8080> öffnen.

## Arduino IDE

- Board: **LOLIN(WEMOS) D1 R2 & mini**
- Für **128 × 64**: Bibliotheken **Adafruit SSD1306** und **Adafruit GFX** installieren.
- Für das **64 × 48 Wemos OLED-Shield**: Bibliothek **U8g2** installieren.
- Für GIF-Import einen aktuellen Chrome- oder Edge-Browser mit `ImageDecoder` / WebCodecs verwenden.

Lange GIFs können auf die ausgewählte Frame-Anzahl begrenzt werden. Die erzeugten Frames liegen im Sketch, daher kann ein sehr langes GIF viel Flash-Speicher belegen.
