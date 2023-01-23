---
label: Linux
order: 998
icon: /static/linux.svg
---

# Emulation auf Linux

==- [!badge variant="contrast" size="2xl" icon="/static/waydroid.png" text="**Waydroid**"]

!!!success GPU Requirements


## WayDroid installieren

### Fedora 36

> **NOTE: Kernels 5.18.18 to 5.19.5 are broken**
1.  Copr Repository hinzufügen

```sh
sudo dnf copr enable aleasto/waydroid
```

2.  WayDroid installieren

```sh
sudo dnf install waydroid
```

Wenn du Waydroid über das Anwendungsmenü startest, kommt die Aufforderung, Waydroid mit verschiedenen Android-Images zu initialisieren. Benutze folgende Links:

System OTA: `https://ota.waydro.id/system`

Vendor OTA: `https://ota.waydro.id/vendor`

> HINWEIS: Dies lädt nicht-freie Komponenten herunter (ffmpeg, möglicherweise andere).
### Ubuntu 22.04

- Installationsvoraussetzungen

```sh
sudo apt install curl ca-certificates -y
```

- Die Repo

Füge die Repo zu der sources.list (für droidian & ubports kann dieser Schritt übersprungen werden)
Ersetze DISTRO="jammy" mit deiner aktuellen Distro. (Optionen: focal, jammy, ubuntu-devel, bookworm, bullseye, sid)

```sh
export DISTRO="jammy"
```

```sh
sudo curl --proto '=https' --tlsv1.2 -Sf https://repo.waydro.id/waydroid.gpg --output /usr/share/keyrings/waydroid.gpg && \
echo "deb [signed-by=/usr/share/keyrings/waydroid.gpg] https://repo.waydro.id/ $DISTRO main" > ~/waydroid.list && \
sudo mv ~/waydroid.list /etc/apt/sources.list.d/waydroid.list && \
sudo apt update
```

- Waydroid installieren

```sh
sudo apt install waydroid -y
```

Starte dann Waydroid über das Anwendungsmenü.

----

### GPU Anforderungen

Waydroid funktioniert derzeit am besten mit **Intel-GPUs**. Sie sollten ohne weitere Modifikationen funktionieren.

AMD-GPUs scheinen gemischte Ergebnisse zu haben (insbesondere die _RX 6800_ funktioniert nicht); wenn Waydroid _nicht_ funktioniert, möchtest du vielleicht auch die NVIDIA-Workarounds unten versuchen.

NVIDIA GPUs do _not_ work currently, but there are 2 workarounds:

