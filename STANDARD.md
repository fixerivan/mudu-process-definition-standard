# Formát vrstevnatej definície procesu MUDU

## Účel

Jeden `definition.md` je úplná kanonická definícia jedného katalógového procesu.
Obsahuje ľudskú kontrolnú vrstvu aj detailnú štruktúrovanú vrstvu; žiadne
podstatné roly, údaje, dokumenty, pravidlá, integrácie, mapovania ani zdroje sa
neuchovávajú iba v inom textovom dokumente.

LLM vytvára a udržiava obe vrstvy. Analytik a gestor kontrolujú ľudskú vrstvu,
odpovedajú na otázky a podľa potreby otvárajú relevantný detail; prijatá verzia
celého Markdown súboru je vstupom pre Petriflow.

## Autorita vrstiev

- Ľudská vrstva určuje vecný význam, hranice, hlavný priebeh a rozhodnutia.
- Detailná vrstva obsahuje úplné rozpracovanie potrebné pre Petriflow, dopady,
  implementáciu, testy a dôkazy.
- Detailná vrstva nesmie potichu meniť prijatý význam.
- Zmena detailu, ktorá mení význam, sa musí premietnuť do ľudskej vrstvy a
  prejsť novým prijatím.

## Jazyk

- Procesný význam a otázky sú po slovensky.
- Metadáta, stabilné ID a povolené stavy sú anglická systémová syntax.
- Presný technický identifikátor zostáva v pôvodnom tvare a zapisuje sa ako kód.
- Výstup LLM, graf ani implementácia samy neurčujú business autoritu.

## Skryté metadáta

```text
<!-- mudu-process-definition-metadata
schema: mudu-process-definition/v1
process_id: MUDU-NNN
catalogue_id: "NNN"
definition_version: 0.1.0
status: DRAFT
authority: UNCONFIRMED
language: sk
related_processes: []
-->
```

## Ľudská kontrolná vrstva

### Nadpis a stav

```markdown
# MUDU-NNN — názov procesu

> DRAFT / UNCONFIRMED — návrh na vecnú kontrolu.
```

### 1. Čo podľa zdrojov proces robí

Krátky opis účelu, spúšťača a úspešného výsledku.

### 2. Hranice procesu

```text
| Patrí do procesu | Nepatrí do procesu |
```

### 3. Navrhovaný priebeh

Malý diagram obsahuje iba hlavné obchodné činnosti, rozhodnutia, stavy a
výsledky. Po prijatí sa musí viazať na skutočný Petriflow model.

### 4. Pravidlá, ktoré treba potvrdiť

```text
| ID | Navrhované pravidlo | Podklad |
```

ID odkazuje na existujúci `REQ-*` alebo `RULE-*` z detailnej vrstvy.

### 5. Rozpory a otázky

```text
| ID | Čo sme našli | Otázka pre gestora |
```

ID odkazuje na existujúci `GAP-*` alebo `Q-*` z detailnej vrstvy. LLM nesmie
rozpor vyriešiť odhadom.

### 6. Čo potrebujeme potvrdiť

Kontrolný zoznam presne pomenúva, čo má recenzent potvrdiť alebo opraviť.

### 7. Zdroje použité pre návrh

Čitateľný zoznam hlavných zdrojov pre ľudskú kontrolu; úplný register je v
detailnej vrstve.

## Detailná štruktúrovaná vrstva

Detail je v rovnakom súbore pod zbaleným blokom:

```markdown
<details>
<summary>Otvoriť úplnú vrstvu pre LLM, Petriflow, dopadovú analýzu a testy</summary>

... sekcie D1 až D19 ...

</details>
```

V zbalenej detailnej vrstve nasledujú tieto referenčné sekcie. Každá sa v dokumente
nachádza práve raz a v tomto poradí. Prázdnu sekciu
nevynechávajte; použite jeden riadok `NOT_APPLICABLE` s dôvodom.

### D1. Identita a stav

```text
| Pole | Hodnota |
```

Required fields: `Katalógové ID`, `Katalógový názov`, `Kanonický názov`,
`Vecný gestor`, `Typ procesu`, `Definičný stav`, `Autorita`, `Jazyk`.

