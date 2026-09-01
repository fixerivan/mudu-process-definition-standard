# Vrstevnatá definícia procesov MUDU

Jeden proces má jeden kanonický Markdown súbor s dvoma prepojenými vrstvami:

1. **ľudská kontrolná vrstva** — účel, hranice, vizuálny priebeh, pravidlá,
   rozpory, otázky a presne požadované potvrdenie;
2. **detailná štruktúrovaná vrstva** — roly, údaje, dokumenty, lehoty,
   integrácie, mapovanie na EA/Petriflow/kód, dopady, testy a zdroje.

Prvá vrstva sa zobrazí priamo. Druhá je v rovnakom `.md` súbore zbalená, takže
detail sa nestratí, ale recenzent ho nemusí čítať celý naraz. Obe vrstvy používajú
rovnaké stabilné ID a nesmú si odporovať.

## Príklady

| Proces | Definícia |
| --- | --- |
| MUDU-060 — Predbežné pridelenie registrovej značky | [Otvoriť](examples/MUDU-060/definition.md) |
| MUDU-061 — Zápis lietadla do registra | [Otvoriť](examples/MUDU-061/definition.md) |
| MUDU-062 — Zmena údajov registra | [Otvoriť](examples/MUDU-062/definition.md) |
| MUDU-063 — Výmaz lietadla z registra | [Otvoriť](examples/MUDU-063/definition.md) |

Všetky príklady sú `DRAFT / UNCONFIRMED`.

## Pracovný postup

`všetky zdroje → LLM vytvorí kompletný vrstevnatý .md → analytik s gestorom skontrolujú ľudskú vrstvu, otázky a relevantné detaily → prijmú presnú verziu .md → systém vytvorí Petriflow → dopadová analýza, testy a overenie`

Pri novom procese alebo zmene LLM používa rovnaký formát, kladie otázky a
priebežne dopĺňa obe vrstvy, kým je definícia pripravená na prijatie.

Formát určuje [`STANDARD.md`](STANDARD.md) a postup pre ľubovoľný schopný LLM
je v [`SKILL.md`](SKILL.md).
