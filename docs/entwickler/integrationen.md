# 🔌 Integrationen

MineBank stellt eine öffentliche API bereit, über die andere Minecraft-Mods das Banksystem verwenden können.

Dadurch können beispielsweise Shops, Grundstückssysteme oder Polizeisysteme Zahlungen über MineBank abwickeln.

!!! info "Wichtig"
    Die Installation von MineBank allein verbindet externe Mods nicht automatisch mit dem Banksystem.

    Die jeweilige Mod muss die MineBank-API tatsächlich verwenden.

---

## 🧩 Vorgesehene Integrationen

In der MineBank-Dokumentation werden folgende typische Integrationen beschrieben:

| Mod | Möglicher API-Einsatz |
|---|---|
| **CityShop** | Firmenzuordnung, Mitarbeiterabfrage, Kontozahlungen und atomare Barzahlung |
| **CityRegion** | Spielerkonto-Zahlungen und Gebühren an die Staatskasse |
| **CityPolice** | Bußgelder vom Spielerkonto an die Staatskasse |

!!! warning "Keine automatische Kompatibilitätszusage"
    Diese Tabelle beschreibt die vorgesehenen beziehungsweise typischen API-Einsatzmöglichkeiten.

    Ob eine konkrete Version einer externen Mod MineBank tatsächlich verwendet, muss separat geprüft werden.

---

# 🛒 CityShop

Ein Shopsystem kann MineBank verwenden, um Zahlungen an ein Firmenkonto abzuwickeln.

Ein möglicher Ablauf sieht so aus:

```text
👤 Spieler
     ↓
🛒 Einkauf
     ↓
🏢 Shop-Firma bestimmen
     ↓
💶 Zahlung über MineBank
     ↓
🏦 Firmenkonto
```

---

## 🏢 Firma eines Spielers bestimmen

Über:

```java
BankApi.getBusinessAccountForPlayer(playerId)
```

kann eine Integration die Firmenkonto-UUID eines Besitzers oder Mitglieds ermitteln.

Wird keine passende Firma gefunden, liefert die Methode:

```java
null
```

Besitzer haben bei dieser Zuordnung Vorrang.

---

## 🔎 Weitere Firmeninformationen

Ergänzend stehen unter anderem folgende Methoden zur Verfügung:

```java
BankApi.getBusinessAccountName(businessAccountId);
```

```java
BankApi.getBusinessAccountOwner(businessAccountId);
```

```java
BankApi.isBusinessMember(businessAccountId, playerId);
```

Damit kann beispielsweise ein Shopsystem die gespeicherte Firmenkonto-UUID verwenden und aktuelle Berechtigungen erneut bei MineBank prüfen.

---

# 💳 Kontozahlung im Shop

Für eine Zahlung vom Privatkonto eines Spielers an eine Firma kann beispielsweise verwendet werden:

```java
boolean paid = BankApi.transferToBusinessEuros(
    player.getUUID(),
    businessAccountId,
    "19,99",
    TransactionSource.CITYSHOP
);
```

Anschließend sollte die aufrufende Mod den Rückgabewert prüfen.

```java
if (paid) {
    // Zahlung erfolgreich
} else {
    // Zahlung fehlgeschlagen
}
```

!!! tip "Gekoppelte Transfermethode verwenden"
    Für eine zusammengehörende Zahlung sollte die vorgesehene MineBank-Transfermethode verwendet werden.

    Nicht selbst zuerst Geld mit `withdraw` abbuchen und anschließend separat mit `deposit` gutschreiben.

---

# 💶 Barzahlung im Shop

MineBank stellt auch eine spezielle Barzahlungsfunktion für Firmen bereit.

Beispiel:

```java
CashPaymentResult result = BankApi.payBusinessWithCashEuros(
    player,
    businessAccountId,
    "19,99",
    TransactionSource.CITYSHOP,
    "Einkauf"
);
```

Diese Funktion berücksichtigt innerhalb der Bank-/Bargeldoperation unter anderem:

- Bargeldentnahme
- Wechselgeld
- Inventarplatz
- Rückrollpfad bei fehlgeschlagener Gutschrift

---

## 🔄 Beispiel

Ein Spieler kauft einen Gegenstand für **19,99 €**:

```text
🛒 Einkauf: 19,99 €
        ↓
💶 vorhandenes Bargeld prüfen
        ↓
🧮 Zahlung + Wechselgeld planen
        ↓
💵 Bargeld entnehmen
        ↓
🏢 Firmenkonto gutschreiben
        ↓
✅ Zahlung erfolgreich
```

Wenn die Gutschrift innerhalb dieser Bank-/Bargeldoperation fehlschlägt, existiert ein Rückrollpfad.

---

## ⚠️ Warenübergabe bleibt Aufgabe des Shops

