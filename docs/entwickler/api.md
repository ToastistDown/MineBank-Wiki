# 👨‍💻 MineBank API

MineBank stellt eine öffentliche Java-API bereit, über die andere Minecraft-Mods auf Konten, Firmenkonten, Bargeld, Kredite und die Staatskasse zugreifen können.

Der öffentliche Einstiegspunkt lautet:

```java
de.codex.bankmod.BankApi
```

---

## ⚙️ Grundregeln

Bei der Verwendung der API gibt es einige wichtige Regeln.

### 💶 Cent oder Euro?

Methoden **ohne `Euros` im Namen** verwenden Beträge in **Cent**.

Beispiel:

```java
BankApi.deposit(playerId, 1999);
```

entspricht:

```text
19,99 €
```

Methoden mit:

```text
Euros
```

im Namen nehmen dagegen einen String entgegen.

Beispiel:

```java
BankApi.depositEuros(playerId, "19,99");
```

---

## 🆔 UUIDs richtig verwenden

Spieler- und Firmenkonten verwenden unterschiedliche IDs.

```text
👤 Spielerkonto
→ Spieler-UUID

🏢 Firmenkonto
→ Firmenkonto-UUID
```

!!! warning "Nicht verwechseln"
    Funktionen für Spielerkonten erwarten die **Spieler-UUID**.

    Funktionen für Firmenkonten erwarten die **UUID des Firmenkontos**.

---

## 🧵 Serverthread

API-Aufrufe, die Inventare oder Konten verändern, sollten auf dem **Serverthread** ausgeführt werden.

Die API ist für vertrauenswürdige Servermods vorgesehen.

Aufrufende Mods müssen ihre eigenen Berechtigungen und fachlichen Voraussetzungen prüfen.

---

# 👤 Privatkonten

## Konto vorhanden?

```java
boolean exists = BankApi.accountExists(playerId);
```

---

## Kontostand abrufen

```java
long balance = BankApi.getBalance(playerId);
```

Der Rückgabewert ist ein Centbetrag.

---

## Guthaben prüfen

```java
boolean enough = BankApi.hasBalance(
    playerId,
    5000
);
```

Euro-Variante:

```java
boolean enough = BankApi.hasBalanceEuros(
    playerId,
    "50,00"
);
```

---

## 📥 Geld gutschreiben

```java
boolean success = BankApi.deposit(
    playerId,
    5000
);
```

Mit Quelle:

```java
boolean success = BankApi.deposit(
    playerId,
    5000,
    source
);
```

Euro-Variante:

```java
boolean success = BankApi.depositEuros(
    playerId,
    "50,00",
    source
);
```

---

## 📤 Geld abbuchen

```java
boolean success = BankApi.withdraw(
    playerId,
    5000
);
```

Euro-Variante:

```java
boolean success = BankApi.withdrawEuros(
    playerId,
    "50,00",
    source
);
```

---

# 💸 Spielerüberweisungen

Für Überweisungen zwischen Spielerkonten stehen gekoppelte Transfermethoden zur Verfügung.

```java
boolean success = BankApi.transfer(
    fromPlayerId,
    toPlayerId,
    1999,
    source
);
```

Euro-Variante:

```java
boolean success = BankApi.transferEuros(
    fromPlayerId,
    toPlayerId,
    "19,99",
    source
);
```

!!! tip "Transfermethoden verwenden"
    Für zusammengehörende Überweisungen sollten die vorgesehenen Transfermethoden verwendet werden, statt selbst zuerst `withdraw` und anschließend `deposit` aufzurufen.

---

# 💰 Kredite

Die API kann persönliche Kredite abrufen, aufnehmen und zurückzahlen.

## Kredite abrufen

```java
List<PersonalLoan> loans =
    BankApi.getPersonalLoans(playerId);
```

---

## Offene Kredite zählen

```java
int count =
    BankApi.getOpenPersonalLoanCount(playerId);
```

---

## Kredit aufnehmen

```java
boolean success =
    BankApi.takePersonalLoan(
        playerId,
        amountCents
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.takePersonalLoanEuros(
        playerId,
        "5000"
    );
```

!!! warning "Abweichung zum NPC"
    Die API-Kreditaufnahme verwendet aktuell einen Überladungsweg mit **Starttag 0**.

    Entwickler sollten deshalb nicht automatisch davon ausgehen, dass die relative Erstfälligkeit exakt dem normalen NPC-Kreditablauf entspricht.

---

## Kredit zurückzahlen

```java
long paid =
    BankApi.repayPersonalLoan(
        playerId,
        amountCents
    );
```

