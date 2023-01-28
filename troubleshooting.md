---
label: Fehlerbehebung
order: 700
icon: tools
---

## Fehler bei der Sicherung

!!!info Wenn kein Backup erstellt werden kann.
Speicherort ändern/wählen.
[!badge variant="dark" icon="/static/base.png" text="Cloudstream"] → [!badge variant="dark" icon="/static/gear.png" text="Einstellungen"] → [!badge variant="dark" icon="download" text="Downloadpfad"] und wähle einen benutzerdefinierten Speicherort.
!!!

## Fehler beim Wiederherstellen des Backups

!!!info Wenn die Sicherungsdatei nicht gelesen werden kann.
Benenne die Dateiendung von "json" in "txt" um. Versuche nun erneut, die Sicherungsdatei einzulesen.
!!!

## Fehler: Kein Speicherplatz verfügbar

!!!info Wenn der Film nicht abgespielt wird und eine Fehlermeldung über fehlenden Speicherplatz erscheint.
Den Video-Cache auf der Festplatte ändern. [!badge variant="dark" icon="/static/base.png" text="Cloudstream"] → [!badge variant="dark" icon="/static/gear.png" text="Einstellungen"] → [!badge variant="dark" text="Player"] > [!badge variant="dark" icon="server" text="Video-Cache in Speicher"] und stelle eine **geringere Menge an Cache** ein.
!!!

## Repositories/Erweiterungen werden nicht geladen.

!!!info Wenn die Repositories im Bereich [der offiziellen Seite](https://cloudstream.cf/repos/) oder [!badge variant="dark" text="Erweiterungen"] nicht geladen werden.
Versuche es über eine VPN-Verbindung erneut.
!!!

## Untertitel fehlerhaft

!!!info Bei der Wiedergabe eines Videos werden die Untertitel unterbrochen.
[!badge variant="dark" text="Videoplayer"] → [!badge variant="dark" text="Quellen"] → [!badge variant="dark" text="Untertitel"] und klicke oben auf [!badge variant="dark" text="Auto"]. Ändere nun die Kodierung der Untertitelsprache.
!!!

##  Untertitel-Casting-Problem

!!!info Wenn die Untertitel nicht mit dem systemeigenen Casting-System auf den Fernseher übertragen werden.
Versuche es mit [dieser Anwendung](https://play.google.com/store/apps/details?id=com.instantbits.cast.webvideo).
[!badge variant="dark" icon="/static/base.png" text="Cloudstream"] → [!badge variant="dark" text="Episodenseite"] → **Drücken und halten der Episode** → [!badge variant="dark" text="Mit Web Video Cast wiedergeben"] → **Wähle den passenden Link und caste diesen.** Die Untertitelauswahl ist möglicherweise nicht so gut wie bei CS3.
!!!

## Safe Mode an

!!!info Wenn die App in den abgesicherten Modus wechselt.
Lösche den Cache der App und starte die App neu. Es kann auch eine kleinere Cache-Größe eingestellt werden, um dieses Problem zu vermeiden.
!!!danger Dies ist eine allgemeine Fehlerbehebung. Unter Umständen wird das Problem dadurch nicht behoben. In diesem Fall poste es im Report-Channel.
!!!

## Sorastream

!!!info Das Laden der Episode dauert zu lange.
Da viele Seiten abgerufen werden, dauert es eine Weile, bis alle Seiten geladen sind. Überspringe das Laden nach 3-5 Sekunden.
!!!

!!!info Einige Quellen werden nicht geladen.
1. Sora hat einige geobeschränkte Quellen. Verwende ein VPN, um auf diese Quellen zuzugreifen.
2. Oder der Exo-Player kann das Video nicht abspielen. Benutze einen externen Player wie VLC.
!!!


!!!info Einige Titel zeigen "Keine Verlinkung gefunden".
Sora verwendet TMDb für den Katalog, nicht für die Quellen. Daher kann es sein, dass Titel angezeigt werden, die keine der Seiten hat.
!!!

!!!info Bei einigen Videos wird kein Video/Audio abgespielt.
Der EXO-Player kann das Video nicht abspielen. Verwende einen externen Player wie z.B. VLC.
!!!

!!!info Fehler beim Herunterladen des Videos.
Versuche 1DM für den Download von Sorastream.
!!!

## WSA

!!!info Install.ps1 is not recognized/missing

![](https://media.discordapp.net/attachments/1044322950725259274/1068243571544690719/9Qf3veK.png)

 If the popup windows disappear without asking administrative permission and Windows Subsystem For Android™ is not installed successfully, you should manually run Install.ps1 as administrator:
      
1. Press Win+x and select Windows™ Terminal (Admin)
      
2. Input the command below and press enter, replacing {X:\path\to\your\extracted\folder} including the {} with the path of the extracted folder
    ```Powershell
        cd "{X:\path\to\your\extracted\folder}"
     ```  
        
3. Input the command below and press enter   
    ```Powershell
        PowerShell.exe -ExecutionPolicy Bypass -File .\Install.ps1
    ```
        
4. The script will run and Windows Subsystem For Android™ will be installed
!!!

!!!info Virtualisierungsfehler

![](https://user-images.githubusercontent.com/68629435/213985345-a6fc6e97-63f3-4741-8965-8d62a0d6b824.png)

1. WSA entfernen

2. Gehe zu "Windows-Features aktivieren oder deaktivieren" und deaktiviere Hyper-V, VM-Plattform, Windows-Hypervisor-Plattform, und Windows-Subsystem für Linux, dann neu starten.

3. Aktiviere diese Features wieder und starte  ein zweites Mal neu.

4. Stelle sicher, dass die Kernisolierung ausgeschaltet ist.

5.  Gehe im Registrierungseditor (regedit) zu `\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\FsDepends`

    Ändere den Wert für "Start" von `3` zu `0`

    !!!
    Du kannst die Zahl auf 3 zurücksetzen, wenn es keinen Unterschied macht.
    !!!

6. Füge dann in CMD (als Administrator ausführen) folgendes ein:
```cmd
bcdedit /set hypervisorlaunchtype auto
```
7. Installiere WSA neu, indem du `Run.bat` ausführst
!!!
