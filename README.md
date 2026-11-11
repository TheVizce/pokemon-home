# Meine Pokémon-Boxen

Ein Tool, um die eigenen Pokémon aus Pokémon Home zu verwalten: Potential, Wesen, Fähigkeit,
Herkunft, Box und Platz. Läuft unter https://thevizce.github.io/pokemon-home/.

## Pokédex-Daten

Beim ersten Öffnen lädt die Seite die offenen Daten des PokéAPI-Projekts (deutsche Namen, Typen,
Fähigkeiten inkl. versteckter, Basiswerte, Attacken, Regionalformen) und speichert sie im Browser.
Danach startet sie ohne erneuten Download. Über „Pokédex-Daten neu laden" holst du Aktualisierungen,
z. B. wenn neue Pokémon dazukommen. Sprites kommen aus dem PokéAPI-Sprite-Archiv.

## Wo liegen meine Einträge?

Im Browser in der IndexedDB `pokemon-home-tool`:

- `mons`: deine Pokémon, ein Datensatz pro Pokémon
- `meta`: die Zuordnung Trainer-ID zu OT-Name (`trainers`) und den Pokédex-Zwischenspeicher (`dex`)

Im localStorage (für alle Tools unter thevizce.github.io gemeinsam) liegen nur zwei kleine Einträge:
`pkbox.theme` (Hell/Dunkel) und `pkbox.draft` (ein ungespeicherter Editor-Entwurf, damit beim Neuladen
oder App-Wechsel nichts verloren geht). Das Tool ruft nie `localStorage.clear()` auf und fasst keine
Schlüssel anderer Tools an.

Kann etwas nicht gespeichert werden (z. B. weil der Speicher voll ist), erscheint oben eine Meldung, die
stehen bleibt, bis du sie ausblendest.

## Abgleich zwischen Geräten

Über den gemeinsamen GitHub-Sync der Startseite (`/startseite/sync-v1.js`) mit dem privaten Repo
`tool-daten`, Ordner `pokemon-home/` (main.json + 16 Teildateien). Abgeglichen werden die Pokémon und
die Trainer-IDs, nicht der Pokédex-Zwischenspeicher. Eingerichtet wird der Sync einmal pro Gerät auf
der Startseite; das ☁︎-Feld unten links zeigt den Stand.

Bis zum 11.11.2026 lag der Abgleich in einer einzelnen Datei `pokemon-home.json`. Sie wird nicht mehr
benutzt und kann gelöscht werden, sobald alle Geräte einmal mit der neuen Version abgeglichen haben.

## Sicherung

„Sicherung exportieren" speichert alle Pokémon und Trainer-IDs als JSON-Datei. „Sicherung importieren"
liest sie wieder ein: Zusammenführen ergänzt nur fehlende Pokémon, Ersetzen löscht alle anderen,
durch den Sync auch auf den anderen Geräten.

Daten aus der allerersten Version (bis 25.10.2026, im localStorage) übernimmt das Tool nicht mehr
automatisch. Liegen auf einem Gerät noch welche, bietet es sie zum Herunterladen an; die Datei lässt
sich dann importieren.
