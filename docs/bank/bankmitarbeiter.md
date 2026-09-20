# 👨‍💼 Bankmitarbeiter

Der **Bankmitarbeiter** ist der zentrale Ansprechpartner für verschiedene Bankdienstleistungen in MineBank.

Über ihn können Spieler unter anderem ihre Bankkarte verwalten, auf Kreditfunktionen zugreifen und weitere Kontodienste verwenden.

---

## 🏦 Bankmitarbeiter platzieren

Der Bankmitarbeiter wird über das entsprechende **Bankmitarbeiter-Item** platziert.

Nach dem Platzieren steht der Mitarbeiter als NPC in der Bank zur Verfügung.

Ein **Rechtsklick** auf den Bankmitarbeiter öffnet das Beratungsmenü.

---

## 📋 Beratungsmenü

Das Beratungsmenü stellt verschiedene MineBank-Dienste bereit.

Dazu gehören unter anderem:

- 💳 Bankkarten
- 💰 Kredite
- 🏦 Kontofunktionen
- weitere Bankservices

Welche Funktionen verfügbar sind, hängt vom jeweiligen Bereich des MineBank-Systems ab.

---

## 💳 Persönliche Bankkarte

Im Bankmitarbeiter-Menü befindet sich der Bereich:

**Eigene Bankkarte**

Dort stehen Funktionen für die persönliche Bankkarte zur Verfügung.

Dazu gehören:

- Bankkarte beantragen
- Ersatzkarte erhalten
- Karteninformationen anzeigen

Eine gecraftete Bankkarte ist zunächst nur ein unaktivierter Kartenrohling.

Erst eine ausgestellte Karte besitzt die notwendige Zuordnung zum persönlichen Konto.

➡️ [Mehr über persönliche Bankkarten](../konten/bankkarte.md)

---

## 🔄 Ersatzkarte

Geht eine persönliche Bankkarte verloren oder wird eine neue Karte benötigt, kann über den Bankmitarbeiter eine Ersatzkarte ausgegeben werden.

Dabei erhöht MineBank die Kartenversion des Kontos.

Dadurch werden frühere Karten dieses Kontos ungültig.

!!! warning "Alte Karten"
    Nach Ausstellung einer Ersatzkarte können ältere Karten des Kontos nicht weiter als gültige persönliche Bankkarten verwendet werden.

---

## 🏢 Firmenkarten

Auch Firmenkarten können über die NPC-Kartenverwaltung verwaltet werden.

Eine Firmenkarte kann dort unter anderem:

- ersetzt
- gesperrt

werden.

Die zugehörige Firma wird automatisch für den Spieler ermittelt.

Der Firmenname muss dabei nicht erneut eingegeben werden.

---

## 👥 Firmenmitglieder

Die Firmenkartenverwaltung ist nicht ausschließlich auf den Besitzer einer Firma beschränkt.

Auch Firmenmitglieder können die entsprechende Kartenverwaltung verwenden.

Bei der automatischen Ermittlung hat die Besitzerzuordnung Vorrang vor einer normalen Mitgliedschaft.

!!! danger "Firmenkarte ersetzen oder sperren"
    Beim Sperren beziehungsweise Ersetzen werden ältere Karten dieser Firma ungültig.

    Dadurch können auch andere Mitarbeiter neue aktuelle Firmenkarten benötigen.

➡️ [Mehr über Firmenkarten](../konten/firmenkarte.md)

---

## 💰 Kredite

Das Beratungsmenü des Bankmitarbeiters besitzt außerdem einen Bereich für das Kreditsystem.

Darüber können die vorgesehenen Kreditfunktionen von MineBank verwendet werden.

➡️ [Mehr über Kredite](../kredite.md)

---

## 🖨️ Kartendrucker

MineBank enthält zusätzlich einen Kartendrucker beziehungsweise einen älteren technischen Druckablauf.

Dabei muss allerdings zwischen dem **aktuellen normalen NPC-Menü** und diesem älteren Ablauf unterschieden werden.

### Aktueller Stand

Der aktuelle normale Kartenmenüweg des Bankmitarbeiters stellt Karten **direkt aus**.

Der ältere Druckablauf wird vom aktuellen normalen Rechtsklick-Menü nicht aufgerufen.

!!! info "Wichtig für MineBank 1.0.3"
    Ein Gang des Bankmitarbeiters zum Kartendrucker ist derzeit **kein verpflichtender Bestandteil** jeder normalen Kartenbeantragung.

---

## 🧪 Vorhandener älterer Druckablauf

Im MineBank-Code existiert zusätzlich ein älterer Ablauf mit:

1. einer leeren Karte
2. einem Gang zum Kartendrucker
3. einer Druckzeit von **20 Sekunden**
4. einer anschließenden Rückkehr

Diese technische Routine ist vorhanden, aber nicht mit dem aktuellen normalen Rechtsklick-Kartenmenü verbunden.

Sie sollte deshalb nicht als normaler Standardablauf der aktuellen Version beschrieben werden.

➡️ [Mehr über den Kartendrucker](kartendrucker.md)

---

## 🔎 Druckersuche

Die vorhandene Druckroutine besitzt bereits eine Suche nach einem Kartendrucker.

Dabei werden Entfernungen von bis zu:

- **12 Blöcken je horizontaler Achse**
- **2 Blöcken Höhenunterschied**

berücksichtigt.

Neben dem Drucker ist außerdem ein geeigneter freier Standplatz mit Boden und Kopffreiheit vorgesehen.

!!! warning "Technisch vorhanden ≠ aktuell angebunden"
    Diese Angaben beschreiben die vorhandene Druckroutine im Code.

    Sie bedeuten nicht, dass der aktuelle normale Bankmitarbeiter-Menüweg diesen Ablauf automatisch verwendet.

---

## 🗑️ Bankmitarbeiter entfernen

Für Bankmitarbeiter besitzt MineBank ein eigenes **Entferner-Werkzeug**.

Damit kann ein platzierter Bankmitarbeiter gezielt entfernt werden.

Dadurch muss der NPC nicht über normale Minecraft-Methoden beseitigt werden.

---

## 🔎 Aktueller Ablauf einer Bankkarte

Für die aktuelle normale Bedienung lässt sich der Ablauf vereinfacht so darstellen:

```text
👤 Spieler
    ↓
👨‍💼 Bankmitarbeiter
    ↓
💳 Eigene Bankkarte
    ↓
🏦 Kartenfunktion auswählen
    ↓
💳 Karte wird über den aktuellen Menüweg ausgestellt
