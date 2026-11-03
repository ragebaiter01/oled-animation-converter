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

## PlatformIO in VS Code

Der erzeugte Code ist auch mit PlatformIO nutzbar. Erstelle in VS Code ein PlatformIO-Projekt mit dem Board **WEMOS D1 mini** und Framework **Arduino**. Kopiere den generierten Sketch in `src/main.cpp` und ersetze dort den Inhalt der Datei.

Für ein 128 × 64 OLED verwende diese `platformio.ini`:

```ini
[env:d1_mini]
platform = espressif8266
board = d1_mini
framework = arduino
lib_deps =
  adafruit/Adafruit SSD1306
  adafruit/Adafruit GFX Library
```

Für das 64 × 48 Wemos OLED-Shield nimm stattdessen diese Bibliothek:

```ini
[env:d1_mini]
platform = espressif8266
board = d1_mini
framework = arduino
lib_deps = olikraus/U8g2
```

PlatformIO lädt die in `lib_deps` angegebenen Bibliotheken beim Build. Board-ID `d1_mini` ist die PlatformIO-Kennung für den Wemos D1 mini. [PlatformIO: Wemos D1 mini](https://docs.platformio.org/en/stable/boards/espressif8266/d1_mini.html) · [PlatformIO: Bibliotheksabhängigkeiten](https://docs.platformio.org/en/latest/projectconf/sections/env/options/library/lib_deps.html)
