# Kardinalitäten

## Aufgabe 1 - ohne Bezeichnung

| Beziehung             | Kardinalität | Annahme                                                                  |
|---------------------------|------------------|------------------------------------------------------------------------------|
| Adresse - Person          | 1 : mc           | An einer Adresse wohnen mehrere Personen, jede Person hat genau eine Adresse |
| Buch - Autor              | mc : m           | Ein Buch hat mindestens einen Autor, ein Autor kann mehrere Bücher haben     |
| Mutter - Kind             | 1 : mc           | Jedes Kind hat genau eine Mutter                                             |
| Mann - Frau               | c : c            | Ehe: höchstens eine Frau pro Mann und umgekehrt                              |
| Mitarbeiter - Vorgesetzte | mc : c           | Ein Vorgesetzter hat mehrere Mitarbeiter, der Chef hat keinen Vorgesetzten   |
| Eltern - Kind             | m : mc           | Ein Kind hat zwei Eltern, Eltern haben mehrere Kinder                        |
| Klasse - Lehrperson       | mc : m           | Eine Klasse hat mehrere Lehrpersonen, eine Lehrperson mehrere Klassen        |
| Zeitung - Inserat         | 1 : mc           | Ein Inserat erscheint in genau einer Zeitung                                 |
| Fahrzeug - Lenkrad        | 1 : 1            | Jedes Fahrzeug hat genau ein Lenkrad                                         |

## Aufgabe 2 - mit Bezeichnung

| Beziehung                                  | Kardinalität                                                                                   |
|------------------------------------------------|----------------------------------------------------------------------------------------------------|
| rechte Schuhe - Paare - linke Schuhe           | 1 : 1                                                                                              |
| Abteilungen - Abteilungsleiter - Personal      | 1 : 1 (jede Abteilung hat genau einen Leiter, eine Person leitet höchstens eine Abteilung → 1 : c) |
| Person - Abteilungszugehörigkeit - Abteilungen | mc : 1                                                                                             |
| Kinder - Familienzugehörigkeit - Ehepaare      | mc : 1                                                                                             |
| Personen - Parteizugehörigkeit - Parteien      | mc : c                                                                                             |
| Projekte - ist Unterprojekt - Projekte         | mc : c (rekursiv)                                                                                  |
| Vorlesungen - Einschreibung - Studenten        | mc : mc                                                                                            |
| Personen - Freundschaften - Personen           | mc : mc (rekursiv)                                                                                 |

## Aufgabe 3 - Auto und Person

| Situation                                               | Bezeichnung | Kardinalität                                                               |
|-------------------------------------------------------------|-----------------|--------------------------------------------------------------------------------|
| Wer mit welchem Auto gerade unterwegs ist                   | fährt gerade    | c : c (ein Auto höchstens eine Person, eine Person höchstens ein Auto)         |
| Der Besitzer jedes Autos wird erfasst                       | besitzt         | 1 : mc (jedes Auto genau einen Besitzer, eine Person kann mehrere Autos haben) |
| Angestellte werden für einen Ausflug auf die Autos verteilt | sitzt in        | mc : 1 (jede Person in genau einem Auto, pro Auto mehrere Personen)            |
| Fahrlizenzen für die verschiedenen Autos pro Person         | darf fahren     | mc : mc                                                                        |

