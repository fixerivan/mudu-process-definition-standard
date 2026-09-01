<!-- mudu-process-definition-metadata
schema: mudu-process-definition/v1
process_id: MUDU-060
catalogue_id: "060"
catalogue_name: "Žiadosť o pridelenie poznávacej značky lietadla"
canonical_name: "Predbežné pridelenie registrovej značky lietadlu"
definition_version: 0.1.3
definition_status: DRAFT
authority_status: UNCONFIRMED
source_selection: SELECTED
implementation_conformance: NONCONFORMANT
formal_verification: NOT_RUN
language: sk
source_baseline_date: 2026-09-01
supersedes: "MUDU-060@0.1.2"
related_processes: [MUDU-059, MUDU-061, MUDU-062, MUDU-063, MUDU-091]
-->

# MUDU-060 — Predbežné pridelenie registrovej značky lietadlu

> **Verejný pracovný príklad:** Verejné právne a oficiálne zdroje sú prepojené
> priamo. Interné projektové podklady sú iba opísané, nie zverejnené. Dokument
> zostáva `DRAFT / UNCONFIRMED` — vecný gestor ho ešte neschválil.

> Dopravný úrad na žiadosť vlastníka pred zápisom lietadla do registra
> predbežne pridelí registrovú značku; rozhodnutie platí jeden rok od
> právoplatnosti a zostane platné, ak vlastník v tejto lehote požiada o zápis
> lietadla procesom MUDU-061.

**Rýchly prehľad**

| Otázka | Odpoveď |
| --- | --- |
| Kto proces spúšťa? | Vlastník lietadla alebo preukázaný zástupca. |
| Čo úrad overuje? | Identitu lietadla, oprávnenie žiadateľa, formát a dostupnosť navrhovanej značky. |
| Aký je úspešný výsledok? | Právoplatné rozhodnutie predbežne pridelí značku na jeden rok. |
| Čo sem nepatrí? | Samotný zápis lietadla patrí MUDU-061; neskoršia zmena MUDU-062 a výmaz MUDU-063. |
| Čo ešte treba rozhodnúť? | Rozsah príloh, osobitná skúšobná značka a ochrana pred súbežným pridelením rovnakej značky. |
| Jednoduchý priebeh | [Otvoriť diagram procesu](graph.md) |

## 1. Identita a stav

| Pole | Hodnota |
| --- | --- |
| Katalógové ID | 060 |
| Katalógový názov | Žiadosť o pridelenie poznávacej značky lietadla |
| Kanonický názov | Predbežné pridelenie registrovej značky lietadlu |
| Vecný gestor | Dopravný úrad, Divízia civilného letectva, register lietadiel |
| Typ procesu | APPLICATION_DECISION |
| Definičný stav | DRAFT |
| Autorita | UNCONFIRMED |
| Jazyk | sk |

## 2. Účel, spúšťač a hranice

| ID | Typ | Tvrdenie | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| SCP-060-001 | PURPOSE | Pred zápisom lietadla do registra predbežne prideliť konkrétnemu lietadlu registrovú značku. | LAW | CONFIRMED | SRC-060-001 |
| SCP-060-002 | TRIGGER | Vlastník lietadla žiada o predbežné pridelenie značky pred podaním žiadosti o zápis lietadla. | LAW | CONFIRMED | SRC-060-001 |
| SCP-060-003 | IN_SCOPE | Predbežné pridelenie štandardnej registrovej značky v tvare podľa kategórie lietadla. | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| SCP-060-004 | IN_SCOPE | Pridelenie špeciálnej registrovej značky držiteľovi povolenia podľa § 23 ods. 1 je samostatná právna vetva; jej zaradenie pod katalógové ID 60 musí potvrdiť gestor. | LAW | CONFLICT | SRC-060-001, SRC-060-002, SRC-060-003 |
| SCP-060-005 | OUT_OF_SCOPE | Zápis lietadla do registra, vznik štátnej príslušnosti SR a vydanie osvedčenia o zápise patria MUDU-061. | LAW | CONFIRMED | SRC-060-001 |
| SCP-060-006 | OUT_OF_SCOPE | Zmena už zapísanej registrovej značky alebo iných údajov registra patrí MUDU-062. | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| SCP-060-007 | OUT_OF_SCOPE | Výmaz lietadla patrí MUDU-063; vydanie lietadlovej knihy patrí MUDU-059; kódy Mode S/ELT patria MUDU-091. | OBSERVATION | CONFIRMED | SRC-060-005, SRC-060-006 |