Euro-Variante:

```java
long paid =
    BankApi.repayPersonalLoanEuros(
        playerId,
        "500"
    );
```

Der Rückgabewert beschreibt den tatsächlich gezahlten Betrag.

---

# 🏢 Firmenkonten

## Firma erstellen

```java
UUID accountId =
    BankApi.createBusinessAccount(
        owner,
        companyName
    );
```

Alternativ kann eine Konto-ID mitgegeben werden:

```java
UUID accountId =
    BankApi.createBusinessAccount(
        accountId,
        owner,
        companyName
    );
```

!!! warning "20.000-€-Gründungsgebühr"
    `createBusinessAccount` ist ein technischer Kontoerzeuger.

    Die 20.000-€-Gründungsgebühr des normalen Spielerablaufs wird **nicht automatisch durch jeden direkten API-Aufruf** von `createBusinessAccount` erhoben.

    Integrationen müssen ihren gewünschten Gründungsablauf selbst entsprechend abstimmen.

---

## Firmenkonto vorhanden?

```java
boolean exists =
    BankApi.businessAccountExists(accountId);
```

---

## Firmenguthaben

```java
long balance =
    BankApi.getBusinessBalance(accountId);
```

---

# 🔎 Firma eines Spielers finden

```java
UUID businessAccountId =
    BankApi.getBusinessAccountForPlayer(
        playerId
    );
```

Die Methode liefert die Firmenkonto-UUID eines Besitzers oder Mitglieds.

Wird keine Firma gefunden, lautet das Ergebnis:

```java
null
```

Besitzer haben bei der Zuordnung Vorrang.

---

## Firmeninformationen

Firmenname:

```java
String name =
    BankApi.getBusinessAccountName(
        businessAccountId
    );
```

Besitzer:

```java
UUID owner =
    BankApi.getBusinessAccountOwner(
        businessAccountId
    );
```

Mitgliedschaft prüfen:

```java
boolean member =
    BankApi.isBusinessMember(
        businessAccountId,
        playerId
    );
```

---

# 👥 Firmenmitglieder verwalten

Mitglied hinzufügen:

```java
boolean success =
    BankApi.addBusinessMember(
        accountId,
        playerId
    );
```

Mitglied entfernen:

```java
boolean success =
    BankApi.removeBusinessMember(
        accountId,
        playerId
    );
```

Besitzer ändern:

```java
boolean success =
    BankApi.changeBusinessOwner(
        accountId,
        newOwner
    );
```

---

# 🏢 Firmenguthaben verändern

Einzahlung:

```java
boolean success =
    BankApi.depositBusiness(
        accountId,
        amountCents,
        source
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.depositBusinessEuros(
        accountId,
        "19,99",
        source
    );
```

Auszahlung:

```java
boolean success =
    BankApi.withdrawBusiness(
        accountId,
        amountCents,
        source
    );
```

---

# 💸 Zahlungen an Firmen

Ein Spieler kann über die API Geld an ein Firmenkonto übertragen.

```java
boolean paid =
    BankApi.transferToBusinessEuros(
        player.getUUID(),
        businessAccountId,
        "19,99",
        TransactionSource.CITYSHOP
    );
```

Damit eignet sich MineBank beispielsweise für Shopsysteme.

---

# 🏢 → 👤 Firmenzahlung an Spieler

```java
boolean success =
    BankApi.transferFromBusiness(
        businessAccountId,
        playerId,
        amountCents,
        source
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.transferFromBusinessEuros(
        businessAccountId,
        playerId,
        "19,99",
        source
    );
```

---

# 🏢 → 🏢 Firmenüberweisung

Auch Überweisungen zwischen zwei Firmenkonten werden unterstützt.

```java
boolean success =
    BankApi.transferBusinessToBusiness(
        fromAccountId,
        toAccountId,
        amountCents,
        source
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.transferBusinessToBusinessEuros(
        fromAccountId,
        toAccountId,
        "19,99",
        source
    );
```

---

# 💶 Bargeld-API

## Bargeldwert ermitteln

```java
long cash =
    BankApi.getCashValue(player);
```

`getCashValue` zählt loses Bargeld im Spielerinventar.

Auch ein vom Menücursor gehaltener Bargeldstapel wird berücksichtigt.

!!! warning "Keine rekursive Suche"
    Bargeld innerhalb von Portemonnaies oder anderen Behältern wird nicht rekursiv mitgezählt.

---

## Bargeld nehmen

```java
boolean success =
    BankApi.takeCash(
        player,
        amountCents
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.takeCashEuros(
        player,
        "19,99"
    );
```

