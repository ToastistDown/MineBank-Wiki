# ⌨️ Befehle

Hier findest du die vollständige Befehlsübersicht für **MineBank 1.0.3**.

!!! info "Platzhalter"
    Angaben in `<...>` sind Platzhalter.

    Die spitzen Klammern werden **nicht** mit eingegeben.

    Beispiel:

    ```text
    /bank deposit <Betrag>
    ```

    wird beispielsweise zu:

    ```text
    /bank deposit 500
    ```

---

## ⚠️ Allgemeine Hinweise

Die meisten MineBank-Befehle benötigen einen Spieler als Ausführenden.

Einen allgemein registrierten:

```text
/bank help
```

Befehl gibt es in MineBank 1.0.3 nicht.

---

# 👤 Privatkonto

## Konto erstellen

```text
/bank account create
```

Stellt das eigene Privatkonto bereit.

---

## 💶 Kontostand anzeigen

```text
/bank balance
```

Zeigt den eigenen Kontostand an.

---

## 🏦 Kontonummer und IBAN

```text
/bank iban
```

Zeigt die eigene:

- Kontonummer
- IBAN

an.

---

## 📥 Bargeld einzahlen

```text
/bank deposit <Betrag>
```

Zahlt passendes Bargeld aus dem Spielerinventar auf das Privatkonto ein.

Beispiel:

```text
/bank deposit 500
```

---

## 📤 Bargeld auszahlen

```text
/bank withdraw <Betrag>
```

Zahlt Privatguthaben als physisches Bargeld aus.

!!! info "Kein ATM-Bestand"
    Bei diesem Befehl ist kein Bargeldbestand eines Bankautomaten beteiligt.

---

# 💸 Überweisungen

## An einen Spieler

```text
/bank transfer player <Spielername> <Betrag>
```

Beispiel:

```text
/bank transfer player FrostyToast 250
```

Das Ziel benötigt ein vorhandenes Spielerkonto.

---

## Über IBAN oder Kontonummer

```text
/bank transfer iban <IBAN-oder-Kontonummer> <Betrag>
```

Die Überweisung verwendet den Privat-/Systemkonto-Suchweg.

Beispiel:

```text
/bank transfer iban MC43100500000920018963 100
```

!!! warning "Firmenkonten"
    Dieser private IBAN-Befehl ist keine allgemeine Firmenzielsuche.

---

# 💳 Persönliche Bankkarte

## Karte ausstellen

```text
/bank card issue
```

Stellt eine aktivierte persönliche Bankkarte aus.

---

## Karteninformationen

```text
/bank card info
```

Zeigt Informationen zur persönlichen Bankkarte in der **Haupthand** an.

---

# 🔄 Private Daueraufträge

## Dauerauftrag erstellen

```text
/bank dauerauftrag add <Ziel> <Betrag> <Intervall> <Grund>
```

---

## Daueraufträge anzeigen

```text
/bank dauerauftrag list
```

Zeigt die eigenen Daueraufträge an.

---

## Dauerauftrag entfernen

```text
/bank dauerauftrag remove <ID>
```

Entfernt einen eigenen Dauerauftrag anhand seiner ID.

➡️ [Mehr über Daueraufträge](dauerauftraege.md)

---

# 🏢 Firmen

## Firma gründen

```text
/bank business create <Firmenname>
```

Gründet eine Firma direkt und kostenpflichtig.

Beispiel:

```text
/bank business create Meine Firma
```

Bei diesem Befehl steht der Firmenname am Ende und darf ohne Anführungszeichen Leerzeichen enthalten.

---

## ℹ️ Firmeninformationen

```text
/bank business info <Firma>
```

Zeigt unter anderem:

- Firma
- Kontonummer
- IBAN
- Guthaben

an.

