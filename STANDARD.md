# Formát definície procesu MUDU v1

## Účel

Tento formát definuje jeden trvalý súbor Markdown pre jeden katalógový proces
MUDU. Musí mu rozumieť vecný expert aj analytik a zároveň ho musia vedieť
spoľahlivo spracovať nástroje pre graf, implementáciu v Netgrife, tvorbu testov,
analýzu dopadov a porovnanie verzií.

Dokument je vecná definícia podložená zdrojmi. Nie je to opis celej rodiny
procesov, voľná analytická úvaha, opis aktuálneho kódu ani dôkaz, že ministerstvo
proces prijalo alebo že ho systém správne vykonáva.

## Ako dokument čítať

Dokument má tri navzájom previazané vrstvy:

- **rýchly prehľad** na začiatku umožní človeku pochopiť proces bez čítania
  technických tabuliek;
- **vecná definícia** v sekciách 2 až 15 opisuje, čo má proces znamenať;
- **technické porovnanie** v sekcii 16 opisuje, čo dnes robí EA, Petriflow,
  konfigurácia a kód. Táto sekcia nikdy nemení vecnú definíciu sama od seba.

Sekcia 17 je pracovný zoznam rozhodnutí. Riadky so stavom `UNKNOWN`,
`CONFLICT` alebo `PROPOSED` sú otvorené. Riadok označený ako vyriešený zostáva
v histórii iba preto, aby sa nestratil dôvod zmeny.

Hodnoty písané veľkými anglickými písmenami sú stabilné strojové značky. Ich
význam vysvetľuje tento dokument a ľudský obsah každého riadka je po slovensky.

## Jazyková hranica

- Procesný a právny význam sa píše po slovensky.
- YAML kľúče, stabilné ID a povolené strojové hodnoty zostávajú v angličtine.
- Presný názov technického artefaktu, poľa, prechodu alebo hodnoty kódu sa
  neprekladá a zapisuje sa v spätných apostrofoch.
- V slovenskej vete sa nepoužíva anglický technický žargón, ak existuje jasné
  slovenské pomenovanie.
- Jazyk nie je zdroj autority. Rozhodujú hodnoty `Vrstva`, `Stav` a `Zdroje`.

Ak neskôr vznikne anglický preklad procesu, je to odvodené zobrazenie s
rovnakými stabilnými ID. Nesmie sa miešať do autoritatívnej slovenskej definície.

## Identita súboru

Kanonické umiestnenie:

```text
process-definitions/MUDU-NNN/definition.md
```

Pre každé katalógové ID existuje práve jedna aktuálna definícia. Staršie verzie
zostávajú v Git. Súvisiace procesy sa uvádzajú odkazom na ich ID; ich životný
cyklus sa nevkladá do definície iného procesu.

Verejné súbory pod `examples/` sú pracovné kópie určené na posúdenie. Riadené
portfólio môže aktuálne definície uchovávať na kanonickom mieste uvedenom vyššie.

## Povinné strojové metadáta na začiatku

Súbor začína neviditeľným komentárom HTML, ktorý obsahuje metadáta YAML s
týmito kľúčmi v uvedenom poradí:

```text
<!-- mudu-process-definition-metadata
schema: mudu-process-definition/v1
process_id: MUDU-NNN
catalogue_id: "NNN"
catalogue_name: "Oficiálny katalógový názov"
canonical_name: "Jednoznačný názov používaný v tejto definícii"
definition_version: 0.1.0
definition_status: DRAFT
authority_status: UNCONFIRMED
source_selection: UNKNOWN
implementation_conformance: NOT_VERIFIED
formal_verification: NOT_RUN
language: sk
source_baseline_date: YYYY-MM-DD
supersedes: null
related_processes: []
-->
```

Komentár je súčasťou zdrojového Markdownu a nástroje ho čítajú deterministicky.
GitHub ho v náhľade nezobrazí, takže človek uvidí najprv názov, stav a rýchly
prehľad procesu. Metadáta sa nesmú duplikovať do viditeľnej technickej tabuľky.

`catalogue_id` je trojmiestny text v úvodzovkách. Hodnotu ako `063` nikdy
nezapisujte bez úvodzoviek: niektoré čítačky YAML ju môžu vyhodnotiť ako osmičkové
číslo a zobraziť `51`.

Povolené hodnoty:

- `definition_status`: `DRAFT`, `REVIEW`, `ACCEPTED`, `FROZEN`, `SUPERSEDED`.
- `authority_status`: `UNCONFIRMED`, `ANALYST_CONFIRMED`,
  `MINISTRY_CONFIRMED`.