## 3. Autorita a právny základ

| ID | Modalita | Normatívne pravidlo | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| REQ-060-001 | MUST | Žiadateľom o predbežné pridelenie registrovej značky je vlastník lietadla. | LAW | CONFIRMED | SRC-060-001 |
| REQ-060-002 | MUST | Rozhodnutie o predbežnom pridelení platí jeden rok odo dňa nadobudnutia právoplatnosti. | LAW | CONFIRMED | SRC-060-001 |
| REQ-060-003 | MUST | Predbežné pridelenie nestratí platnosť, ak vlastník počas jedného roka podá žiadosť MUDU-061. | LAW | CONFIRMED | SRC-060-001 |
| REQ-060-004 | MUST | Žiadosť musí obsahovať všetky náležitosti v § 4 vyhlášky č. 274/2024 Z. z. | LAW | CONFIRMED | SRC-060-002 |
| REQ-060-005 | MUST | Registrová značka musí mať formát určený kategóriou lietadla podľa § 6 vyhlášky. | LAW | CONFIRMED | SRC-060-002 |
| REQ-060-006 | MUST_NOT | Predbežné pridelenie samo nezapisuje lietadlo do registra a nepriznáva mu štátnu príslušnosť SR. | LAW | CONFIRMED | SRC-060-001 |
| REQ-060-007 | MUST | Špeciálna značka pre skúšobný let sa prideľuje iba držiteľovi povolenia podľa § 23 ods. 1 a má formát podľa § 7 vyhlášky. | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| REQ-060-008 | DESCRIPTIVE | Zákonná kontrola pátrania v SIS podľa § 26 ods. 13 sa vzťahuje na zápis MUDU-061 a zmenu MUDU-062, nie na predbežné pridelenie MUDU-060. | LAW | CONFIRMED | SRC-060-001 |

## 4. Aktéri a oprávnenia

| ID | Aktér | Typ | Oprávnenie a zodpovednosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| ACT-060-001 | Vlastník lietadla | Externý žiadateľ | Podáva žiadosť a navrhuje registrovú značku. | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| ACT-060-002 | Spoluvlastníci lietadla | Externé dotknuté osoby | Ich údaje sa uvádzajú v rozsahu podľa § 26 ods. 5 písm. a); oprávnenie jedného spoluvlastníka konať za ostatných musí byť preukázané. | LAW | CONFIRMED | SRC-060-002 |
| ACT-060-003 | Prevádzkovateľ lietadla | Externá dotknutá osoba | Jeho údaje sú súčasťou žiadosti; zákon ho pri predbežnom pridelení neurčuje ako samostatného žiadateľa. | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| ACT-060-004 | Splnomocnený zástupca | Externý zástupca | Aktuálny formulár pripúšťa konanie na základe plnej moci; presné pravidlá zastúpenia sú mimo osobitnej úpravy § 26 ods. 4. | OFFICIAL_PROCEDURE | CONFIRMED | SRC-060-003 |
| ACT-060-005 | Držiteľ povolenia podľa § 23 ods. 1 | Externý žiadateľ osobitnej vetvy | Môže žiadať o špeciálnu značku na skúšobný let; zaradenie vetvy do MUDU-060 čaká na rozhodnutie gestora. | LAW | CONFLICT | SRC-060-001, SRC-060-002 |
| ACT-060-006 | Dopravný úrad | Orgán verejnej moci | Rozhoduje o predbežnom pridelení a prideľuje špeciálnu značku v zákonnom rozsahu. | LAW | CONFIRMED | SRC-060-001 |
| ACT-060-007 | Referent a schvaľovateľ registra lietadiel | Interné roly | Presné rozdelenie prípravy, schválenia a podpisu rozhodnutia musí potvrdiť gestor. | PROPOSAL | PROPOSED | SRC-060-007 |

## 5. Vstupy a predpoklady

