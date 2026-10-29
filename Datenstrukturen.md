## Datenstrukturen

### Fragestellung 1 – Adressliste mit mehreren 100 Einträgen

- **Liste von Objekten:** Jede Adresse ist ein Objekt mit Name, Strasse und Ort. Man kann die Liste einfach durchgehen und sortieren.
- **Tabelle in einer Datenbank:** Bei so vielen Einträgen die beste Lösung, weil man leicht suchen, filtern und sortieren kann.
- **Dictionary:** Der Name ist der Schlüssel. Gut, wenn man oft eine bestimmte Person sucht.

### Fragestellung 2 – Viele Werte, schneller Zugriff

- **Dictionary (Hash-Map):** Mit dem Schlüssel findet man einen Wert sofort, egal wie viele Werte gespeichert sind.
- **Array:** Wenn man die Position (Index) kennt, hat man den Wert sofort.
- **Nicht gut:** Eine verkettete Liste, weil man sie von vorne bis zum gesuchten Wert durchgehen muss.

### Fragestellung 3 – Zahlen sortieren

- **Array:** Beim Sortieren (z. B. Bubble Sort oder Quicksort) muss man Zahlen an bestimmten Positionen tauschen. Das geht im Array am einfachsten.
- Eine verkettete Liste geht auch, ist aber langsamer, weil man nicht direkt zu einer Position springen kann.

### Fragestellung 4 – Modulanmeldung an der Uni

- **Queue (Warteschlange, FIFO = First In, First Out):** Wer zuerst kommt, ist zuerst dran. Neue Anfragen kommen hinten dazu, vorne wird eine nach der anderen bearbeitet. So wird der Server nicht überlastet. Genau so wurde das Problem auch gelöst.