- `source_selection`: `SELECTED`, `PARTIAL`, `CONFLICT`, `UNKNOWN`.
- `implementation_conformance`: `NOT_VERIFIED`, `MISSING`, `PARTIAL`,
  `CONFORMANT`, `NONCONFORMANT`.
- `formal_verification`: `NOT_RUN`, `PARTIAL`, `PASS`, `FAIL`.

Hodnoty `ACCEPTED`, `FROZEN`, `ANALYST_CONFIRMED` a `MINISTRY_CONFIRMED` smie
nastaviť iba oprávnený človek.

`NONCONFORMANT` použite iba vtedy, keď je v sekcii 16 alebo 17 uvedený aspoň
jeden konkrétny nesúlad implementácie. `PARTIAL` znamená, že sa preverila iba
časť implementácie. `NOT_VERIFIED` znamená, že presné porovnanie neprebehlo.

## Význam tvrdení

Každý vecný riadok uvádza vrstvu tvrdenia aj jeho stav.

Vrstvy:

- `LAW`: záväzný právny predpis EÚ alebo Slovenskej republiky;
- `OFFICIAL_PROCEDURE`: aktuálny postup, formulár, metodika alebo zverejnená
  inštrukcia úradu;
- `ACCEPTED_INTENT`: výslovne prijaté rozhodnutie analytika alebo ministerstva;
- `CURRENT_IMPLEMENTATION`: pozorované správanie EA, Petriflow, kódu,
  konfigurácie, šablóny alebo bežiaceho systému;
- `OBSERVATION`: zdrojovo podložený kontext, ktorý sám neurčuje požiadavku;
- `PROPOSAL`: zatiaľ neprijatý návrh.

Stavy:

- `CONFIRMED`: tvrdenie priamo podkladá uvedený zdroj v uvedenej vrstve;
- `PROPOSED`: čaká na rozhodnutie oprávnenej osoby;
- `CONFLICT`: zdroje si odporujú alebo implementácia nezodpovedá požiadavke;
- `UNKNOWN`: dôkazy nestačia;
- `NOT_APPLICABLE`: riadok sa nepoužije a obsahuje dôvod.

Vo verejnej kópii môže `CONFIRMED` pri vrstve `CURRENT_IMPLEMENTATION` znamenať,
že autor priamo skontroloval pomenovaný interný podklad. Neznamená to verejne
zopakovateľné overenie ani ľudské schválenie procesu. Súkromný zdroj musí zostať
označený ako nezverejnený a príklad ako `DRAFT / UNCONFIRMED`.

Modality sú `MUST` (musí), `MUST_NOT` (nesmie), `SHOULD` (mal by), `MAY`
(môže) a `DESCRIPTIVE` (opis). `MUST` a `MUST_NOT` môžu byť `CONFIRMED` iba
s odkazom na `LAW`, `OFFICIAL_PROCEDURE` alebo `ACCEPTED_INTENT`.

## Stabilné identifikátory

Používajte trojmiestne katalógové ID a rastúce trojmiestne čísla záznamov:

```text
SCP-060-001  rozsah a hranica
REQ-060-001  normatívna požiadavka
ACT-060-001  aktér alebo rola
PRE-060-001  predpoklad alebo vstup
FLD-060-001  údaj
DOC-060-001  dokument alebo príloha
TIM-060-001  lehota alebo časové pravidlo
FEE-060-001  poplatkové pravidlo
RULE-060-001 invariant alebo rozhodovacie pravidlo
STEP-060-001 krok procesu
OUT-060-001  výstup, účinok alebo koncový stav
INT-060-001  integrácia
NOT-060-001  notifikácia
ALT-060-001  alternatívny, chybový alebo opravný scenár
DEP-060-001  závislosť alebo dopad
AC-060-001   akceptačný scenár
MAP-060-001  mapovanie na EA, Petriflow alebo kód
GAP-060-001  medzera alebo konflikt
Q-060-001    nevyriešená otázka
DEC-060-001  čakajúce alebo prijaté rozhodnutie
SRC-060-001  zdroj
```

Identifikátory sú trvalé. Zmenený význam dostane nové ID. Odstránené prijaté
záznamy zostávajú v histórii Git a v prehľade zmien definície.

## Povinný rýchly prehľad

Hneď za úvodným opisom procesu musí byť táto tabuľka:

```text
| Otázka | Odpoveď |
| --- | --- |
| Kto proces spúšťa? | ... |
| Čo úrad alebo iný vykonávateľ overuje? | ... |
| Aký je úspešný výsledok? | ... |
| Čo sem nepatrí? | ... |
| Čo ešte treba rozhodnúť alebo opraviť? | ... |
| Jednoduchý priebeh | [Otvoriť diagram procesu](graph.md) |
```

