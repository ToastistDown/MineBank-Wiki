# 🪙 Münzeinzahlautomat

Der Münzeinzahlautomat ergänzt den normalen Bankautomaten von **MineBank**.

Während der normale ATM Geldscheine verarbeitet, ist der Münzeinzahlautomat für **Münzen** vorgesehen.

---

## 🏦 Wofür ist der Münzeinzahlautomat gedacht?

Mit dem Münzeinzahlautomaten können Münzen für das persönliche Bankkonto verarbeitet werden.

Damit sind Geldscheine und Münzen in MineBank auf zwei unterschiedliche Automaten aufgeteilt:

| Automat | Bargeld |
|---|---|
| 🏧 Bankautomat | Geldscheine |
| 🪙 Münzeinzahlautomat | Münzen |

---

## 🪙 Unterstützte Münzen

MineBank besitzt Euro- und Centmünzen.

### Euromünzen

| Münze | Wert |
|---|---:|
| 1 € | 1,00 € |
| 2 € | 2,00 € |

### Centmünzen

| Münze | Wert |
|---|---:|
| 1 Cent | 0,01 € |
| 2 Cent | 0,02 € |
| 5 Cent | 0,05 € |
| 10 Cent | 0,10 € |
| 20 Cent | 0,20 € |
| 50 Cent | 0,50 € |

Damit können auch Geldbeträge unter einem Euro als physisches Bargeld dargestellt werden.

---

## 💶 Geldscheine gehören zum normalen ATM

Der Münzeinzahlautomat ist nicht für die normalen MineBank-Geldscheine gedacht.

Folgende Scheine werden über den normalen Bankautomaten verarbeitet:

- 5 €
- 10 €
- 20 €
- 50 €
- 100 €
- 200 €
- 500 €

➡️ [Mehr über den Bankautomaten](bankautomat.md)

---

## 👤 Persönliches Konto

Der separate Münzeinzahlautomat ist für das **persönliche Konto** dokumentiert.

Damit unterscheidet er sich vom normalen Bankautomaten, der auch unterstützte Firmenkonto-Funktionen besitzt.

!!! warning "Firmenkarten"
    Eine fertige Firmenkartenunterstützung für den separaten Münzeinzahlautomaten ist im aktuellen Stand von MineBank nicht dokumentiert.

    Die Wiki beschreibt sie deshalb nicht als verfügbare Funktion.

---

## 👛 Münzen im Portemonnaie

Das MineBank-Portemonnaie kann zur Aufbewahrung von Bargeld verwendet werden.

Automatische Bargeldabfragen durchsuchen Taschen und Koffer allerdings nicht rekursiv.

Wenn eine Funktion Münzen aus dem normalen Spielerinventar erwartet, müssen die benötigten Münzen deshalb zunächst aus dem Portemonnaie genommen werden.

➡️ [Mehr über das Portemonnaie](portemonnaie.md)

---

## 💰 Geldwerte mit Cent

Durch die verschiedenen Centmünzen können kleinere Beträge dargestellt werden.

Beispiel:

```text
2 € + 50 Cent + 20 Cent + 5 Cent
= 2,75 €