| ID | Podmienka alebo vstup | Povinnosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| PRE-060-001 | Jednoznačne identifikované lietadlo: typ, výrobné číslo, rok výroby a výrobca. | REQUIRED | LAW | CONFIRMED | SRC-060-002 |
| PRE-060-002 | Identifikácia vlastníka/spoluvlastníkov a prevádzkovateľa v zákonnom rozsahu. | REQUIRED | LAW | CONFIRMED | SRC-060-002 |
| PRE-060-003 | Návrh registrovej značky zodpovedajúci kategórii lietadla. | REQUIRED | LAW | CONFIRMED | SRC-060-002 |
| PRE-060-004 | Názov a miestny identifikačný kód základného letiska alebo osobitného letiska, ak bol pridelený. | CONDITIONAL | LAW | CONFIRMED | SRC-060-002 |
| PRE-060-005 | Povolenie podľa § 23 ods. 1 pri špeciálnej značke. | CONDITIONAL | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| PRE-060-006 | Elektronická identifikácia a autorizácia pri portálovom podaní. | CONDITIONAL | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-005 |
| PRE-060-007 | Voľnosť navrhovanej značky v zozname disponibilných značiek. | REQUIRED | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-004 |

## 6. Údaje formulára

| ID | Údaj | Typ | Kardinalita | Zdroj/hodnota | Validácia | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| FLD-060-001 | Vlastník/spoluvlastníci | Štruktúrovaná identita | 1..* | § 26 ods. 5 písm. a) | Úplnosť podľa typu FO, FOP, PO | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| FLD-060-002 | Prevádzkovateľ | Štruktúrovaná identita | 1 | § 26 ods. 5 písm. a) | Úplnosť podľa typu FO, FOP, PO | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| FLD-060-003 | Návrh registrovej značky | Text | 1 | OM + tri písmená alebo štyri číslice | RULE-060-001, RULE-060-002 | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-004 | Typ lietadla | Číselník | 1 | Kategória lietadla | Určuje formát značky | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-005 | Výrobné číslo lietadla | Text | 1 | Výrobný identifikátor | Neprázdne; jednoznačnosť v rámci lietadla | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-006 | Rok výroby | Rok | 1 | Rok výroby lietadla | Platný rok | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-007 | Výrobca | Text | 1 | Označenie výrobcu | Neprázdne | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-008 | Základné letisko | Referencia/text | 0..1 | Názov a kód, ak pridelený | Podmienené existenciou prideleného kódu | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-009 | Predpokladaný dátum uvedenia do prevádzky | Dátum | 1 | Dátum uvedený žiadateľom | Platný dátum | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-010 | Dátum a miesto vyhotovenia | Dátum + text | 1 | Žiadateľ | Neprázdne | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-011 | Podpis žiadateľa | Podpis/autorizácia | 1 | Listinný podpis alebo elektronická autorizácia | Podľa kanála podania | LAW | CONFIRMED | SRC-060-002 |
| FLD-060-012 | Predchádzajúca značka, motory, vrtule, MTOW a podrobná klasifikácia | Zložené údaje | 0..* | Aktuálny F469 a MUDU formulár | Nie sú náležitosťami § 4; gestor musí rozhodnúť o ich zachovaní | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-003, SRC-060-004 |
| FLD-060-013 | Viac návrhov značky v poradí preferencie | Zoznam | 0..* | Návrh projektového manažéra | Bez prijatého pravidla | PROPOSAL | PROPOSED | SRC-060-007 |

## 7. Dokumenty a prílohy

| ID | Dokument/príloha | Povinnosť | Forma | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| DOC-060-001 | Osobitné prílohy podľa § 4 vyhlášky č. 274/2024 Z. z. | NOT_APPLICABLE | N/A | LAW | CONFIRMED | SRC-060-002 |
| DOC-060-002 | Výpis z registra/živnostenský doklad pre zahraničný subjekt | OPTIONAL | Originál alebo overená kópia podľa F469 | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-003, SRC-060-004 |
| DOC-060-003 | Plná moc | CONDITIONAL | Originál alebo overená kópia podľa F469 | OFFICIAL_PROCEDURE | CONFIRMED | SRC-060-003 |
| DOC-060-004 | Fotografie štítkov trupu, motorov a vrtúľ | REQUIRED | F469 a konfigurácia MUDU | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-003, SRC-060-004 |
| DOC-060-005 | Duplicitná príloha výpisu z ORSR | OPTIONAL | Konfigurácia MUDU | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-004 |
| DOC-060-006 | Doklad o vlastníctve, zahraničnom výmaze alebo výnimke ministerstva | CONDITIONAL | Návrh v zdrojovom DOCX | PROPOSAL | PROPOSED | SRC-060-007 |

## 8. Poplatky, lehoty a časové pravidlá

