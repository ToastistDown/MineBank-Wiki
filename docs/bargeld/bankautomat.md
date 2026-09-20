# 🏧 Bankautomat

Der Bankautomat – kurz **ATM** – ist eine der zentralen Funktionen von MineBank.

Über ihn können Spieler ihr Privatkonto und mit einer gültigen Firmenkarte auch unterstützte Funktionen eines Firmenkontos verwenden.

Der normale Bankautomat verarbeitet dabei **Geldscheine**.

---

## 💳 Zugriff auf den Bankautomaten

Für den Zugriff auf ein Konto wird eine gültige Bankkarte benötigt.

### Privatkonto

Mit einer gültigen persönlichen Bankkarte kann der Spieler auf sein persönliches Bankkonto zugreifen.

Die Karte muss zum interagierenden Spieler gehören.

### Firmenkonto

Mit einer gültigen Firmenkarte können unterstützte Funktionen des Firmenkontos verwendet werden.

Dabei prüft MineBank zusätzlich die Mitgliedschaft beziehungsweise entsprechende Administratorrechte.

Der Besitz einer fremden Firmenkarte allein reicht nicht aus.

---

## 💶 Bargeld einzahlen

Der normale Bankautomat verarbeitet **Geldscheine aus dem Spielerinventar**.

Bei einer Einzahlung werden die vorhandenen Banknoten berücksichtigt.

Unterstützte Geldscheine:

| Schein |
|---:|
| 5 € |
| 10 € |
| 20 € |
| 50 € |
| 100 € |
| 200 € |
| 500 € |

Bei einer erfolgreichen Einzahlung passiert grundsätzlich Folgendes:

```text
Geldscheine im Inventar
        ↓
Bankautomat
        ↓
Kontoguthaben steigt
        +
ATM-Bargeldbestand steigt
