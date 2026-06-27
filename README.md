# Sketch MeaZure (meaZure26)

**Sketch-Plugin zum Markieren von Design-Specs und zum Exportieren von Spec-Dokumenten.**
Dieses Repo ist der **öffentliche Release-/Distributionskanal** des Plugins: es enthält die
gepackten Build-Artefakte (`*.sketchplugin` in `*.zip`) und den Sparkle-Appcast für die
automatische Update-Prüfung in Sketch. **Hier liegt kein Quellcode** — der wird separat
gepflegt (siehe [Beziehung zu `meaZure`](#beziehung-zu-meazure)).

> ⚠️ **Keine kanonische Design-Spec vorhanden.** Diese Doku spiegelt den
> **Implementierungs-Stand** (aus dem Repo-Inhalt und den gepackten Artefakten gelesen am
> 2026-06-27), nicht das Zieldesign. Fehlen eines Features hier = „noch nicht
> dokumentiert / nicht im Release-Artefakt sichtbar", nicht „nicht gewollt". Der Quellcode
> liegt in einem anderen Repo (`N0TB0T/meaZure`, privat) — für autoritative Aussagen über
> Implementierungsdetails dort nachsehen.

---

## Was dieses Repo ist

`meaZure26` ist ein **Veröffentlichungs-Repo**, kein Source-Repo. Der Tree enthält
ausschließlich:

| Datei | Zweck |
|---|---|
| `SketchMeaZure-<version>-<datum>.zip` | Gepacktes, installierbares Plugin-Bundle (`sketch-meazure.sketchplugin`). Als Git-`binary` markiert (`.gitattributes`). |
| `appcast.xml` | Sparkle-Appcast (RSS). Listet die verfügbaren Versionen als `<enclosure>`-URLs für Sketchs automatische Update-Prüfung. |
| `README.md` | Diese Datei. |
| `.gitattributes` | `*.zip binary`. |

Aktuelle Version laut Tree: **3.4.7 (2026-05-21)**.

Die gepackten Bundles bestehen aus kompilierten/gebündelten Assets — u. a.
`Contents/Sketch/mark_bundle.js` (gebündeltes Plugin-Skript), `Contents/Sketch/manifest.json`
(Sketch-Plugin-Manifest), HTML-Panels unter `Contents/Resources/panel/`, ein Export-Template
(`Contents/Resources/template.html`) und i18n-Dateien (`zh-cn`, `zh-tw`). Diese Artefakte
sind **Build-Output**, nicht der bearbeitbare Quellcode.

## Funktionsumfang (aus dem Plugin-Manifest gelesen)

Das Manifest (`manifest.json`, Version 3.4.7) registriert u. a. folgende Sketch-Befehle:

- **Spec Export** (`ctrl shift e`) — exportiert ein Spec-Dokument
- **Toolbar** (`ctrl shift b`)
- **Mark Overlay / Sizes / Spacings / Properties / Note / Coordinate** (`ctrl shift 1`…`6`)
- **Toggle Hidden** (`ctrl shift h`), **Toggle Locked** (`ctrl shift l`)
- **Clear Marks**, **Settings**, **Rename Old Markers**, **Run Script**
- **Feedback**, **Home** (Links), **Init** (`OpenDocument`-Action-Handler)

Manifest-Metadaten: `name`/`identifier` = „Sketch MeaZure", `description` = „Spec Exports Only",
`homepage` und `appcast` zeigen auf dieses Repo (`N0TB0T/meaZure26`).

## Installation

1. Aktuelles Zip herunterladen:
   [SketchMeaZure-3.4.7-20260521.zip](https://github.com/N0TB0T/meaZure26/raw/main/SketchMeaZure-3.4.7-20260521.zip)
2. Entzippen — es erscheint `sketch-meazure.sketchplugin`.
3. Doppelklick auf die `.sketchplugin` — Sketch installiert das Plugin automatisch.

### Automatische Updates

Nach der Installation prüft Sketch über den Sparkle-Appcast
(`https://raw.githubusercontent.com/N0TB0T/meaZure26/main/appcast.xml`, im Manifest
hinterlegt) automatisch auf neue Versionen und bietet die Installation an — kein manueller
Download nötig.

## Beziehung zu `meaZure`

Aus Code, Manifest und Commit-Historie ablesbarer Stand:

- **`N0TB0T/meaZure`** (privat, GitHub-Primärsprache TypeScript; enthält `src/`, `ui/`,
  `package.json`, `webpack.skpm.config.js`, `tsconfig.json`, `autobuild.sh`) ist das
  **Quell-/Build-Repo**.
- **`N0TB0T/meaZure26`** (dieses Repo, öffentlich) ist der **Release-/Distributionskanal**:
  Es nimmt die aus `meaZure` gebauten `.sketchplugin`-Bundles auf und stellt sie samt
  Appcast öffentlich zum Download bereit.
- Diese Aufteilung ist in der Quell-Historie belegt — ein Commit dort lautet
  „appcast auf meaZure26 (public) korrigiert". Das gebündelte Manifest verweist mit
  `homepage` und `appcast` ebenfalls auf `meaZure26`.

Beide Repos teilen dieselbe Versionslinie (3.4.7 ist der jeweils jüngste Stand). Frühere
Versionen (≤ 3.3.4) wurden noch über GitHub-Releases im `meaZure`-Repo unter dem
Dateinamen `sketch-meaxure.sketchplugin.zip` verteilt (siehe ältere `<enclosure>`-Einträge
im Appcast).

### Herkunft / Lineage

Die mitgelieferte `LICENSE` im Bundle ist **MIT, © 2014 utom**. Zusammen mit den
Legacy-Dateinamen `sketch-meaxure.sketchplugin.zip` deutet das auf eine Abstammung von der
**sketch-measure / MeaXure**-Plugin-Linie hin. Dieses Repo führt diese Linie als
„Sketch MeaZure" fort. (Genauer Fork-Punkt und Umfang der Eigenänderungen sind nur im
Quell-Repo `meaZure` bestimmbar.)

## Versionshistorie

> Die folgende Historie ist aus den Commit-Messages und dem bisherigen README dieses Repos
> übernommen.

### 3.4.7 (2026-05-21)
- Fix: `CSSAttributes`-Fehler für bestimmte Layer-Typen (CocoaScript-`typeof`-Check
  unzuverlässig → try-catch).

### 3.4.6 (2026-05-21)
- 1× PNG direkt im Exportordner (Root) statt in `preview/`; Retina (`-2x`) bleibt in
  `preview/`.

### 3.4.5 (2026-05-20)
- Bei einzelnem Artboard-Export: Artboard-Name als Vorschlag für den Exportordner (statt
  Dokumentname). *(Kein eigenes Zip im Tree; im Quell-Repo als Commit vorhanden.)*

### 3.4.4 (2026-05-20)
- Fix: unscharfes Vorschaubild im Viewer — Viewer nutzt jetzt die 2×-Retina-Version.

### 3.4.2 (2026-05-20)
- Windows-kompatible Dateinamen: Umlaute transliteriert (ä→ae, …, ß→ss), `@` erhalten,
  Originalschreibweise beibehalten.
- Vorschaubilder: 1× nativ + 2× Retina (`-2x`-Suffix), beide im `preview/`-Ordner.
- Unabhängige Rahmenbreiten (Sketch 2026.1+): seitenweise Dicke in der Spec; nur aktive
  Seiten angezeigt (z. B. `L:4px`), Rundum-Rahmen ohne Präfix.

### 3.3.5 (2026-04-17)
- Fix: CSS-Attribut-Export kompatibel mit Sketch 2025.3+ (`CSSAttributeString`).

### 3.3.4 (2026-03-02)
- Siehe `SketchMeaZure-3.3.4-20260302.zip`.

## Lizenz

MIT (Lizenztext liegt im Plugin-Bundle: `Contents/Resources/LICENSE`, © 2014 utom).

---

## Bekannte offene Punkte / Unsicherheiten

- **Appcast-Selbstlink:** Der `<link>` in `appcast.xml` zeigt auf
  `raw.githubusercontent.com/N0TB0T/meaZure/main/appcast.xml` (das private Quell-Repo),
  während `<enclosure>`-URLs und das Manifest auf `meaZure26` zeigen. Beobachteter Stand,
  hier nicht „korrigiert" — Klärung gehört ins Quell-Repo, das den Appcast generiert.
- **Kein Quellcode in diesem Repo:** Build- und Entwicklungsanleitung (skpm/webpack)
  existieren nur im Quell-Repo `N0TB0T/meaZure`. Dieses README dokumentiert bewusst nur den
  Distributionskanal.
- **3.4.5** ist in der Quell-Historie als Version vorhanden, hat aber kein eigenes
  Zip-Artefakt in diesem Tree (Sprung 3.4.4 → 3.4.6 bei den ausgelieferten Bundles).