| ID | Typ pravidla | Hodnota | Spúšťač/začiatok | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| TIM-060-001 | Platnosť rozhodnutia | 1 rok | Nadobudnutie právoplatnosti rozhodnutia | LAW | CONFIRMED | SRC-060-001 |
| TIM-060-002 | Zachovanie platnosti | Bez zániku po uplynutí roka | Podanie MUDU-061 vlastníkom počas TIM-060-001 | LAW | CONFIRMED | SRC-060-001 |
| FEE-060-001 | Správny poplatok | 40 EUR za každú registrovú alebo špeciálnu registrovú značku osobitne | Podanie žiadosti | LAW | CONFIRMED | SRC-060-008 |
| FEE-060-002 | Elektronické zníženie | 50 % zo sadzby, najviac o 50 EUR; iba ak sú prílohy v elektronickej podobe | Elektronické podanie spĺňajúce § 6 ods. 2 | LAW | CONFIRMED | SRC-060-008 |
| FEE-060-003 | Aktuálny režim MUDU | Poplatok + lustrácia | Vytvorenie podania ID 60 | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-004 |

## 9. Rozhodovacie pravidlá a invarianty

| ID | Modalita | Pravidlo/invariant | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| RULE-060-001 | MUST | Letún, rotorové lietadlo a ornitoptéra používajú tri veľké písmená latinskej abecedy. | LAW | CONFIRMED | SRC-060-002 |
| RULE-060-002 | MUST | Klzák, vzducholoď, voľný a pripútaný balón používajú štyri arabské číslice s výnimkami uvedenými v § 6 ods. 2. | LAW | CONFIRMED | SRC-060-002 |
| RULE-060-003 | MUST | Špeciálna značka používa formát podľa kategórie a vyžaduje oprávnenie podľa REQ-060-007. | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| RULE-060-004 | MUST_NOT | Rovnaká disponibilná značka nesmie byť súčasne pridelená dvom lietadlám. | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-004 |
| RULE-060-005 | MUST_NOT | Úspešné MUDU-060 nesmie vytvoriť účinky zápisu lietadla, štátnej príslušnosti ani osvedčenia o zápise. | LAW | CONFIRMED | SRC-060-001 |
| RULE-060-006 | MUST | Platnosť sa počíta od právoplatnosti rozhodnutia, nie od vytvorenia podania alebo dokumentu. | LAW | CONFIRMED | SRC-060-001 |
| RULE-060-007 | SHOULD | Systém má rezervovať disponibilnú značku atómovo proti súbežným žiadostiam. | PROPOSAL | PROPOSED | SRC-060-007 |

## 10. Procesný tok

| ID | Poradie | Stav pred | Činnosť | Aktér | Podmienka | Stav po | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| STEP-060-001 | 1 | Neexistuje podanie | Vlastník podá žiadosť s náležitosťami podľa REQ-060-004. | ACT-060-001 | PRE-060-001 až PRE-060-004 | Podanie prijaté | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| STEP-060-002 | 2 | Podanie prijaté | Úrad overí úplnosť údajov a oprávnenie žiadateľa. | ACT-060-006 | REQ-060-001, REQ-060-004 | Podanie úplné alebo vyžaduje opravu | OFFICIAL_PROCEDURE | PROPOSED | SRC-060-001, SRC-060-002 |
| STEP-060-003 | 3 | Podanie úplné | Úrad overí formát a disponibilitu navrhovanej značky. | ACT-060-006 | RULE-060-001 až RULE-060-004 | Značka prípustná alebo neprípustná | OFFICIAL_PROCEDURE | PROPOSED | SRC-060-002, SRC-060-004 |
| STEP-060-004 | 4 | Značka prípustná | Úrad vydá rozhodnutie o predbežnom pridelení. | ACT-060-006 | Štandardná vetva | Rozhodnutie vydané | LAW | CONFIRMED | SRC-060-001, SRC-060-006 |
| STEP-060-005 | 5 | Rozhodnutie vydané | Po právoplatnosti začne plynúť jednoročná platnosť. | ACT-060-006 | OUT-060-001 je právoplatný | Predbežná značka platná | LAW | CONFIRMED | SRC-060-001 |
| STEP-060-006 | 6 | Predbežná značka platná | Vlastník podá MUDU-061 alebo lehota uplynie. | ACT-060-001 | TIM-060-001 | Platnosť zachovaná cez MUDU-061 alebo zaniknutá | LAW | CONFIRMED | SRC-060-001 |
| STEP-060-007 | I1 | Podanie prijaté | MUDU aktivuje pracovný postup pre poplatok a lustráciu. | Systém CRDÚ | Aktuálna konfigurácia ID 60 | Technické podprocesy vytvorené | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-004 |

