# 🏛️ Staatskasse

Die **Staatskasse** ist ein dauerhaftes Systemkonto von MineBank.

Anders als ein Privat- oder Firmenkonto besitzt sie keinen normalen Spieler als Kontoinhaber.

Sie kann beispielsweise von Servern und anderen Mods für Gebühren, Bußgelder und andere staatliche Zahlungen verwendet werden.

---

## 🏦 Identität der Staatskasse

Die Staatskasse besitzt eine feste technische Identität.

| Eigenschaft | Wert |
|---|---|
| Kontonummer | `4310050000` |
| IBAN | `MC43100500000920018963` |
| Kontotyp | Systemkonto |
| Spielerbesitzer | Keiner |

Die technische UUID der Staatskasse ist ebenfalls fest definiert.

---

## 💾 Speicherung

MineBank speichert Informationen zur Staatskasse dauerhaft.

Dazu gehören:

- Kontostand
- Verwalter
- Staatskassenbuchungen

Dadurch bleibt der Zustand der Staatskasse über Serverneustarts hinweg Bestandteil der gespeicherten MineBank-Daten.

---

## 💶 Getrennter Geldbestand

Die Staatskasse besitzt einen eigenen Bestand.

Sie darf nicht mit anderen MineBank-Geldbeständen verwechselt werden.

```text
🏛️ Staatskasse
      ≠
👤 Privatkonto
      ≠
🏢 Firmenkonto
      ≠
🔐 Tresorbestand
