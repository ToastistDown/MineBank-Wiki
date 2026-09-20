# 🛠️ Crafting-Rezepte

Auf dieser Seite findest du die Crafting-Rezepte von **MineBank 1.0.3**.

Die hier aufgeführten Rezepte stammen aus den vorhandenen Rezeptdateien der Mod und werden an einer normalen Werkbank hergestellt.

!!! info "Hinweis"
    Zusätzliche Datapacks auf einem Server können Rezepte verändern.

---

## 📖 So liest du die Rezepte

Die Rezepte werden als 3×3-Raster dargestellt.

Ein Punkt:

```text
.
```

steht für einen **leeren Platz**.

Beispiel:

```text
.E.
.R.
.S.
```

---

# 🏧 Bankautomat

**Rezept-ID:** `bankmod:atm`

```text
IGI
ICI
IRI
```

| Zeichen | Zutat |
|---|---|
| `I` | `minecraft:iron_ingot` |
| `G` | `minecraft:glass_pane` |
| `C` | `bankmod:bank_computer` |
| `R` | `minecraft:redstone` |

**Ergebnis:** 1× Bankautomat

➡️ [Mehr über den Bankautomaten](bargeld/bankautomat.md)

---

# 🔗 Bank-Zuordnungstool

**Rezept-ID:** `bankmod:bank_assignment_tool`

```text
.E.
.R.
.S.
```

| Zeichen | Zutat |
|---|---|
| `E` | `minecraft:emerald` |
| `R` | `minecraft:redstone` |
| `S` | `minecraft:stick` |

**Ergebnis:** 1× Bank-Zuordnungstool

Das Tool wird verwendet, um unterstützte Bankgeräte einer vorhandenen Bankzone zuzuordnen.

➡️ [Mehr über Bankzonen](bank/bankzonen.md)

---

# 💳 Bankkarte

**Rezept-ID:** `bankmod:bank_card`

```text
III
PBG
III
```

| Zeichen | Zutat |
|---|---|
| `I` | `minecraft:iron_nugget` |
| `P` | `minecraft:paper` |
| `B` | `minecraft:blue_dye` |
| `G` | `minecraft:gold_nugget` |

**Ergebnis:** 1× Bankkarte

!!! warning "Kartenrohling"
    Eine gecraftete Bankkarte ist noch keine aktivierte persönliche Kontokarte.

    Das Crafting-Rezept erzeugt zunächst einen **Kartenrohling**.

➡️ [Mehr über Bankkarten](konten/bankkarte.md)

---

# 🖥️ Bankcomputer

**Rezept-ID:** `bankmod:bank_computer`

```text
IGI
IRI
SSS
```

| Zeichen | Zutat |
|---|---|
| `I` | `minecraft:iron_ingot` |
| `G` | `minecraft:glass_pane` |
| `R` | `minecraft:redstone` |
| `S` | `minecraft:smooth_stone` |

**Ergebnis:** 1× Bankcomputer

➡️ [Mehr über den Bankcomputer](bank/bankcomputer.md)

---

# 🗑️ Bankmitarbeiter-Entferner

**Rezept-ID:** `bankmod:bank_npc_remover`

```text
.R.
.I.
.S.
```

| Zeichen | Zutat |
|---|---|
| `R` | `minecraft:redstone` |
| `I` | `minecraft:iron_ingot` |
| `S` | `minecraft:stick` |

**Ergebnis:** 1× Bankmitarbeiter-Entferner

Mit diesem Werkzeug kann ein platzierter Bankmitarbeiter gezielt entfernt werden.

➡️ [Mehr über Bankmitarbeiter](bank/bankmitarbeiter.md)

---

# 👨‍💼 Bankmitarbeiter-Spawn-Ei

**Rezept-ID:** `bankmod:bank_npc_spawn_egg`

```text
.E.
.B.
.P.
```

| Zeichen | Zutat |
|---|---|
| `E` | `minecraft:emerald` |
| `B` | `bankmod:bank_card` |
| `P` | `minecraft:paper` |

**Ergebnis:** 1× Bankmitarbeiter-Spawn-Ei

!!! note "Bankkarte als Zutat"
    Für dieses Rezept wird `bankmod:bank_card` als Crafting-Zutat verwendet.

➡️ [Mehr über Bankmitarbeiter](bank/bankmitarbeiter.md)

---

# 🖨️ Kartendrucker

**Rezept-ID:** `bankmod:bank_printer`

```text
III
RPR
IPI
```

| Zeichen | Zutat |
|---|---|
| `I` | `minecraft:iron_ingot` |
| `R` | `minecraft:redstone` |
| `P` | `minecraft:paper` |

**Ergebnis:** 1× Kartendrucker

!!! info "Aktueller Stand"
    Der Kartendrucker besitzt eine vorhandene technische Druckroutine.

    Der aktuelle normale Kartenmenüweg des Bankmitarbeiters verwendet diese Routine jedoch nicht automatisch.

