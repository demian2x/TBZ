# Reisebüro

## Erkannte Redundanzen

- Kundendaten (Name, Adresse) stehen bei jeder Buchung erneut - Tippfehler wie "Jakob/Jacob Gutermann" oder "St. Gallen/St Gallen" entstehen.
- Mehrere Hotels, Reiseorte und Flüge in einer Zelle (nicht 1. Normalform).
- Flugnummer bestimmt die Route und die Abflugzeit - das steht trotzdem bei jeder Buchung.

## Physisches ERM (3. Normalform)

```mermaid
erDiagram
  Ort ||--o{ Kunde : "wohnt in"
  Kunde ||--o{ Buchung : "macht"
  Buchung ||--o{ Hotelbuchung : ""
  Hotel ||--o{ Hotelbuchung : ""
  Reiseort ||--o{ Hotel : "liegt in"
  Buchung ||--o{ Flugbuchung : ""
  Flug ||--o{ Flugbuchung : ""
  Flugroute ||--o{ Flug : "wird geflogen als"
  Ort {
    int OrtId PK
    varchar PLZ "NN"
    varchar Ortsname "NN"
  }
  Kunde {
    int KundeId PK
    varchar Name "NN"
    varchar Vorname "NN"
    varchar Adresse
    int OrtId FK "NN"
  }
  Buchung {
    int BuchungId PK
    int KundeId FK "NN"
    date Buchungsdatum "NN"
    int AnzahlPersonen "NN"
  }
  Reiseort {
    int ReiseortId PK
    varchar Name "NN UQ"
  }
  Hotel {
    int HotelId PK
    varchar Name "NN"
    int ReiseortId FK "NN"
    decimal PreisProNacht "NN"
  }
  Hotelbuchung {
    int HotelbuchungId PK
    int BuchungId FK "NN"
    int HotelId FK "NN"
    int AnzahlNaechte "NN"
  }
  Flugroute {
    varchar Flugnummer PK
    varchar VonOrt "NN"
    varchar NachOrt "NN"
    time Abflugzeit "NN"
    decimal Preis "NN"
  }
  Flug {
    int FlugId PK
    varchar Flugnummer FK "NN"
    date Flugdatum "NN"
  }
  Flugbuchung {
    int FlugbuchungId PK
    int BuchungId FK "NN"
    int FlugId FK "NN"
    varchar Typ "Hin/Rueck NN"
  }
```

- Flugroute (Flugnummer, von, nach, Zeit, Preis) ist von Flug (Datum) getrennt, weil eine Route an vielen Tagen fliegt, aber nie zweimal am selben Tag.
- Hotel hat einen Preis pro Nacht, die Anzahl Nächte steht in der Hotelbuchung.
- Eine Buchung kann mehrere Hotels und mehrere Flüge enthalten (Hin/Rück).

