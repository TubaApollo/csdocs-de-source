---
label: NGINX
order: 997
icon: /static/nginx.png
---

# NGINX Einrichtung

### Was ist NGINX?

Es handelt sich dabei um eine freie und quelloffene Software, die sehr leistungsfähig ist, die wir hier aber nur zur Darstellung von Dateien auf einer einfachen Weboberfläche verwenden werden.
Bei den Dateien, die wir verwenden, handelt es sich um Medien wie Filme oder Animationen, welche selbst heruntergeladen werden müssen (hier verwenden wir Torrents).

In diesem Tutorial werde ich NGINX auch als "HTTP-Zugriff" bezeichnen, da es dem Benutzer erlaubt, über http auf seine Datei zuzugreifen.

**Ein Server und eine Mediensammlung wird benötigt (z.B. Raspberry Pi, NAS oder Seedbox), um diese Funktion nutzen zu können!**

___
### Warum habe ich das erstellt?

I used to be a user of [jellyfin](https://jellyfin.org/) because I didn't want to Ich habe früher [Jellyfin](https://jellyfin.org/) benutzt, weil ich kein Abonnement bezahlen wollte und keine proprietäre Software wie Plex benutzen wollte. Aber es funktionierte nicht wirklich gut und ich konnte manchmal keine Filme abspielen und hat eine Menge Ressourcen verbraucht. Die Lösung? Scrapen der Mediendateien und ihrer Metadaten mit Cloudstream-3.

Die Vorteile dieses Anbieters gegenüber Jellyfin sind, dass er schlank und mit Cloudstream integriert ist.

___
**Um NGINX zu installieren, wird ein Medienserver benötigt:**
- Eine 'managed' Seedbox: ist ein Service, den du mieten kannst und der sich um das Finden, Herunterladen und Seeden von Torrents für dich kümmert, siehe [hier](https://www.sarlays.com/my-media-server/), die einfachste Methode (die ich benutze).
- Du kannst den Medienserver auch selbst hosten, ich beschreibe die Installation von NGINX [hier](https://www.sarlays.com/unlisted/self-host-nginx) (schwieriger).

Hier beschreibe ich die Installation auf einer Managed Seedbox mit ultra.cc

![](https://media.discordapp.net/attachments/1015131233824538624/1063102592508506133/image.png)

___
### Was sind Tracker?

Dabei handelt es sich um Websites, auf denen man ein Konto einrichtet und die dann Inhalte auflisten, die von anderen auf der Website registrierten Benutzern gehostet werden (sie selbst hosten die Inhalte nicht).
Sonarr und Radarr fordern dann Prowlarr auf, nach etwas Bestimmtem zu suchen, z. B. nach einem Film oder einem Anime in der vom Tracker erstellten Liste.

Sobald der Film gefunden ist, wird die Torrent-Datei an Transmission gesendet.
Transmission ist im Grunde ein Torrent-Downloader, der die von Radarr und Sonarr angegebenen Dateien herunterlädt.

___
### Installation mit Ultraseedbox

Ultraseedbox (jetzt ultra.cc genannt) ist ein Dienst, der es ermöglicht, Torrents mit schnellen Downloadgeschwindigkeiten herunterzuladen und diese Torrents dann zu seeden (d.h. sie mit anderen Nutzern zu teilen, die sie jederzeit herunterladen wollen), allerdings kostet es etwas Geld, [hier](https://ultra.cc/) findest du die Website (ich bin in keiner Weise mit ihnen verpartnert, aber ich finde ihren Support und Service wirklich solide).

**Du kannst jeden Seedbox-Dienst verwenden, der http-Zugriff über NGINX bietet.**

Für meine Installation musst du...

**erforderlich (für Metadaten):**
- Sonarr (für TV-Shows) - auch Anime
- Radarr (für Filme)
- Nginx - http-Zugriff (bereits standardmäßig auf ultra.cc installiert)

...installieren
___
### Einrichten von Radarr / Sonarr
Du musst einen Metadaten-Downloader verwenden (der .nfo-Dateien herunterlädt), ich benutze Radarr und Sonarr, weil es für mich am einfachsten ist (eventuell ist es möglich, Metadaten mit etwas anderem herunterzuladen, aber ich habe es nicht versucht).

Um Radar und Sonar zu installieren, gehe zu deinem Control Panel und suche unter Installers nach Sonar und Radar.

Nun muss der Download der Metadaten aktiviert werden.

Für Radarr gehe dazu auf:

`Einstellungen > Metadaten`

Dort muss Kodi (XMBC) / Emby Metadaten aktiviert werden.

Ich verwende folgende Einstellungen in Radarr

![image](https://user-images.githubusercontent.com/18114966/187868344-b20c29ff-efdd-4f24-a655-a019eab06f2b.png)

das Häkchen bei "use Movie.nfo" muss entfernt werden, wie auf dem Screenshot zu sehen ist.

Für Sonarr gehe dazu auf:

`Einstellungen > Metadaten`

Und aktiviere folgende Einstellungen

![image](https://user-images.githubusercontent.com/18114966/187868381-0c766ce5-0ab9-4d07-b555-44764665d2f6.png)

Wenn die Metadaten nicht vorhanden sind, wird der Film / die TV-Show von Cloudstream nicht angezeigt.

Jetzt sind wir bereit, falls neue Ordner dem http-Zugang hinzugefügt werden sollen, folge dieser Dokumentation von [ultra.cc](https://docs.usbx.me/books/http-access/page/downloading-files-from-your-ultracc-slot-using-http-access)

___
### In cloudstream
Gehe in die Cloudstream-3 Einstellungen -> Erweiterungen -> English providers repository -> nach "NGINX" suchen -> das Einstellungssymbol drücken, es öffnet sich ein Dialogfeld, dort "Quelle" auswählen. 

Hier muss die genaue URL des http-NGINX-Servers eingegeben werden, über den auf die Dateien zugegriffen werden soll, z. B. https://myusername.myles.usbx.me/.

Der http-Zugang erfordert eine Authentifizierung, unter NGINX Zugangsdaten muss der Benutzernamen und das Passwort eingeben werden.

Diese Anmeldedaten sind im Controlpanel von ultra.cc hier zu finden:

`Access details > HTTP proxy access`

Wie in der Beschreibung angegeben, müssen diese Anmeldedaten in einem bestimmten Format eingeben werden,
angenommen, der Benutzername ist `meincoolerusername` und Ihr Passwort ist `passwort1234` (bitte benutze einen Passwortmanager lol), dann muss folgendes eingegeben werden: "mycoolusername:password1234".

![image](https://user-images.githubusercontent.com/18114966/187868588-98bfd993-1eee-4274-97b6-88934b877342.png)


Nun muss die Anwendung neu gestartet werden, um die Änderungen zu übernehmen.

NGINX wird nun in der Liste der Quellen auf der Startseite angezeigt.

Es kann sein, dass beim Starten der Anwendung angezeigt wird, dass keine URL angegeben wurde.

Das war's, NGINX wurde zu Cloudstream hinzugefügt