MineBank wickelt dabei nicht automatisch den vollständigen Shopkauf ab.

Die aufrufende Shop-Mod ist weiterhin beispielsweise für ihre eigene Warenübergabe und Speicherung verantwortlich.

```text
MineBank
   ↓
💶 Zahlungsoperation

Shop-Mod
   ↓
📦 Warenübergabe
   ↓
💾 eigene Speicherung
```

!!! warning "Transaktion nicht mit Shoplogik verwechseln"
    Die MineBank-Barzahlung macht die gesamte Shoplogik nicht automatisch zu einer gemeinsamen Transaktion.

---

# 👛 Bargeld erkennen

Mit:

```java
BankApi.getCashValue(player)
```

kann loses Bargeld im Spielerinventar ermittelt werden.

Dabei wird auch ein vom Menücursor gehaltener Bargeldstapel berücksichtigt.

Geld innerhalb von Behältern wird jedoch nicht rekursiv durchsucht.

Das betrifft beispielsweise Bargeld, das in einem MineBank-Behälter verstaut ist.

---

# ⚠️ `takeCash` und `giveCash`

Die Methoden:

```java
BankApi.takeCash(...)
```

und:

```java
BankApi.giveCash(...)
```

sind jeweils einzelne Operationen.

Werden sie mit anderen beliebigen API-Aufrufen kombiniert, entsteht daraus nicht automatisch eine gemeinsame Gesamttransaktion.

Für passende Zahlungsfälle sollten deshalb die dafür vorgesehenen gekoppelten Methoden verwendet werden.

---

# 📝 Verwendungszweck bei Barzahlung

`payBusinessWithCash` besitzt einen Parameter:

```java
note
```

Dieser wird in der aktuellen Implementierung jedoch nicht als eigener Firmen-Buchungstext gespeichert.

!!! info "Keine vollständige Firmen-Buchhaltung ableiten"
    Aus dem `note`-Parameter sollte deshalb keine vollständige Firmen-Buchhaltung mit dauerhafter Verwendungszweckhistorie abgeleitet werden.

---

# 🗺️ CityRegion

Ein Regions- oder Grundstückssystem kann MineBank für Spielerkonto-Zahlungen und Gebühren an die Staatskasse verwenden.

Ein möglicher Ablauf:

```text
🗺️ Region / Grundstück
        ↓
💶 Gebühr
        ↓
👤 Privatkonto
        ↓
🏛️ Staatskasse
```

Für allgemeine Gebühren an die Staatskasse stehen beispielsweise die dafür vorgesehenen `collectToStateTreasury`-Methoden zur Verfügung.

Beispiel:

```java
boolean success = BankApi.collectToStateTreasuryEuros(
    playerId,
    "250",
    source,
    note
);
```

---

# 🚓 CityPolice

Ein Polizeisystem kann MineBank verwenden, um Bußgelder von einem Spielerkonto einzuziehen und an die Staatskasse zu übertragen.

Dafür besitzt die API spezielle Methoden.

Beispiel:

```java
boolean success = BankApi.collectCityPoliceFineEuros(
    playerId,
    "250",
    "Bußgeld"
);
```

Vereinfacht:

```text
🚓 Bußgeld
    ↓
👤 Spielerkonto
    ↓
💸 250 €
    ↓
🏛️ Staatskasse
```

---

# 🏛️ Staatskasse für Integrationen

Für allgemeine Gebühren kann eine Integration verwenden:

```java
BankApi.collectToStateTreasury(...)
```

beziehungsweise:

```java
BankApi.collectToStateTreasuryEuros(...)
```

Dadurch kann eine Mod eine Zahlung vom Spielerkonto zur Staatskasse abwickeln.

➡️ [Mehr über die Staatskasse](../staatskasse.md)

---

# 📤 Auszahlungen aus der Staatskasse

Für allgemeine Auszahlungen existiert außerdem:

```java
BankApi.payFromStateTreasury(...)
```

beziehungsweise:

```java
BankApi.payFromStateTreasuryEuros(...)
```

!!! danger "Berechtigungen selbst prüfen"
    `payFromStateTreasury` besitzt keinen Verwalterparameter.

    Eine aufrufende Mod muss deshalb ihre eigene Berechtigungsprüfung durchführen.

---

# 🏢 Firmen über eine Integration erstellen

Eine externe Mod kann technisch ein Firmenkonto über:

```java
BankApi.createBusinessAccount(...)
```

erzeugen.

Dabei ist jedoch ein wichtiger Unterschied zum normalen MineBank-Spielerablauf zu beachten.

Die normale **20.000-€-Gründungsgebühr** wird im Spieler-Gründungsservice erhoben.

Ein direkter Aufruf von:

```java
createBusinessAccount(...)
```

