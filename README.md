# Sketch MeaZure

**Nur Spec-Exports** — Ein Sketch-Plugin zum Exportieren von Design-Specs.

## Download

[SketchMeaZure-3.4.7-20260521.zip](https://github.com/N0TB0T/meaZure26/raw/main/SketchMeaZure-3.4.7-20260521.zip)

## Installation

1. Zip-Datei herunterladen
2. Entzippen — es erscheint `sketch-meazure.sketchplugin`
3. Doppelklick auf die `.sketchplugin`-Datei — Sketch installiert das Plugin automatisch

## Automatische Updates

Nach der Installation benachrichtigt Sketch automatisch, wenn eine neue Version verfügbar ist, und bietet die Installation an — kein manueller Download nötig.

## Versionshistorie

### 3.4.7 (2026-05-21)

- Fix: `CSSAttributes`-Fehler für bestimmte Layer-Typen (CocoaScript `typeof`-Check unzuverlässig → try-catch)

### 3.4.6 (2026-05-21)

- **1× PNG direkt im Exportordner** (root), nicht mehr in `preview/`; Retina (`-2x`) bleibt in `preview/`

### 3.4.5 (2026-05-20)

- Bei einzelnem Artboard-Export: Artboard-Name als Vorschlag für den Exportordner (statt Dokumentname)

### 3.4.4 (2026-05-20)

- Fix: Vorschaubild im Viewer war unscharf — Viewer nutzt jetzt die 2× Retina-Version

### 3.4.2 (2026-05-20)

- **Windows-kompatible Dateinamen**: Umlaute transliteriert (ä→ae, Ä→Ae, ö→oe, Ö→Oe, ü→ue, Ü→Ue, ß→ss), `@` erhalten, Originalschreibweise beibehalten
- **Vorschaubilder**: 1× nativ + 2× Retina (`-2x`-Suffix), beide im gleichen `preview/`-Ordner
- **Unabhängige Rahmenbreiten** (Sketch 2026.1+): seitenweise Dicke in der Spec; nur aktive Seiten angezeigt (z.B. `L:4px`), rundum-Rahmen ohne Präfix

### 3.3.5 (2026-04-17)

- Fix: CSS-Attribut-Export kompatibel mit Sketch 2025.3+ (`CSSAttributeString`)

### 3.3.4 (2026-03-02)

- siehe [SketchMeaZure-3.3.4-20260302.zip](SketchMeaZure-3.3.4-20260302.zip)