Odpovede používajú bežný jazyk a nesmú zavádzať nové tvrdenie. Každá odpoveď
musí byť v súlade s podrobnými záznamami nižšie. Ak podrobný záznam obsahuje
rozpor alebo neistotu, rýchly prehľad to nesmie skryť.

## Povinné sekcie a tabuľky

Po rýchlom prehľade nasledujú tieto referenčné sekcie. Každá sa v dokumente
nachádza práve raz a v tomto poradí. Prázdnu sekciu
nevynechávajte; použite jeden riadok `NOT_APPLICABLE` s dôvodom.

### 1. Identita a stav

```text
| Pole | Hodnota |
```

Required fields: `Katalógové ID`, `Katalógový názov`, `Kanonický názov`,
`Vecný gestor`, `Typ procesu`, `Definičný stav`, `Autorita`, `Jazyk`.

Typ procesu je napríklad `APPLICATION_DECISION`, `NOTIFICATION`,
`REGISTRY_MUTATION`, `EXAMINATION`, `CERTIFICATION`, `APPROVAL`, `STATEMENT`,
`SUPERVISION`, `INTERNAL`, `INTER_AUTHORITY`, and `OTHER`.

### 2. Účel, spúšťač a hranice

```text
| ID | Typ | Tvrdenie | Vrstva | Stav | Zdroje |
```

Použite `PURPOSE`, `TRIGGER`, `IN_SCOPE` alebo `OUT_OF_SCOPE`. Susedné
katalógové procesy oddeľte výslovne.

### 3. Autorita a právny základ

```text
| ID | Modalita | Normatívne pravidlo | Vrstva | Stav | Zdroje |
```

Každé právne tvrdenie odkazuje na konkrétne ustanovenie. Samotný všeobecný
odkaz na predpis nestačí.

### 4. Aktéri a oprávnenia

```text
| ID | Aktér | Typ | Oprávnenie a zodpovednosť | Vrstva | Stav | Zdroje |
```

Oddeľte žiadateľa, dotknutú osobu, zástupcu, spracovateľa, schvaľovateľa, iný
orgán a systémovú rolu.

### 5. Vstupy a predpoklady

```text
| ID | Podmienka alebo vstup | Povinnosť | Vrstva | Stav | Zdroje |
```

Použite `REQUIRED`, `CONDITIONAL`, `OPTIONAL` alebo `NOT_APPLICABLE`.

### 6. Údaje formulára

```text
| ID | Údaj | Typ | Kardinalita | Zdroj/hodnota | Validácia | Vrstva | Stav | Zdroje |
```

Kardinalita je výslovná (`1`, `0..1`, `1..*`, `0..*`). Podmienka odkazuje na
stabilné ID pravidla. Skupinové pole možno použiť, ak zdroj určuje štruktúrovanú
skupinu údajov.

### 7. Dokumenty a prílohy

```text
| ID | Dokument/príloha | Povinnosť | Forma | Vrstva | Stav | Zdroje |
```

Nekopírujte prílohy zo súvisiaceho procesu. Oddeľte právne požiadavky, oficiálne
formuláre a dnešnú konfiguráciu implementácie.

### 8. Poplatky, lehoty a časové pravidlá

```text
| ID | Typ pravidla | Hodnota | Spúšťač/začiatok | Vrstva | Stav | Zdroje |
```

Oddeľte zákonné lehoty, prevádzkové ciele, platnosť, prerušenia, obnovovanie a
poplatky. Pri lehote vždy uveďte udalosť, od ktorej začína plynúť.

### 9. Rozhodovacie pravidlá a invarianty

```text
| ID | Modalita | Pravidlo/invariant | Vrstva | Stav | Zdroje |
```

Uveďte pravidlá jedinečnosti, vzájomného vylúčenia, predchodcu, právoplatnosti,
vedľajších účinkov a súbehu potrebné na formalizáciu.

### 10. Procesný tok

```text
| ID | Poradie | Stav pred | Činnosť | Aktér | Podmienka | Stav po | Vrstva | Stav | Zdroje |
```

Kroky opisujú vecný priebeh procesu. Čisto implementačné kroky musia byť takto
označené. Vetvenie odkazuje na `RULE-*`; poradie sa nesmie domyslieť iba z
usporiadania kódu.

### 11. Výstupy, právne účinky a koncové stavy

```text
| ID | Typ | Výstup/účinok | Právoplatnosť/platnosť | Vrstva | Stav | Zdroje |
```

Oddeľte dokumenty, rozhodnutia, osvedčenia, zmeny registra, zverejnenia,
notifikácie a negatívne výsledky. Čas vytvorenia dokumentu nie je automaticky
časom právneho účinku.

