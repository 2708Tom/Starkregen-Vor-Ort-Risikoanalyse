# Starkregen: Risikoanalyse vor Ort

**Gefahr aus der Karte, Verwundbarkeit von der Straße: ein Werkzeug, um das Überflutungsrisiko eines Objekts zu bewerten, und zwar Eintrittsstelle für Eintrittsstelle.**

Geeignet für alles, wo Wasser von außen eindringen kann: Tiefgaragen, Unterführungen, U-Bahn-Zugänge, Kellereingänge, Lichtschächte, Untergeschosse von Krankenhäusern oder Pflegeheimen, Trafostationen.

## Die Idee

Starkregengefahrenkarten zeigen, wo sich Wasser sammelt. Ob es in ein Bauwerk läuft, entscheiden Schwellen, Einläufe, Gefälle und deren Zustand, und die stehen in keiner Karte. Darum gilt hier nicht *Wahrscheinlichkeit × Schaden*, sondern:

> **Risiko = f(Gefahr, Verwundbarkeit)**

Die **Gefahr** ist der Wasserstand an der Eintrittsstelle laut Karte. Die **Verwundbarkeit** kommt aus einer Begehung. Erst beides zusammen zeigt, wo der **Kipppunkt** liegt, ab dem das Risiko sprunghaft steigt.

![Ablauf](abbildungen/forschungsdesign.png)

## Was man braucht

- eine Starkregengefahrenkarte, z. B. die bundesweite *Hinweiskarte Starkregengefahren* des BKG oder eine kommunale Karte
- das [Erfassungsprotokoll](werkzeug/erfassungsprotokoll.docx) (Word), Zollstock und Kamera
- die Excel [`werkzeug/starkregen_vor_ort.xlsx`](werkzeug/starkregen_vor_ort.xlsx) mit drei Blättern: *Anleitung*, *Eingabe*, *Ergebnis*. Gelbe Felder sind Eingaben, graue werden berechnet.

## So geht es

**1. Eintrittsstellen festlegen.** Jede Öffnung, über die Wasser eindringen kann, bekommt eine ID: Treppe, Rampe, Tür, Lichtschacht, Einfahrt, Aufzug.

**2. Gefahr ablesen.** An jeder Eintrittsstelle den Wasserstand aus der Karte ablesen, und zwar dort, wo Wasser eintreten würde (oberste Stufe, Kante der Einfahrt). Unter 10 cm ist die Gefahr gering, 10 bis 30 cm mittel, über 30 cm hoch.

**3. Begehen.** Je Eintrittsstelle ein Erfassungsprotokoll ausfüllen und Fotos machen. Alles wird von 1 (günstig) bis 5 (ungünstig) eingeschätzt:

| Kategorie (Gewicht) | Faktoren | 1 | 5 |
|---|---|---|---|
| **Bauliche Struktur** (20 %) | Schwellenhöhe | ≥ 15 cm | keine Schwelle |
| | Gefälle zur Öffnung | steigt zur Öffnung an | starkes Gefälle zur Öffnung |
| | Direktschutz | überdacht oder geschlossen | offen |
| **Entwässerung** (40 %) | Einlauf/Rinne vor der Öffnung | frei | verstopft oder keiner vorhanden |
| **Umfeld** (20 %) | Mikrotopografie, Versiegelung (5 m), Einläufe (20 m), Baustellen (20 m) | leitet ab, grün, frei, keine | leitet hin, versiegelt, verstopft, großflächig |
| **Schutzziel Mensch** (10 %) | Entfluchtung, Warnung | sicherer Vorplatz, redundante Warnung | Straßenverkehr, keine Warnung |
| **Technik im Inneren** (10 %) | Energie, IT/Kommunikation, Förder-/Gebäudetechnik | nicht vorhanden | exponiert (geschützt = 3) |

Die Entwässerung zählt am meisten, weil ein verstopfter Einlauf das System kippen lässt.

**4. Eintragen.** Im Blatt *Eingabe* eine Zeile je Eintrittsstelle. Das Protokoll nennt bei jedem Feld die passende Spalte (→ A, → B …).