---

## Bargeld geben

```java
boolean success =
    BankApi.giveCash(
        player,
        amountCents
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.giveCashEuros(
        player,
        "19,99"
    );
```

!!! warning "Keine automatische Gesamttransaktion"
    `takeCash` und `giveCash` sind einzelne Operationen.

    Mehrere beliebig kombinierte API-Aufrufe bilden nicht automatisch eine gemeinsame atomare Gesamttransaktion.

---

# 🛒 Barzahlung an eine Firma

MineBank besitzt eine speziell dafür vorgesehene Barzahlungsfunktion.

```java
CashPaymentResult result =
    BankApi.payBusinessWithCashEuros(
        player,
        businessAccountId,
        "19,99",
        TransactionSource.CITYSHOP,
        "Einkauf"
    );
```

Die Barzahlung plant unter anderem:

- Bargeldentnahme
- Wechselgeld
- notwendigen Inventarplatz

Außerdem besitzt die Bank-/Bargeldoperation einen Rückrollpfad, falls die Gutschrift fehlschlägt.

!!! warning "Warenübergabe gehört nicht dazu"
    Die MineBank-Operation umfasst nicht automatisch die Warenübergabe oder die Speicherung der aufrufenden Shop-Mod.

    Diese Logik bleibt Aufgabe der integrierenden Mod.

---

## 📝 Parameter `note`

Der Parameter:

```java
note
```

von `payBusinessWithCash` wird in der aktuellen Implementierung nicht als eigener Firmen-Buchungstext gespeichert.

Aus dieser Signatur sollte deshalb keine vollständige Firmen-Buchhaltung mit Verwendungszweckhistorie abgeleitet werden.

---

# 🏛️ Staatskassen-API

## Besitzer-ID

```java
UUID treasuryId =
    BankApi.getStateTreasuryOwnerId();
```

---

## IBAN

```java
String iban =
    BankApi.getStateTreasuryIban();
```

---

## Kontostand

```java
long balance =
    BankApi.getStateTreasuryBalance();
```

---

## Buchungen

```java
List<StateTreasuryBooking> bookings =
    BankApi.getStateTreasuryBookings();
```

---

# 🚓 Bußgelder

Für CityPolice-artige Integrationen existieren spezielle Methoden.

```java
boolean success =
    BankApi.collectCityPoliceFine(
        playerId,
        amountCents
    );
```

Mit Notiz:

```java
boolean success =
    BankApi.collectCityPoliceFine(
        playerId,
        amountCents,
        note
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.collectCityPoliceFineEuros(
        playerId,
        "250",
        note
    );
```

---

# 🏛️ Allgemeine Gebühren

Für allgemeine Gebühren kann Geld vom Spielerkonto an die Staatskasse übertragen werden.

```java
boolean success =
    BankApi.collectToStateTreasury(
        playerId,
        amountCents,
        source,
        note
    );
```

Euro-Variante:

```java
boolean success =
    BankApi.collectToStateTreasuryEuros(
        playerId,
        "250",
        source,
        note
    );
```

---

# 📥 Administrative Staatskassen-Gutschrift

```java
boolean success =
    BankApi.depositToStateTreasury(
        actorId,
        amountCents
    );
```

Auch Varianten mit Notiz und Euro-String stehen zur Verfügung.

---

# 👨‍💼 Staatskassen-Verwalter

Verwalter prüfen:

```java
boolean manager =
    BankApi.isStateTreasuryManager(
        managerId
    );
```

Verwalterstatus setzen:

```java
BankApi.setStateTreasuryManager(
    managerId,
    true
);
```

---

# 📤 Staatskasse → Spieler

Über den Verwalterweg:

```java
boolean success =
    BankApi.transferStateTreasuryToPlayer(
        managerId,
        receiverId,
        amountCents
    );
```

Hierbei existieren ebenfalls Varianten mit Notiz und Euro-Betrag.

---

# ⚠️ Allgemeine Staatskassenauszahlung

Zusätzlich existiert:

```java
boolean success =
    BankApi.payFromStateTreasury(
        receiverId,
        amountCents,
        source,
        note
    );
```

sowie:

```java
boolean success =
    BankApi.payFromStateTreasuryEuros(
        receiverId,
        "250",
        source,
        note
    );
```

!!! danger "Eigene Berechtigungsprüfung erforderlich"
    `payFromStateTreasury` besitzt keinen Verwalterparameter.

    Die aufrufende Mod muss deshalb ihre eigene Berechtigungsprüfung durchführen.

---

# 📡 Events

