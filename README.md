# Mitsukaru

Weiterleitungen für die Bewertungsständer und Fenster-Plättchen von Mitsukaru.

Jeder QR-Code und jeder NFC-Tag zeigt auf **mitsukaru.de/r/CODE**, zum Beispiel `mitsukaru.de/r/001`.
Nie direkt auf Google. So lässt sich das Ziel jederzeit ändern, ohne neu zu drucken.

## So funktioniert es

| Aufruf | Ergebnis |
|---|---|
| Code ist einem Kunden zugeordnet | Google-Bewertungsseite des Kunden |
| Code ist noch frei | Seite `frei.html` mit Kontaktmöglichkeit |
| Alles andere | Startseite |

## Dateien

| Datei | Zweck |
|---|---|
| `kunden.json` | **Die einzige Datei, die du regelmäßig änderst.** Code → Kunde |
| `404.html` | Router: liest den Code aus der Adresse und leitet weiter |
| `frei.html` | Seite für noch nicht vergebene Codes |
| `index.html` | Startseite mitsukaru.de |
| `CNAME` | Verbindet das Repository mit mitsukaru.de. Nicht ändern. |

## Neuen Kunden zuweisen

1. Place ID des Betriebs heraussuchen: [Place ID Finder](https://developers.google.com/maps/documentation/places/web-service/place-id)
2. `kunden.json` öffnen, Stift-Symbol, eine Zeile ergänzen:

```json
{
  "001": { "name": "Friseur Beispiel", "placeId": "ChIJ..." },
  "002": { "name": "Café Beispiel", "placeId": "ChIJ..." }
}
```

3. „Commit changes". Nach etwa einer Minute ist die Weiterleitung aktiv.

Achtung: Nach dem letzten Eintrag kommt **kein Komma**. Ein Tippfehler in der Datei schickt alle Codes auf die Seite „frei".

## Testen

`mitsukaru.de/r/001` im Browser öffnen.
