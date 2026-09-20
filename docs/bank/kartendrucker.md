# 🖨️ Kartendrucker

Der **Kartendrucker** ist ein Bestandteil des MineBank-Banksystems.

Im Code von MineBank existiert bereits ein Druckablauf, bei dem ein Bankmitarbeiter eine leere Karte zu einem Kartendrucker bringt, die Karte dort verarbeitet wird und der Mitarbeiter anschließend zurückkehrt.

In **MineBank 1.0.3** muss allerdings zwischen dieser vorhandenen Druckroutine und dem aktuell verwendeten Bankmitarbeiter-Menü unterschieden werden.

---

## ⚠️ Aktueller Stand

Der aktuelle normale Kartenmenüweg des Bankmitarbeiters stellt Bankkarten **direkt aus**.

Der Kartendrucker wird dabei momentan nicht automatisch als verpflichtender Zwischenschritt verwendet.

!!! info "MineBank 1.0.3"
    Für eine normale Bankkartenbeantragung über das aktuelle Rechtsklick-Menü des Bankmitarbeiters ist der vorhandene Kartendrucker-Ablauf derzeit nicht automatisch angebunden.

---

## 🧪 Vorhandene Druckroutine

Im MineBank-Code existiert bereits ein älterer beziehungsweise vorbereiteter Druckablauf.

Dieser sieht grundsätzlich so aus:

```text
👨‍💼 Bankmitarbeiter
        ↓
💳 leere Karte
        ↓
🚶 Weg zum Kartendrucker
        ↓
🖨️ Karte wird gedruckt
        ↓
⏱️ 20 Sekunden
        ↓
🚶 Bankmitarbeiter kehrt zurück
