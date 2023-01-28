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
!!!

## Anforderungen
___
|     [!badge variant="primary" size="l" icon="/static/win11.svg" text="Windows 11"]    |    [!badge variant="primary" size="l" icon="/static/win10.svg" text="Windows 10"]  { class="compact" }     |
|:-------------------------:|:-----------------------:|
| **RAM**: 6 GB (minimum) und 16 GB (empfohlen).| **RAM**: 6 GB (minimum) und 16 GB (empfohlen).|
| **Build**: 22000.526 oder höher.| **Build**: 22H2 10.0.19045.2311 oder höher.|
| **Partition**: NTFS <br /> Windows-Subsystem für Android™ kann nur auf einer NTFS-Partition installiert werden, nicht auf einer exFAT-Partition  | **Partition**: NTFS <br /> Windows-Subsystem für Android™ kann nur auf einer NTFS-Partition installiert werden, nicht auf einer exFAT-Partition|
| Der Computer muss Virtualisierung unterstützen, die im BIOS/UEFI und in den optionalen Funktionen aktiviert sein muss. [**Guide for this process.**](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-11-pcs-c5578302-6e43-4b4b-a449-8ced115f58e1)| Der Computer muss Virtualisierung unterstützen, die im BIOS/UEFI und in den optionalen Funktionen aktiviert sein muss. [**Guide for this process.**](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-11-pcs-c5578302-6e43-4b4b-a449-8ced115f58e1)|

!!!warning GPU-Kompatibilität
Jeder kompatible Grafikprozessor von Intel, AMD oder Nvidia. Die GPU-Leistung kann je nach Kompatibilität mit dem Windows-Subsystem für Android™ variieren. Nvidia GPUs sind dafür bekannt, Probleme zu verursachen. Wenn Windows-Subsystem für Android™ nicht startet oder Grafikprobleme auftreten, wenn ein Nvidia-Grafikprozessor verwendet wird, [folge diesen Anweisungen](https://github.com/MustardChef/WSABuilds/blob/master/Guides/ChangingGPU.md), um zu einem anderen iGPU/dGPU/eGPU zu wechseln, die du möglicherweise besitzt, oder um zum Microsoft Basic Renderer zu wechseln.
!!!

___
## Installation

!!!warning Um MagiskOnWSA verwenden zu können, muss das offizielle WSA [vollständig deinstalliert](#deinstallation) werden.
!!!

[!badge variant="light" text="Schritt 1"] **Lade die WSA** Zip-Datei von [!badge variant="secondary" text="hier"](https://github.com/MustardChef/WSABuilds#downloads) herunter

!!!danger Nicht den "Source Code" herunterladen.
!!!

[!badge variant="light" text="Schritt 2"] **Entpacke** die Zip-Datei

[!badge variant="light" text="Schritt 3"] Öffne den WSA-Ordner und **führe** die Datei `Run.bat` aus.

!!!dark
Wenn du bereits eine MagiskOnWSA-Installation hast, wird diese automatisch unter Beibehaltung aller Benutzerdaten deinstalliert und eine neue Installation durchgeführt. Du brauchst dir also keine Sorgen um deine Daten zu machen.
!!!

[!badge variant="light" text="Schritt 4"] Sobald der Installationsvorgang abgeschlossen ist, wird WSA gestartet.

!!!dark
Wenn es sich um eine Erstinstallation handelt, wird ein Fenster angezeigt, in dem Sie um Zustimmung zu Diagnoseinformationen gebeten werden. Manchmal werden zwei identische Fenster angezeigt. Klicke in beiden Fenstern auf Weiter).
!!!

!!!light Der Installationsvorgang ist abgeschlossen!
Schließe nun die Windows Powershell, indem du eine beliebige Taste drückst.
!!!

!!!contrast Fehlerbehebung
Wenn du Probleme bei der Installation von WSA hast, besuche den [**Support Server**](https://discord.com/invite/2thee7zzHZ). Die häufigsten Fehlerbehebungen sind [!badge text="hier"](/troubleshooting.md/#wsa) aufgeführt. Du kannst auch diesen folgen.
!!!

___
## Sideloading

[!badge variant="light" text="Schritt 1"] Lade [**WSA Pacman**](https://github.com/alesimula/wsa_pacman/releases) oder [**WSA Sideloader**](https://github.com/infinitepower18/WSA-Sideloader) herunter und installiere es.

[!badge variant="light" text="Schritt 2"] Gehe zu [!badge variant="dark" text="Windows-Subsystem für Android™"] → [!badge variant="dark" text="Developer"] und aktiviere den **Entwicklermodus**.

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
## Deinstallation

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
