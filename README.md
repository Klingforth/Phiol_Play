# Phiol Playground

> **Probiere Phiol direkt im Browser aus – kein Download nötig!**

🌐 **[Playground öffnen](https://klingforth.github.io/Phiol_Play/)**

---

## Was ist der Playground?

Der Phiol Playground ist ein vollständiger Phiol Interpreter der direkt im Browser läuft. Er visualisiert das **Glass Grid** in Echtzeit – du siehst wie Sand durch die Kammern fließt während dein Code ausgeführt wird.

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
| 300 | Volle Phiol Spezifikation |

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
| **IF-ELSE** | Kontrollfluss mit Flag-System |
| **Pointer** | Variablen mit `<NL` |
| **Flag °** | IF mit Flag-System |

---

## Kommentare

Kommentare werden mit runden Klammern geschrieben und überall ignoriert:

```
( Das ist ein Kommentar )

<5 >3  ( lade 5 und 3 )
|      ( addieren )
<"     ( ausgeben )
```

---

## Phiolen im Playground

Der Playground unterstützt **Phiolen** – wiederverwendbare Module die Phiol erweitern.

### Phiole im Code definieren

Ab Version 0.2 können Phiolen direkt im Editor definiert werden:

```
§add   { | }
§swap  { ! }
§doppelt { | }

<5 >3 add <"
```

`§name { code }` definiert eine neue Phiole. Sie erscheint sofort in der Phiolen-Liste und kann direkt per Name aufgerufen werden — kein `@` nötig.

### Phiole über das Panel eingeben

1. Phiolen-Panel unten aufklappen (⚗️ Phiolen ▼)
2. Name eingeben (z.B. `add`)
3. Phiol Code eingeben (z.B. `|`)
4. `+ Hinzufügen` klicken

### .phi Datei hochladen

1. `📂 .phi laden` klicken
2. Eine oder mehrere `.phi` Dateien auswählen
3. Dateien werden automatisch als Phiolen registriert

### .phi Datei speichern

1. Name und Code eingeben
2. `💾 .phi speichern` klicken
3. Datei wird als `name.phi` heruntergeladen

### Standard Phiolen

| Phiole | Code | Beschreibung |
|--------|------|--------------|
| `add` | `\|` | Flush – Addition |
| `clr` | `<0 >0` | Kammern leeren |

### Primitive sind geschützt

Eingebaute Symbole (`< > + - * ~ ! | : " # ' ? ; §`) können nicht durch Phiolen überschrieben werden. Ein Versuch erzeugt eine Fehlermeldung.

---

## Schnellstart Beispiele

### Hello World
```
<42 "
```

### Addition
```
( 5 + 3 = 8 )
<5 >3 | <"
```

### Mit Phiole
```
§add { | }
<5 >3 add <"
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

## Step-Modus

Mit `→ Step` kann man den Code **Schritt für Schritt** ausführen:

1. Code eintippen
2. `→ Step` klicken
3. Jeder Klick führt einen Befehl aus
4. Das Glass Grid aktualisiert sich nach jedem Schritt

Ideal zum Debuggen und Verstehen wie Phiol funktioniert.

---

## Technische Details

Der Playground ist eine einzelne HTML-Datei ohne externe Abhängigkeiten:

- Reines JavaScript – kein Framework
- Tokenizer + Executor vollständig implementiert
- Unterstützt die komplette Phiol Syntax v0.2
- Kommentare mit `( )`
- Phiolen-Definition mit `§name { }` direkt im Code
- Direkter Phiolen-Aufruf per Name
- Phiolen werden als `.phi` Dateien gespeichert und geladen

---

## Änderungen in Version 0.2

| Was | Vorher | Jetzt |
|-----|--------|-------|
| Phiole definieren | `@def name { }` | `§name { }` |
| Phiole aufrufen | `@name` | `name` |
| Kommentare | Text wurde ignoriert | `( )` explizit |
| Dateiendung | `.fx` | `.phi` |
| Primitive schützen | — | Überschreiben verboten |

---

*Phiol Playground v0.2 · By Patrick Klingforth (Rick)* ⚗️