## 11. Výstupy, právne účinky a koncové stavy

| ID | Typ | Výstup/účinok | Právoplatnosť/platnosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| OUT-060-001 | Rozhodnutie | Rozhodnutie o predbežnom pridelení konkrétnej registrovej značky. | Jeden rok od právoplatnosti; TIM-060-002 | LAW | CONFIRMED | SRC-060-001, SRC-060-006 |
| OUT-060-002 | Technický stav | Disponibilná značka sa vedie ako predbežne pridelená konkrétnemu lietadlu. | Počas platnosti OUT-060-001 | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-004 |
| OUT-060-003 | Prerušenie | Rozhodnutie o prerušení konania. | Podľa rozhodnutia | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-004 |
| OUT-060-004 | Zastavenie | Rozhodnutie o zastavení konania. | Po právoplatnosti | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-004 |
| OUT-060-005 | Zakázaný účinok | Žiadny zápis lietadla, štátna príslušnosť SR ani osvedčenie o zápise. | N/A | LAW | CONFIRMED | SRC-060-001 |

## 12. Integrácie a notifikácie

| ID | Typ | Systém/príjemca | Účel/obsah | Kritickosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- |
| INT-060-001 | INTEGRATION | Portál DÚ/ÚPVS | Elektronické podanie a autorizácia žiadosti. | HIGH | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-005 |
| INT-060-002 | INTEGRATION | Fabasoft/registratúra | Evidencia podania, spisu a výstupu. | HIGH | PROPOSAL | PROPOSED | SRC-060-007 |
| INT-060-003 | INTEGRATION | Platobný modul/PEP | Vytvorenie a kontrola úhrady poplatku. | HIGH | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-004 |
| INT-060-004 | INTEGRATION | CLK/SIS | Konfigurácia ID 60 vyžaduje lustráciu, ale zákon viaže kontrolu SIS na MUDU-061 a MUDU-062 a príslušná vetva nemá integračné volanie. | HIGH | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-001, SRC-060-004 |
| NOT-060-001 | NOTIFICATION | Žiadateľ | Potvrdenie prijatia podania. | MEDIUM | PROPOSAL | PROPOSED | SRC-060-007 |
| NOT-060-002 | NOTIFICATION | Žiadateľ | Výzva na opravu/doplnenie alebo iný návrh značky. | MEDIUM | PROPOSAL | PROPOSED | SRC-060-007 |
| NOT-060-003 | NOTIFICATION | Žiadateľ | Doručenie rozhodnutia a informácia o jednoročnej platnosti a MUDU-061. | HIGH | PROPOSAL | PROPOSED | SRC-060-007 |

## 13. Alternatívne, chybové a opravné scenáre

| ID | Spúšťač | Očakávané správanie | Koncový stav | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| ALT-060-001 | Značka nezodpovedá kategórii lietadla. | Žiadosť sa neopraví na inú kategóriu automaticky; žiadateľ musí navrhnúť prípustnú značku. | Čaká na opravu alebo negatívny výsledok | LAW | CONFIRMED | SRC-060-002 |
| ALT-060-002 | Navrhovaná značka nie je disponibilná. | Úrad neudelí rovnakú značku druhému lietadlu a vyžiada nový návrh alebo rozhodne negatívne. | Čaká na nový návrh alebo negatívny výsledok | CURRENT_IMPLEMENTATION | CONFLICT | SRC-060-004 |
| ALT-060-003 | Chýba zákonná náležitosť žiadosti. | Úrad použije riadny opravný/prerušovací postup; presný postup musí byť zdrojovo doplnený. | Prerušené alebo zastavené | CURRENT_IMPLEMENTATION | UNKNOWN | SRC-060-004 |
| ALT-060-004 | Žiadosť o špeciálnu značku bez povolenia podľa § 23 ods. 1. | Špeciálna značka sa nepridelí. | Negatívny výsledok | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| ALT-060-005 | Vlastník nepodá MUDU-061 do jedného roka od právoplatnosti. | Predbežné pridelenie stratí platnosť. | Platnosť zaniknutá | LAW | CONFIRMED | SRC-060-001 |
| ALT-060-006 | Dve žiadosti súbežne požadujú rovnakú voľnú značku. | Potrebné je atómové pridelenie alebo rezervácia; aktuálna garancia nebola preukázaná. | UNKNOWN | PROPOSAL | UNKNOWN | SRC-060-004, SRC-060-007 |