-   Wechsel, wenn möglich, zu einer integrierten Grafikkarte;
-   Software-Rendering verwenden:
    -   Stelle sicher, dass `waydroid init` (siehe [#Installation](https://wiki.archlinux.org/title/Waydroid#Installation) section) bereits läuft
    -   Bearbeite `/var/lib/waydroid/waydroid_base.prop` und setze:

        ```
        ro.hardware.gralloc=default
        ro.hardware.egl=swiftshader
        ```

    -   [Neustarten](https://wiki.archlinux.org/title/Restart "Starte") den `waydroid-container.service` neu.
!!!  
___
## Fedora 36
___

!!!danger
Kernels 5.18.18 to 5.19.5 are broken.
!!!

[!badge variant="light" text="Step 1"] Add the Copr repository

```sh
sudo dnf copr enable aleasto/waydroid
```

[!badge variant="light" text="Step 2"] Install waydroid

```sh
sudo dnf install waydroid
```

When launching waydroid from the application menu you'll be asked to initialize waydroid with some android images. Use the following links:

System OTA: `https://ota.waydro.id/system`

Vendor OTA: `https://ota.waydro.id/vendor`

!!!warning
This will download non-free components (ffmpeg, possibly others).
!!!

___
## Ubuntu 22.04
___

[!badge variant="light" text="Step 1"] Install Pre-requisites

```sh
sudo apt install curl ca-certificates -y
```

[!badge variant="light" text="Step 2"] The Repo

Add the repo to your sources.list (for droidian & ubports, this step can be skipped)
Replace DISTRO="jammy" with your current target. Options: focal, jammy, ubuntu-devel, bookworm, bullseye, sid

```sh
export DISTRO="jammy"
```

```sh
sudo curl --proto '=https' --tlsv1.2 -Sf https://repo.waydro.id/waydroid.gpg --output /usr/share/keyrings/waydroid.gpg && \
echo "deb [signed-by=/usr/share/keyrings/waydroid.gpg] https://repo.waydro.id/ $DISTRO main" > ~/waydroid.list && \
sudo mv ~/waydroid.list /etc/apt/sources.list.d/waydroid.list && \
sudo apt update
```

[!badge variant="light" text="Step 3"] Install Waydroid

```sh
sudo apt install waydroid -y
```

Then start Waydroid from the applications menu.

___
## Install and Run Android Applications
___

Waydroid ist in der Lage, einige verschiedene Operationen durchzuführen, die mit dem Befehl waydroid app -h angezeigt werden:

```
usage: waydroid app [-h] {install,remove,launch,list} ...
optional arguments:
  -h, --help            show this help message and exit
subaction:
  {install,remove,launch,list}
    install             push a single package to the container and install it
    remove              remove single app package from the container
    launch              start single application
    list                list installed applications
```

Um eine App über CLI zu starten, sollten Sie den waydroid app launch <appname> Command verwenden:

```sh
waydroid app launch xyz.apk
```

Es ist auch möglich Android-Anwendungen über die Befehlszeile zu installieren.

```sh
waydroid app install xyz.apk
```

Die apk-Dateien, die man manchmal im Internet finden, haben meist nur Arm-Unterstützung und funktionieren daher nicht auf x86_64.

Unter Umständen möchtest du [F-Droid](https://f-droid.org/) installieren, um Apps über ein grafisches Interface zu installieren. Beachte, dass der Google Play Store in dieser Form nicht funktioniert, da er auf den proprietären Google Play Services basiert, die nicht installiert sind.

___
## Waydroid Eigenschaft-Optionen
___
Waydroid verwendet verschiedene Eigenschaften, um dem zugrunde liegenden Android-System mitzuteilen, wie es sich an einigen Stellen verhalten soll. Um dies zu tun, benutzen wir den Befehl `waydroid prop`. Um eine Eigenschaft zu deaktivieren,  `waydroid prop set <property> ""`

### Eigenschaften

- waydroid prop set persist.waydroid.multi_windows true/false (bool) Enables/Disables persistent freeform window mode
- waydroid prop set persist.waydroid.invert_colors true/false (bool) Swaps the color space from RGBA to BGRA (only works with our patched mutter so far)
- waydroid prop set persist.waydroid.height_padding 0-9999 (int) Adjust Height padding (30 will allow you to use navbar on mobile)
- waydroid prop set persist.waydroid.width_padding 0-9999 (int) Adjust width padding
- waydroid prop set waydroid.display_width 0-9999 (int) (auto-generated) Auto generated size of Waydroid screen
- waydroid prop set persist.waydroid.width 0-9999 (int) Used for user to override desired resolution
- waydroid prop set persist.waydroid.suspend true/false (bool) Keep Waydroid awake and do not let container sleep

___
## Gemeinsamen Ordner einrichten
___

!!!dark
Einrichten eines gemeinsamen Ordners zum Kopieren von Dateien aus `Quelle` zu `Ziel`.   
!!!

> `Quell-` Dateien sind dann vom `Ziel` abrufbar, aber nicht editierbar.
```sh
sudo mount --bind <source> <target>
```

!!!dark
Wir werden den Ordner `host` einrichten, um Dateien vom Host zu kopieren, und den Ordner `droid`, um Dateien von Waydroid zu kopieren. 
!!!

- Dateien von Linux nach Waydroid kopieren
    - auf Waydroid erstelle einen `/Waydroid/host` Ordner
    - auf Host erstelle einen `~/Waydroid/host` Ordner
```sh
mkdir ~/Waydroid/host
```
    - Linux-Ordner mit Android-Ordner verknüpfen
```sh
sudo mount --bind ~/Waydroid/host ~/.local/share/waydroid/data/media/0/Waydroid/host
```

- Kopieren von Dateien von Waydroid nach Linux:
    - auf Waydroid erstelle einen `/Waydroid/droid` Ordner
    - auf Host erstelle einen `~/Waydroid/droid` Ordner
```sh
mkdir ~/Waydroid/droid
```
    - Linux-Ordner mit Android-Ordner verknüpfen
```sh
sudo mount --bind ~/.local/share/waydroid/data/media/0/Waydroid/droid ~/Waydroid/droid
```

___
## Zwischenablage
___

!!!dark
Ersetze `dnf` durch den entsprechenden Befehl für deine Distro.
!!!

[!badge variant="light" text="Schritt 1"] Installiere pip

```sh
sudo dnf install pip
```

[!badge variant="light" text="Schritt 2"]  Installiere wl-clipboard

```sh
sudo dnf install wl-clipboard
```

[!badge variant="light" text="Schritt 3"] Installiere pyclip

```sh
pip install --upgrade pip pyclip
```

[!badge variant="light" text="Schritt 4"] füge `$HOME/.local/bin/`zu deinem $PATH hinzu

füge

```
export PATH="$PATH:$(du "$HOME/.local/bin/" | cut -f2 | tr '\n' ':' | sed 's/:*$//')"
```

in die entsprechende Datei `.zshenv` oder `.bashrc` oder `.profile` hinzu

[!badge variant="light" text="Schritt 5"] Starte das System neu

===

==- [!badge variant="light" size="2xl" icon="https://github.com/anbox.png" text="**Anbox**"]
Demnächst...
===