### 12. Integrácie a notifikácie

```text
| ID | Typ | Systém/príjemca | Účel/obsah | Kritickosť | Vrstva | Stav | Zdroje |
```

Použite `INTEGRATION` alebo `NOTIFICATION`. Existencia nakonfigurovaného
adaptéra nedokazuje, že externé volanie prebehlo úspešne.

### 13. Alternatívne, chybové a opravné scenáre

```text
| ID | Spúšťač | Očakávané správanie | Koncový stav | Vrstva | Stav | Zdroje |
```

Podľa potreby pokryte chýbajúce dôkazy, neplatné údaje, negatívne rozhodnutie,
prerušenie, zastavenie, opravný prostriedok, externé zlyhanie, opakovanie a súbeh.

### 14. Väzby na iné procesy a dopad zmien

```text
| ID | Smer | Proces/artefakt | Typ väzby | Dopad | Vrstva | Stav | Zdroje |
```

Použite presné ID procesov a `PREDECESSOR`, `SUCCESSOR`, `DEPENDS_ON`, `PRODUCES_FOR`,
`SHARED_ENTITY`, `SHARED_INTEGRATION`, `SHARED_OUTPUT`, or `OUT_OF_SCOPE`.

### 15. Akceptačné scenáre

```text
| ID | Given | When | Then | Pokrýva | Stav |
```

Scenáre odkazujú na ID `REQ`, `RULE`, `STEP`, `OUT`, `ALT` a `INT`. Sú to
kontrolovateľné vecné príklady, z ktorých neskôr vzniknú kontroly API, dát,
Playwrightu a formálne pravidlá.

### 16. Mapovanie na EA, Petriflow a kód

```text
| ID | Vrstva implementácie | Artefakt | Presná väzba | Stav | Zdroje |
```

Uveďte presný GUID alebo Object ID v EA, súbor/proces/prechod/pole v Petriflow,
cestu ku kódu a jeho verziu, riadok konfigurácie, výstupnú šablónu a dôkaz z
behu systému. Táto sekcia iba opisuje implementáciu a nemôže meniť sekcie 2 až 15.

### 17. Medzery, konflikty a otvorené rozhodnutia

```text
| ID | Typ | Otázka/konflikt | Potrebné rozhodnutie | Vlastník | Stav | Zdroje |
```

Použite `SOURCE_CONFLICT`, `INTENT_QUESTION`, `IMPLEMENTATION_GAP`,
`EVIDENCE_GAP` alebo `PROPOSAL`. Nevyriešená vec nesmie zostať skrytá iba v
súvislom texte.

### 18. Schválenie a história zmien

```text
| Verzia | Dátum | Zmena | Autorita | Stav |
```

Zaznamenajte každú verziu definície. Pri prijatí musí riadený pracovný postup
určiť oprávnenú osobu aj konkrétnu prijatú verziu súboru v Git.

### 19. Register zdrojov

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

## Verzionovanie a uzamknutie prijatej definície

- Patch: spresnenie alebo oprava dôkazu bez zmeny požadovaného správania.
- Minor: nová prijatá požiadavka, vetva, pole, výsledok alebo mapovanie.
- Major: nekompatibilná zmena zmluvy procesu alebo jeho identity.
- `FROZEN` znamená, že konkrétna prijatá verzia je východiskový stav. Ďalšia
  zmena dostane novú verziu, výslovný rozdiel, kontrolu dopadov a nové dôkazy.
- `SUPERSEDED` odkazuje na nástupnícku definíciu, ale zostáva čitateľný pre históriu.

## Hranica úplnosti

Úspešná kontrola štruktúry znamená iba to, že dokument dodržiava tento formát.
Nedokazuje aktuálnosť zdrojov, správnosť významu, prijatie ministerstvom,
zhodu implementácie Netgrif ani úspešné formálne či prevádzkové testy. Každý
z týchto stavov musí zostať uvedený samostatne.

## Pravidlá súboru `graph.md`

- Diagram zobrazuje iba skutočný priebeh procesu.
- Činnosť alebo stav používa obdĺžnik; rozhodnutie používa kosoštvorec a každá
  odchádzajúca hrana pomenúva výsledok rozhodnutia.
- Otázka, medzera, zdroj, spoločná entita ani možný dopad sa nesmú tváriť ako
  krok procesu. Uvádzajú sa pod diagramom s presným `GAP-*`, `Q-*` alebo `DEP-*`.
- Zjednodušenie nesmie vymyslieť poradie, ktoré podrobná definícia nepotvrdzuje.
- Diagram musí prejsť kompiláciou Mermaid a vizuálnou kontrolou v skutočnom
  zobrazení GitHubu.