!!! warning "Aktueller Stand"
    `business info` prüft aktuell keine Mitgliedschaft.

    Die angezeigten Firmendaten einschließlich des Guthabens sind über diesen Befehl daher nicht auf Firmenmitarbeiter beschränkt.

---

## 💳 Firmenkarte ausstellen

```text
/bank business card <Firma>
```

Stellt eine Firmenkarte aus.

Der Spieler muss Mitglied der Firma oder entsprechend administrativ berechtigt sein.

---

# 👥 Firmenmitglieder

## Mitglied hinzufügen

```text
/bank business member add <Firmenkennung> <Spieler>
```

Der Zielspieler muss online sein.

Ausführen kann dies der Besitzer beziehungsweise ein entsprechend berechtigter Administrator.

---

## Mitglied entfernen

```text
/bank business member remove <Firmenkennung> <Spieler>
```

Auch hier wird ein Online-Spieler verwendet.

---

## 🔎 Firmenkennung

Eine Firmenkennung kann je nach Argument sein:

- Firmenname
- technische Konto-UUID
- zehnstellige Kontonummer

Bei:

```text
member add
member remove
```

ist die Firmenkennung jedoch ein **einzelnes Wortargument**.

Besitzt der Firmenname Leerzeichen, sollte deshalb die Kontonummer oder UUID verwendet werden.

Beispiel:

```text
/bank business member add 0045273819 FrostyToast
```

!!! note "Beispielnummer"
    `0045273819` ist hier nur eine Beispielnummer und muss durch die tatsächliche Kontonummer der Firma ersetzt werden.

---

# 🔄 Firmen-Daueraufträge

## Dauerauftrag erstellen

```text
/bank business dauerauftrag add <Firma> <Ziel> <Betrag> <Intervall> <Grund>
```

Der Spieler muss Firmenmitglied oder entsprechend administrativ berechtigt sein.

---

## Daueraufträge anzeigen

```text
/bank business dauerauftrag list <Firma>
```

---

## Dauerauftrag entfernen

```text
/bank business dauerauftrag remove <Firma> <ID>
```

---

## 📝 Firmennamen mit Leerzeichen

Bei Firmen-Daueraufträgen sollten Firmennamen mit Leerzeichen in **Anführungszeichen** angegeben werden.

Beispiel:

```text
"Meine Firma"
```

Bei:

```text
business create
business info
business card
```

steht der Firmenname dagegen am Befehlsende und kann ohne Anführungszeichen Leerzeichen enthalten.

---

# 🏛️ Staatskasse

Alle folgenden Staatskassenbefehle benötigen Minecraft-Berechtigungsstufe **2**.

## Informationen

```text
/bank treasury info
```

---

## Administrative Gutschrift

```text
/bank treasury deposit <Betrag>
```

Beispiel:

```text
/bank treasury deposit 1000
```

!!! warning "Administrative Gutschrift"
    Dieser Befehl entnimmt kein Bargeld aus dem Inventar und belastet nicht das Privatkonto des Administrators.

---

## Verwalter hinzufügen

```text
/bank treasury manager add <Spieler>
```

Der Zielspieler muss online sein.

---

## Verwalter entfernen

```text
/bank treasury manager remove <Spieler>
```

---

## Geld auszahlen

```text
/bank treasury payout <Spieler> <Betrag>
```

Zahlt Geld auf das Konto eines Online-Spielers aus.

Dieser Befehl benötigt:

**Berechtigungsstufe 2 + Staatskassen-Verwalter**

➡️ [Mehr über die Staatskasse](staatskasse.md)

---

# 🏛️ Staatskassen-Aliase

MineBank besitzt zusätzlich Staatskassen-Aliase mit identischer Bedeutung:

```text
/staatskasse info

/staatskasse deposit <Betrag>

/staatskasse manager add <Spieler>

/staatskasse manager remove <Spieler>

/staatskasse payout <Spieler> <Betrag>
```

---

# 🏦 Bankzonen

