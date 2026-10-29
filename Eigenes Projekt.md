# Eigenes Projekt

## Projektbeschreibung

## Musikvideo-Produktion

Ich schneide Musikvideos und Visualizer für Künstler. Bis jetzt speichere ich Aufträge, Versionen und Rechnungen in Ordnern und Notizen.

Die Datenbank soll das festhalten:

- welcher Kunde welches Projekt bestellt hat
- welche Videos zu einem Projekt gehören
- welche Versionen es von einem Video gibt, jeweils mit Feedback
- welche Software verwendet wurde
- ob die Rechnung bezahlt ist

## Konzeptionelles ERM

```mermaid
erDiagram
  Kunde ||--o{ Projekt : "beauftragt"
  Projekt ||--o{ Video : "enthaelt"
  Video }o--o{ Software : "geschnitten mit"
  Projekt ||--o{ Rechnung : "wird verrechnet"
  Video ||--o{ Version : "hat"
```

## Physisches ERM

```mermaid
erDiagram
  Kunde ||--o{ Projekt : ""
  Projekt ||--o{ Video : ""
  Video ||--o{ VideoSoftware : ""
  Software ||--o{ VideoSoftware : ""
  Projekt ||--o{ Rechnung : ""
  Video ||--o{ Version : ""
  Kunde {
    int KundeId PK
    varchar Kuenstlername "NN"
    varchar Email "NN UQ"
    varchar Instagram
  }
  Projekt {
    int ProjektId PK
    int KundeId FK "NN"
    varchar Titel "NN"
    date Auftragsdatum "NN"
    date Deadline
    decimal Preis
  }
  Video {
    int VideoId PK
    int ProjektId FK "NN"
    varchar Typ "NN"
    int LaengeSek
    varchar Aufloesung
  }
  Version {
    int VersionId PK
    int VideoId FK "NN"
    int Nummer "NN"
    date Datum "NN"
    varchar Feedback
  }
  Software {
    int SoftwareId PK
    varchar Name "NN UQ"
  }
  VideoSoftware {
    int VideoId PK, FK
    int SoftwareId PK, FK
  }
  Rechnung {
    int RechnungId PK
    int ProjektId FK "NN"
    date Datum "NN"
    decimal Betrag "NN"
    bool Bezahlt "NN"
  }
```

## Beschreibung der Tabellen

| Tabelle   | Inhalt                                                                    |
|---------------|-------------------------------------------------------------------------------|
| Kunde         | Künstler mit Kontaktdaten (Instagram-Handle)                                  |
| Projekt       | Ein Auftrag eines Kunden mit Deadline und Preis                               |
| Video         | Ein Video im Projekt (Musikvideo, Visualizer, Teaser) mit Länge und Auflösung |
| Version       | Jeder Export mit Datum und Kundenfeedback                                     |
| Software      | Premiere Pro, After Effects usw.                                              |
| VideoSoftware | Zwischentabelle: welches Video mit welcher Software (m:m)                     |
| Rechnung      | Rechnungen pro Projekt mit Betrag und Status                                  |

