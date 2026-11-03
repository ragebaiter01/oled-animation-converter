# Pixel to OLED

Ein kleiner Browser-Konverter für Bilder und GIFs auf monochromen OLEDs. Die Seite wandelt Bilddateien in Frames um und erstellt Arduino- oder PlatformIO-Code für den gewählten Controller und Displaytyp.

Das `favicon.png` im Projektstamm ist das Tab-Icon der Webseite und muss beim Upload mit übernommen werden.

Die Bildoptimierung bietet drei Modi: klare Kanten ohne Rasterung für Schrift und Logos, Floyd–Steinberg-Dithering für mehr Detail in Fotos sowie ein festes 4×4-Raster für GIFs. Mit Kontrast, Bildanpassung und Abspieltempo kannst du die Vorschau weiter abstimmen.

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

## Unterstützte Auswahl

- Boards: **ESP8266 Wemos D1 mini** (Standard) und **ESP32 Dev Module**.
- Displays: **SSD1306 128×64** (Standard), SSD1306 128×32, SH1106 128×64 und Wemos OLED-Shield SSD1306 64×48.
- Für SSD1306 128×64/128×32: Adafruit SSD1306 + Adafruit GFX.
- Für SH1106 128×64 und das 64×48 Shield: U8g2.

## Arduino IDE

- Wähle in der Arduino IDE das Board passend zur Auswahl: Wemos D1 mini oder ESP32 Dev Module.
- Installiere die zum Display passende Bibliothek aus der obigen Liste.
- Für GIF-Import einen aktuellen Chrome- oder Edge-Browser mit `ImageDecoder` / WebCodecs verwenden.

Lange GIFs können auf die ausgewählte Frame-Anzahl begrenzt werden. Die erzeugten Frames liegen im Sketch, daher kann ein sehr langes GIF viel Flash-Speicher belegen.

## PlatformIO in VS Code

Der erzeugte Code und die Konfiguration sind auch mit PlatformIO nutzbar. Wähle in der Webseite dein Board und Display sowie **PlatformIO** als Code-Ausgabe. Lade `main.cpp` und `platformio.ini` herunter. Lege `main.cpp` in `src/` und `platformio.ini` ins Projektverzeichnis. Die Datei enthält die passende Board-ID und Display-Bibliotheken.

Die PlatformIO-Board-IDs sind `d1_mini` für den Wemos D1 mini und `esp32dev` für das ESP32 Dev Module. [PlatformIO: Wemos D1 mini](https://docs.platformio.org/en/stable/boards/espressif8266/d1_mini.html) · [PlatformIO: ESP32 Dev Module](https://docs.platformio.org/en/stable/boards/espressif32/esp32dev.html) · [PlatformIO: Bibliotheksabhängigkeiten](https://docs.platformio.org/en/latest/projectconf/sections/env/options/library/lib_deps.html)