Die Bankzonenbefehle benötigen Minecraft-Berechtigungsstufe **2**.

## Position 1

```text
/bankzone pos1
```

Setzt die erste Ecke an der aktuellen Spielerposition.

---

## Position 2

```text
/bankzone pos2
```

Setzt die zweite Ecke an der aktuellen Spielerposition.

---

## Bankzone erstellen

```text
/bankzone create <Name>
```

Beispiel:

```text
/bankzone create Staatsbank
```

---

## Bankzonen anzeigen

```text
/bankzone list
```

➡️ [Mehr über Bankzonen](bank/bankzonen.md)

---

# 🏢 Firmenauszahlungen und Firmenüberweisungen

In MineBank 1.0.3 ist **kein separater Firmen-Auszahlungs- oder Firmen-Überweisungsbefehl registriert**.

Dafür werden stattdessen:

- Firmenkarte und Bankautomat
- oder die Integrations-API

verwendet.

Firmen-ATM-Überweisungen unterstützen sowohl Spieler- als auch Firmenziele.

---

# 📚 Komplette Übersicht

| Befehl | Funktion |
|---|---|
| `/bank account create` | Privatkonto bereitstellen |
| `/bank balance` | Eigenen Kontostand anzeigen |
| `/bank iban` | Kontonummer und IBAN anzeigen |
| `/bank deposit <Betrag>` | Inventarbargeld einzahlen |
| `/bank withdraw <Betrag>` | Privatguthaben als Bargeld auszahlen |
| `/bank transfer player <Spielername> <Betrag>` | An Spielerkonto überweisen |
| `/bank transfer iban <IBAN-oder-Kontonummer> <Betrag>` | Privat-/Systemkonto-Suchweg |
| `/bank card issue` | Persönliche Karte ausstellen |
| `/bank card info` | Karte in Haupthand anzeigen |
| `/bank dauerauftrag add ...` | Privaten Dauerauftrag erstellen |
| `/bank dauerauftrag list` | Private Daueraufträge anzeigen |
| `/bank dauerauftrag remove <ID>` | Dauerauftrag entfernen |
| `/bank business create <Firmenname>` | Firma gründen |
| `/bank business info <Firma>` | Firmeninformationen anzeigen |
| `/bank business card <Firma>` | Firmenkarte ausstellen |
| `/bank business member add ...` | Firmenmitglied hinzufügen |
| `/bank business member remove ...` | Firmenmitglied entfernen |
| `/bank business dauerauftrag add ...` | Firmen-Dauerauftrag erstellen |
| `/bank business dauerauftrag list ...` | Firmen-Daueraufträge anzeigen |
| `/bank business dauerauftrag remove ...` | Firmen-Dauerauftrag entfernen |
| `/bank treasury info` | Staatskasse anzeigen |
| `/bank treasury deposit <Betrag>` | Administrative Gutschrift |
| `/bank treasury manager add <Spieler>` | Verwalter hinzufügen |
| `/bank treasury manager remove <Spieler>` | Verwalter entfernen |
| `/bank treasury payout <Spieler> <Betrag>` | Staatskassenauszahlung |
| `/bankzone pos1` | Erste Zonenecke |
| `/bankzone pos2` | Zweite Zonenecke |
| `/bankzone create <Name>` | Bankzone erstellen |
| `/bankzone list` | Bankzonen anzeigen |

---

## ❓ Gibt es `/bank help`?

Nein.

In MineBank 1.0.3 ist kein allgemeiner:

```text
/bank help
```

Befehl registriert.

Nutze deshalb diese Befehlsübersicht als Referenz.

---

## ➡️ Nächster Schritt

Wenn ein Befehl, eine Bankkarte, ein ATM oder eine andere MineBank-Funktion nicht wie erwartet funktioniert, hilft die nächste Seite weiter:

**🛠️ Problemlösungen**

**Weiter: [🛠️ Problemlösungen](probleme.md)**
