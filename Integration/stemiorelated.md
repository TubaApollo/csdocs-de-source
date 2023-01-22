---
label: Stremio
order: 996
icon: /static/stremio.png
---

# Stremio addon

!!! warning **Read this before installing**
Die Stremio-Erweiterung ist noch experimentell. Erwarte kein Stremio-ähnliches Erlebnis. Quellen können in CS3 mit dieser Methode hinzugefügt werden, aber nur für die Bibliothek. Wenn also versucht wird, die Episoden abzuspielen, kommt die Meldung **Keine Verlinkung gefunden**.
!!!

## Installing Stremio

[!badge variant="light" text="Schritt 1"] Navigiere zu der [Repo-Seite](https://www.cloudstream.cf/repos) und installiere die [English repo](cloudstreamrepo://raw.githubusercontent.com/recloudstream/cloudstream-extensions/builds/repo.json)

[!badge variant="light" text="Schritt 2"] öffne **Cloudstream**, gehe zu [!badge variant="dark" icon="/static/gear.png" text="Einstellungen"] → [!badge variant="dark" text="Erweiterungen"] → [!badge variant="dark" text="English Repository"] → **wische hinüber zu** [!badge variant="dark" text="Andere"] und **Installiere das Stremio-Plugin**

___
## Stremio-Addon erhalten

[!badge variant="light" text="Schritt 3"] Gehe zurück zu deinem Webbrowser und navigiere zu [Stremio addon list](https://stremio-addons.netlify.app/).

[!badge variant="light" text="Schritt 4"] Finde ein Stremio-Addon deiner Wahl und klicke auf **Link kopieren**.  **Entferne die `manifest.json` am Ende der URL und kopiere den Rest.

___
## Erweiterung hinzufügen

[!badge variant="light" text="Schritt 5"] Gehe zurück zu Cloudstream, gehe zu [!badge variant="dark" icon="/static/gear.png" text="Einstellungen"] → [!badge variant="dark" text="General"] → [!badge variant="dark" icon="plus" text="Website klinen"] → [!badge variant="dark" text="Stremio example"]

[!badge variant="light" text="Schritt 6"] Für das Klonen

1. In `MeineCooleSeite` wird ein Namen für das Stremio-Addon eingegeben,
2. In `example.com` wird die aus Schritt 4 kopierte Domain eingefügt
3. In `Sprachcode` gebe "en" ein.

[!badge variant="light" text="Schritt 7"] Klicke auf "Website klonen" und starte Cloudstream neu,

[!badge variant="light" text="Schritt 8"] Nach dem Neustart von Cloudstream klicke auf **None** (Die Schaltfläche zum Wechseln des Anbieters), klicke unten auf **Andere**, und das neue Addon sollte erscheinen.

[!embed](https://www.youtube.com/watch?v=iHZENk0MKXs)