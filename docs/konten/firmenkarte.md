# 💳 Firmenkarte

Die Firmenkarte ermöglicht berechtigten Spielern den Zugriff auf ein **Firmenkonto** in MineBank.

Anders als die persönliche Bankkarte ist sie nicht für das Privatkonto eines Spielers gedacht, sondern für das gemeinsame Konto einer Firma.

---

## 🏢 Verbindung zum Firmenkonto

Eine Firmenkarte gehört zu einem bestimmten Firmenkonto.

Das Firmenkonto besitzt unter anderem:

- ein eigenes Guthaben
- eine eigene Kontonummer
- eine eigene IBAN
- einen Besitzer
- Mitglieder

Die Firmenkarte ermöglicht den Zugriff auf dieses Konto, sofern der Spieler dazu berechtigt ist.

➡️ [Mehr über Firmenkonten](firmenkonto.md)

---

## 🏧 Verwendung am Bankautomaten

Mit einer gültigen Firmenkarte kann ein MineBank-Bankautomat verwendet werden.

Dort stehen Funktionen für das Firmenkonto zur Verfügung.

Dazu gehören:

- 💰 Firmenguthaben anzeigen
- 💶 Geldscheine einzahlen
- 💵 Bargeld auszahlen
- 💸 Überweisungen vom Firmenkonto

➡️ [Mehr über Bankautomaten](../bargeld/bankautomat.md)

---

## 🔐 Berechtigungsprüfung

Der Besitz einer Firmenkarte allein reicht nicht aus, um auf das Firmenkonto zuzugreifen.

MineBank prüft zusätzlich, ob der Spieler für die Firma berechtigt ist.

Dabei werden unter anderem:

- Firmenmitgliedschaft
- Administratorrechte

berücksichtigt.

!!! warning "Eine fremde Karte reicht nicht aus"
    Wenn du eine Firmenkarte einer fremden Firma findest oder erhältst, bekommst du dadurch nicht automatisch Zugriff auf deren Firmenkonto.

---

## 👥 Verwendung durch Firmenmitglieder

Nicht nur der Firmenbesitzer kann das Firmenkonto verwenden.

Auch Firmenmitglieder können mit einer gültigen Firmenkarte auf unterstützte Firmenfunktionen zugreifen.

Dazu gehören unter anderem:

- Verwendung des Firmenkontos am Bankautomaten
- Verwaltung von Firmen-Daueraufträgen

Das aktuelle System besitzt dabei keine getrennten Detailrollen wie beispielsweise:

- nur lesen
- nur einzahlen
- nur auszahlen

---

## 👨‍💼 Firmenkarte beim Bankmitarbeiter

Die Firmenkarte kann über das Menü des Bankmitarbeiters verwaltet werden.

Dort kann die Karte unter anderem:

- ersetzt
- gesperrt

werden.

MineBank ermittelt die zugehörige Firma automatisch für den Spieler.

Der Firmenname muss deshalb bei dieser Kartenverwaltung nicht erneut eingegeben werden.

---

## 👑 Besitzer und Mitglieder

Bei der automatischen Ermittlung einer Firma hat die Besitzerzuordnung Vorrang vor einer normalen Mitgliedschaft.

Die Kartenverwaltung beim Bankmitarbeiter ist jedoch nicht ausschließlich auf den Firmenbesitzer beschränkt.

Auch Firmenmitglieder können die entsprechende NPC-Kartenverwaltung verwenden.

---

## 🔄 Firmenkarte ersetzen

Eine Firmenkarte kann ersetzt werden.

Dabei ist wichtig:

**Das Ersetzen betrifft nicht nur das einzelne Karten-Item.**

Ältere Karten dieser Firma werden dadurch ungültig.

### Beispiel

Mehrere Mitarbeiter besitzen eine aktuelle Firmenkarte.

Wird anschließend eine neue Karte ausgegeben und die bisherige Kartengeneration ungültig gemacht, funktionieren die älteren Firmenkarten nicht mehr.

Die betroffenen Mitarbeiter benötigen anschließend ebenfalls aktuelle Karten.

!!! danger "Andere Mitarbeiter beachten"
    Nach dem Ersetzen einer Firmenkarte können auch die Karten anderer Mitarbeiter ungültig sein.

    Gib den betroffenen Mitarbeitern anschließend aktuelle Firmenkarten.

---

## 🚫 Firmenkarte sperren

Eine Firmenkarte kann ebenfalls über die Kartenverwaltung gesperrt werden.

Auch beim Sperren werden ältere Karten dieser Firma ungültig.

Das ist beispielsweise wichtig, wenn eine Firmenkarte verloren geht oder nicht mehr verwendet werden soll.

---

## 🔒 Schutz bei Kartenverlust

Der Zugriff auf das Firmenkonto basiert nicht ausschließlich darauf, wer das Karten-Item besitzt.

MineBank überprüft zusätzlich die Berechtigung des Spielers.

Dadurch bedeutet der Verlust einer Firmenkarte nicht automatisch, dass ein fremder Spieler Zugriff auf das Firmenkonto erhält.

Trotzdem sollte eine verlorene Karte über die Kartenverwaltung ersetzt beziehungsweise gesperrt werden.

---

## 🔄 Firmen-Daueraufträge

Firmenmitglieder können Firmen-Daueraufträge verwalten.

Damit können wiederkehrende Zahlungen über das Firmenkonto eingerichtet werden.

➡️ [Mehr über Daueraufträge](../dauerauftraege.md)

---

## 🛠️ Firmenkarte wird abgelehnt

Wenn eine Firmenkarte am Bankautomaten nicht akzeptiert wird, solltest du folgende Punkte überprüfen:

1. Existiert das Firmenkonto noch?
2. Bist du Besitzer oder Mitglied der Firma?
3. Verwendest du eine gültige und aktuelle Firmenkarte?
4. Wurde zwischenzeitlich eine Ersatzkarte ausgegeben?
5. Wurde die bisherige Kartengeneration gesperrt?

Eine ältere Firmenkarte kann nach einer Sperrung oder einem Ersatz nicht weiterverwendet werden.

---

## 💳 Persönliche Bankkarte vs. Firmenkarte

| Persönliche Bankkarte | Firmenkarte |
|---|---|
| Gehört zum Privatkonto | Gehört zum Firmenkonto |
| Zugriff auf persönliches Guthaben | Zugriff auf Firmenguthaben |
| An persönlichen Spieler gebunden | Firmenberechtigung wird geprüft |
| Ersatz macht ältere persönliche Karten ungültig | Ersatz/Sperrung macht ältere Firmenkarten ungültig |
| Für private Bankgeschäfte | Für geschäftliche Bankgeschäfte |

---

## 💡 Beispiel

Angenommen, die Firma **BlockBau GmbH** besitzt ein MineBank-Firmenkonto.

Der Firmenbesitzer nimmt einen weiteren Spieler als Mitglied auf.

Dieser Spieler erhält eine gültige Firmenkarte.

Am Bankautomaten kann MineBank anschließend prüfen:

```text
Firmenkarte vorhanden
        ↓
Firmenkonto gefunden
        ↓
Spieler ist Firmenmitglied?
        ↓
JA
        ↓
Zugriff auf unterstützte Firmenfunktionen
