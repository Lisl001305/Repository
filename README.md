# Trainingsstagebuch – Progressive Web App (PWA)

Diese Version baut auf dem vorhandenen Trainingsstagebuch auf und kann als statische Website über GitHub Pages veröffentlicht werden.

## Enthalten

- `index.html`: Trainingsstagebuch mit bisherigen Trainingsfunktionen und eigenen Kraft-/Cardio-Plänen
- `manifest.json`: Installationsinformationen für Android, iOS (zum Home-Bildschirm), Windows und kompatible Browser
- `service-worker.js`: Offline-App-Shell und Zwischenspeicherung der App-Dateien
- `icons/`: App-Symbole in 192 × 192 und 512 × 512

## GitHub Pages veröffentlichen

1. Auf GitHub ein neues Repository anlegen, z. B. `trainingsstagebuch`.
2. Den Inhalt dieses Ordners direkt in das Stammverzeichnis (`/`) des Repositorys hochladen: `index.html`, `manifest.json`, `service-worker.js` und `icons/`.
3. Im Repository `Settings` → `Pages` öffnen.
4. Unter `Build and deployment` `Deploy from a branch` wählen.
5. Branch `main`, Ordner `/ (root)` auswählen und speichern.
6. Nach der Veröffentlichung die angezeigte Pages-Adresse öffnen. Die PWA-Funktionen benötigen HTTPS; GitHub Pages stellt HTTPS bereit.

Bei Änderungen an App-Dateien muss in `service-worker.js` der Cache-Name (`trainingsstagebuch-pwa-v1`) erhöht werden, z. B. auf `v2`, damit installierte/offline genutzte Versionen die Aktualisierung laden.

## Installation

- Android: Website in Chrome öffnen und `App installieren` oder `Zum Startbildschirm hinzufügen` wählen.
- iPhone/iPad: Website in Safari öffnen → Teilen → `Zum Home-Bildschirm`.
- Desktop: Installationssymbol in der Browser-Adressleiste oder Browser-Menü verwenden, sofern angeboten.

## Daten und Datenschutz

Die Trainingsdaten werden weiterhin im lokalen Browser-Speicher (`localStorage`) auf dem jeweiligen Gerät gehalten. Es gibt keine Anmeldung, keine zentrale Trainingsdatenbank und keine Synchronisierung zwischen Geräten. Die App-Dateien werden über GitHub Pages ausgeliefert; persönliche Trainingsprotokolle werden von der App nicht an GitHub übertragen.

Planvorlagen werden als JSON-Datei exportiert und enthalten nur die Planbeschreibung und Einheiten, nicht das persönliche Trainingslogbuch. Auf unterstützten Geräten kann der Browser die Datei direkt über das Teilen-Menü weitergeben; ansonsten wird sie heruntergeladen und kann als Anhang verschickt werden.

PDF-Berichte werden über die Druckfunktion des Browsers erstellt. Im Druckdialog `Als PDF speichern` auswählen. Anschließend kann die gespeicherte PDF über die Teilen-Funktion des Geräts, E-Mail oder Messenger verschickt werden.

**Wichtig:** Lokale Browserdaten können durch Löschen der Website-Daten, Browser-Reset oder Deinstallation verloren gehen. Deshalb regelmäßig über `Einstellungen` → `Daten exportieren` eine Sicherung erstellen und sicher aufbewahren. Der Browser kann persistenten Speicher gewähren; das ist aber keine Garantie gegen manuelles Löschen oder Geräteverlust.

## Hinweise

- Diese Version verwendet weiterhin den bestehenden lokalen Speicher, damit vorhandene Datenstruktur und Funktionen erhalten bleiben. Eine Migration zu IndexedDB ist nicht erforderlich für die PWA-Funktion und wäre ein separater, sorgfältig zu testender Schritt.
- Der PDF-Export nutzt die native Druck-/PDF-Funktion des Browsers, da diese plattformübergreifend verfügbar ist. Das anschließende Teilen erfolgt über das Betriebssystem bzw. den Browser.
- Vor der öffentlichen Weitergabe sollte die App auf den tatsächlich verwendeten Geräten und Browsern getestet werden.
