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

In einer IndexedDB-Datenbank namens `pokemon-home-tool` im Browser, auf dem du die Seite benutzt.
Sie werden **nicht** auf GitHub gespeichert. Die Datenbank enthält:

- `mons`: deine Pokémon, ein Datensatz pro Pokémon
- `meta`: die Zuordnung Trainer-ID zu OT-Name (`trainers`), den Pokédex-Zwischenspeicher (`dex`)
  und einen Vermerk über die einmalige Übernahme aus dem alten Speicher

Im localStorage liegt nur noch `pkbox.theme` (Hell/Dunkel). Das Tool ruft nie `localStorage.clear()` auf
und fasst keine Schlüssel anderer Tools an.

Bis zum 25.10.2026 lagen die Daten im localStorage (`pkbox.mons.v1`, `pkbox.trainers.v1`, `pkbox.dex.v1`).
Beim ersten Start der neuen Version werden sie automatisch in die Datenbank übernommen. Die alten Schlüssel
werden erst gelöscht, nachdem geprüft wurde, dass alle Einträge in der Datenbank stehen.

Kann etwas nicht gespeichert werden (z. B. weil der Speicher voll ist), erscheint oben eine Meldung, die
stehen bleibt, bis du sie ausblendest.

Für Sicherungen oder einen Gerätewechsel: „Sicherung exportieren" (JSON-Datei) und auf dem anderen Gerät
„Sicherung importieren".