**5. Ergebnis ablesen.** Das Blatt *Ergebnis* zeigt für jede Eintrittsstelle die Kategorien, den **Verwundbarkeitsindex** (bis 2 gering, bis 4 mittel, darüber hoch), das **Risiko** und das **Risiko bei Versagen**. Daneben steht die **Ergebnismatrix**: In jedem Feld stehen die IDs der Eintrittsstellen, die Farbe zeigt das Risiko.

| Gefahr ↓ · Verwundbarkeit → | gering | mittel | hoch |
|---|---|---|---|
| **hoch** | 🟨 niedrig | 🟧 mittel | 🟥 hoch |
| **mittel** | 🟩 kein | 🟨 niedrig | 🟧 mittel |
| **gering** | 🟩 kein | 🟩 kein | 🟨 niedrig |

*Bei Versagen* heißt: Der Schutz fällt aus, etwa weil Laub den Einlauf verstopft, und die Eintrittsstelle rutscht in die Spalte „hoch“. Springt das Risiko dabei, liegt dort ein **Kipppunkt**. Eintrittsstellen mit hoher Gefahr und Kipppunkt sind die ersten Kandidaten für Maßnahmen. Oft hilft schon eine regelmäßige Reinigung der Einläufe vor der Starkregensaison.

Gewichte und Grenzwerte stehen oben im Blatt *Ergebnis* und lassen sich anpassen.

## Beispiel: U-Bahn-Haltestelle Steinstraße/Königsallee, Düsseldorf

[`beispiel/beispiel_u-bahn_steinstrasse.xlsx`](beispiel/beispiel_u-bahn_steinstrasse.xlsx): 9 Zugänge, begangen am 11. April 2026, Wasserstände aus dem Szenario „extrem“.

![Gefahrenkarte mit Zugängen](abbildungen/gefahrenkarte.png)

| Zugang T6 | Einlaufgitter an T6 |
|---|---|
| ![Zugang](abbildungen/zugang_t6.jpg) | ![Einlaufgitter](abbildungen/einlaufgitter_t6.jpg) |

Ergebnismatrix der Station (mittlerer Index 2,50, alle Zugänge mit mittlerer Verwundbarkeit):

| Gefahr ↓ · Verwundbarkeit → | gering | mittel | hoch |
|---|---|---|---|
| **hoch** | | 🟧 **T1** (40 cm) | |
| **mittel** | | 🟨 T2 · T3 · T6 · T8 | |
| **gering** | | 🟩 A1 · T4 · T5 · T7 | |

Solange die Einläufe frei sind, hält die Station. Verstopfen sie, springt jeder Zugang eine Stufe nach oben, und T1 landet im roten Feld. Zum Vergleich: Ab etwa 0,35 m Wassertiefe bei 0,5 m/s kann ein Kind den Halt verlieren. Beim Aufzug A1 zeigt die Karte 0 cm, obwohl die Straße daneben überflutet ist. Das ist vermutlich ein Artefakt des Rasters, und deshalb gehört die Begehung dazu.

## Grenzen

- Gefahrenkarten im 1-m-Raster glätten: Schwellen und Einläufe fehlen. Manche Karten rechnen ohne Kanalnetz und sind damit bewusst ungünstig.
- Die Begehung ist eine Momentaufnahme. Laub und Wartung ändern den Zustand der Einläufe ständig.
- Die Einschätzungen sind subjektiv. Fotos und eine zweite Person, die unabhängig bewertet, sichern sie ab.
- Gewichte und Grenzwerte sind begründet, aber nicht empirisch hergeleitet.

## Herkunft

Methode von Hendrik Platz und Tom Thum, entwickelt im Modul Naturgefahren und -risiken (Prof. Dr. Alexander Fekete), Institut für Rettungsingenieurwesen und Gefahrenabwehr, TH Köln, 2026. Die ursprüngliche Anwendung: [Steckbrief in RIW-Projekte](https://github.com/2708Tom/RIW-Projekte/tree/main/2026-07_NGR_Starkregen-U-Bahn).

Daten im Beispiel: Hinweiskarte Starkregengefahren © BKG; Starkregengefahrenkarte NRW, Geobasis NRW; © OpenStreetMap-Mitwirkende.