## 14. Väzby na iné procesy a dopad zmien

| ID | Smer | Proces/artefakt | Typ väzby | Dopad | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DEP-060-001 | OUT | MUDU-061 | SUCCESSOR | Včasná žiadosť o zápis zachová platnosť predbežnej značky. | LAW | CONFIRMED | SRC-060-001 |
| DEP-060-002 | OUT | MUDU-062 | OUT_OF_SCOPE | Zmena už zapísanej značky nesmie meniť definíciu MUDU-060. | LAW | CONFIRMED | SRC-060-001, SRC-060-002 |
| DEP-060-003 | OUT | MUDU-063 | OUT_OF_SCOPE | Výmaz registrovaného lietadla je samostatný proces. | LAW | CONFIRMED | SRC-060-001 |
| DEP-060-004 | SHARED | registration_mark.xml | SHARED_ENTITY | Zmena dostupnosti/rezervácie značiek ovplyvní MUDU-060 a procesy registra lietadiel. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-060-004 |
| DEP-060-005 | SHARED | MUDU-091 | SHARED_ENTITY | Mode S/ELT kód používa kontext lietadla a značky, ale nie je automatickým účinkom MUDU-060. | OBSERVATION | CONFIRMED | SRC-060-005 |
| DEP-060-006 | SHARED | MUDU-059 | OUT_OF_SCOPE | Lietadlová kniha je samostatný výstup a nevzniká predbežným pridelením značky. | OBSERVATION | CONFIRMED | SRC-060-005 |

## 15. Akceptačné scenáre

| ID | Given | When | Then | Pokrýva | Stav |
| --- | --- | --- | --- | --- | --- |
| AC-060-001 | Vlastník podal úplnú žiadosť a prípustná značka je voľná. | Úrad vydá kladné rozhodnutie. | Značka je predbežne pridelená a platí jeden rok od právoplatnosti; lietadlo ešte nie je zapísané. | REQ-060-001, REQ-060-002, RULE-060-005, OUT-060-001 | DRAFT |
| AC-060-002 | Vlastník má platné predbežné pridelenie. | Počas jedného roka podá MUDU-061. | Predbežné pridelenie nestratí platnosť uplynutím roka. | REQ-060-003, DEP-060-001 | DRAFT |
| AC-060-003 | Kategória vyžaduje štyri číslice. | Žiadateľ navrhne písmenovú značku. | Návrh je označený ako neprípustný a nevznikne pridelenie. | REQ-060-005, RULE-060-002, ALT-060-001 | DRAFT |
| AC-060-004 | Jedna značka je predmetom dvoch súbežných žiadostí. | Obe sa pokúsia značku získať. | Najviac jedna môže skončiť kladným pridelením; druhá dostane riadený alternatívny výsledok. | RULE-060-004, RULE-060-007, ALT-060-006 | DRAFT |
| AC-060-005 | ID 60 je nakonfigurované s CLK. | Spustí sa lustračná vetva. | Test nesmie považovať stav „odoslaná“ za dôkaz externého volania SIS a musí odhaliť chýbajúcu integráciu. | REQ-060-008, INT-060-004, MAP-060-008 | DRAFT |
| AC-060-006 | Zdrojový formulár vyžaduje fotografie a duplicitný ORSR výpis, ale § 4 ich neurčuje. | Definícia sa predkladá gestorovi. | Konflikt zostane otvorený a prílohy sa nestanú potvrdenou požiadavkou bez rozhodnutia. | DOC-060-001, DOC-060-004, DOC-060-005, GAP-060-002 | DRAFT |

## 16. Mapovanie na EA, Petriflow a kód