➡️ [Mehr über den Kartendrucker](bank/kartendrucker.md)

---

# 🔐 Tresor

**Rezept-ID:** `bankmod:bank_vault`

```text
OIO
ICI
OIO
```

| Zeichen | Zutat |
|---|---|
| `O` | `minecraft:obsidian` |
| `I` | `minecraft:iron_block` |
| `C` | `minecraft:chest` |

**Ergebnis:** 1× Tresor

➡️ [Mehr über den Tresor](bank/tresor.md)

---

# 🏢 Firmenkarte

**Rezept-ID:** `bankmod:business_bank_card`

```text
GGG
PBE
GGG
```

| Zeichen | Zutat |
|---|---|
| `G` | `minecraft:gold_nugget` |
| `P` | `minecraft:paper` |
| `B` | `minecraft:black_dye` |
| `E` | `minecraft:emerald` |

**Ergebnis:** 1× Firmenkarte

!!! warning "Kartenrohling"
    Auch dieses Kartenrezept erzeugt zunächst einen Rohling und keine automatisch aktivierte Firmenkarte.

➡️ [Mehr über Firmenkarten](konten/firmenkarte.md)

---

# 🪙 Münzeinzahlautomat

**Rezept-ID:** `bankmod:coin_deposit_atm`

```text
IGI
IAI
IHI
```

| Zeichen | Zutat |
|---|---|
| `I` | `minecraft:iron_ingot` |
| `G` | `minecraft:glass_pane` |
| `A` | `bankmod:atm` |
| `H` | `minecraft:hopper` |

**Ergebnis:** 1× Münzeinzahlautomat

Für dieses Rezept wird bereits ein normaler MineBank-Bankautomat benötigt.

➡️ [Mehr über den Münzeinzahlautomaten](bargeld/muenzautomat.md)

---

# 💼 Geldkoffer

**Rezept-ID:** `bankmod:money_case`

```text
III
LCL
III
```

| Zeichen | Zutat |
|---|---|
| `I` | `minecraft:iron_ingot` |
| `L` | `minecraft:leather` |
| `C` | `minecraft:chest` |

**Ergebnis:** 1× Geldkoffer

➡️ [Mehr über den Geldkoffer](bargeld/geldkoffer.md)

---

# 👛 Portemonnaie

**Rezept-ID:** `bankmod:wallet`

```text
LLL
LGL
LLL
```

| Zeichen | Zutat |
|---|---|
| `L` | `minecraft:leather` |
| `G` | `minecraft:gold_nugget` |

**Ergebnis:** 1× Portemonnaie

➡️ [Mehr über das Portemonnaie](bargeld/portemonnaie.md)

---

## 📚 Alle Rezepte im Überblick

| Gegenstand | Rezept-ID |
|---|---|
| 🏧 Bankautomat | `bankmod:atm` |
| 🔗 Bank-Zuordnungstool | `bankmod:bank_assignment_tool` |
| 💳 Bankkarte | `bankmod:bank_card` |
| 🖥️ Bankcomputer | `bankmod:bank_computer` |
| 🗑️ Bankmitarbeiter-Entferner | `bankmod:bank_npc_remover` |
| 👨‍💼 Bankmitarbeiter-Spawn-Ei | `bankmod:bank_npc_spawn_egg` |
| 🖨️ Kartendrucker | `bankmod:bank_printer` |
| 🔐 Tresor | `bankmod:bank_vault` |
| 🏢 Firmenkarte | `bankmod:business_bank_card` |
| 🪙 Münzeinzahlautomat | `bankmod:coin_deposit_atm` |
| 💼 Geldkoffer | `bankmod:money_case` |
| 👛 Portemonnaie | `bankmod:wallet` |

**Insgesamt: 12 Crafting-Rezepte**

---

## 💶 Was kann nicht normal gecraftet werden?

Das physische Bargeld von MineBank besitzt keine regulären Crafting-Rezepte.

Dazu gehören insbesondere die Geldscheine und Münzen.

Spieler können ihr Geld deshalb nicht einfach aus normalen Minecraft-Materialien herstellen.

---

## ⚠️ Datapacks

Serverbetreiber können Rezepte über zusätzliche Datapacks verändern.

Dadurch können die tatsächlich auf einem bestimmten Server verwendeten Rezepte von dieser Wiki abweichen.

Diese Seite dokumentiert die standardmäßig vorhandenen Rezepte von **MineBank 1.0.3**.

---

## ➡️ Nächster Schritt

Neben den Crafting-Rezepten besitzt MineBank verschiedene Befehle für Spieler und Administratoren.

Als Nächstes erstellen wir deshalb die vollständige:

**⌨️ Befehlsübersicht**

**Weiter: [⌨️ Befehle](befehle.md)**
