# Tramlinien

## Kardinalitäten aus den Daten

- Linie - Fahrer: 1 : mc (Alexandra hat keine Linie, Linie 203 hat zwei Fahrer).
- Fahrer - Fahrer (Vorgesetzter): c : mc (Alexandra hat keinen Vorgesetzten, 1001 ist Vorgesetzte von zwei Fahrern).
- Bezirk - Haltestelle: 1 : mc (Bezirk 5013 und 5014 haben keine Haltestelle).
- Linie - Haltestelle: mc : mc, aufgelöst durch LinieHaltetAn mit Reihenfolge.

```mermaid
erDiagram
  Linie ||--o{ Fahrer : "faehrt auf"
  Fahrer |o--o{ Fahrer : "Vorgesetzter"
  Bezirk ||--o{ Haltestelle : "liegt in"
  Linie ||--o{ LinieHaltetAn : ""
  Haltestelle ||--o{ LinieHaltetAn : ""
  Fahrer {
    int Id PK
    varchar Name "NN"
    int FahrerId FK "Vorgesetzter, NULL erlaubt"
    int LinieId FK "NULL erlaubt"
  }
  Linie {
    int Id PK
    int Nummer "NN UQ"
  }
  Bezirk {
    int Id PK
    varchar Name "NN"
  }
  Haltestelle {
    int Id PK
    varchar Name "NN"
    int BezirkId FK "NN"
  }
  LinieHaltetAn {
    int LinieId PK, FK
    int HaltestelleId PK, FK
    int Reihenfolge "NN"
  }
```

In Workbench: FahrerId (Vorgesetzter) und LinieId bei Fahrer ohne NN, weil die Daten leere Werte enthalten. Reihenfolge, Name und Nummer NN.

