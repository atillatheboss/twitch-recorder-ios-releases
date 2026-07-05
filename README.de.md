# Twitch Recorder iOS Releases

[🇬🇧 English README](README.md)

Dieses Repository enthält öffentliche Release-Builds und eine AltStore-kompatible Source für die **Twitch Recorder iOS** App.

Twitch Recorder iOS kann direkt lokal auf dem iPhone gestartet und genutzt werden, ohne dass vorher ein Recorder-Server verbunden werden muss. Du kannst die App öffnen, Einstellungen ansehen und die verfügbaren lokalen App-Funktionen verwenden, ohne den Server zu starten.

Für die beste Erfahrung und für echte unbeaufsichtigte Twitch-Aufnahmen solltest du zusätzlich den Twitch Recorder Server installieren und laufen lassen. Der Server übernimmt die eigentliche Aufnahme im Hintergrund, sodass dein iPhone nicht dauerhaft geöffnet oder verbunden bleiben muss.

## AltStore Source

Du kannst Twitch Recorder iOS über die AltStore-kompatible Source aus diesem Repository installieren.

Source URL:

```txt
https://raw.githubusercontent.com/atillatheboss/twitch-recorder-ios-releases/main/altstore-source.json
```

Die AltStore Source wird automatisch aus dem neuesten Release generiert. Wenn ein neuer Release veröffentlicht wird, wird die Source aktualisiert, damit kompatible Apps die neueste Version erkennen können.

## Funktionsweise

Die iOS-App ist eine Companion-App für den Twitch Recorder Server.

Die App selbst führt kein Streamlink oder FFmpeg direkt auf dem iPhone aus. Stattdessen übernimmt der Recorder-Server die eigentliche Aufnahme, den Download, die Verarbeitung und die Medienverwaltung.

Du kannst die App auf zwei Arten verwenden:

### Lokaler Modus

Nutze die App ohne Verbindung zu einem Server.

Das ist praktisch für:

- App öffnen und testen
- Oberfläche ansehen
- Lokale Einstellungen verwalten
- App vorbereiten, bevor ein Recorder-Server verbunden wird

### Server-Modus

Verbinde die App mit einem laufenden Twitch Recorder Server.

Dadurch wird die komplette Recorder-Erfahrung freigeschaltet:

- Echte Twitch-Aufnahmen starten
- Aufnahmen planen
- Streams aufnehmen, ohne selbst dabei zu sein
- Aktive und geplante Jobs verwalten
- Aufnahmen durchsuchen
- Medien abspielen
- VODs und Clips suchen und herunterladen
- Recorder-Metriken und Server-Einstellungen anzeigen

Für echte Aufnahmen wird der Server-Modus empfohlen.

## Automatische Server-Erkennung

Die App kann einen kompatiblen Recorder-Server im Netzwerk automatisch erkennen.

So verwendest du die Erkennung:

1. Starte den Twitch Recorder Server auf deinem Mac, NAS, Heimserver oder Docker-Host.
2. Stelle sicher, dass dein iPhone im selben Netzwerk ist oder per VPN verbunden ist.
3. Öffne die App.
4. Tippe auf **Recorder Server konfigurieren**.
5. Wähle den erkannten Server aus oder trage den Server bei Bedarf manuell ein.

## Funktionen

- App lokal nutzen, ohne zuerst einen Server einzurichten
- Recorder-Server automatisch aus der App erkennen
- Twitch-Aufnahmen direkt vom iPhone starten
- Stream-Qualität, Zeitplan, Dauer, Endzeit und Chat-Optionen auswählen
- Twitch-Kanäle mit Live-/Offline-Status suchen
- Aktive und geplante Aufnahme-Jobs verwalten
- Jobs pausieren, fortsetzen, stoppen, abbrechen und verlängern
- Aufgenommene Medien durchsuchen
- Aufnahme-Links kopieren
- MP4-Aufnahmen finalisieren
- Aufnahmen nativ unter iOS abspielen
- Twitch-VODs und Clips über den Server suchen und herunterladen
- Download-Jobs und heruntergeladene Medien verwalten
- Recorder-Metriken sowie App- und Server-Einstellungen anzeigen

