<img src="img/easygraph_logo.svg" alt="header" width="400"/>

# Was ist EasyGraph? 

## Datenerfassung mit log.flow und EasyGraph { data-search-exclude }
Log.flow kann als hervorragendes Werkzeug zur Datenaufzeichnung eingesetzt werden. Mit der PC-Software EasyGraph können hochdynamische Prozesse mit Abtastraten von bis zu 
1000 Hz analysiert werden. Die Durchflussrate und das Volumen beider Kanäle können gleichzeitig aufgezeichnet werden.

<video controls autoplay loop src="img/easygraphdemo.mp4"> </video>  

### Highlights { data-search-exclude }

- Perfekt für schnelle Diagnose und Analyse
- Hochpräzise Frequenzmessung und Impulszählung
- GPU-beschleunigte Live-Diagramme 
- Einstellbare Abtastrate (1-1000 Hz) und Filterstufen
- Berechnungsfunktionen zur Skalierung der Eingangswerte
- Datenaufzeichnung mit Triggerfunktion
- Import/Export der aufgezeichneten Daten
- Schnelle Erstellung von Excel/PDF-Berichten zur Dokumentation
- Version Log.flow: 2x Impulseingang
- Version Log.flowV: 1x Impulseingang, 1x analoger Spannungseingang (0..10V)
- Version Log.flowI: 1x Impulseingang, 1x analoger Stromeingang (0/4..20 mA)

### Das log.flow Gerät { data-search-exclude }

Das Log.flow (VSE Art. Nr.: 4881) ist ein externes USB-Gerät, das an einen PC angeschlossen wird, um Signalmessungen und Berechnungen von zwei angeschlossenen Durchflussmessern oder anderen Frequenzsensoren durchzuführen. Die Hardware-Spezifikationen des Geräts finden Sie [hier](logflow.md "Log.flow Device Description").

### Andere unterstützte Geräte { data-search-exclude }



Neben dem [log.flow](devices.md#logflow-datalogging-system) sind auch andere Geräte mit EasyGraph kompatibel:

- [IO.flow®](devices.md#ioflow-with-usb-master)

- [Display/FU-Wandler](devices.md#displayfu-wandler-rs232) (A341/A350/FU210)

- [esi-Drucksensoren](devices.md#esi-usb-pressure-sensor)

## Struktur { data-search-exclude }

Diese Dokumentation gliedert sich in die folgenden Hauptkapitel:

* [Erste Schritte](gettingstarted.md) für Anweisungen zur Einrichtung/Aktivierung und zum Starten einer Aufzeichnung
* [Unterstützte Geräte](devices.md) beschreibt, wie die verschiedenen Hardware-Geräte angeschlossen werden 
* [Benutzeroberfläche](uiguide.md) zeigt, wie die einzelnen Softwarekomponenten funktionieren
* [Sonderfunktionen](advanced.md) zeigt Beispiele für fortgeschrittene Anwendungen 
* [Log.flow](logflow.md) erklärt die Hardware-Funktionen und Spezifikationen des log.flow-Geräts
* [Fehlerbehebung](faqs.md) zeigt, wie man häufig gestellte Fragen und Probleme lösen kann



## Hardware-Voraussetzungen

Der PC, auf dem die EasyGraph-Software läuft, sollte folgende Mindestanforderungen an die Hardware erfüllen:

* 2 GHz Prozessor (x64) oder schneller
* 64-Bit-Windows-Installation
* 4GB RAM oder mehr
* Grafikkarte oder iGPU mit DirectX11-Unterstützung
* 200 MB freier Festplattenspeicher
* Bildschirmauflösung: mindestens 1440x900 px
* USB 2.0-Schnittstelle oder besser (USB 3.0-Anschluss für maximale Strombelastbarkeit)
* Optionale Internetverbindung für Update-Check

## Software-Anforderungen

* Microsoft Visual C++ Redistributable 2015-2022 ([:material-link: Direct Download](https://aka.ms/vs/17/release/vc_redist.x64.exe))
* .NET Framework v4.7.2 ([:material-link: Download](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net472))
* .NET 6.0 Desktop Runtime ([:material-link: Download](https://dotnet.microsoft.com/en-us/download/dotnet/6.0))

## Lizenzinformationen

Die EULA und Lizenzinformationen der verwendeten Softwarekomponenten finden Sie im Abschnitt [About](about.md).
