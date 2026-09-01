# MUDU-061 — zápis lietadla do registra

`DRAFT / UNCONFIRMED` — pracovný návrh bez schválenia vecným gestorom.

Diagram ukazuje iba zjednodušený priebeh. Úplné pravidlá sú v
[`definition.md`](definition.md), najmä v sekciách 10 a 17.

```mermaid
graph TD
    A["Vlastník alebo jeho zástupca podá žiadosť"] --> B{"Je podanie úplné a podmienky sú splnené?"}
    B -->|Nedostatok možno odstrániť| B1["Doplnenie alebo prerušenie konania"]
    B1 --> B
    B -->|Podmienky nie sú splnené| X["Lietadlo sa nezapíše"]
    B -->|Áno| C{"Výsledok kontroly lietadla a všetkých motorov v SIS"}
    C -->|Jednoznačný nález| Y["Lietadlo sa nezapíše a informuje sa Policajný zbor"]
    C -->|Bez jednoznačného nálezu| D{"Úrad žiadosti vyhovie?"}
    D -->|Zamietnutie alebo zastavenie| X
    D -->|Kladné právoplatné rozhodnutie| E["Zápis do registra a vznik štátnej príslušnosti SR"]
    E --> F["Pridelenie značky, vydanie osvedčenia a aktualizácia verejnej časti registra"]
```

**Voliteľný predchodca:** MUDU-060 — predbežné pridelenie značky.
**Samostatné neskoršie procesy:** MUDU-062 — zmena údajov a MUDU-063 — výmaz.
MUDU-091 používa spoločné údaje, ale nie je krokom zápisu.

## Najdôležitejšie otvorené otázky — nie sú súčasťou toku

- `GAP-061-005`: chýba preukázateľné volanie SIS, výsledok a vetva pre nález;
- `GAP-061-008`: treba presne zviazať doručenie, rozklad, právoplatnosť, zápis a osvedčenie;
- `GAP-061-011`: treba dokázať jedinečnosť lietadla a značky pri súbežných žiadostiach.

Úplný zoznam je v sekcii 17 súboru [`definition.md`](definition.md).
