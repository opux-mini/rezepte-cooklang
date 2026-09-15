# rezepte-cooklang

Testweise Ablage der Familienrezepte im [Cooklang](https://cooklang.org)-Format (`.cook`, Plain Text) — parallel zu Mealie, um im Alltag zu vergleichen, ob Cooklang eine Alternative ist (Offline-Nutzung aufs Handy ohne Kosten, git-versioniert, unabhängig vom Server).

## Struktur

```
rezepte/          – alle Rezepte als .cook-Dateien, flach (Kategorisierung folgt bei Bedarf, wie bei Mealie: label-as-you-go)
```

## Nutzung

- **Server (talos):** CookCLI liest diesen Ordner (geklont/gepullt) und stellt ihn als Weboberfläche bereit (`stacks/cookcli` im mini-system-Repo).
- **Handy:** Cook-App (cooklang.org/app) zeigt denselben Ordner an, aktuell manuell synchron gehalten (git pull) — das ist Teil des Tests.
- **Rezepte erstellen/ändern:** direkt als `.cook`-Text, kein Import-Parser, keine Mengen-Fehlinterpretation wie bei Mealie.

## Status

Testphase seit 15.09.2026 (parallel zu Mealie). Ergebnis offen: wird's zur Alternative, folgt eine Migration + Mealie-Abbau; wenn nicht, bleibt Mealie (ggf. mit Ghee Pro fürs Handy) die Lösung.