Typ procesu je napríklad `APPLICATION_DECISION`, `NOTIFICATION`,
`REGISTRY_MUTATION`, `EXAMINATION`, `CERTIFICATION`, `APPROVAL`, `STATEMENT`,
`SUPERVISION`, `INTERNAL`, `INTER_AUTHORITY`, and `OTHER`.

### D2. Účel, spúšťač a hranice

```text
| ID | Typ | Tvrdenie | Vrstva | Stav | Zdroje |
```

Použite `PURPOSE`, `TRIGGER`, `IN_SCOPE` alebo `OUT_OF_SCOPE`. Susedné
katalógové procesy oddeľte výslovne.

### D3. Autorita a právny základ

```text
| ID | Modalita | Normatívne pravidlo | Vrstva | Stav | Zdroje |
```

Každé právne tvrdenie odkazuje na konkrétne ustanovenie. Samotný všeobecný
odkaz na predpis nestačí.

### D4. Aktéri a oprávnenia

```text
| ID | Aktér | Typ | Oprávnenie a zodpovednosť | Vrstva | Stav | Zdroje |
```

Oddeľte žiadateľa, dotknutú osobu, zástupcu, spracovateľa, schvaľovateľa, iný
orgán a systémovú rolu.

### D5. Vstupy a predpoklady

```text
| ID | Podmienka alebo vstup | Povinnosť | Vrstva | Stav | Zdroje |
```

Použite `REQUIRED`, `CONDITIONAL`, `OPTIONAL` alebo `NOT_APPLICABLE`.

### D6. Údaje formulára

```text
| ID | Údaj | Typ | Kardinalita | Zdroj/hodnota | Validácia | Vrstva | Stav | Zdroje |
```

Kardinalita je výslovná (`1`, `0..1`, `1..*`, `0..*`). Podmienka odkazuje na
stabilné ID pravidla. Skupinové pole možno použiť, ak zdroj určuje štruktúrovanú
skupinu údajov.

### D7. Dokumenty a prílohy

```text
| ID | Dokument/príloha | Povinnosť | Forma | Vrstva | Stav | Zdroje |
```

Nekopírujte prílohy zo súvisiaceho procesu. Oddeľte právne požiadavky, oficiálne
formuláre a dnešnú konfiguráciu implementácie.

### D8. Poplatky, lehoty a časové pravidlá

```text
| ID | Typ pravidla | Hodnota | Spúšťač/začiatok | Vrstva | Stav | Zdroje |
```

Oddeľte zákonné lehoty, prevádzkové ciele, platnosť, prerušenia, obnovovanie a
poplatky. Pri lehote vždy uveďte udalosť, od ktorej začína plynúť.

### D9. Rozhodovacie pravidlá a invarianty

```text
| ID | Modalita | Pravidlo/invariant | Vrstva | Stav | Zdroje |
```

Uveďte pravidlá jedinečnosti, vzájomného vylúčenia, predchodcu, právoplatnosti,
vedľajších účinkov a súbehu potrebné na formalizáciu.

### D10. Procesný tok

```text
| ID | Poradie | Stav pred | Činnosť | Aktér | Podmienka | Stav po | Vrstva | Stav | Zdroje |
```

Kroky opisujú vecný priebeh procesu. Čisto implementačné kroky musia byť takto
označené. Vetvenie odkazuje na `RULE-*`; poradie sa nesmie domyslieť iba z
usporiadania kódu.

### D11. Výstupy, právne účinky a koncové stavy

```text
| ID | Typ | Výstup/účinok | Právoplatnosť/platnosť | Vrstva | Stav | Zdroje |
```

Oddeľte dokumenty, rozhodnutia, osvedčenia, zmeny registra, zverejnenia,
notifikácie a negatívne výsledky. Čas vytvorenia dokumentu nie je automaticky
časom právneho účinku.

### D12. Integrácie a notifikácie

```text
| ID | Typ | Systém/príjemca | Účel/obsah | Kritickosť | Vrstva | Stav | Zdroje |
```

Použite `INTEGRATION` alebo `NOTIFICATION`. Existencia nakonfigurovaného
adaptéra nedokazuje, že externé volanie prebehlo úspešne.

### D13. Alternatívne, chybové a opravné scenáre

```text
| ID | Spúšťač | Očakávané správanie | Koncový stav | Vrstva | Stav | Zdroje |
```