## Voraussetzungen

Für die lokale Nutzung benötigst du:

- Ein iPhone
- Einen gültigen IPA-Build oder die AltStore-kompatible Source
- Eine Sideloading-Methode wie LiveContainer, SideStore oder AltStore

Für die vollständige Recorder-Erfahrung benötigst du zusätzlich:

- Einen laufenden Twitch Recorder Server
- Netzwerkzugriff vom iPhone auf den Server
- Genügend Speicherplatz auf dem Server-System für Aufnahmen

## Installation

Du kannst die App über die AltStore-kompatible Source oder manuell über die IPA-Datei installieren.

### Option 1: Installation über die AltStore Source

1. Installiere **LiveContainer**, **SideStore** oder **AltStore** auf deinem iPhone.
2. Öffne die App, die du zum Sideloading verwenden möchtest.
3. Öffne den Bereich **Sources**.
4. Füge die Source URL aus dieser README hinzu.
5. Suche in der Source nach **Twitch Recorder iOS**.
6. Installiere die App.
7. Öffne Twitch Recorder iOS.
8. Nutze die App lokal oder tippe auf **Recorder Server konfigurieren**, um deinen Recorder-Server zu verbinden.

### Option 2: IPA manuell installieren

1. Öffne die [Releases-Seite](https://github.com/atillatheboss/twitch-recorder-ios-releases/releases).
2. Lade die neueste IPA-Datei herunter.
3. Öffne LiveContainer, SideStore oder AltStore.
4. Importiere oder installiere die heruntergeladene IPA.
5. Öffne Twitch Recorder iOS.
6. Nutze die App lokal oder konfiguriere den Recorder-Server für alle Aufnahmefunktionen.

## LiveContainer-Status

Die App wurde bisher nur mit **LiveContainer** getestet.

Die Installation über SideStore und AltStore sollte grundsätzlich über denselben IPA- oder AltStore-Source-Workflow funktionieren, wurde aber bisher noch nicht getestet.

Getestet:

- LiveContainer

Noch nicht getestet:

- SideStore
- AltStore

## Empfohlenes Setup

Für die beste Erfahrung:

1. Installiere die iOS-App über LiveContainer.
2. Starte den Twitch Recorder Server auf einem Gerät, das dauerhaft online bleiben kann.
3. Öffne die App.
4. Tippe auf **Recorder Server konfigurieren**.
5. Lasse die App den Server automatisch erkennen.
6. Starte und verwalte deine Aufnahmen direkt vom iPhone.

Mit diesem Setup können Aufnahmen weiterlaufen, auch wenn du dein iPhone gerade nicht aktiv benutzt.

## Wiedergabe

Die native iOS-Wiedergabe wird über eine `AVPlayerViewController` Bridge umgesetzt. Für die Wiedergabe ist kein zusätzliches Flutter-Video-Plugin erforderlich.

## Hinweise

- Die App kann ohne Recorder-Server geöffnet und lokal genutzt werden.
- Echte Twitch-Aufnahmen benötigen den Recorder-Server.
- Der Server übernimmt Aufnahme, Download, Verarbeitung, Streamlink und FFmpeg.
- Die iOS-App dient als lokale Oberfläche, Fernsteuerung und Medienbrowser.
- Stelle sicher, dass dein iPhone und Server sich im selben Netzwerk oder über VPN erreichen können, wenn du den Server-Modus verwendest.
- Die AltStore Source wird automatisch aus dem neuesten Release aktualisiert.

## Haftungsausschluss

Dieses Projekt ist nicht mit Twitch verbunden, wird nicht von Twitch unterstützt und nicht von Twitch gesponsert. Nutze es verantwortungsvoll und beachte die Twitch-Nutzungsbedingungen sowie geltende Gesetze.
