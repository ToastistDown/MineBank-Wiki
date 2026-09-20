# 🛠️ Problemlösungen

Auf dieser Seite findest du Lösungen und Hinweise zu häufigen Problemen mit **MineBank 1.0.3**.

Wenn eine Bankkarte, ein Bankautomat, Firmenkonto oder eine andere Funktion nicht wie erwartet funktioniert, kannst du hier die wichtigsten Punkte überprüfen.

---

# 💳 „Aktivierte Bankkarte benötigt“

Wenn MineBank meldet, dass eine aktivierte Bankkarte benötigt wird, überprüfe zuerst die verwendete Karte.

Eine frisch gecraftete Bankkarte ist zunächst nur ein **Kartenrohling**.

Sie muss zuerst ausgestellt werden.

Außerdem muss sich die passende persönliche Bankkarte tatsächlich in der Hand befinden.

```text
💳 Karte gecraftet
      ↓
Kartenrohling
      ↓
🏦 Karte ausstellen lassen
      ↓
💳 aktivierte Bankkarte
```

➡️ [Mehr über Bankkarten](konten/bankkarte.md)

---

# 🔒 „Bankkarte gesperrt“

Wenn eine persönliche Bankkarte als gesperrt beziehungsweise ungültig erkannt wird, sollte eine Ersatzkarte beim Bankmitarbeiter besorgt werden.

Eine Ersatzkarte erhöht die Kartenversion.

Ältere Karten des Kontos können anschließend nicht weiterverwendet werden.

```text
💳 Alte Karte
      ↓
🔄 Ersatzkarte
      ↓
Kartenversion steigt
      ↓
❌ Alte Karte ungültig
      ↓
✅ Neue Karte verwenden
```

---

# 🏢 Firmenkarte wird abgelehnt

Wenn eine Firmenkarte nicht akzeptiert wird, überprüfe:

1. Existiert das Firmenkonto?
2. Ist der Spieler noch Mitglied der Firma?
3. Wird eine aktuelle Firmenkarte verwendet?

Der Besitz einer fremden Firmenkarte allein reicht nicht aus.

➡️ [Mehr über Firmenkarten](konten/firmenkarte.md)

---

# 🔎 Firma nicht gefunden

Wenn MineBank eine Firma nicht findet, überprüfe:

- Firmenname
- Kontonummer
- verwendeten Befehl

Bei Firmen-Daueraufträgen sollten Namen mit Leerzeichen in Anführungszeichen geschrieben werden.

Beispiel:

```text
"Meine Firma"
```

Bei `member add/remove` ist die Firmenkennung dagegen ein einzelnes Wortargument. Für Firmennamen mit Leerzeichen sollte dort die Kontonummer oder technische Konto-UUID verwendet werden.

---

# 🏢 „Firma bereits vorhanden“

Firmennamen müssen eindeutig sein.

Außerdem kann ein Besitzer nur eine eigene Firma besitzen.

Wenn die Firmengründung deshalb abgelehnt wird, überprüfe:

- ob der Firmenname bereits verwendet wird
- ob du bereits Besitzer einer Firma bist

➡️ [Mehr über Firmenkonten](konten/firmenkonto.md)

---

# 💶 Firmengründung funktioniert nicht

Für die Firmengründung werden mindestens:

# **20.000 €**

auf dem **Privatkonto** benötigt.

Bargeld im normalen Inventar reicht dafür nicht aus.

```text
❌ 20.000 € nur im Inventar

✅ 20.000 € auf dem Privatkonto
```

---

# 🏧 ATM zahlt kein Geld aus

Wenn ein Bankautomat eine Auszahlung verweigert, überprüfe:

1. Ist genügend Guthaben auf dem Konto?
2. Hat der Bankautomat genügend Bargeld?
3. Kann der gewünschte Betrag mit den vorhandenen Scheinen dargestellt werden?
4. Ist genügend Platz im Spielerinventar vorhanden?
5. Wird die passende Bankkarte verwendet?

Bankkonto und ATM-Bargeldbestand sind zwei getrennte Werte.

```text
🏦 Kontoguthaben
      ≠
🏧 ATM-Bargeldbestand
```

➡️ [Mehr über Bankautomaten](bargeld/bankautomat.md)

---

# 💶 Bargeld wird nicht erkannt

Wenn MineBank vorhandenes Bargeld nicht erkennt, überprüfe, wo sich das Geld befindet.

Automatische Bargeldabfragen durchsuchen:

