# 🏢 Firmenkonto

Mit einem Firmenkonto können Unternehmen in **MineBank** ihre Finanzen getrennt von den privaten Konten ihrer Spieler verwalten.

Eine Firma besitzt ein eigenes Bankkonto mit eigenem Guthaben, eigener Kontonummer und eigener IBAN.

---

## 🏦 Was besitzt eine Firma?

Eine MineBank-Firma besitzt unter anderem:

- einen Firmennamen
- einen Besitzer
- Mitglieder
- eine dauerhaft gespeicherte Konto-UUID
- eine eigene Kontonummer
- eine eigene IBAN
- einen eigenen Kontostand

Das Firmenvermögen ist damit vom Privatkonto des Firmenbesitzers getrennt.

---

## 🏗️ Firma gründen

Ein Spieler kann ein eigenes Firmenkonto gründen.

Dabei gelten einige Voraussetzungen.

### Gründungsgebühr

Die Gründung kostet einmalig:

**20.000 €**

Das Geld wird vom **Privatkonto des Gründers** abgezogen.

Es reicht deshalb nicht aus, 20.000 € als Bargeld im Inventar zu besitzen.

Die Gründungsgebühr wird anschließend der **Staatskasse** gutgeschrieben.

!!! warning "20.000 € auf dem Privatkonto erforderlich"
    Die Gründungsgebühr wird direkt vom Privatkonto bezahlt.

    Bargeld im Inventar zählt für die Firmengründung nicht.

---

## 👤 Ein Firmenkonto pro Besitzer

Ein Spieler darf ein Firmenkonto besitzen.

Dadurch kann ein Spieler nicht beliebig viele eigene Firmenkonten als Besitzer erstellen.

---

## 🏷️ Firmenname

Für die Gründung ist ein Firmenname erforderlich.

Bereits vorhandene Firmennamen werden von MineBank blockiert.

Bei der Prüfung normalisiert MineBank unter anderem:

- Groß- und Kleinschreibung
- überzählige Leerzeichen

Dadurch sollen Firmen nicht mehrfach unter praktisch identischen Namen erstellt werden.

### Beispiel

Wenn bereits eine entsprechende Firma existiert, sollen unterschiedliche Schreibweisen nicht einfach zur Umgehung der Namensprüfung verwendet werden können.

---

## 🔢 Eigene Kontonummer und IBAN

Das Firmenkonto erhält eine eigene:

- Kontonummer
- IBAN

Diese gehören zum Firmenkonto und nicht zum privaten Konto des Firmenbesitzers.

Dadurch können Zahlungen eindeutig dem Unternehmen zugeordnet werden.

---

## 💶 Eigenes Firmenguthaben

Eine Firma besitzt einen eigenen Kontostand.

Das bedeutet:

```text
Privatkonto des Spielers
        ≠
Firmenkonto