| ID | Vrstva implementácie | Artefakt | Presná väzba | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| MAP-060-001 | Katalóg | `katalog_sluzieb.csv` | ID 60, XML `vehicle`, úloha `portal_aircraft_registration_mark_new_complete_form`; účel výslovne hovorí o predbežnom pridelení. | CONFIRMED | SRC-060-005 |
| MAP-060-002 | Petriflow | `vehicle.xml` | Prechod `portal_aircraft_registration_mark_new_complete_form`. | CONFIRMED | SRC-060-004 |
| MAP-060-003 | Petriflow | `aircraft.xml` | Dve skladané časti `portal_aircraft_registration_mark_new_complete_form_part_1` a `_part_2`. | CONFIRMED | SRC-060-004 |
| MAP-060-004 | Petriflow | registration_mark.xml | Disponibilné značky a vyhľadanie značky pre vstupný formulár. | CONFIRMED | SRC-060-004 |
| MAP-060-005 | Konfigurácia | `katalog_workflow.csv` | ID 60 je `Poplatok + Lustrácie`. | CONFIRMED | SRC-060-004 |
| MAP-060-006 | Konfigurácia | prilohy_formularov.csv | Štyri riadky: fotografie povinné, plná moc a dva prekrývajúce sa ORSR doklady nepovinné. | CONFLICT | SRC-060-004 |
| MAP-060-007 | Výstup | `Rozhodnutie_o_prideleni_poznavacej_znacky.docx` | Koncový výstup s režimom právoplatnosti 15 dní; šablóna opakuje jednoročné pravidlo. | CONFIRMED | SRC-060-006 |
| MAP-060-008 | Integrácia | lustration CLK/SIS | Parametre existujú, ale SIS vetva nemá integračné volanie a spoločný koniec napriek tomu nastaví stav odoslania. | CONFLICT | SRC-060-004 |
| MAP-060-009 | EA | Object IDs 9482, 9923, 20919, 20926, 9925, 9929, 13387, 13406, 16820, 43400, 40113, 49232 | Zachytené čiastočné mapovanie lietadla, značky, vlastníka, prevádzkovateľa, záložného práva a životného cyklu; nejde o samostatnú autoritu požiadaviek. | CONFIRMED | SRC-060-004 |

## 17. Medzery, konflikty a otvorené rozhodnutia

| ID | Typ | Otázka/konflikt | Potrebné rozhodnutie | Vlastník | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| GAP-060-001 | SOURCE_CONFLICT | Zdrojový DOCX spája predbežné pridelenie so zápisom, štátnou príslušnosťou a zmenou značky. | Potvrdiť hranicu MUDU-060 podľa § 26 ods. 4 a oddeliť MUDU-061/062. | Vecný gestor | CONFLICT | SRC-060-001, SRC-060-007 |
| GAP-060-002 | SOURCE_CONFLICT | § 4 vyhlášky neurčuje osobitné prílohy, ale starší F469 a MUDU vyžadujú fotografie a ďalšie doklady. | Rozhodnúť, ktoré dodatočné dôkazy majú platný právny/akceptovaný základ. | Vecný gestor + legislatíva | CONFLICT | SRC-060-002, SRC-060-003, SRC-060-004 |
| Q-060-001 | INTENT_QUESTION | Patrí špeciálna značka podľa § 26 ods. 3 do MUDU-060 alebo potrebuje samostatnú definovanú vetvu/proces? | Priradiť presnú katalógovú hranicu a akceptovať variant. | Vecný gestor | UNKNOWN | SRC-060-001, SRC-060-002, SRC-060-003 |
| GAP-060-003 | EVIDENCE_GAP | Vyriešené vo verzii 0.1.1:aktuálna položka 92 písm. e) určuje 40 EUR za každú značku a § 6 ods. 2 určuje elektronické zníženie. | Bez ďalšieho rozhodnutia; pri novej časovej verzii predpisu obnoviť kontrolu. | Sémantický autor | CONFIRMED | SRC-060-008 |
| GAP-060-004 | IMPLEMENTATION_GAP | CLK je nakonfigurované pre ID 60 bez zákonnej väzby SIS na predbežné pridelenie a integračná vetva nie je implementovaná. | Potvrdiť vecný účel CLK; potom odstrániť alebo realizovať presne schválenú kontrolu. | Vecný gestor + Netgrif | CONFLICT | SRC-060-001, SRC-060-004 |
| Q-060-002 | INTENT_QUESTION | Má byť možné uviesť viac návrhov značky v poradí preferencie? | Prijať alebo zamietnuť návrh a určiť vplyv na poplatok a súbeh. | Vecný gestor | PROPOSED | SRC-060-007 |
| GAP-060-005 | IMPLEMENTATION_GAP | Atómová rezervácia značky proti súbežným žiadostiam nebola preukázaná. | Definovať okamih rezervácie, uvolnenie, expiráciu a konflikt dvoch podaní. | Vecný gestor + Netgrif | UNKNOWN | SRC-060-004, SRC-060-007 |
| GAP-060-006 | SOURCE_CONFLICT | Katalóg používa „poznávacia“, zákon/vyhláška „registrová“ a účel katalógu „predbežné pridelenie“. | Zachovať katalógový alias, ale prijať kanonický právny názov. | Vecný gestor | PROPOSED | SRC-060-001, SRC-060-002, SRC-060-005 |
| GAP-060-007 | EVIDENCE_GAP | Presné interné roly, notifikácie, lehoty na doplnenie a doručovanie sú v zdrojovom DOCX návrhom bez presnej autority. | Doplniť oficiálny postup alebo ich schváliť ako ACCEPTED_INTENT. | Vecný gestor | UNKNOWN | SRC-060-007 |