- Portemonnaies
- Geldkoffer

nicht rekursiv.

Nimm das benötigte Bargeld deshalb zunächst in das normale Spielerinventar.

---

## 🏧 Scheine oder Münzen?

Der normale Bankautomat verarbeitet **Geldscheine**.

Für Münzen existiert der separate Münzeinzahlautomat.

| Bargeld | Richtiger Automat |
|---|---|
| 5–500-€-Scheine | 🏧 Bankautomat |
| 1 € / 2 € | 🪙 Münzeinzahlautomat |
| Centmünzen | 🪙 Münzeinzahlautomat |

➡️ [Mehr über den Münzeinzahlautomaten](bargeld/muenzautomat.md)

---

# 🔄 Dauerauftrag läuft unerwartet oft

MineBank-Daueraufträge orientieren sich an **Minecraft-Tagen** und nicht an realen Tagen.

Deshalb können unter anderem:

- Schlafen
- Zeitbefehle

für die zeitliche Verarbeitung relevant sein.

```text
Minecraft-Tage
      ≠
reale Tage
```

➡️ [Mehr über Daueraufträge](dauerauftraege.md)

---

# ⏭️ Dauerauftrag wurde ausgelassen

Wenn eine erwartete Zahlung nicht ausgeführt wurde, überprüfe:

1. Guthaben des Ausgangskontos
2. Zielkonto

Fehlgeschlagene Termine werden im Zeitplan weitergesetzt.

Ein fehlgeschlagener Zahlungstermin hält den gesamten Dauerauftrag also nicht dauerhaft an.

---

# 💰 Kredit ist überfällig

Wenn eine Kreditrate nicht bezahlt werden konnte, wird der Kredit als **überfällig** behandelt.

Lade ausreichend Guthaben auf das Privatkonto.

Der Kredit wird bei einer späteren Tagesprüfung erneut berücksichtigt.

Je nach vorgesehenem Ablauf kann außerdem eine manuelle Rückzahlung verwendet werden.

➡️ [Mehr über Kredite](kredite.md)

---

# 🔐 Tresor ist nicht zugeordnet

Ein Tresor benötigt eine Bankzuordnung.

Wenn der Tresor keiner Bank zugeordnet ist:

```text
🏦 Bankzone einrichten
```

oder:

```text
🔗 Bank-Zuordnungstool verwenden
```

Der Tresorbestand gehört anschließend zur entsprechenden Bankzone.

➡️ [Mehr über den Tresor](bank/tresor.md)

➡️ [Mehr über Bankzonen](bank/bankzonen.md)

---

# 🏛️ Staatskassenbefehl funktioniert nicht

Die Staatskassenbefehle benötigen Minecraft-Berechtigungsstufe:

# **2**

Wenn ein entsprechender Befehl fehlt oder nicht funktioniert, überprüfe:

- Berechtigungsstufe
- tatsächlich geladene MineBank-Version

➡️ [Mehr über die Staatskasse](staatskasse.md)

---

# 🏛️ Staatskassenauszahlung scheitert

Für eine Auszahlung aus der Staatskasse reicht OP-Berechtigung allein nicht aus.

Beim entsprechenden Auszahlungsbefehl müssen zusätzlich:

- der ausführende Spieler als Staatskassen-Verwalter eingetragen sein
- genügend Guthaben in der Staatskasse vorhanden sein

```text
Berechtigungsstufe 2
        +
Staatskassen-Verwalter
        +
genügend Guthaben
        ↓
💸 Auszahlung
```

---

# 💾 Wo speichert MineBank seine Daten?

Die zentrale Speicherung verwendet Minecraft **SavedData** in der Overworld.

Name:

```text
bankmod_accounts
```

Üblicher Dateipfad:

```text
<Weltordner>/data/bankmod_accounts.dat
```

Dort werden unter anderem zentrale MineBank-Daten gespeichert.

---

# 💾 Welche Daten werden gespeichert?

Zu den gespeicherten Daten gehören unter anderem:

- Konten
- Identitäten
- Guthaben
- Firmen
- Firmenmitglieder
- Kartenversionen
- Kredite
- Daueraufträge
- Staatskassenbuchungen
- Staatskassen-Verwalter
- Automaten
- Bankzonen
- Gerätezuordnungen

Zusätzlich liegen bestimmte Informationen an anderen Stellen.

**Karten- und Behälterdaten** befinden sich zusätzlich im Item-NBT.

