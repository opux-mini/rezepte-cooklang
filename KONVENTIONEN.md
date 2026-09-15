# Schreibkonventionen für .cook-Dateien

Gegenstück zur `mealie-json-konvention.md`. Entstanden bei der Konvertierung der ersten Mealie-Rezepte (15.09.2026) — jede Regel geht auf einen echten Fall zurück, nicht auf Theorie.

## Mengen

**Dezimaltrennzeichen ist der Punkt, nie das Komma.** `@Knoblauchpulver{0.5%TL}`, nicht `{0,5%TL}`. Cooklang kennt Punkt-Dezimalzahlen und Brüche (`1/2`); das deutsche Komma ist nicht spezifiziert und würde beim Portionen-Skalieren vermutlich als Text durchgereicht. Gemischte Brüche (`1 1/4`) sind ebenfalls nicht dokumentiert — deshalb durchgängig Punkt, eine Regel ohne Sonderfälle (`1.25`, `0.75`).

**Bereiche: unterer Wert in den Timer, Spannweite in den Text.** `~{30%Minuten} simmern lassen (30 bis 40 Minuten)`. Timer nehmen nur einen Wert.

**Einkaufsmenge an die Zutat, Teilmenge in den Text.** Wenn im Schritt weniger verbraucht wird als eingekauft: `von der @Gemüsebrühe{500%ml} 320 bis 380 ml angießen`. Sonst stimmt die Einkaufsliste nicht.

**Menge unbekannt: leere Klammern.** `@schwarzer Pfeffer{}` statt eine Zahl zu erfinden.

## Zutatennamen

**Singular und kanonisch.** Cooklang hat keine Pluralbehandlung — `@Ei{4}` und `@Karotte{1}`, nicht mal „Ei" und mal „Eier", sonst stehen zwei Einträge auf der Einkaufsliste.

**Keine Modifikatoren im Namen.** Zubereitungs- und Sortenhinweise als Klartext dahinter: `@Kreuzkümmel{1%TL}, gemahlen` statt `@gemahlener Kreuzkümmel{1%TL}`; `@Kartoffeln{1%kg} (vorwiegend festkochend)`. Deklinierte Formen im Namen erzeugen sonst drei Varianten derselben Zutat.

**Optional und Alternativen als Klartext in Klammern.** `(optional)`, `(ersatzweise 50 g mehr Paniermehl)` — wie in der Mealie-Konvention.

**Gleiche Zutat mehrfach einfach an jeder Stelle nennen.** `@Mehl{400%g}` im Spätzleteig und `@Mehl{30%g}` in der Einbrenne: Cooklang summiert das für die Einkaufsliste auf 430 g. In Mealie standen dafür zwei getrennte Zeilen mit Notiz.

## Struktur

**Abschnitte mit `== Name ==`.** Ersetzt den Mealie-Workaround, Zwischenüberschriften mit Doppelpunkt in den Schritt-Text zu schreiben. Auch dort anwenden, wo Mealie die Überschrift als eigenen leeren Schritt geführt hat (Plov).

**Ein Absatz = ein Schritt.** Leerzeile trennt.

**Notizen mit `>`** für alles, was kein Arbeitsschritt ist: Rezeptbeschreibung am Anfang, Warnungen, Richtwerte.

**Kochgeschirr mit `#`**, mehrteilige Namen immer mit `{}`: `#weiten Topf{}`. Mealies Tools-Feature bleibt weiter ungenutzt — in Cooklang steht das Gerät ohne Zusatzaufwand im Fließtext.

**Temperaturen, Ofeneinstellungen, Maße** haben kein eigenes Element: Klartext (`auf 200 °C Umluft vorheizen`, `4 cm große Stücke`).

## Metadaten (YAML-Frontmatter)

Belegt sind `title`, `servings`, `prep_time`, `cook_time`, `source`, `tags`. Die Mealie-Kategorie wandert als **erster Tag** mit (`tags: [Hauptgericht, Lamm, Usbekisch]`), da Cooklang Kategorie und Tag nicht trennt.

**Dateiname = Rezepttitel**, da die Apps danach sortieren und suchen.

## Was beim Wechsel verloren geht

Kein Cooklang-Gegenstück haben: **Bewertung** (`rating`, z. B. 5 bei den Nuggets), **lastMade**, **Bilder**, sowie die **Trennung von Kategorie und Tag**. Wenn sich diese Felder im Alltag als wichtig erweisen, ist das ein Argument für Mealie — bitte während der Testphase bewusst beobachten.

## Beobachtung aus der Migration

Der Plov-Export zeigt Mealie-Parserschaden: Bei Kreuzkümmel (`1.25`) und Koriander (`0.75`) fehlt die Einheit komplett, die Anzeige liest sich als „1 ¹/₄ Kreuzkümmel". Beim Konvertieren als `%TL` ergänzt — **bitte gegenprüfen**. Bei Chiliflocken war die Menge ebenfalls einheitenlos (`1`), dort steht jetzt bewusst nichts. Solche Fälle können in Cooklang nicht entstehen, weil es keinen Import-Parser gibt: Was dasteht, ist was geschrieben wurde.
