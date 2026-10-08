# Unterschiede: Veröffentlichte Version vs. Arbeitsversion

**Vergleich:** `ICoM_LaTex_Vorlage_2025-10-17` (letzte veröffentlichte Version) ↔ `ICoM_Vorlage_Merged` (Arbeitsversion)

---

## Überblick

Die Arbeitsversion ist ein Merge aus mehreren ICoM-Vorlagen (inkl. Verbesserungen von Yannick/Fabian Edenhofner). Sie ist **zweisprachig**, **zentral konfigurierbar** und verwendet modernere LaTeX-Pakete.

---

## Wesentliche Änderungen

| Bereich | Veröffentlicht (2025-10-17) | Arbeitsversion (Merged) |
|---|---|---|
| **Sprache** | Nur Deutsch (fest) | Deutsch **oder** Englisch, umschaltbar über `\ThesisLanguage` |
| **Konfiguration** | Daten verteilt im Code | Zentral in neuer Datei `config.tex` (Name, Titel, Betreuer, Datum, Arbeitstyp) |
| **Deckblatt** | Statisch | Parametrisiert (Bachelor/Master + Sprache, automatische Datenübernahme aus `config.tex`) |
| **Abkürzungen** | Paket `acronym` + `VIII_myglossary.tex` | Modernes Paket `acro` + neue Datei `Acronyms_Definition.tex` (nur verwendete Abkürzungen werden gedruckt) |
| **Fußnoten** | Pro Kapitel zurückgesetzt | Durchgehende Nummerierung (`chngcntr` / `\counterwithout`) |
| **Anleitung** | – | Neues Kapitel `YY_Bearbeitungsinformationen.tex` (vor Abgabe entfernen) |
| **KI-Hinweise** | – | Neues Kapitel `V_KI_Hinweise.tex` (zweisprachig) direkt nach dem Abstract: Dokumentation der Nutzung von KI-Tools inkl. Verantwortungserklärung |
| **Dokumentation** | – | Neue `README.md` (Setup, Editoren, Troubleshooting) |

---

## Neue Pakete in der Arbeitsversion

- `acro` (ersetzt `acronym`)
- `chngcntr` – durchgehende Fußnotennummerierung
- `placeins` – `\FloatBarrier` zur Float-Steuerung
- `comment` – mehrzeilige Kommentare `\begin{comment}...\end{comment}`
- `varwidth` – variable Minipage-Breite
- `makecell` – Formatierung einzelner Tabellenzellen

## Entfernte / ersetzte Pakete

- `acronym`, `glossaries` → ersetzt durch `acro`
- Doppelte/redundante `\usepackage`-Aufrufe bereinigt (z. B. doppeltes `babel`, `amsmath`, `rotating`)

---

## Struktur- und Code-Änderungen

- **`config.tex`** (neu): zentrale Benutzerkonfiguration mit `\ThesisLanguage`, `\ThesisType`, Name, Matrikelnummer, Titel (DE/EN), Betreuer, Prüfer, Abgabedatum.
- **`settings.tex`**: aufgeräumt — `geometry` (Seitenränder) ist nach `Basis.tex` verschoben; auskommentierte Altlasten entfernt.
- **`Basis.tex`**: durchgängig zweisprachig über `\ifnum\ThesisLanguage=1 ... \else ... \fi`; `\hypersetup{pageanchor=...}` am Deckblatt; `\emergencystretch=3em` gegen Overfull-Boxen; biblatex-`shortauthor`-Fix für APA-Stil.
- **Aufgabenstellung & Eidesstattliche Versicherung**: jetzt standardmäßig auskommentiert (PDF selbst einfügen).
- **`.vscode/tasks.json`** (neu): Task „Export ZIP" für saubere Weitergabe ohne Build-Artefakte.

---

## Geänderte / neue Dateien

**Neu:** `config.tex`, `README.md`, `Chapters/Acronyms_Definition.tex`, `Chapters/V_KI_Hinweise.tex`, `Chapters/YY_Bearbeitungsinformationen.tex`, `.vscode/tasks.json`

**Entfernt:** `Chapters/VIII_myglossary.tex` (durch `Acronyms_Definition.tex` ersetzt)

**Geändert:** `Basis.tex`, `settings.tex`, `Chapters/00_Deckblatt.tex` (und weitere Kapitel an die Zweisprachigkeit angepasst)