**NPC-Zustände** werden in Entity-Daten gespeichert.

---

# 🛡️ Backup vor einem Update

Vor einem MineBank-Update sollte die **komplette Minecraft-Welt** gesichert werden.

!!! danger "Nicht nur bankmod_accounts.dat sichern"
    Nur die zentrale Datei `bankmod_accounts.dat` zu kopieren ist **kein vollständiges Backup**.

    Bargeld, Karten, NPCs und weitere Daten können zusätzlich in Spieler-, Item- oder Entity-Daten liegen.

Für eine konsistente Sicherung sollte der Server vorher sauber gestoppt werden.

Empfohlener Ablauf:

```text
🛑 Server sauber stoppen
        ↓
💾 komplette Welt sichern
        ↓
📦 MineBank aktualisieren
        ↓
▶️ Server starten
        ↓
🔎 Funktionen kontrollieren
```

---

# 🔄 Ältere MineBank-Daten

Beim Laden kann der vorhandene MineBank-Code ältere Kontostrukturen auf das aktuelle:

```text
Kontonummer + MC-IBAN
```

Schema migrieren.

Dabei bleiben technische Identität und Guthaben dem Konto zugeordnet.

Vorhandene Kreditsummen können gegebenenfalls in Kreditdatensätze überführt werden.

---

# 💳 Alte Karten nach einem Update

Alte Bankkarten sollten nicht dadurch „repariert“ werden, dass Konten neu erstellt werden.

Die technische Kontozuordnung der Karte ist entscheidend.

!!! warning "Keine Konten zur Kartenreparatur neu erstellen"
    Wenn nach einer Migration eine alte Karte Probleme verursacht, sollte nicht einfach das zugehörige Konto neu erstellt werden.

    Die vorhandene technische Kontozuordnung muss berücksichtigt werden.

---

# 🚧 Aktuelle Grenzen von MineBank 1.0.3

Nicht alle Menüs und Systeme sind bereits gleich weit ausgebaut.

Für MineBank 1.0.3 sollte insbesondere nicht als fertige Funktion versprochen werden:

| Funktion | Aktueller Stand |
|---|---|
| Vollständiges Bonitätssystem | ❌ Nicht fertig |
| Jährliches Zinsmodell | ❌ Nicht vorhanden |
| Automatische externe Shop-Verknüpfung allein durch MineBank-Installation | ❌ Nicht vorhanden |

---

## 🏪 Externe Shops

MineBank besitzt eine API, über die andere Mods angebunden werden können.

Die Installation von MineBank allein verbindet jedoch nicht automatisch externe Shopsysteme mit dem Banksystem.

Die andere Mod muss die MineBank-API tatsächlich verwenden.

```text
MineBank installiert
      ↓
❌ keine automatische Shop-Integration

MineBank API
      +
andere Mod nutzt API
      ↓
✅ Integration möglich
```

➡️ [Mehr über Integrationen](entwickler/integrationen.md)

---

# 🔎 Schnelle Fehlerübersicht

| Problem | Prüfen |
|---|---|
| Aktivierte Bankkarte benötigt | Karte in Hand? Rohling ausgestellt? |
| Bankkarte gesperrt | Ersatzkarte verwenden |
| Firmenkarte abgelehnt | Konto, Mitgliedschaft, Kartenversion |
| Firma nicht gefunden | Name/Kontonummer prüfen |
| Firma bereits vorhanden | Eindeutiger Name, nur eine Firma pro Besitzer |
| Firmengründung scheitert | 20.000 € auf Privatkonto |
| ATM zahlt nicht aus | Konto, ATM-Bestand, Stückelung, Inventar |
| Bargeld fehlt | Aus Portemonnaie/Koffer nehmen |
| Dauerauftrag läuft zu oft | Minecraft-Zeit prüfen |
| Dauerauftrag ausgelassen | Guthaben und Ziel prüfen |
| Kredit überfällig | Privatkonto aufladen |
| Tresor nicht zugeordnet | Bankzone oder Zuordnungstool |
| Staatskassenbefehl fehlt | Stufe 2 und Modversion prüfen |
| Staatskassenauszahlung scheitert | Verwalter + Guthaben prüfen |

---

## ➡️ Nächster Schritt

Damit ist auch der allgemeine Referenzbereich fast fertig.

Als Nächstes geht es in den Bereich für Mod-Entwickler:

**👨‍💻 MineBank API**

**Weiter: [👨‍💻 API](entwickler/api.md)**
