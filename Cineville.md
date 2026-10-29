# Cineville

## Anforderungen

- Film mit Länge, Sprache, Mindestalter.
- Vorstellung = ein Film an einem Tag/Uhrzeit in einem Saal mit einem Preis (Preis gilt für alle Plätze).
- Saal mit Anzahl Plätze und Wechselzeit, gehört zu einem Kino.
- Ticket pro Vorstellung, Vorverkauf als Kennzeichen, optional einem Stammkunden zugeordnet.
- Stammkunde mit Adresse, Telefon, optional E-Mail.
- Erweiterung: Parkplätze pro Kino, die ein Kunde reservieren kann.

## ERM (3. Normalform)

```mermaid
erDiagram
  Film ||--o{ Vorstellung : "wird gezeigt in"
  Saal ||--o{ Vorstellung : "findet statt in"
  Kino ||--o{ Saal : "hat"
  Vorstellung ||--o{ Ticket : "verkauft"
  Kunde |o--o{ Ticket : "kauft"
  Kino ||--o{ Parkplatz : "bietet"
  Parkplatz |o--o{ Parkreservation : ""
  Kunde ||--o{ Parkreservation : ""
  Film {
    int FilmId PK
    varchar Titel "NN"
    int LaengeMin "NN"
    varchar Sprache "NN"
    int Mindestalter "NN"
  }
  Kino {
    int KinoId PK
    varchar Name "NN"
    varchar Adresse
  }
  Saal {
    int SaalId PK
    int KinoId FK "NN"
    varchar Bezeichnung "NN"
    int AnzahlPlaetze "NN"
    int WechselzeitMin "NN"
  }
  Vorstellung {
    int VorstellungId PK
    int FilmId FK "NN"
    int SaalId FK "NN"
    datetime Beginn "NN"
    decimal Preis "NN"
  }
  Ticket {
    int TicketId PK
    int VorstellungId FK "NN"
    int KundeId FK
    int Platznummer
    bool Vorverkauf "NN"
    datetime Kaufdatum "NN"
  }
  Kunde {
    int KundeId PK
    varchar Name "NN"
    varchar Vorname "NN"
    varchar Strasse
    varchar PLZ
    varchar Ort
    varchar Telefon "NN"
    varchar Email
  }
  Parkplatz {
    int ParkplatzId PK
    int KinoId FK "NN"
    varchar Nummer "NN"
  }
  Parkreservation {
    int ResId PK
    int ParkplatzId FK "NN"
    int KundeId FK "NN"
    datetime Von "NN"
    datetime Bis "NN"
  }
```

3\. Normalform: Jede Tabelle beschreibt genau eine Sache, keine Wiederholungen (Film-Daten stehen nur in Film, nicht bei jeder Vorstellung), alle Nicht-Schlüssel hängen nur vom Primärschlüssel ab.

