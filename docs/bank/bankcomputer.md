# 🖥️ Bankcomputer

Der **Bankcomputer** ist die zentrale Verwaltungsoberfläche einer MineBank-Bank.

Über ihn können unter anderem registrierte Bankautomaten und Informationen über den zugehörigen Tresor beziehungsweise die Bankzone eingesehen werden.

---

## 🖱️ Bankcomputer öffnen

Der Bankcomputer wird mit einem **Rechtsklick** geöffnet.

Anschließend erscheint die Verwaltungsoberfläche.

---

## 🏦 Bankzuordnung

Ein Bankcomputer kann einer bestimmten Bank zugeordnet werden.

Dafür kann das **Bank-Zuordnungstool** verwendet werden.

Voraussetzung dafür ist eine bereits eingerichtete Bankzone.

➡️ [Mehr über Bankzonen](bankzonen.md)

---

## 🔗 Bankcomputer einer Bank zuordnen

Mit dem Bank-Zuordnungstool können verschiedene MineBank-Geräte einer Bank zugewiesen werden.

Dazu gehören unter anderem:

- 🏧 Bankautomat
- 🪙 Münzeinzahlautomat
- 🖥️ Bankcomputer
- 🖨️ Kartendrucker
- 🔐 Tresor

Wird der Bankcomputer einer Bank zugeordnet, kann seine Ansicht entsprechend nach dieser Bank gefiltert werden.

---

## 🏧 ATM-Übersicht

Ein wichtiger Bestandteil des Bankcomputers ist die Übersicht über registrierte Bankautomaten.

Die ATM-Liste kann Informationen anzeigen wie:

- registriertes Gerät
- zugeordnete Bank
- aktueller Bargeldbestand
- Zielbestand
- Füllstand
- Bewegungsinformationen

Dadurch kann der Bargeldstatus der Automaten zentral eingesehen werden.

---

## 🏦 Zugeordneter Bankcomputer

Ist der Bankcomputer einer bestimmten Bank zugeordnet, wird die ATM-Anzeige nach dieser Bank gefiltert.

Dadurch können beispielsweise mehrere Banken auf demselben Server getrennt verwaltet werden.

Vereinfacht:

```text
🏦 Bank A
   │
   ├── 🖥️ Bankcomputer
   │
   ├── 🏧 ATM 1
   │
   └── 🏧 ATM 2

🏦 Bank B
   │
   ├── 🖥️ Bankcomputer
   │
   └── 🏧 ATM 3
