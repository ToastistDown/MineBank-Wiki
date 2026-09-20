# 🏦 Privatkonto

Das Privatkonto ist das persönliche Bankkonto eines Spielers in **MineBank**.

Es bildet die Grundlage für viele Funktionen der Mod. Darüber werden unter anderem digitales Guthaben, Überweisungen, Bankkarten, Kredite und Daueraufträge verwaltet.

---

## 💳 Was gehört zu einem Privatkonto?

Ein MineBank-Privatkonto besitzt unter anderem:

- einen Kontoinhaber
- einen Kontostand
- eine Kontonummer
- eine IBAN
- eine Kartenversion
- Informationen zu Krediten
- Daueraufträge

Das Konto ist einem bestimmten Minecraft-Spieler zugeordnet.

---

## 🔢 Kontonummer

Jedes Konto besitzt eine eigene Kontonummer.

Die Kontonummer kann verwendet werden, um das Konto eindeutig innerhalb von MineBank zu identifizieren.

Sie wird beispielsweise bei Bankfunktionen und Überweisungen verwendet.

---

## 🌍 IBAN

Zusätzlich zur Kontonummer besitzt das Konto eine eigene IBAN.

Damit können Zahlungen innerhalb des MineBank-Systems einem bestimmten Konto zugeordnet werden.

Kontonummer und IBAN gehören fest zum jeweiligen Konto.

---

## 💶 Kontostand

Auf dem Privatkonto wird das digitale Guthaben des Spielers gespeichert.

Das Guthaben kann sich beispielsweise durch folgende Aktionen verändern:

- Bargeld einzahlen
- Bargeld abheben
- Überweisungen senden
- Überweisungen empfangen
- Kredite
- Daueraufträge

!!! info "Digitales Guthaben und Bargeld"
    Das Guthaben auf deinem Konto ist nicht dasselbe wie physisches Bargeld in deinem Inventar.

    Bargeld muss über entsprechende MineBank-Funktionen ein- oder ausgezahlt werden.

---

## 🏧 Zugriff über Bankautomaten

Mit einer gültigen Bankkarte kann das Privatkonto über einen MineBank-Bankautomaten verwendet werden.

Je nach verfügbarer Funktion können dort beispielsweise:

- Kontoinformationen angezeigt
- Bargeld eingezahlt
- Bargeld ausgezahlt
- Überweisungen durchgeführt

werden.

➡️ [Mehr über Bankautomaten](../bargeld/bankautomat.md)

---

## 💳 Bankkarte

Die persönliche Bankkarte ist mit deinem Konto verbunden.

Sie ermöglicht den Zugriff auf verschiedene Bankfunktionen.

Die Karte enthält beziehungsweise verwendet Informationen, mit denen MineBank das zugehörige Konto erkennen kann.

➡️ [Mehr über die Bankkarte](bankkarte.md)

---

## 💸 Überweisungen

Geld kann zwischen MineBank-Konten übertragen werden.

Dadurch ist es nicht notwendig, einem anderen Spieler physisches Bargeld zu übergeben.

Bei einer Überweisung wird das Guthaben entsprechend zwischen den beteiligten Konten verschoben.

---

## 🔄 Daueraufträge

Mit einem Dauerauftrag können wiederkehrende Zahlungen eingerichtet werden.

Dadurch können Zahlungen automatisch ausgeführt werden, ohne dass der Spieler jede Überweisung einzeln durchführen muss.

➡️ [Mehr über Daueraufträge](../dauerauftraege.md)

---

## 💰 Kredite

Das Privatkonto ist außerdem mit dem Kreditsystem von MineBank verbunden.

Aufgenommene Kredite und deren Rückzahlung werden über das Banksystem verwaltet.

➡️ [Mehr über Kredite](../kredite.md)

---

## 🏢 Privatkonto und Firmenkonto

MineBank unterscheidet zwischen persönlichen und geschäftlichen Konten.

| Privatkonto | Firmenkonto |
|---|---|
| Gehört einem Spieler | Gehört einer Firma |
| Persönliches Guthaben | Eigenes Firmenguthaben |
| Eigene Kontonummer | Eigene Firmen-Kontonummer |
| Eigene IBAN | Eigene Firmen-IBAN |
| Persönliche Bankkarte | Firmenkarte möglich |

Dadurch bleiben private und geschäftliche Finanzen voneinander getrennt.

➡️ [Mehr über Firmenkonten](firmenkonto.md)

---

## 💾 Speicherung

Die Kontodaten werden server- beziehungsweise weltseitig über Minecraft **SavedData** gespeichert.

Die zentrale MineBank-Datendatei befindet sich üblicherweise unter:

```text
<Weltordner>/data/bankmod_accounts.dat
