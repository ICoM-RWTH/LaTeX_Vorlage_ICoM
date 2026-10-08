# ICoM LaTeX Vorlage / ICoM LaTeX Template

> **Lehrstuhl und Institut für Baumanagement, Digitales Bauen und Robotik im Bauwesen (ICoM)**
> RWTH Aachen University

---

## Inhaltsverzeichnis / Table of Contents

- [Deutsch](#deutsch)
- [English](#english)

---

<a id="deutsch"></a>

# Deutsch

## Überblick

Diese LaTeX-Vorlage ist für Bachelor- und Masterarbeiten am ICoM, RWTH Aachen konzipiert. Sie unterstützt **Deutsch** und **Englisch** als Hauptsprache.

## Schnellstart

1. **`config.tex` öffnen** und ausfüllen:
   - `\ThesisLanguage` → `1` für Deutsch, `2` für Englisch
   - `\ThesisType` → `1` für Bachelorarbeit, `2` für Masterarbeit
   - Name, Matrikelnummer, Titel, Betreuer, Prüfer, Abgabedatum
2. **Abkürzungen** in `Chapters/Acronyms_Definition.tex` definieren
3. **Literatur** in `Literatur/samplebibfile.bib` eintragen
4. **Eigene Kapitel** in `Chapters/` anlegen und in `Basis.tex` mit `\include{}` einbinden
5. **Hinweise zur Nutzung von KI** in `Chapters/V_KI_Hinweise.tex` an die eigene Nutzung anpassen (eingesetzte KI-Tools, Art, Zweck und Umfang sowie Verantwortungserklärung)
6. **Aufgabenstellung** als PDF unter `Chapters/Aufgabenstellung_dummy.pdf` ablegen und in `Basis.tex` einkommentieren
7. **Eidesstattliche Versicherung** als PDF unter `Chapters/EidesstattlicheVersicherung_dummy.pdf` ablegen und in `Basis.tex` einkommentieren
8. **Kompilieren** mit `pdflatex` → `biber` → `pdflatex` → `pdflatex`

## Dateistruktur

```
ICoM_Vorlage_Merged/
├── Basis.tex                          ← Hauptdatei (kompilieren!)
├── config.tex                         ← HIER DATEN EINTRAGEN
├── settings.tex                       ← Seitenlayout, Kopfzeile
├── Bilder/                            ← Abbildungen hier ablegen
│   └── rwth_icom_de_rgb.png
├── Chapters/
│   ├── 00_Deckblatt.tex               ← Titelseite (automatisch aus config.tex)
│   ├── Acronyms_Definition.tex        ← Abkürzungen definieren
│   ├── III_Kurzfassung.tex            ← Deutsche Kurzfassung
│   ├── IV_Abstract.tex                ← Englisches Abstract
│   ├── V_KI_Hinweise.tex              ← Hinweise zur Nutzung von KI (ausfüllen!)
│   ├── IX_mysymbols.tex               ← Symbolverzeichnis
│   ├── X_myformulas.tex               ← Formelverzeichnis
│   ├── 1_Einleitung.tex               ← Beispielkapitel
│   ├── 2_Theoretische Grundlagen.tex  ← Beispiele (Zitieren, Grafiken, Tabellen, Formeln)
│   ├── Konsultationsverzeichnis.tex   ← Konsultationsverzeichnis
│   ├── A_Anhang.tex                   ← Anhang
│   └── YY_Bearbeitungsinformationen.tex ← Anleitung (vor Abgabe entfernen!)
└── Literatur/
    └── samplebibfile.bib              ← Literaturquellen
```

## Editoren / Arbeitsumgebungen

> **Empfehlung:** Für Versionskontrolle und ein Cloud-Backup eignet sich ein **lokaler Editor** zusammen mit **Git** — siehe [Versionskontrolle mit Git / GitHub](#versionskontrolle-mit-git--github-empfohlen). Am einfachsten geht das mit **VS Code**, das Git bereits **eingebaut** hat (grafische Source-Control-Ansicht). In Overleaf ist die Git-Anbindung nur in der **kostenpflichtigen** Version verfügbar.
>
> **Lokal ohne Git arbeiten (etwas einfachere Variante):** Du kannst die Vorlage auch einfach als **ZIP herunterladen** (auf GitHub: grüner Button *Code* → *Download ZIP*), den Ordner **entpacken** und mit deinem Editor öffnen. Allerdings **ohne** Versionskontrolle und Cloud-Backup. Denk in diesem Fall selbst an regelmäßige Sicherungen (z. B. Sciebo, OneDrive).

### a) Overleaf (empfohlen für Einsteiger)

> **Hinweis:** Diese Vorlage ist für die kostenlose Overleaf-Version zu umfangreich (Kompilierzeit-Limit von 20 Sekunden). Tipps zum Verkleinern findest du unter [Fehlerbehebung → Overleaf Gratis-Version](#fehlerbehebung--troubleshooting).
>
> **Tipp:** Die RWTH Aachen stellt über Sciebo eine **Overleaf-Professional**-Lizenz kostenlos bereit. Damit entfällt das Kompilierzeit-Limit. Anmeldung mit dem RWTH-Account unter [rwth-aachen.sciebo.de](https://rwth-aachen.sciebo.de/).

1. ZIP dieser Vorlage erstellen
2. Auf Overleaf → *New Project* → *Upload Project*
3. In den **Projekteinstellungen** (Gear-Icon):
   - Compiler: **pdfLaTeX**
   - Main document: **Basis.tex**
4. Kompilieren (grüner Button oder Ctrl+Enter)

### b) VS Code + LaTeX Workshop (für Versionskontrolle mit Git)

1. [VS Code](https://code.visualstudio.com/) installieren
2. Extension **LaTeX Workshop** (James Yu) installieren
3. MiKTeX oder TeX Live lokal installieren (s.u.)
4. `Basis.tex` öffnen → Ctrl+Alt+B zum Kompilieren
5. PDF-Vorschau mit Ctrl+Alt+V

**Empfohlene `settings.json` für VS Code:**
```json
{
  "latex-workshop.latex.tools": [
    {
      "name": "pdflatex",
      "command": "pdflatex",
      "args": ["-synctex=1", "-interaction=nonstopmode", "-file-line-error", "%DOC%"]
    },
    {
      "name": "biber",
      "command": "biber",
      "args": ["%DOCFILE%"]
    }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "pdflatex → biber → pdflatex × 2",
      "tools": ["pdflatex", "biber", "pdflatex", "pdflatex"]
    }
  ]
}
```

### c) TeXstudio / Texmaker (lokal)

1. [MiKTeX](https://miktex.org/) (Windows) oder [TeX Live](https://tug.org/texlive/) (alle Plattformen) installieren
2. [TeXstudio](https://www.texstudio.org/) oder [Texmaker](https://www.xm1math.net/texmaker/) installieren
3. `Basis.tex` öffnen, Biber als Bibliographie-Tool einstellen
4. Kompilieren: F5 (oder Build & View)

## Fehlerbehebung / Troubleshooting

### Overleaf Gratis-Version: Kompilierzeit > 20 Sekunden

Die kostenlose Overleaf-Version begrenzt die Kompilierzeit auf **20 Sekunden**. Hier einige Tipps:

1. **Draft-Modus nutzen** — Bilder werden als Platzhalter geladen:
   ```latex
   \documentclass[11pt, draft]{scrreprt}
   ```
   Vor der finalen Abgabe `draft` entfernen!

2. **Bilder komprimieren** — Große PNG/JPG-Dateien vorher verkleinern:
   - Ziel: < 500 KB pro Bild
   - Vektorgrafiken (PDF) bevorzugen
   - Tools: [TinyPNG](https://tinypng.com/), [Squoosh](https://squoosh.app/)

3. **Nicht benötigte Kapitel auskommentieren** — In `Basis.tex`:
   ```latex
   % \include{./Chapters/2_Theoretische Grundlagen}
   ```

4. **Auxiliary-Dateien bereinigen** — In Overleaf: *Logs and output files* → *Clear cached files*

5. **Weniger Pakete laden** — Ungenutzte `\usepackage{}`-Zeilen in `Basis.tex` auskommentieren

6. **`\listoffigures` / `\listoftables` temporär auskommentieren** — Diese benötigen zusätzliche Kompilierläufe

### Biber / Bibliographie funktioniert nicht

- Sicherstellen, dass Biber (nicht BibTeX) als Backend eingestellt ist
- Kompilierreihenfolge einhalten: `pdflatex` → `biber` → `pdflatex` → `pdflatex`
- In Overleaf: Einstellung prüfen (pdfLaTeX + Biber ist Standard)

### Abkürzungen erscheinen nicht im Verzeichnis

- Die Vorlage nutzt `print-only-used`: nur im Text verwendete Abkürzungen werden gedruckt
- Prüfen, ob `\ac{kürzel}` mindestens einmal im Text verwendet wird

### Umlaute / Sonderzeichen werden falsch dargestellt

- Datei muss in **UTF-8** gespeichert sein (Standard in allen modernen Editoren)

---

<a id="english"></a>

# English

## Overview

This LaTeX template is designed for Bachelor's and Master's theses at ICoM, RWTH Aachen University. It supports both **German** and **English** as the main language — controlled by a single variable.

## Quick Start

1. **Open `config.tex`** and fill in:
   - `\ThesisLanguage` → `1` for German, `2` for English
   - `\ThesisType` → `1` for Bachelor's Thesis, `2` for Master's Thesis
   - Name, matriculation number, title, supervisors, examiners, submission date
2. **Define abbreviations** in `Chapters/Acronyms_Definition.tex`
3. **Add references** to `Literatur/samplebibfile.bib`
4. **Create your chapters** in `Chapters/` and include them in `Basis.tex` with `\include{}`
5. **Notes on the use of AI**: adapt `Chapters/V_KI_Hinweise.tex` to your own use (AI tools used, type, purpose and extent, statement of responsibility)
6. **Place your task description** PDF at `Chapters/Aufgabenstellung_dummy.pdf` and uncomment in `Basis.tex`
7. **Place your statutory declaration** PDF at `Chapters/EidesstattlicheVersicherung_dummy.pdf` and uncomment in `Basis.tex`
8. **Compile** with `pdflatex` → `biber` → `pdflatex` → `pdflatex`

## File Structure

```
ICoM_Vorlage_Merged/
├── Basis.tex                          ← Main file (compile this!)
├── config.tex                         ← ENTER YOUR DATA HERE
├── settings.tex                       ← Page layout, headers
├── Bilder/                            ← Place your images here
│   └── rwth_icom_de_rgb.png
├── Chapters/
│   ├── 00_Deckblatt.tex               ← Cover page (auto-filled from config.tex)
│   ├── Acronyms_Definition.tex        ← Define abbreviations
│   ├── III_Kurzfassung.tex            ← German abstract
│   ├── IV_Abstract.tex                ← English abstract
│   ├── V_KI_Hinweise.tex              ← Notes on the use of AI (fill in!)
│   ├── IX_mysymbols.tex               ← List of symbols
│   ├── X_myformulas.tex               ← List of equations
│   ├── 1_Einleitung.tex               ← Example chapter
│   ├── 2_Theoretische Grundlagen.tex  ← Examples (citing, figures, tables, equations)
│   ├── Konsultationsverzeichnis.tex   ← Consultation directory
│   ├── A_Anhang.tex                   ← Appendix
│   └── YY_Bearbeitungsinformationen.tex ← Instructions (remove before submission!)
└── Literatur/
    └── samplebibfile.bib              ← Bibliography entries
```

## Editors / Environments

> **Recommendation:** For productive work, use a **local editor** together with **Git** — see [Version control with Git / GitHub](#version-control-with-git--github-recommended). That gives you version control and a cloud backup from the start. The easiest way is **VS Code**, which has Git **built in** (graphical Source Control view). In Overleaf, Git integration is only available in the **paid** version.
>
> **Working without Git (easiest option):** You can also simply **download the template as a ZIP** (on GitHub: green *Code* button → *Download ZIP*), **unzip** the folder and open it in your editor. Fast and requires no prior knowledge — but **without** version control or automatic cloud backup. In that case, remember to make regular backups yourself (e.g. Sciebo, OneDrive).

### a) Overleaf (recommended for beginners)

> **Note:** This template is too large for the free Overleaf tier (20-second compile-time limit). See [Troubleshooting → Overleaf Free Tier](#troubleshooting) for ways to reduce it.
>
> **Tip for RWTH members:** RWTH Aachen provides a free **Overleaf Professional** license via Sciebo, which removes the compile-time limit. Sign in with your RWTH account at [rwth-aachen.sciebo.de](https://rwth-aachen.sciebo.de/).

1. Create a ZIP of this template
2. Go to Overleaf → *New Project* → *Upload Project*
3. In **Project Settings** (gear icon):
   - Compiler: **pdfLaTeX**
   - Main document: **Basis.tex**
4. Compile (green button or Ctrl+Enter)

### b) VS Code + LaTeX Workshop

1. Install [VS Code](https://code.visualstudio.com/)
2. Install the **LaTeX Workshop** extension (James Yu)
3. Install MiKTeX or TeX Live locally (see below)
4. Open `Basis.tex` → Ctrl+Alt+B to compile
5. PDF preview with Ctrl+Alt+V

**Recommended `settings.json` for VS Code:**
```json
{
  "latex-workshop.latex.tools": [
    {
      "name": "pdflatex",
      "command": "pdflatex",
      "args": ["-synctex=1", "-interaction=nonstopmode", "-file-line-error", "%DOC%"]
    },
    {
      "name": "biber",
      "command": "biber",
      "args": ["%DOCFILE%"]
    }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "pdflatex → biber → pdflatex × 2",
      "tools": ["pdflatex", "biber", "pdflatex", "pdflatex"]
    }
  ]
}
```

### c) TeXstudio / Texmaker (local)

1. Install [MiKTeX](https://miktex.org/) (Windows) or [TeX Live](https://tug.org/texlive/) (all platforms)
2. Install [TeXstudio](https://www.texstudio.org/) or [Texmaker](https://www.xm1math.net/texmaker/)
3. Open `Basis.tex`, set Biber as the bibliography tool
4. Compile: F5 (or Build & View)

## Troubleshooting

### Overleaf Free Tier: Compile time > 20 seconds

The free Overleaf version limits compile time to **20 seconds**. Tips to stay within the limit:

1. **Use draft mode** — images load as placeholders:
   ```latex
   \documentclass[11pt, draft]{scrreprt}
   ```
    Remove `draft` before final submission!

2. **Compress images** — reduce large PNG/JPG files:
   - Target: < 500 KB per image
   - Prefer vector graphics (PDF)
   - Tools: [TinyPNG](https://tinypng.com/), [Squoosh](https://squoosh.app/)

3. **Comment out unused chapters** — in `Basis.tex`:
   ```latex
   % \include{./Chapters/2_Theoretische Grundlagen}
   ```

4. **Clear auxiliary files** — in Overleaf: *Logs and output files* → *Clear cached files*

5. **Remove unused packages** — comment out unused `\usepackage{}` lines in `Basis.tex`

6. **Temporarily comment out `\listoffigures` / `\listoftables`** — these require extra compile passes

### Biber / Bibliography not working

- Make sure Biber (not BibTeX) is set as the backend
- Follow the correct compilation order: `pdflatex` → `biber` → `pdflatex` → `pdflatex`
- On Overleaf: check settings (pdfLaTeX + Biber is the default)

### Abbreviations not showing in the list

- This template uses `print-only-used`: only abbreviations used in the text are printed
- Check that `\ac{abbreviation}` is used at least once in the text

### Umlauts / special characters display incorrectly

- Files must be saved in **UTF-8** encoding (default in all modern editors)
