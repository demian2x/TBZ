# Leistungserfassung

## Konzeptionelles Modell

```mermaid
erDiagram
  Kunde ||--o{ Projekt : "hat"
  Projekt ||--o{ Leistung : "enthaelt"
  Mitarbeiter ||--o{ Leistung : "erbringt"
  Rolle ||--o{ Leistung : "gilt fuer"
  Rolle ||--o{ Tarif : "hat"
  Projekt ||--o{ Rechnung : "wird verrechnet"
  Rechnung ||--o{ Leistung : "enthaelt"
  Kunde {
    int KundeId PK
    varchar Firma
    varchar Adresse
    varchar Email
  }
  Projekt {
    int ProjektId PK
    int KundeId FK
    varchar Name
    date Start
    date Ende
  }
  Mitarbeiter {
    int MitarbeiterId PK
    varchar Vorname
    varchar Nachname
  }
  Rolle {
    int RolleId PK
    varchar Bezeichnung
  }
  Tarif {
    int TarifId PK
    int RolleId FK
    decimal StundenAnsatz
    date GueltigAb
  }
  Leistung {
    int LeistungId PK
    int ProjektId FK
    int MitarbeiterId FK
    int RolleId FK
    int RechnungId FK
    date Datum
    decimal Stunden
    varchar Beschreibung
  }
  Rechnung {
    int RechnungId PK
    int ProjektId FK
    date Von
    date Bis
    date Rechnungsdatum
    decimal Total
  }
```

## Beziehungen und Kardinalitäten

- **Kunde – Projekt (1 : mc):** Jedes Projekt gehört zu genau einem Kunden.
- **Projekt – Leistung (1 : mc):** Jede Leistung gehört zu genau einem Projekt.
- **Mitarbeiter – Leistung (1 : mc):** Jede Leistung wird von genau einem Mitarbeiter gemacht.
- **Rolle – Leistung (1 : mc):** Die Rolle wird bei jeder Leistung gespeichert. So kann Kevin einmal Projektleiter und einmal Hilfsperson sein.
- **Rolle – Tarif (1 : mc):** Jeder Tarif hat ein Datum «gültig ab». Wenn sich ein Tarif ändert, stimmen alte Rechnungen trotzdem noch.
- **Rechnung – Leistung (1 : mc):** Eine Rechnung fasst alle Leistungen aus einem Zeitraum zusammen.
