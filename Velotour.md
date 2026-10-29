# Velotour

## Sind die Informationen ausreichend? Ergänzungen

- **Fehlt – Anmeldung:** Ein Gast meldet sich für einen Termin an, mit Status «bezahlt». Ohne Anmeldung weiss man nicht, wer mitfährt.
- **Fehlt – Infos zum Termin:** Jeder Termin braucht eine maximale Teilnehmerzahl und einen Guide.
- **Partner und Kinder:** Kein Freitext. Besser eine Beziehung Gast – Gast für den Partner und ein Feld «Anzahl Kinder».
- **Start- und Zielort:** Eine eigene Tabelle «Ort». So gibt es keine Schreibfehler.
- **Wartung und Zubehör:** Je eine eigene Tabelle, weil ein Velo mehrere Wartungen und mehrere Zubehörteile haben kann.
- **Mietvelos:** Nur Teilnehmer können ein Velo mieten. Darum gehört die Miete zur Anmeldung und nicht direkt zum Gast.
## Konzeptionelles Modell

```mermaid
erDiagram
  Gast }o--o{ Termin : "meldet sich an"
  Tour ||--o{ Termin : "findet statt am"
  Gast }o--o{ Velo : "mietet"
  Velo ||--o{ Wartung : "hat"
  Velo }o--o{ Zubehoer : "hat"
  Gast |o--o{ Gast : "Partner / Kinder"
```

## Physisches Modell (3. Normalform)

```mermaid
erDiagram
  Ort ||--o{ Gast : ""
  Gast |o--o{ Gast : "Partner"
  Tour ||--o{ Termin : ""
  Ort ||--o{ Tour : "Start"
  Ort ||--o{ Tour : "Ziel"
  Gast ||--o{ Anmeldung : ""
  Termin ||--o{ Anmeldung : ""
  Anmeldung ||--o{ Miete : ""
  Velo ||--o{ Miete : ""
  Velo ||--o{ Wartung : ""
  Velo ||--o{ VeloZubehoer : ""
  Zubehoer ||--o{ VeloZubehoer : ""
  Ort {
    int OrtId PK
    varchar PLZ "NN"
    varchar Name "NN"
  }
  Gast {
    int GastId PK
    varchar Anrede
    varchar Vorname "NN"
    varchar Name "NN"
    date Geburtstag
    varchar Strasse
    int OrtId FK
    varchar Telefon
    varchar Email
    int PartnerId FK
    int AnzahlKinder
  }
  Tour {
    int TourId PK
    varchar Name "NN"
    text Beschreibung
    int Schwierigkeit "NN"
    decimal LaengeKm "NN"
    varchar Anforderung
    int StartOrtId FK "NN"
    int ZielOrtId FK "NN"
    decimal Preis "NN"
  }
  Termin {
    int TerminId PK
    int TourId FK "NN"
    date Datum "NN"
    time Startzeit
    int MaxTeilnehmer
    int GuideId
  }
  Anmeldung {
    int AnmeldungId PK
    int GastId FK "NN"
    int TerminId FK "NN"
    date Anmeldedatum "NN"
    bool Bezahlt "NN"
  }
  Velo {
    int VeloId PK
    varchar Hersteller "NN"
    varchar Typ "NN"
    varchar Marke
    varchar Groesse "NN"
    decimal Anschaffungspreis
    date Anschaffungsdatum
    decimal MietpreisTag "NN"
  }
  Miete {
    int MieteId PK
    int AnmeldungId FK "NN"
    int VeloId FK "NN"
    date Von "NN"
    date Bis "NN"
    bool Versicherung "NN"
    decimal Kaution "NN"
  }
  Wartung {
    int WartungId PK
    int VeloId FK "NN"
    date Datum "NN"
    varchar Beschreibung
    decimal Kosten
  }
  Zubehoer {
    int ZubehoerId PK
    varchar Name "NN UQ"
  }
  VeloZubehoer {
    int VeloId PK, FK
    int ZubehoerId PK, FK
  }
```