## 18. Schválenie a história zmien

| Verzia | Dátum | Zmena | Autorita | Stav |
| --- | --- | --- | --- | --- |
| 0.1.0 | 2026-09-01 | Prvá pevná Markdown definícia odvodená zo zdrojového DOCX; oddelené právne fakty, implementácia, návrhy a konflikty; opravená hranica MUDU-060/061/062. | UNCONFIRMED | DRAFT |
| 0.1.1 | 2026-09-01 | Krížová kontrola s MUDU-061 zviazala aktuálny poplatok 40 EUR za značku a elektronické zníženie s presnou časovou verziou zákona č. 145/1995 Z. z.; hranica MUDU-060/061 zostala nezmenená. | UNCONFIRMED | DRAFT |
| 0.1.2 | 2026-09-01 | Doplnený ľudský rýchly prehľad a jazykové spresnenia bez zmeny vecných pravidiel procesu. | UNCONFIRMED | DRAFT |
| 0.1.3 | 2026-09-01 | Strojové metadáta presunuté do neviditeľného komentára, aby sa pri otvorení dokumentu zobrazil najprv ľudský obsah; vecné pravidlá sa nezmenili. | UNCONFIRMED | DRAFT |

## 19. Register zdrojov

| ID | Typ | Názov/verzia | Lokátor | Ustanovenie/rozsah | Účinnosť/pozorovanie |
| --- | --- | --- | --- | --- | --- |
| SRC-060-001 | LAW | Zákon č. 143/1998 Z. z., časová verzia | https://static.slov-lex.sk/pdf/SK/ZZ/1998/143/ZZ_1998_143_20260101.pdf | § 25; § 26 ods. 1-15; najmä ods. 3-4, 13-14 | účinné od 2026-01-01 |
| SRC-060-002 | LAW | Vyhláška č. 274/2024 Z. z. | https://static.slov-lex.sk/static/SK/ZZ/2024/274/20241115.html | § 4; § 6-7; úplný text § 1-8 | účinné od 2024-11-15; HTML text pozorovaný 2026-09-01 |
| SRC-060-003 | OFFICIAL_FORM | DÚ F469-B/v1/OSL | https://letectvo.nsat.sk/wp-content/uploads/sites/2/2023/03/F469_B_v1_PRIDELENIE-POZN%C3%81VACEJ-ZNA%C4%8CKY_FINAL.pdf | všetkých 8 strán | aktuálne prepojené DÚ; pozorované 2026-08-31 |
| SRC-060-004 | CONFIGURATION | Kontext registra lietadiel v EA a kóde v2 | nezverejnené v tomto repozitári | ID 60 až 63, EA, CSV, XML, výstupy a CLK | zachytené 2026-08-31 |
| SRC-060-005 | CONFIGURATION | Katalóg služieb IS CRDÚ | nezverejnené v tomto repozitári | riadok ID 60 | zachytená revízia |
| SRC-060-006 | OUTPUT_TEMPLATE | Rozhodnutie o pridelení poznávacej značky | nezverejnené v tomto repozitári | celý dokument | zachytená revízia |
| SRC-060-007 | SOURCE_DRAFT | Návrh projektového manažéra „MUDU ID 060 Žiadosť o pridelenie poznávacej značky lietadla“ v1.0 | nezverejnené v tomto repozitári | celý dokument, 18 kapitol, 16 tabuliek | návrh 2026-08-28; prijaté 2026-09-01 |
| SRC-060-008 | LAW | Zákon č. 145/1995 Z. z., časová verzia | https://static.slov-lex.sk/static/SK/ZZ/1995/145/20260901.html | § 6 ods. 2; § 8-9; sadzobník položka 92 písm. e) | účinné od 2026-09-01; text HTML zachytený 2026-09-01 |