erhebt diese Gebühr nicht automatisch in jedem Fall.

!!! warning "Eigener Gründungsablauf"
    Eine Integration, die Firmen selbst erstellt, muss ihren gewünschten Gründungsablauf und mögliche Gebühren entsprechend selbst abstimmen.

---

# 💰 Kreditintegrationen

Auch persönliche Kredite sind über die MineBank-API erreichbar.

Dabei gibt es aktuell jedoch eine technische Besonderheit:

Die API-Kreditaufnahme verwendet einen Überladungsweg mit:

```text
Starttag 0
```

Dieser Ablauf entspricht deshalb nicht zwingend exakt dem relativen Erstfälligkeitstermin des normalen NPC-Ablaufs.

!!! warning "Vor Integration berücksichtigen"
    Externe Mods sollten keine identische relative Erstfälligkeit zum NPC-Kreditablauf versprechen, ohne diese Abweichung zu berücksichtigen.

---

# 📡 Events für andere Mods

Integrationen können einen:

```java
BankEventListener
```

registrieren.

```java
BankApi.registerListener(listener);
```

und wieder entfernen:

```java
BankApi.unregisterListener(listener);
```

Ein `BankTransactionEvent` stellt Informationen zur jeweiligen Transaktion bereit.

Dazu gehören:

- Konto-ID
- Betrag
- alter Kontostand
- neuer Kontostand
- Typ
- Quelle
- Gegenkonto
- Transaktions-ID
- Zeitstempel

---

## ⚠️ Events sind keine vollständige Transaktionshistorie

Das Beobachten von Events bedeutet nicht automatisch, dass dadurch eine dauerhaft gespeicherte vollständige Historie sämtlicher Kontotransaktionen entsteht.

Eine Integration, die eine eigene langfristige Historie benötigt, muss ihre eigene Speicherung entsprechend planen.

---

# ↩️ Rückgabewerte

Integrationen sollten API-Rückgabewerte immer auswerten.

Besonders wichtig:

| Rückgabe | Bedeutung |
|---|---|
| `boolean` | Erfolg oder Fehlschlag prüfen |
| `createBusinessAccount(...)` | Kann `null` liefern |
| Kreditrückzahlung | Liefert tatsächlich gezahlten Centbetrag |
| `CashPaymentResult` | Enthält Erfolgsstatus sowie Zahlungs-/Wechselgeldwerte |

Beispiel:

```java
boolean paid = BankApi.transferToBusinessEuros(
    player.getUUID(),
    businessAccountId,
    "19,99",
    TransactionSource.CITYSHOP
);

if (!paid) {
    // Kauf nicht abschließen
}
```

---

# 🔐 Sicherheit und Berechtigungen

Die MineBank-API ist für vertrauenswürdige Servermods vorgesehen.

Die aufrufende Mod muss selbst prüfen, ob ein Spieler eine bestimmte Aktion überhaupt durchführen darf.

Das betrifft beispielsweise:

```text
👤 Spieler
    ↓
🔐 Berechtigung der externen Mod prüfen
    ↓
🏦 MineBank API aufrufen
```

Technische API-Verfügbarkeit bedeutet nicht automatisch, dass jeder Spieler die entsprechende Aktion ausführen dürfen sollte.

---

# 🧵 Serverthread

API-Aufrufe mit:

- Inventarmutationen
- Kontomutationen

sollten auf dem Serverthread ausgeführt werden.

---

# 🔌 Integrationsübersicht

```text
                  🏦 MineBank
                      │
          ┌───────────┼───────────┐
          │           │           │
          ↓           ↓           ↓
      🛒 Shop      🗺️ Region    🚓 Polizei
          │           │           │
          ↓           ↓           ↓
     Firmenkonto    Gebühren    Bußgelder
          │           │           │
          └───────────┴─────→ 🏛️ Staatskasse
```

MineBank stellt dabei die Bankfunktionen bereit.

Die jeweilige externe Mod bleibt für ihre eigene Spiellogik, Berechtigungen und Speicherung verantwortlich.

---

## 📚 Weitere Entwicklerdokumentation

Die vollständigen öffentlichen Methoden findest du auf der API-Seite:

➡️ [MineBank API](api.md)

Für Spieler- und Serverfunktionen:

➡️ [Befehle](../befehle.md)

➡️ [Problemlösungen](../probleme.md)

---

## ✅ Stand MineBank 1.0.3

Diese Seite beschreibt die Integrationsmöglichkeiten des dokumentierten Stands von **MineBank 1.0.3**.

Sie stellt keine Zusage dar, dass externe Mods wie CityShop, CityRegion oder CityPolice bereits automatisch mit MineBank verbunden sind.

Eine tatsächliche Integration muss die MineBank-API verwenden.
