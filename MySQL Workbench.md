## MySQL Workbench

### Installation

- Workbench von dev.mysql.com/downloads/workbench heruntergeladen (Windows, ohne MySQL-Server).
- Nach dem Start: **File → New Model**, dann **Add Diagram**.

### Tabellen erstellen

- Mit **Place a New Table** eine Tabelle ins Diagramm setzen. Mit Doppelklick öffnet sich der Editor.
- Spalten eintragen: Name, Datentyp (z. B. INT, VARCHAR(45), DATE) und Eigenschaften:
  - **PK** = Primärschlüssel
  - **NN** = darf nicht leer sein (Not Null)
  - **UQ** = jeder Wert darf nur einmal vorkommen (Unique)
  - **AI** = Zahl zählt automatisch hoch (Auto Increment)

### Beziehungen

- **1:m:** Werkzeug **1:n Non-Identifying Relationship**. Zuerst die m-Tabelle anklicken, dann die 1-Tabelle. Workbench setzt den Fremdschlüssel automatisch in die m-Tabelle.
- **m:m:** Werkzeug **n:m Relationship**. Workbench erstellt automatisch eine Zwischentabelle. Die beiden Fremdschlüssel bilden zusammen ihren Primärschlüssel.
- **Gelernt:** Workbench löst m:m selbst auf. In draw.io geht das nicht, dort muss man die Zwischentabelle selbst zeichnen.