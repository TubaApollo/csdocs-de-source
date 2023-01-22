---
label: Windows
order: 999
icon: /static/win11.png
---

# WSA-Installationsanleitung

!!!info Dieser WSA-Build umfasst
- Gerootetes Android 13
- Google Play Services und Magisk
- Kein Amazon-App-Store
!!!

## Anforderungen
___
|     [!badge variant="primary" size="l" icon="/static/win11.svg" text="Windows 11"]    |    [!badge variant="primary" size="l" icon="/static/win10.svg" text="Windows 10"]  { class="compact" }     |
|:-------------------------:|:-----------------------:|
| **RAM**: 6 GB (mindestens) und 16 GB (empfohlen).| **RAM**: 6 GB (mindestens) und 16 GB (empfohlen).|
| **Build**: 22000.526 oder höher.| **Build**: 22H2 10.0.19045.2311 oder höher.|
| Der Computer muss Virtualisierung unterstützen. Diese muss im BIOS/UEFI und in den optionalen Funktionen aktiviert sein. [**Leitfaden für diesen Vorgang.**](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-11-pcs-c5578302-6e43-4b4b-a449-8ced115f58e1)| Der Computer muss Virtualisierung unterstützen. Diese muss im BIOS/UEFI und in den optionalen Funktionen aktiviert sein. [**Leitfaden für diesen Vorgang.**](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-11-pcs-c5578302-6e43-4b4b-a449-8ced115f58e1)|

___
## Installation

!!!warning Um MagiskOnWSA verwenden zu können, muss das offizielle WSA [vollständig deinstalliert](#uninstallation) werden.
!!!

[!badge variant="light" text="Schritt 1"] **Lade die WSA** Zip-Datei von [!badge variant="secondary" text="hier"](https://github.com/MustardChef/WSABuilds#downloads) herunter

!!!danger Nicht den "Source Code" herunterladen.
!!!

[!badge variant="light" text="Schritt 2"] **Entpacke** die Zip-Datei

[!badge variant="light" text="Schritt 3"] Öffne den WSA-Ordner und **führe** die Datei `Run.bat` aus.

[!badge variant="light" text="Schritt 4"] Sobald der Installationsvorgang abgeschlossen ist, wird WSA gestartet.

!!!info Wenn es sich um eine Erstinstallation handelt, wird ein Fenster angezeigt, in dem um Zustimmung zu Diagnoseinformationen gebeten wird. Manchmal werden zwei identische Fenster angezeigt. Klicke in beiden Fenstern auf OK.
!!!

!!!info Der Installationsvorgang ist abgeschlossen!
Schließe nun die Windows Powershell durch Drücken einer beliebigen Taste.
!!!

___
## Sideloading

[!badge variant="light" text="Step 1"] Lade [**WSA Pacman**](https://github.com/alesimula/wsa_pacman/releases) oder [**WSA Sideloader**](https://github.com/infinitepower18/WSA-Sideloader) herunter und installiere es.

[!badge variant="light" text="Step 2"] Gehe zu [!badge variant="dark" text="Windows-Subsystem für Android™"] → [!badge variant="dark" text="Developer"] und aktiviere den **Entwicklermodus**.

!!!danger Pacman oder andere Sideloader-Anwendungen benötigen ADB-Rechte.
![](https://media.discordapp.net/attachments/1015131233824538624/1062611905249820733/allow.png)
!!!

!!!info Falls die Schaltfläche „Installieren“ während der Installation der APK ausgegraut ist, **öffne** WSA Pacman und **aktiviere** WSA von dort aus.
![](https://media.discordapp.net/attachments/1015131233824538624/1062610433506287708/WSA-pacman_x7UaiviLSW.png)
!!!

___
## Update

Dafür den neuen und alten WSA-Ordner **zusammenführen** und die alten Dateien durch die neuen **ersetzen.**

___
## Sichern & Wiederherstellen

### Sichern
Falls du deine Daten sichern willst, erstelle eine Sicherung von dieser Datei </br> `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache\userdata.vhdx`.

### Wiederherstellen
Die VHDX-Datei wird wieder in diesen Ordner eingefügt </br> `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache` .

___
## Uninstallation

1. Zum Startmenü gehen
2. Suche nach `Windows-Subsystem für Android™`
3. Sobald die WSA-Anwendung angezeigt wird, klicke im rechten Bereich auf `App-Einstellungen`.
4. Das Fenster "Einstellungen" öffnet sich. Scrolle nach unten und klicke auf `Beenden`.
5. Klicke `Reparieren`
6. Klicke `Zurücksetzen`
7. Schließe die Einstellungen
8. Gehe zurück zum Startmenü
9. Suche nach `Windows-Subsystem für Android™`
10. Sobald die WSA-Anwendung angezeigt wird, klicke im rechten Bereich auf `Deinstallieren`.