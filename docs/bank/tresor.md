# 🔐 Tresor

Der **Tresor** ist der zentrale Bargeldspeicher einer MineBank-Bank.

Er gehört zu einer Bankzone und kann für die Lagerung beziehungsweise den Transport größerer Bargeldbestände verwendet werden.

Der Geldkoffer dient dabei als Transportmittel für Bargeld zwischen Tresor und anderen Bereichen des Banksystems.

---

## 🏦 Bankzuordnung

Ein Tresor benötigt eine Zuordnung zu einer Bank.

Diese Zuordnung kann über:

- eine Bankzone
- das Bank-Zuordnungstool

erfolgen.

Ohne entsprechende Bankzuordnung kann der Tresor nicht korrekt dem Bestand einer bestimmten Bank zugeordnet werden.

➡️ [Mehr über Bankzonen](bankzonen.md)

---

## 💶 Bestand des Tresors

Der Bargeldbestand eines Tresors gehört zur entsprechenden **Bankzone**.

Dadurch kann MineBank den Bargeldbestand einer bestimmten Bank zuordnen.

Vereinfacht:

```text
🏦 Bankzone
    │
    └── 🔐 Tresor
            │
            └── 💶 Bankbestand
