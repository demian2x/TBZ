# Open Data

## Gewählte Quelle

COVID-19-Daten des Bundesamts für Gesundheit (BAG), veröffentlicht auf opendata.swiss und auf covid19.admin.ch.

## Wie kommt man an die Daten?

- opendata.swiss öffnen und nach "COVID-19 Schweiz" suchen.
- Datensatz "COVID-19 Schweiz" des BAG auswählen.
- Bei "Ressourcen" das gewünschte Format wählen: CSV, JSON oder XLSX. Der Download startet direkt.
- Keine Registrierung, kein API-Key nötig. Die Daten stehen unter einer offenen Lizenz (Quellenangabe BAG ist Pflicht).
- Zusätzlich gibt es eine JSON-API (Link "context"), die alle Dateien auflistet - praktisch für Programme.

## Wichtigste Felder

| Feld    | Bedeutung                                      |
|-------------|----------------------------------------------------|
| geoRegion   | Kanton (z. B. ZH) oder CH / FL                     |
| datum       | Datum der Meldung                                  |
| entries     | Anzahl neue Fälle an diesem Tag                    |
| sumTotal    | Kumulierte Fälle seit Beginn                       |
| inz_entries | Inzidenz pro 100'000 Einwohner                     |
| pop         | Bevölkerung der Region                             |
| type        | Art der Zahl: Fälle, Hospitalisationen, Todesfälle |

## Nutzen und Anwendungszweck

- Dashboards und Medien zeigen damit die aktuelle Lage (z. B. das BAG-Dashboard).
- Kantone und Spitäler können Kapazitäten planen.
- Forschung: Vergleich von Massnahmen zwischen Kantonen.
- Schule: Diagramme und Statistik üben mit echten Daten.



