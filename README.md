# Druckkosten-Rechner

<img src="https://github.com/Applejuice-DE/PDF-Druckkosten-Rechner/blob/main/Screenshot_DK.png" width="60%"></img>


Ein browserbasierter Rechner zur ungefähren Ermittlung der Druckkosten
mehrseitiger PDF-Dokumente.

Der Rechner analysiert jede PDF-Seite, ermittelt die durchschnittliche
Farbdeckung der Kanäle Cyan, Magenta, Yellow und Black und berechnet daraus
einen geschätzten Seiten- und Dokumentpreis.

> **Hinweis:** Dieses Projekt wurde im Rahmen von Vibe Coding mit Unterstützung
> von künstlicher Intelligenz erstellt. Der Code wurde iterativ durch
> natürliche Sprache beschrieben, erzeugt und angepasst. Vor einem produktiven
> Einsatz sollte der Code fachlich geprüft, getestet und gegebenenfalls
> weiterentwickelt werden.

---

## Funktionen

- Analyse mehrseitiger PDF-Dokumente.
- Automatische Erkennung des Seitenformats.
- Umrechnung abweichender Seitenformate auf eine A4-Flächenbasis.
- Auswertung der ungefähren Farbdeckung für:
  - Cyan
  - Magenta
  - Yellow
  - Black
- Berechnung der Gesamtdeckung pro Seite.
- Einstellbarer Preis für eine A4-Seite bei 5 % Gesamtdeckung.
- Standardpreis von 0,9 Cent pro A4-Seite bei 5 % Gesamtdeckung.
- Einstellbare Renderauflösung, standardmäßig 300 DPI.
- Anzeige der geschätzten Kosten je PDF-Seite in Euro.
- Anzeige des Gesamtpreises für das gesamte Dokument.
- Export der Ergebnisse als CSV-Datei.
- Semikolon-getrennte CSV-Spalten für die Verwendung mit deutschen
  Tabellenkalkulationsprogrammen.
- Die PDF-Datei wird vollständig lokal im Browser verarbeitet.

---

## Berechnungsgrundlage

Der Preis basiert auf einer DIN-A4-Seite mit einer angenommenen
Gesamtfarbdeckung von 5 %.

Die Farbdeckung wird näherungsweise über die gerenderte Darstellung der
PDF-Seite ermittelt:

```text
Gesamtdeckung = Cyan + Magenta + Yellow + Black
```

Die ungefähren Kosten einer Seite werden nach folgendem Modell berechnet:

```text
Kosten =
(Gesamtdeckung / 5)
× Preis einer A4-Seite bei 5%
× A4-Flächenfaktor
```

Der A4-Flächenfaktor berücksichtigt die tatsächliche Größe der PDF-Seite im
Verhältnis zu DIN A4.

Der Gesamtpreis des Dokuments entspricht der Summe der Kosten aller Seiten.

---

## Technischer Hinweis zur Farbauswertung

Die PDF-Seiten werden mit PDF.js im Browser gerendert. Das Canvas-Rendering im
Browser liefert normalerweise RGB-Pixeldaten. Daher wird die Farbdeckung in
dieser Version aus den gerenderten RGB-Werten näherungsweise in CMYK-Werte
umgerechnet.

Die Anwendung liest nicht garantiert die ursprünglichen CMYK-Objekte oder
ICC-Profile aus der PDF-Datei aus. Deshalb handelt es sich um eine
Orientierungsberechnung und nicht um eine verbindliche Druckvorstufen- oder
Preflight-Analyse.

Für eine produktionsgenaue Analyse wären unter anderem folgende Punkte
erforderlich:

- Direkte Auswertung der PDF-Farbräume.
- Berücksichtigung eingebetteter ICC-Profile.
- Verwendung eines definierten Druckstandards.
- Berücksichtigung von Transparenzen, Überdrucken und Sonderfarben.
- Abstimmung mit dem konkreten Druckverfahren und Druckdienstleister.

## Änderungen in Beta3
- Neue Funktion für abweichenden Farbtintenpreis (optional)
- Kalkulation von Druckkopf-Reinigungskosten des Druckers (optional)

---

# English Version

## Print Cost Calculator

A browser-based tool for estimating the approximate printing costs of
multi-page PDF documents.

The calculator analyzes every PDF page, determines the approximate average
coverage of the Cyan, Magenta, Yellow and Black channels, and calculates an
estimated page and document price from these values.

> **Note:** This project was created through Vibe Coding with the assistance of
> artificial intelligence. The code was generated and refined iteratively
> using natural-language descriptions. Before production use, the code should
> be reviewed, tested and further developed where necessary.

---

## Features

- Analysis of multi-page PDF documents.
- Automatic detection of page dimensions.
- Conversion of non-A4 page sizes to an A4 area basis.
- Approximate coverage analysis for:
  - Cyan
  - Magenta
  - Yellow
  - Black
- Calculation of total coverage per page.
- Configurable price for an A4 page at 5% total coverage.
- Default price of 0.9 cents for an A4 page at 5% total coverage.
- Configurable rendering resolution, set to 300 DPI by default.
- Display of estimated costs per PDF page in euros.
- Display of the total document price.
- CSV export.
- Semicolon-separated CSV columns for use with spreadsheet software.
- Complete local processing of the PDF in the browser.

---

## Calculation Model

The price is based on an A4 page with an assumed total color coverage of 5%.

The color coverage is approximately determined from the rendered PDF page:

```text
Total coverage = Cyan + Magenta + Yellow + Black
```

The estimated cost of a page is calculated using the following model:

```text
Cost =
(Total coverage / 5)
× Price of an A4 page at 5%
× A4 area factor
```

The A4 area factor takes the actual PDF page size into account relative to
DIN A4.

The total document price is the sum of the costs of all pages.

---

## Technical Color Analysis Note

The PDF pages are rendered in the browser using PDF.js. Browser canvas
rendering normally provides RGB pixel data. Therefore, this version
approximately converts the rendered RGB values into CMYK coverage values.

The application does not guarantee that it reads the original CMYK objects or
ICC profiles embedded in the PDF. Consequently, the result is intended as an
estimate rather than a production-grade prepress or billing analysis.

Production-grade analysis would require, among other things:

- Direct inspection of PDF color spaces.
- Support for embedded ICC profiles.
- A defined printing standard.
- Handling of transparency, overprinting and spot colors.
- Consideration of the actual printing process and service provider.

## Changes in Beta3
- New feature for different color ink prices (optional)
- Calculation of printer printhead cleaning costs (optional)

---

