# FLUX Playground

> **Probiere FLUX direkt im Browser aus – kein Download nötig!**

🌐 **[Playground öffnen](https://klingforth.github.io/Flux_Playground/)**

---

## Was ist der Playground?

Der FLUX Playground ist ein vollständiger FLUX Interpreter der direkt im Browser läuft. Er visualisiert das **Glass Grid** in Echtzeit – du siehst wie Sand durch die Kammern fließt während dein Code ausgeführt wird.

---

## Benutzeroberfläche

```
┌─────────────────────────────────────────────────────────────┐
│  ▶ Run  → Step  ↺ Reset  |  Beispiele  |  Ebenen: [64▼]    │
├───────────────────────────┬─────────────────────────────────┤
│  CODE              Ctrl+Enter = Run                         │
│                           │  GLASS GRID          L0 · Links │
│  <5 >3 | <"               │                                 │
│                           │  L3  [ 0  |  0  ]              │
│                           │  L2  [ 0  |  0  ]              │
│  OUTPUT                   │  L1  [ 0  |  0  ]              │
│  8                        │  L0  [██5 |  0  ] ◀            │
├───────────────────────────┴─────────────────────────────────┤
│  ● bereit  Ebene: 0  Fokus: Links  Links: 5  Flag L: 🌑     │
├─────────────────────────────────────────────────────────────┤
│  Syntax Referenz  ▼                                         │
├─────────────────────────────────────────────────────────────┤
│  ⚗️ Phiolen  ▼                                              │
└─────────────────────────────────────────────────────────────┘
```

---

## Buttons

| Button | Tastenkürzel | Beschreibung |
|--------|-------------|--------------|
| ▶ Run | `Ctrl+Enter` | Kompletten Code ausführen |
| → Step | – | Code Schritt für Schritt ausführen |
| ↺ Reset | – | Zustand zurücksetzen |

---

## Ebenen einstellen

Oben rechts kann die Anzahl der Ebenen gewählt werden:

| Einstellung | Beschreibung |
|-------------|--------------|
| 16 | Minimal – für einfache Programme |
| 32 | Klein |
| **64** | **Standard** |
| 128 | Groß |
| 300 | Volle FLUX Spezifikation |

---

## Glass Grid

Das Glass Grid zeigt den aktuellen Zustand in Echtzeit:

- **Aktive Ebene** – hervorgehoben mit Rahmen
- **◀ / ▶** – zeigt auf welche Seite der Fokus zeigt
- **Füllbalken** – visualisiert den Sand-Wert (logarithmische Skala)
- **L / R** – linke und rechte Kammer

---

## Status-Leiste

```
● bereit  Ebene: 2  Fokus: Links  Links: 5  Rechts: 0  Flag L: ☀️  Flag R: 🌑
```

| Anzeige | Beschreibung |
|---------|--------------|
| `● bereit` | Interpreter-Status |
| `Ebene: 2` | Aktueller Level Pointer |
| `Fokus: Links` | Aktuelle Fokus-Seite |
| `Links: 5` | Wert der linken Kammer |
| `Rechts: 0` | Wert der rechten Kammer |
| `Flag L: ☀️` | Linke Flag AN |
| `Flag R: 🌑` | Rechte Flag AUS |

---

## Beispiele

Der Playground enthält eingebaute Beispiele:

| Beispiel | Beschreibung |
|----------|--------------|
| **Addition** | `<5 >3 \| <"` → 8 |
| **Subtraktion** | 10 - 3 = 7 |
| **Multiplikation** | 6 × 8 = 48 |
| **IF-ELSE** | Kontrollfluss mit Kontrollkorn |
| **Pointer** | Variablen mit `<NL` |
| **Flag °** | IF mit Flag-System |

---

## Phiolen im Playground

Der Playground unterstützt **Phiolen** – wiederverwendbare FLUX Module.

### Phiole eingeben

1. Phiolen-Panel unten aufklappen (⚗️ Phiolen ▼)
2. Name eingeben (z.B. `blink`)
3. FLUX Code eingeben
4. `+ Hinzufügen` klicken

### .fx Datei hochladen

1. `📂 .fx laden` klicken
2. Eine oder mehrere `.fx` Dateien auswählen
3. Dateien werden automatisch als Phiolen registriert

### Phiole benutzen

```
@add     → Addition Phiole aufrufen
@blink   → eigene Phiole aufrufen
```

### Standard Phiolen

| Phiole | Code | Beschreibung |
|--------|------|--------------|
| `@add` | `\|` | Flush – Addition |
| `@clr` | `<0 >0` | Kammern leeren |

### Eigene Phiole – Strata Beispiel

**`blink` Phiole erstellen:**
```
Name: blink
Code: + <0L # <0L ^ <1L d <0L v <1L d -
```

**Aufrufen mit Parametern:**
```
<13 + <500 - @blink   LED Pin 13, 500ms
<9  + <100 - @blink   LED Pin 9,  100ms
```

---

## Schnellstart Beispiele

### Hello World
```
<42 "
```

### Addition
```
<5 >3 | <"
```

### Zähler (5 mal)
```
<5 | * :
"
```

### IF mit Flag
```
<3 ~ ~ ~ <° " ;
```

### Pointer als Variable
```
+ <42 -
<1L "
```

### Division (15 ÷ 3)
```
+ <15 - >3 | >° + + * - - ! ; < + ~ <° - <0 >0; - : + + < "
```

---

## Kommentare

**Alles was kein FLUX Symbol ist wird ignoriert!**

```
<5   linke Kammer = 5
>3   rechte Kammer = 3
|    Flush (addieren)
<"   ausgeben

Das ergibt: 8
```

Text zwischen den Symbolen ist einfach Kommentar und wird übersprungen.

---

## Step-Modus

Mit `→ Step` kann man den Code **Schritt für Schritt** ausführen:

1. Code eintippen
2. `→ Step` klicken
3. Jeder Klick führt einen Befehl aus
4. Das Glass Grid aktualisiert sich nach jedem Schritt

Ideal zum Debuggen und Verstehen wie FLUX funktioniert!

---

## Technische Details

Der Playground ist eine einzelne HTML-Datei ohne externe Abhängigkeiten:

- Reines JavaScript – kein Framework
- Tokenizer + Executor vollständig implementiert
- Unterstützt die komplette FLUX Syntax inkl. Flag-System
- Phiolen werden im Browser gespeichert (Session)

---

*FLUX Playground · By Patrick Klingforth (Rick)* ⚗️