MineBank unterstützt `BankEventListener`.

Listener registrieren:

```java
BankApi.registerListener(listener);
```

Listener entfernen:

```java
BankApi.unregisterListener(listener);
```

Ein `BankTransactionEvent` liefert Informationen wie:

- Konto-ID
- Betrag
- alter Kontostand
- neuer Kontostand
- Typ
- Quelle
- Gegenkonto
- Transaktions-ID
- Zeitstempel

!!! info "Event ≠ vollständige Buchhaltung"
    Das Beobachten von Events bedeutet nicht automatisch, dass eine dauerhaft gespeicherte vollständige Transaktionshistorie aller Konten vorhanden ist.

---

# ↩️ Rückgabewerte prüfen

Integrationen sollten die Rückgabewerte der API immer prüfen.

Beispielsweise:

```java
boolean success =
    BankApi.depositEuros(
        playerId,
        "100",
        source
    );

if (!success) {
    // Zahlung / Gutschrift fehlgeschlagen
}
```

Besonders wichtig:

- boolesche Rückgabewerte prüfen
- `createBusinessAccount` kann `null` liefern
- Kreditrückzahlung liefert den tatsächlich gezahlten Centbetrag
- Barzahlungen liefern ein `CashPaymentResult`

---

# 🧩 Beispielintegration: Shop

Ein Shopsystem könnte MineBank beispielsweise so verwenden:

```text
🛒 Spieler kauft Ware
        ↓
🏢 Firmenkonto des Shops ermitteln
        ↓
💶 Preis 19,99 €
        ↓
BankApi.transferToBusinessEuros(...)
        ↓
   ┌────┴────┐
   │         │
 true      false
   │         │
   ↓         ↓
Ware      Kauf
geben    abbrechen
```

Die Warenübergabe bleibt Aufgabe der Shop-Mod.

---

# 🧩 Typische Integrationen

| Integration | MineBank-Funktionen |
|---|---|
| CityShop | Firmenzuordnung, Mitarbeiterabfrage, Kontozahlungen, atomare Barzahlung |
| CityRegion | Spielerkonto-Zahlungen und Gebühren an die Staatskasse |
| CityPolice | Bußgelder vom Spielerkonto an die Staatskasse |

Diese Namen beschreiben die in der MineBank-Dokumentation vorgesehenen Integrationsbeispiele. Ob eine konkrete externe Mod die API tatsächlich verwendet, muss separat geprüft werden.

---

# 📚 Öffentliche API-Signaturen

Die folgenden Methoden entsprechen den dokumentierten öffentlichen statischen Methoden aus `BankApi.java`.

