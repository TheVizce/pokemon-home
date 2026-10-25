# Meine Pokémon-Boxen

Ein kleines Tool, um die eigenen Pokémon aus Pokémon Home zu verwalten – als einzelne Datei für GitHub Pages.

## Auf GitHub Pages veröffentlichen

1. Auf github.com ein neues Repository anlegen, z. B. `pokemon-boxen` (öffentlich).
2. **Add file → Upload files** und `index.html` (und diese README) hochladen, dann **Commit changes**.
3. **Settings → Pages**: unter *Build and deployment* als Quelle **Deploy from a branch**, Branch `main`, Ordner `/ (root)` wählen, speichern.
4. Nach ein bis zwei Minuten ist die Seite unter `https://<dein-name>.github.io/pokemon-boxen/` erreichbar.

## Woher kommen die Pokémon-Daten?

Beim ersten Öffnen lädt die Seite die offenen Daten des PokéAPI-Projekts (deutsche Namen, Typen,
Fähigkeiten inkl. versteckter, Basiswerte, Attacken, Regionalformen) und speichert sie im Browser.
Danach startet sie ohne erneuten Download. Über „Pokédex-Daten neu laden" holst du Aktualisierungen,
z. B. wenn neue Pokémon dazukommen. Sprites kommen ebenfalls aus dem PokéAPI-Sprite-Archiv.

## Wo liegen meine Einträge?

Im lokalen Speicher des Browsers, auf dem du die Seite benutzt. Sie werden **nicht** auf GitHub
gespeichert. Für Sicherungen oder einen Gerätewechsel: „Sicherung exportieren" (JSON-Datei) und auf
dem anderen Gerät „Sicherung importieren".