Podľa potreby pokryte chýbajúce dôkazy, neplatné údaje, negatívne rozhodnutie,
prerušenie, zastavenie, opravný prostriedok, externé zlyhanie, opakovanie a súbeh.

### D14. Väzby na iné procesy a dopad zmien

```text
| ID | Smer | Proces/artefakt | Typ väzby | Dopad | Vrstva | Stav | Zdroje |
```

Použite presné ID procesov a `PREDECESSOR`, `SUCCESSOR`, `DEPENDS_ON`, `PRODUCES_FOR`,
`SHARED_ENTITY`, `SHARED_INTEGRATION`, `SHARED_OUTPUT`, or `OUT_OF_SCOPE`.

### D15. Akceptačné scenáre

```text
| ID | Given | When | Then | Pokrýva | Stav |
```

Scenáre odkazujú na ID `REQ`, `RULE`, `STEP`, `OUT`, `ALT` a `INT`. Sú to
kontrolovateľné vecné príklady, z ktorých neskôr vzniknú kontroly API, dát,
Playwrightu a formálne pravidlá.

### D16. Mapovanie na EA, Petriflow a kód

```text
| ID | Vrstva implementácie | Artefakt | Presná väzba | Stav | Zdroje |
```

Uveďte presný GUID alebo Object ID v EA, súbor/proces/prechod/pole v Petriflow,
cestu ku kódu a jeho verziu, riadok konfigurácie, výstupnú šablónu a dôkaz z
behu systému. Táto sekcia iba opisuje implementáciu a nemôže meniť sekcie 2 až 15.

### D17. Medzery, konflikty a otvorené rozhodnutia

```text
| ID | Typ | Otázka/konflikt | Potrebné rozhodnutie | Vlastník | Stav | Zdroje |
```

Použite `SOURCE_CONFLICT`, `INTENT_QUESTION`, `IMPLEMENTATION_GAP`,
`EVIDENCE_GAP` alebo `PROPOSAL`. Nevyriešená vec nesmie zostať skrytá iba v
súvislom texte.

### D18. Schválenie a história zmien

```text
| Verzia | Dátum | Zmena | Autorita | Stav |
```

Zaznamenajte každú verziu definície. Pri prijatí musí riadený pracovný postup
určiť oprávnenú osobu aj konkrétnu prijatú verziu súboru v Git.

### D19. Register zdrojov

```text
| ID | Typ | Názov/verzia | Lokátor | Ustanovenie/rozsah | Účinnosť/pozorovanie |
```

Typ zdroja je napríklad `LAW`, `OFFICIAL_PROCEDURE`, `OFFICIAL_FORM`,
`ACCEPTED_DECISION`, `EA`, `SHAREPOINT`, `KNOWLEDGE_TRANSFER`, `PETRIFLOW`,
`SOURCE_CODE`, `CONFIGURATION`, `OUTPUT_TEMPLATE`, `RUNTIME_EVIDENCE`, and
`SOURCE_DRAFT`.

Každý odkaz na zdroj použitý v dokumente musí existovať v tomto registri.
Uveďte presné vydanie, umiestnenie, ustanovenie alebo rozsah a dátum účinnosti
alebo pozorovania.

Verejná kópia môže súkromné umiestnenie nahradiť textom
`nezverejnené v tomto repozitári`. Musí však jasne povedať, že interný podklad
nebol zverejnený. Verejný čitateľ preto vie posúdiť obsah návrhu, ale nevie
nezávisle zopakovať kontrolu internej implementácie.


## Stav a pracovný postup

- `DRAFT / UNCONFIRMED`: LLM vytvára obe vrstvy a kladie otázky.
- `REVIEW`: analytik a gestor kontrolujú význam a relevantný detail.
- `ACCEPTED`: oprávnený človek prijal presnú verziu celého Markdown súboru.
- `FROZEN`: prijatá verzia je základom pre Petriflow, implementáciu a testy.

`všetky zdroje → kompletný vrstevnatý .md → ľudská kontrola a odpovede → prijatá presná verzia .md → Petriflow → dopady, implementácia, testy a dôkazy`

Pri novom procese alebo zmene LLM kladie otázky a dopĺňa obe vrstvy, kým je
súbor úplný a pripravený na prijatie. Pri zmene sa zachovávajú stabilné ID a
zobrazuje sa ľudsky čitateľný rozdiel.
