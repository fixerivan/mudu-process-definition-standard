# Formát návrhu procesu MUDU na vecnú kontrolu

## Účel

Jeden súbor `definition.md` obsahuje návrh jedného katalógového procesu určený
na kontrolu analytikom alebo vecným gestorom. Musí sa dať pochopiť bez znalosti
EA, Petriflow XML, Java/Groovy kódu, grafovej databázy alebo testovacieho systému.

Dokument nie je dôkaz, implementačný dossier ani automatické schválenie. Je to
presná formulácia toho, čo LLM pochopil a čo potrebuje človek potvrdiť.

## Jazyk

- Procesný význam a otázky sú po slovensky.
- Strojové metadáta, stabilné ID a povolené stavy sú v angličtine.
- Presné technické identifikátory sa uvádzajú iba vtedy, keď ich človek potrebuje
  na rozhodnutie; zapisujú sa ako kód.
- Angličtina ani výstup LLM neurčujú autoritu. Rozhoduje človek.

## Skryté metadáta

Súbor začína neviditeľným komentárom:

```text
<!-- mudu-process-review-metadata
schema: mudu-process-review/v1
process_id: MUDU-NNN
catalogue_id: "NNN"
review_version: 0.1.0
status: DRAFT
authority: UNCONFIRMED
language: sk
-->
```

GitHub preto zobrazí najprv ľudský názov a obsah.

## Povinná štruktúra

### Nadpis a stav

```markdown
# MUDU-NNN — názov procesu

> DRAFT / UNCONFIRMED — návrh na vecnú kontrolu.
```

### 1. Čo podľa zdrojov proces robí

Krátky súvislý opis účelu, spúšťača a úspešného výsledku. Nesmie obsahovať
technické vnútornosti systému.

### 2. Hranice procesu

```text
| Patrí do procesu | Nepatrí do procesu |
```

Susedné katalógové procesy sa pomenúvajú presným `MUDU-NNN`.

### 3. Navrhovaný priebeh

Obsahuje malý diagram a iba hlavné obchodné kroky. Činnosť alebo stav je
obdĺžnik; rozhodnutie je kosoštvorec s pomenovanými výsledkami.

Diagram je návrh na kontrolu. Po potvrdení sa musí viazať na skutočný Petriflow
model; nesmie zostať nezávislou paralelnou definíciou.

### 4. Pravidlá, ktoré treba potvrdiť

```text
| ID | Navrhované pravidlo | Podklad |
```

Používajú sa iba pravidlá podstatné pre ľudské rozhodnutie. ID majú tvar
`R1`, `R2`, ... a zostávajú stabilné počas kontroly návrhu.

### 5. Rozpory a otázky

```text
| ID | Čo sme našli | Otázka pre gestora |
```

LLM nesmie rozpor vyriešiť odhadom. Každá otázka musí vyžadovať konkrétnu
odpoveď. ID majú tvar `Q1`, `Q2`, ...

### 6. Čo potrebujeme potvrdiť

Krátky kontrolný zoznam presne pomenúva, čo má recenzent potvrdiť alebo opraviť.

### Zdroje

Uvádzajú sa čitateľné názvy a odkazy na použité verejné zdroje. Interné zdroje
sa môžu pomenovať bez zverejnenia obsahu. Verejný dokument neobsahuje hashové
ani fingerprintové polia.

## Čo do návrhu nepatrí

- úplné mapovanie EA, kódu a konfigurácie;
- zoznam každého poľa a interného objektu;
- kompletná evidencia grafových hrán;
- implementačné testy a dôkazy;
- technické chyby, ktoré nevyžadujú vecné rozhodnutie;
- návrhy vydávané za potvrdené fakty.

Tieto údaje systém udržiava interne a po prijatí procesu ich viaže na konkrétne
pravidlá a prvky Petriflow.

## Stav

- `DRAFT / UNCONFIRMED`: LLM návrh pred ľudskou kontrolou.
- `REVIEW`: analytik návrh kontroluje a odpovedá na otázky.
- `ACCEPTED`: oprávnený človek prijal význam procesu.
- `FROZEN`: prijatá verzia je základom pre Petriflow, implementáciu a testy.