```java
public static void bindServer(MinecraftServer server);
public static void clearServer(MinecraftServer server);

public static boolean accountExists(UUID playerId);
public static long getBalance(UUID playerId);
public static boolean hasBalance(UUID playerId, long amountCents);
public static boolean hasBalanceEuros(UUID playerId, String amountEuros);

public static boolean deposit(UUID playerId, long amountCents);
public static boolean deposit(UUID playerId, long amountCents, TransactionSource source);
public static boolean depositEuros(UUID playerId, String amountEuros);
public static boolean depositEuros(UUID playerId, String amountEuros, TransactionSource source);

public static boolean withdraw(UUID playerId, long amountCents);
public static boolean withdraw(UUID playerId, long amountCents, TransactionSource source);
public static boolean withdrawEuros(UUID playerId, String amountEuros);
public static boolean withdrawEuros(UUID playerId, String amountEuros, TransactionSource source);

public static boolean transfer(UUID fromPlayerId, UUID toPlayerId, long amountCents);
public static boolean transfer(UUID fromPlayerId, UUID toPlayerId, long amountCents, TransactionSource source);
public static boolean transferEuros(UUID fromPlayerId, UUID toPlayerId, String amountEuros);
public static boolean transferEuros(UUID fromPlayerId, UUID toPlayerId, String amountEuros, TransactionSource source);

public static List<PersonalLoan> getPersonalLoans(UUID playerId);
public static int getOpenPersonalLoanCount(UUID playerId);
public static boolean takePersonalLoan(UUID playerId, long amountCents);
public static boolean takePersonalLoanEuros(UUID playerId, String amountEuros);
public static long repayPersonalLoan(UUID playerId, long amountCents);
public static long repayPersonalLoanEuros(UUID playerId, String amountEuros);

public static UUID createBusinessAccount(UUID owner, String companyName);
public static UUID createBusinessAccount(UUID accountId, UUID owner, String companyName);
public static boolean businessAccountExists(UUID accountId);
public static long getBusinessBalance(UUID accountId);
public static UUID getBusinessAccountForPlayer(UUID playerId);
public static String getBusinessAccountName(UUID businessAccountId);
public static UUID getBusinessAccountOwner(UUID businessAccountId);
public static boolean isBusinessMember(UUID businessAccountId, UUID playerId);

public static boolean depositBusiness(UUID accountId, long amountCents, TransactionSource source);
public static boolean depositBusinessEuros(UUID accountId, String amountEuros, TransactionSource source);
public static boolean withdrawBusiness(UUID accountId, long amountCents, TransactionSource source);
public static boolean withdrawBusinessEuros(UUID accountId, String amountEuros, TransactionSource source);

public static boolean transferToBusiness(UUID playerId, UUID accountId, long amountCents, TransactionSource source);
public static boolean transferToBusinessEuros(UUID playerId, UUID accountId, String amountEuros, TransactionSource source);
public static boolean transferFromBusiness(UUID accountId, UUID playerId, long amountCents, TransactionSource source);
public static boolean transferFromBusinessEuros(UUID accountId, UUID playerId, String amountEuros, TransactionSource source);
public static boolean transferBusinessToBusiness(UUID fromAccountId, UUID toAccountId, long amountCents, TransactionSource source);
public static boolean transferBusinessToBusinessEuros(UUID fromAccountId, UUID toAccountId, String amountEuros, TransactionSource source);

public static boolean addBusinessMember(UUID accountId, UUID playerId);
public static boolean removeBusinessMember(UUID accountId, UUID playerId);
public static boolean changeBusinessOwner(UUID accountId, UUID newOwner);

public static long getCashValue(Player player);
public static boolean takeCash(Player player, long amountCents);
public static boolean takeCashEuros(Player player, String amountEuros);
public static boolean giveCash(Player player, long amountCents);
public static boolean giveCashEuros(Player player, String amountEuros);

public static boolean depositCashToBusiness(UUID businessAccountId, Player player, long amountCents, TransactionSource source);
public static boolean depositCashToBusinessEuros(UUID businessAccountId, Player player, String amountEuros, TransactionSource source);

public static CashPaymentResult payBusinessWithCash(Player player, UUID businessAccountId, long amountCents, TransactionSource source, String note);
public static CashPaymentResult payBusinessWithCashEuros(Player player, UUID businessAccountId, String amountEuros, TransactionSource source, String note);

public static UUID getStateTreasuryOwnerId();
public static String getStateTreasuryIban();
public static long getStateTreasuryBalance();
public static java.util.List<StateTreasuryBooking> getStateTreasuryBookings();

public static boolean collectCityPoliceFine(UUID playerId, long amountCents);
public static boolean collectCityPoliceFine(UUID playerId, long amountCents, String note);
public static boolean collectCityPoliceFineEuros(UUID playerId, String amountEuros, String note);

public static boolean collectToStateTreasury(UUID playerId, long amountCents, TransactionSource source, String note);
public static boolean collectToStateTreasuryEuros(UUID playerId, String amountEuros, TransactionSource source, String note);

public static boolean depositToStateTreasury(UUID actorId, long amountCents);
public static boolean depositToStateTreasury(UUID actorId, long amountCents, String note);
public static boolean depositToStateTreasuryEuros(UUID actorId, String amountEuros, String note);

public static boolean isStateTreasuryManager(UUID managerId);
public static void setStateTreasuryManager(UUID managerId, boolean allowed);

public static boolean transferStateTreasuryToPlayer(UUID managerId, UUID receiverId, long amountCents);
public static boolean transferStateTreasuryToPlayer(UUID managerId, UUID receiverId, long amountCents, String note);
public static boolean transferStateTreasuryToPlayerEuros(UUID managerId, UUID receiverId, String amountEuros, String note);

public static boolean payFromStateTreasury(UUID receiverId, long amountCents, TransactionSource source, String note);
public static boolean payFromStateTreasuryEuros(UUID receiverId, String amountEuros, TransactionSource source, String note);

public static void registerListener(BankEventListener listener);
public static void unregisterListener(BankEventListener listener);
```

!!! note "Technische Methoden"
    `bindServer` und `clearServer` sind technische Lebenszyklusmethoden.

    Sie sind keine Spielerfunktionen oder Minecraft-Befehle.

---

## ➡️ Nächster Schritt

Für konkrete Beispiele zur Zusammenarbeit von MineBank mit anderen Mods gibt es eine eigene Seite:

**Weiter: [🔌 Integrationen](integrationen.md)**
