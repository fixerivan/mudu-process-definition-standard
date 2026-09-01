---
schema: mudu-process-definition/v1
process_id: MUDU-062
catalogue_id: "062"
catalogue_name: "Žiadosť o zmenu zápisu do registra lietadiel"
canonical_name: "Zmena údajov zapísaných v registri lietadiel Slovenskej republiky"
definition_version: 0.1.1
definition_status: DRAFT
authority_status: UNCONFIRMED
source_selection: SELECTED
implementation_conformance: NONCONFORMANT
formal_verification: NOT_RUN
language: sk
source_baseline_date: 2026-09-01
supersedes: "MUDU-062@0.1.0"
related_processes: [MUDU-060, MUDU-061, MUDU-063, MUDU-091]
---

# MUDU-062 — Zmena údajov zapísaných v registri lietadiel Slovenskej republiky

> **Public example:** normative public sources remain exactly cited. Private project and implementation evidence is described but not redistributed; its public locator and hash are therefore `UNKNOWN`. This document remains `DRAFT` and `UNCONFIRMED`.

> Dopravný úrad na žiadosť vlastníka, prípadne v zákonom obmedzenom rozsahu
> záložného veriteľa, zmení preukázané údaje už zapísaného lietadla, vykoná
> povinnú SIS kontrolu a iba pri zmene údajov osvedčenia vydá nové osvedčenie.

## 1. Identita a stav

| Pole | Hodnota |
| --- | --- |
| Katalógové ID | 062 |
| Katalógový názov | Žiadosť o zmenu zápisu do registra lietadiel |
| Kanonický názov | Zmena údajov zapísaných v registri lietadiel Slovenskej republiky |
| Vecný gestor | Dopravný úrad, Divízia civilného letectva, register lietadiel |
| Typ procesu | REGISTRY_MUTATION |
| Definičný stav | DRAFT |
| Autorita | UNCONFIRMED |
| Jazyk | sk |

## 2. Účel, spúšťač a hranice

| ID | Typ | Tvrdenie | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| SCP-062-001 | PURPOSE | Zmeniť iba preukázané údaje existujúceho lietadla zapísané v registri a zachovať auditovateľnú predchádzajúcu hodnotu. | LAW | CONFIRMED | SRC-062-001 |
| SCP-062-002 | TRIGGER | Vlastník lietadla požiada o zmenu najneskôr do 30 dní odo dňa, keď sa zmena stala. | LAW | CONFIRMED | SRC-062-001 |
| SCP-062-003 | TRIGGER | Záložný veriteľ môže podať žiadosť iba o zápis alebo zmenu údajov záložného práva, veriteľa a zabezpečenej pohľadávky. | LAW | CONFIRMED | SRC-062-001 |
| SCP-062-004 | IN_SCOPE | Identifikácia existujúceho zápisu, presný predmet a dôvod zmeny, dotknuté údaje a doklady, povinná kontrola lietadla a motorov v SIS, rozhodnutie a zmena verejnej alebo neverejnej projekcie. | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| SCP-062-005 | IN_SCOPE | Zmena vlastníka, prevádzkovateľa, záložných údajov, registrovej značky, výnimočného zápisu, technických údajov alebo iného konkrétneho údaja podľa § 26 ods. 5 zostáva variantom jedného MUDU-062, nie novou službou. | LAW | CONFIRMED | SRC-062-001, SRC-062-002, SRC-062-009 |
| SCP-062-006 | OUT_OF_SCOPE | Oprava preukázane nesprávnych údajov z vlastného podnetu podľa § 26 ods. 9 je interná zákonná vetva bez žiadosti a nie je preukázané, že ju elektronická služba MUDU-062 realizuje. | LAW | CONFIRMED | SRC-062-001 |
| SCP-062-007 | OUT_OF_SCOPE | Predbežné pridelenie značky je MUDU-060, prvý zápis a vznik štátnej príslušnosti je MUDU-061 a výmaz lietadla je MUDU-063. | LAW | CONFIRMED | SRC-062-001, SRC-062-009 |
| SCP-062-008 | OUT_OF_SCOPE | Zmena údajov registra sama neschvaľuje technickú alebo letovú spôsobilosť, údržbový program ani zmenu konštrukcie; dotknuté samostatné procesy sa musia posúdiť podľa konkrétneho technického delta. | LAW | CONFIRMED | SRC-062-001, SRC-062-031 |
| SCP-062-009 | OUT_OF_SCOPE | Pridelenie alebo zmena kódu módu S alebo ELT je samostatný MUDU-091; zdieľané lietadlo a značka nie sú automatickým účinkom MUDU-062. | OBSERVATION | CONFIRMED | SRC-062-009, SRC-062-031 |
| SCP-062-010 | IN_SCOPE | Verejne prepojený formulár F471 „Zmena v technických parametroch“ sa vedie ako formulárový variant MUDU-062, pretože katalóg nemá samostatnú identitu; jeho presná portálová väzba zostáva otvorená. | OFFICIAL_PROCEDURE | CONFLICT | SRC-062-006, SRC-062-008, SRC-062-009 |

## 3. Autorita a právny základ

| ID | Modalita | Normatívne pravidlo | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| REQ-062-001 | MUST | Vlastník požiada o zmenu zapísaných údajov a doloží doklady preukazujúce zmenu najneskôr do 30 dní od jej vzniku. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-002 | MAY | Záložný veriteľ môže žiadať iba zápis alebo zmenu údajov podľa § 26 ods. 5 písm. e). | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-003 | MAY | Dopravný úrad môže z vlastného podnetu zmeniť údaj, ak je preukázané, že údaj registra nezodpovedá skutočnosti; tým nezaniká povinnosť vlastníka podľa REQ-062-001. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-004 | MUST | Žiadosť obsahuje údaje a prílohy podľa § 2 a formu podľa § 5 vyhlášky č. 274/2024 Z. z. | LAW | CONFIRMED | SRC-062-002 |
| REQ-062-005 | MUST | Pred každou zmenou Dopravný úrad preverí v SIS lietadlo aj motor lietadla podľa nariadenia EÚ 2018/1862. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-006 | MUST_NOT | Pri jednoznačnom a nepochybnom pátraní v SIS Dopravný úrad zmenu nevykoná a bezodkladne informuje Policajný zbor. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-007 | MUST | Ak zmena zasahuje údaj uvedený v osvedčení o zápise, Dopravný úrad vydá nové osvedčenie, ktoré nahrádza pôvodné. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-008 | MUST | Vlastník odovzdá pôvodné osvedčenie najneskôr v deň vydania nového osvedčenia. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-009 | MUST_NOT | Zápis alebo zmena údajov záložného práva v registri sama nevytvára ani nemení záložné právo. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-010 | MUST | Verejná časť sa aktualizuje iba v rozsahu § 26 ods. 6; údaje neverejnej časti sa nesmú zverejniť. | LAW | CONFIRMED | SRC-062-001 |
| REQ-062-011 | MUST | Na konanie sa vzťahuje správny poriadok a proti rozhodnutiu možno podať rozklad, o ktorom rozhoduje predseda Dopravného úradu na návrh osobitnej komisie. | LAW | CONFIRMED | SRC-062-001, SRC-062-004 |
| REQ-062-012 | MUST | Poplatok sa určuje ako 25 % príslušnej sadzby položky 92 písm. a), c), e) alebo f) podľa dokladu a účinku, ktorý sa mení. | LAW | CONFIRMED | SRC-062-003 |

## 4. Aktéri a oprávnenia

| ID | Aktér | Typ | Oprávnenie a zodpovednosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| ACT-062-001 | Vlastník lietadla | Externý žiadateľ | Podáva všeobecnú žiadosť o zmenu, dodrží 30-dňovú povinnosť, preukáže delta a vráti nahrádzané osvedčenie. | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| ACT-062-002 | Spoluvlastníci | Externé dotknuté osoby | Ich údaje alebo podiely sa menia len na základe preukázaného právneho delta a oprávneného konania za vlastníka. | LAW | CONFIRMED | SRC-062-001, SRC-062-002, SRC-062-004 |
| ACT-062-003 | Prevádzkovateľ | Externá dotknutá osoba | Jeho údaje a prevádzkové oprávnenie sú predmetom zmeny, ale zákon ho neurčuje ako všeobecného žiadateľa namiesto vlastníka. | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| ACT-062-004 | Splnomocnený zástupca vlastníka | Externý zástupca | Podáva a podpisuje v rozsahu platného splnomocnenia; verejná stránka DÚ pripúšťa iba vlastníka alebo jeho splnomocnenú osobu. | OFFICIAL_PROCEDURE | CONFIRMED | SRC-062-004, SRC-062-006, SRC-062-007 |
| ACT-062-005 | Záložný veriteľ | Obmedzený externý žiadateľ | Môže iniciovať iba zmenu záložných údajov podľa REQ-062-002. | LAW | CONFIRMED | SRC-062-001 |
| ACT-062-006 | Dopravný úrad | Orgán verejnej moci | Vedie register, overuje delta a doklady, vykonáva SIS kontrolu, rozhoduje, aktualizuje register a podmienene vydáva osvedčenie. | LAW | CONFIRMED | SRC-062-001 |
| ACT-062-007 | Policajný zbor | Iný orgán verejnej moci | Prijíma bezodkladné oznámenie pri jednoznačnom a nepochybnom SIS hite. | LAW | CONFIRMED | SRC-062-001 |
| ACT-062-008 | Ministerstvo dopravy SR | Iný orgán verejnej moci | Jeho rozhodnutie a dátum sa zapisujú alebo menia pri výnimočnom zápise podľa § 25 ods. 4; nejde o voľné zaškrtnutie bez rozhodnutia. | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| ACT-062-009 | Referent registra lietadiel | Interná rola | Aktuálne spracúva podanie a vyberá jeden z konfigurovaných výstupov; presné rozhodovacie a podpisové oprávnenia nie sú prijato definované. | CURRENT_IMPLEMENTATION | UNKNOWN | SRC-062-010, SRC-062-011 |
| ACT-062-010 | Predseda Dopravného úradu a osobitná komisia | Odvolací orgán | Predseda rozhoduje o rozklade na návrh komisie. | LAW | CONFIRMED | SRC-062-001 |

## 5. Vstupy a predpoklady

| ID | Podmienka alebo vstup | Povinnosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| PRE-062-001 | Existujúci aktuálny zápis lietadla MUDU-061 identifikovaný registrovou značkou a identitou lietadla. | REQUIRED | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| PRE-062-002 | Presne určený predmet a dôvod zmeny a dvojica predchádzajúca/požadovaná hodnota pre každý dotknutý údaj. | REQUIRED | LAW | CONFIRMED | SRC-062-002 |
| PRE-062-003 | Doklad preukazujúci dôvod zmeny a iba dotknuté registračné podklady podľa DOC-062-001 a DOC-062-002. | REQUIRED | LAW | CONFIRMED | SRC-062-002 |
| PRE-062-004 | Oprávnenie žiadateľa: vlastník alebo jeho zástupca; záložný veriteľ iba pre záložné údaje. | REQUIRED | LAW | CONFIRMED | SRC-062-001, SRC-062-004, SRC-062-006 |
| PRE-062-005 | Údaje lietadla a každého motora umožňujúce preukázateľnú SIS kontrolu. | REQUIRED | LAW | CONFIRMED | SRC-062-001 |
| PRE-062-006 | Správny poplatok určený podľa skutočného meneného dokladu je zaplatený pred vykonaním úkonu v lehote po výzve. | REQUIRED | LAW | CONFIRMED | SRC-062-003 |
| PRE-062-007 | Pri zmene údaja osvedčenia je pôvodné osvedčenie dostupné na vrátenie najneskôr v deň vydania nového. | CONDITIONAL | LAW | CONFIRMED | SRC-062-001 |
| PRE-062-008 | Pri elektronickom podaní je podanie autorizované a prílohy spĺňajú elektronickú formu alebo zaručenú konverziu podľa § 5 ods. 2. | CONDITIONAL | LAW | CONFIRMED | SRC-062-002 |
| PRE-062-009 | Pri portálovej ceste sa načíta presný existujúci Vehicle/Aircraft graf vrátane vlastníka, prevádzkovateľa, záložných vzťahov, motorov, vrtúľ a značky. | REQUIRED | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-013, SRC-062-014, SRC-062-016 |
| PRE-062-010 | Základná verzia zápisu sa od okamihu zobrazenia do rozhodnutia nezmenila alebo sa konflikt explicitne znovu zosúladil. | REQUIRED | PROPOSAL | PROPOSED | SRC-062-012, SRC-062-031 |

## 6. Údaje formulára

| ID | Údaj | Typ | Kardinalita | Zdroj/hodnota | Validácia | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| FLD-062-001 | Vlastník alebo spoluvlastníci | Štruktúrovaná identita | 1..* | Rozsah § 26 ods. 5 písm. a) | Povinná identifikácia aktuálneho vlastníka; nové údaje len pri dotknutom delta | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-002 | Prevádzkovateľ | Štruktúrovaná identita | 1 | Rozsah § 26 ods. 5 písm. a) | Aktuálna identita; nový právny titul pri zmene prevádzkovateľa | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-003 | Záložný veriteľ, záložné právo a zabezpečená pohľadávka | Štruktúrované údaje | 0..* | Iba ak je lietadlo, motor alebo vrtuľa zaťažená alebo sa mení záložný údaj | Oddeliť pridanie, zmenu a ukončenie; RULE-062-006 | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-004 | Typ a výrobné číslo motora | Opakovateľná štruktúra | 0..* | Každý motor, ak je súčasťou lietadla | Každý aktuálny motor musí vstúpiť do SIS kontroly bez ohľadu na predmet delta | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-005 | Typ a výrobné číslo vrtule | Opakovateľná štruktúra | 0..* | Každá vrtuľa, ak je súčasťou lietadla | Samostatná identita a preukázaný delta | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-006 | Registrová značka existujúceho lietadla | Text alebo referencia | 1 | Aktuálna značka | Jednoznačne identifikuje cieľový zápis; pri zmene značky sa zachová predchodca a časová história | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-007 | Predmet zmeny | Enumerácia plus presný opis delta | 1 | Právne ľubovoľný dotknutý údaj § 26 ods. 5 | Nesmie sa redukovať na implementačné labely bez vetvy `iné` | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-008 | Dátum a miesto vyhotovenia žiadosti | Dátum a text | 1 | Žiadateľ | Platný dátum a neprázdne miesto | LAW | CONFIRMED | SRC-062-002 |
| FLD-062-009 | Podpis žiadateľa | Podpis alebo elektronická autorizácia | 1 | Listinný podpis alebo autorizované elektronické podanie | Listinný podpis je výslovne povinný; elektronicky podľa § 5 ods. 2 | LAW | CONFIRMED | SRC-062-002 |
| FLD-062-010 | Dátum vzniku zmeny | Dátum | 1 | Skutočná udalosť | Určuje 30-dňovú lehotu TIM-062-001; aktuálny F470 ho samostatne nezachytáva | LAW | CONFLICT | SRC-062-001, SRC-062-007 |
| FLD-062-011 | Sedem hodnôt `enum_change_subject` | Enumerácia | 1 | owner,operator,new_lien,delete_lien,registration_mark,exceptional_entry,other | Všetky sú varianty MUDU-062; `other` musí niesť presný dôvod/delta | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-013 |
| FLD-062-012 | Typ,model,rok,výrobca,výrobné číslo,MTOW,počet osôb a umiestnenie | Technické údaje | 0..* | F470,F471 a Aircraft part1 | Povinné iba podľa predmetu zmeny a dôkazu; plošná editácia nesmie vytvoriť nežiadané delta | OFFICIAL_PROCEDURE | CONFLICT | SRC-062-007, SRC-062-008, SRC-062-014 |
| FLD-062-013 | Výrobca a rok motorov a vrtúľ | Technické údaje súčastí | 0..* | F470/F471 a subformuláre | Vyhláška § 2 výslovne uvádza typ a výrobné číslo; ďalšie údaje potrebujú prijatý účel | OFFICIAL_PROCEDURE | CONFLICT | SRC-062-002, SRC-062-007, SRC-062-008 |
| FLD-062-014 | Číslo a dátum rozhodnutia ministerstva o výnimočnom zápise | Text a dátum | 0..1 | Iba pri zmene vetvy exceptional_entry | Typy musia zostať text/dátum; vyžaduje existujúce rozhodnutie ministerstva | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| FLD-062-015 | Predchádzajúca a nová hodnota každého meneného údaja | Auditované delta | 1..* | Existujúci register versus žiadosť | Nezmenené polia sa nesmú materializovať ako zmena | PROPOSAL | PROPOSED | SRC-062-012, SRC-062-031 |
| FLD-062-016 | Verejnosť údaja | Enum PUBLIC/NONPUBLIC | 1 | Odvodené z § 26 ods. 6-8 | Riadi aktualizáciu verejnej projekcie bez úniku neverejných údajov | LAW | CONFIRMED | SRC-062-001 |

## 7. Dokumenty a prílohy

| ID | Dokument/príloha | Povinnosť | Forma | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| DOC-062-001 | Doklad preukazujúci dôvod zmeny | REQUIRED | Listinne originál alebo úradne osvedčená kópia; elektronicky podľa § 5 ods. 2; pri inom jazyku úradný preklad okrem češtiny | LAW | CONFIRMED | SRC-062-002 |
| DOC-062-002 | Doklady podľa § 1 ods. 2 dotknuté zmenou | CONDITIONAL | Povinnosť,forma a preklad podľa konkrétnej dotknutej prílohy | LAW | CONFIRMED | SRC-062-002 |
| DOC-062-003 | Palubný denník alebo náhradný doklad | CONDITIONAL | Originál; iba ak bol vydaný v listinnej podobe | LAW | CONFIRMED | SRC-062-002 |
| DOC-062-004 | Lietadlová kniha | CONDITIONAL | Originál; iba ak bola vydaná v listinnej podobe | LAW | CONFIRMED | SRC-062-002 |
| DOC-062-005 | Pôvodné osvedčenie o zápise | CONDITIONAL | Originál odovzdaný najneskôr v deň vydania nového; iba ak sa mení údaj osvedčenia | LAW | CONFIRMED | SRC-062-001 |
| DOC-062-006 | Plná moc | CONDITIONAL | Forma preukazujúca rozsah zastúpenia | OFFICIAL_PROCEDURE | CONFIRMED | SRC-062-004, SRC-062-006, SRC-062-007 |
| DOC-062-007 | Doklad o poistení,dohoda o prevádzkovaní a príslušný registračný doklad | CONDITIONAL | Iba ak sú konkrétnou zmenou dotknuté | LAW | CONFIRMED | SRC-062-002 |
| DOC-062-008 | Vyhlásenie o súkromnom používaní,fotografie výrobných štítkov a doklad o zaplatení | CONDITIONAL | F470,F471 a konfigurácia ich vyžadujú širšie než § 2 | OFFICIAL_PROCEDURE | CONFLICT | SRC-062-002, SRC-062-007, SRC-062-008, SRC-062-019 |
| DOC-062-009 | Osem nakonfigurovaných príloh ID62 | CONDITIONAL | Elektronicky,poštou alebo osobne podľa konfigurácie | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-002, SRC-062-019 |
| DOC-062-010 | Výpis z obchodného,živnostenského alebo registra združení | NOT_APPLICABLE | Verejná stránka DÚ uvádza,že ho netreba prikladať | OFFICIAL_PROCEDURE | CONFIRMED | SRC-062-006 |

## 8. Poplatky, lehoty a časové pravidlá

| ID | Typ pravidla | Hodnota | Spúšťač/začiatok | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| TIM-062-001 | Oznamovacia lehota vlastníka | Najneskôr 30 dní | Deň,keď zmena nastala | LAW | CONFIRMED | SRC-062-001 |
| TIM-062-002 | Vrátenie pôvodného osvedčenia | Najneskôr v deň vydania nového osvedčenia | Zmena údaja uvedeného v osvedčení | LAW | CONFIRMED | SRC-062-001 |
| TIM-062-003 | Rozhodnutie správneho orgánu | Bezodkladne v jednoduchej veci,inak 30 dní;vo zvlášť zložitej veci 60 dní,ak osobitný predpis neurčí inak | Úplné a rozhodnuteľné podanie;lehoty neplynú počas zákonného prerušenia | LAW | CONFIRMED | SRC-062-004 |
| TIM-062-004 | Rozklad | 15 dní | Oznámenie rozhodnutia | LAW | CONFIRMED | SRC-062-001, SRC-062-004 |
| FEE-062-001 | Základ poplatku | 25 % príslušnej sadzby položky 92 písm. a),c),e) alebo f) podľa meneného dokladu | Určenie presného predmetu zmeny | LAW | CONFIRMED | SRC-062-003 |
| FEE-062-002 | Zmena registračného dokladu podľa MTOW | 25 EUR do 2 750 kg;125 EUR od 2 751 do 5 700 kg;250 EUR pri použiteľnej 1 000 EUR základnej sadzbe | Ak je príslušným základom položka 92 písm. a) | LAW | CONFIRMED | SRC-062-003 |
| FEE-062-003 | Zmena registrovej značky alebo lietadlovej knihy | 10 EUR | Ak je príslušným základom položka 92 písm. e) alebo f) | LAW | CONFIRMED | SRC-062-003 |
| FEE-062-004 | Presných 5 701 kg | Výsledok nie je jednoznačný,pretože základná sadzba písm. a) nepokrýva presne 5 701 kg,ale kód používa horné pásmo od 5 701 kg | MTOW presne 5 701 kg a základ písm. a) | LAW | CONFLICT | SRC-062-003, SRC-062-014 |
| FEE-062-005 | Elektronické zníženie | 50 % vypočítaného poplatku,najviac o 50 EUR;iba ak sú prílohy elektronické | Elektronické podanie spĺňajúce § 6 ods. 2 | LAW | CONFIRMED | SRC-062-003 |
| TIM-062-005 | Splatnosť percentuálneho poplatku | Do 15 dní od doručenia písomnej výzvy a pred vykonaním úkonu | Doručenie výzvy | LAW | CONFIRMED | SRC-062-003 |
| TIM-062-006 | Aktuálne správoplatnenie | Konfigurácia používa 15-dňový výstup,automatický job je vypnutý a dokončenie je manuálne | Spracovanie výstupu vo Fabasofte/backoffice | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-011, SRC-062-020, SRC-062-022 |

## 9. Rozhodovacie pravidlá a invarianty

| ID | Modalita | Pravidlo/invariant | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| RULE-062-001 | MUST | Cieľom zmeny je presne jeden existujúci aktuálny zápis; MUDU-062 nesmie vytvoriť druhé lietadlo ani nový prvotný zápis. | LAW | CONFIRMED | SRC-062-001 |
| RULE-062-002 | MUST | Žiadateľské oprávnenie závisí od delta: vlastník všeobecne,záložný veriteľ iba pre § 26 ods. 5 písm. e). | LAW | CONFIRMED | SRC-062-001 |
| RULE-062-003 | MUST | SIS kontrola zahŕňa lietadlo aj každý aktuálny motor pri každom predmete zmeny; označenie CLK ako „MOŽNÁ“ alebo stav „odoslaná“ bez volania zákonnú povinnosť neplní. | LAW | CONFIRMED | SRC-062-001, SRC-062-015, SRC-062-017, SRC-062-021 |
| RULE-062-004 | MUST_NOT | Pri jednoznačnom SIS hite sa nesmie zmeniť žiadny údaj a musí sa bezodkladne informovať Policajný zbor. | LAW | CONFIRMED | SRC-062-001 |
| RULE-062-005 | MUST | Nové osvedčenie vzniká iba vtedy,ak sa mení údaj osvedčenia; samotná iná zmena nesmie automaticky vydať duplikát. | LAW | CONFIRMED | SRC-062-001 |
| RULE-062-006 | MUST_NOT | Zmena záložných údajov nesmie predstierať vznik,zmenu ani zánik záložného práva bez hmotnoprávneho dokumentu. | LAW | CONFIRMED | SRC-062-001 |
| RULE-062-007 | DESCRIPTIVE | Sedem hodnôt implementačného selektora zostáva vetvami jedného procesu a vetva `other` potrebuje konkrétny predmet,dôvod a dôkaz. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-013 |
| RULE-062-008 | MUST | Časová história vlastníka,prevádzkovateľa,záložného práva a značky musí zachovať predchodcu a novú hodnotu bez prekrývajúcich sa aktuálnych vzťahov. | LAW | CONFIRMED | SRC-062-001 |
| RULE-062-009 | MUST_NOT | Predvolený dátum „včera“ nesmie byť prijatý ako právny účinok bez väzby na skutočný dátum zmeny a právoplatnosť rozhodnutia. | PROPOSAL | PROPOSED | SRC-062-013, SRC-062-012 |
| RULE-062-010 | MUST | Technický delta sa musí posúdiť voči všetkým procesom používajúcim Aircraft,Engine alebo Propeller; zmena registra sama nepovoľuje technickú prevádzku. | PROPOSAL | PROPOSED | SRC-062-001, SRC-062-012, SRC-062-031 |
| RULE-062-011 | MUST | Poplatkový základ sa vyberá podľa meneného dokladu/účinku,nie iba podľa MTOW. | LAW | CONFIRMED | SRC-062-003 |
| RULE-062-012 | MUST_NOT | Nezmenené polia,zdieľané subformuláre alebo staré vzorové hodnoty sa nesmú materializovať ako autorizované delta. | PROPOSAL | PROPOSED | SRC-062-013, SRC-062-014, SRC-062-022 |
| RULE-062-013 | MUST | Verejná a neverejná projekcia sa aktualizujú podľa klasifikácie konkrétneho údaja a nikdy nie kopírovaním celého formulára do verejnej časti. | LAW | CONFIRMED | SRC-062-001 |

## 10. Procesný tok

| ID | Poradie | Stav pred | Činnosť | Aktér | Podmienka | Stav po | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| STEP-062-001 | 1 | Existuje aktuálny zápis | Vlastník,zástupca alebo v obmedzenej vetve záložný veriteľ podá žiadosť s presným delta. | ACT-062-001,ACT-062-004 alebo ACT-062-005 | PRE-062-001 až PRE-062-004 | Konanie začaté | LAW | CONFIRMED | SRC-062-001, SRC-062-002, SRC-062-004 |
| STEP-062-002 | 2 | Konanie začaté | Úrad overí žiadateľa,30-dňovú povinnosť,predmet zmeny,úplnosť a formu dokladov. | ACT-062-006 | RULE-062-002 | Podanie úplné alebo vyžaduje doplnenie | LAW | CONFIRMED | SRC-062-001, SRC-062-002, SRC-062-004 |
| STEP-062-003 | 3 | Predmet zmeny známy | Úrad určí správny poplatkový základ podľa meneného dokladu,vyzve na úhradu a overí platbu. | ACT-062-006 | RULE-062-011 | Poplatok splnený alebo čaká na úhradu | LAW | CONFIRMED | SRC-062-003 |
| STEP-062-004 | 4 | Podanie úplné | Úrad načíta a uzamkne presnú základnú verziu existujúceho zápisu a vypočíta navrhované delta. | ACT-062-006 | PRE-062-001,PRE-062-010 | Kandidát zmeny pripravený | PROPOSAL | PROPOSED | SRC-062-012, SRC-062-031 |
| STEP-062-005 | 5 | Kandidát zmeny pripravený | Dopravný úrad vykoná a preukázateľne vyhodnotí SIS kontrolu lietadla a všetkých aktuálnych motorov. | ACT-062-006 | PRE-062-005 | SIS bez hitu alebo SIS hit | LAW | CONFIRMED | SRC-062-001 |
| STEP-062-006 | 6 | SIS bez jednoznačného hitu | Úrad posúdi dôvod,doklady,oprávnenie a dopad na osvedčenie,verejnú časť a súvisiace procesy. | ACT-062-006 | RULE-062-005 až RULE-062-013 | Vec pripravená na rozhodnutie | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| STEP-062-007 | 7 | Vec pripravená | Úrad vydá rozhodnutie o presnom autorizovanom delta alebo negatívne rozhodnutie. | ACT-062-006 | Výsledok dokazovania | Rozhodnutie oznámené | LAW | CONFIRMED | SRC-062-001, SRC-062-004 |
| STEP-062-008 | 8 | Rozhodnutie je právoplatné a základná verzia stále sedí | Úrad materializuje iba autorizované delta,zachová predchodcu a aktualizuje príslušnú verejnú alebo neverejnú projekciu. | ACT-062-006 | RULE-062-008,RULE-062-012,RULE-062-013 | Register zmenený | PROPOSAL | PROPOSED | SRC-062-001, SRC-062-012 |
| STEP-062-009 | 9 | Register zmenený | Ak sa zmenil údaj osvedčenia,úrad prevezme pôvodné a vydá nové osvedčenie;inak osvedčenie nevymieňa. | ACT-062-006 | RULE-062-005 | Osvedčenie nahradené alebo nezmenené | LAW | CONFIRMED | SRC-062-001 |
| STEP-062-010 | A1 | SIS hit | Úrad zmenu nevykoná a bezodkladne oznámi hit Policajnému zboru. | ACT-062-006 | RULE-062-004 | Nezmenené a oznámené PZ | LAW | CONFIRMED | SRC-062-001 |
| STEP-062-011 | A2 | Rozhodnutie oznámené | Oprávnená osoba môže podať rozklad a register sa nesmie prezentovať ako definitívne zmenený iba podľa času vytvorenia dokumentu. | ACT-062-001 alebo ACT-062-004 | TIM-062-004 | Rozkladové konanie alebo právoplatnosť | LAW | CONFIRMED | SRC-062-001, SRC-062-004 |
| STEP-062-012 | I1 | Elektronické podanie | Portál načíta existujúce entity,vyplní XML a odošle ho s prílohami cez ÚPVS/Fabasoft do backoffice. | Systém CRDÚ a Fabasoft | Portálový kanál | Backoffice podanie s klonovanými kandidátmi | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-011, SRC-062-016 |
| STEP-062-013 | I2 | Používateľ mení `enum_change_subject` | Groovy ukončuje staré owner/operator/lien vzťahy predchádzajúcim dňom,vytvára nové,prepína značku,výnimočný zápis alebo komentár. | Systém CRDÚ | Jedna zo siedmich vetiev | Kandidátske entity zmenené | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-013 |
| STEP-062-014 | I3 | Backoffice podanie | Backoffice vytvorí CLK iba pre motory a iba pri vetve `other`; všeobecná SIS vetva nemá volanie,ale nastaví stav odoslania. | Systém CRDÚ | Aktuálny kód | Neúplná/falošne odoslaná lustrácia | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-015, SRC-062-017 |
| STEP-062-015 | I4 | Referent vyberie výstup | Backoffice generuje jednu zo šiestich šablón a Fabasoftom riadi prerušenie,zastavenie alebo manuálne správoplatnenie. | ACT-062-009 a systém CRDÚ | Konfigurovaný výstup | Aktuálny technický koncový stav | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-011, SRC-062-022 až SRC-062-028 |

## 11. Výstupy, právne účinky a koncové stavy

| ID | Typ | Výstup/účinok | Právoplatnosť/platnosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| OUT-062-001 | Rozhodnutie | Rozhodnutie viažuce presný predmet,predchádzajúcu a novú hodnotu zmeny. | Podľa právoplatnosti a prijatého pravidla účinku | LAW | CONFIRMED | SRC-062-001, SRC-062-004 |
| OUT-062-002 | Register mutation | Aktualizácia iba autorizovaných údajov so zachovaním histórie. | Presný okamih účinku musí zodpovedať rozhodnutiu a nie technickému defaultu | LAW | CONFIRMED | SRC-062-001 |
| OUT-062-003 | Verejná projekcia | Aktualizácia verejných údajov podľa § 26 ods. 6. | Spolu s účinnou zmenou;nikdy širší rozsah | LAW | CONFIRMED | SRC-062-001 |
| OUT-062-004 | Nové osvedčenie | Nové osvedčenie nahrádzajúce pôvodné. | Iba ak sa mení údaj osvedčenia a pôvodné je vrátené | LAW | CONFIRMED | SRC-062-001 |
| OUT-062-005 | Bez nového osvedčenia | Register sa zmení bez automatického vydania osvedčenia. | Ak delta nezasahuje údaje osvedčenia | LAW | CONFIRMED | SRC-062-001 |
| OUT-062-006 | Záložné údaje | Zápis,zmena alebo ukončenie registračných údajov záložného práva. | Deklaratórny účinok;právo nevzniká zápisom | LAW | CONFIRMED | SRC-062-001 |
| OUT-062-007 | Prerušenie | Rozhodnutie o prerušení bez zmeny registra. | Lehoty neplynú počas zákonného prerušenia | LAW | CONFIRMED | SRC-062-004 |
| OUT-062-008 | Zastavenie | Rozhodnutie o zastavení bez zmeny registra. | Podľa dôvodu a správneho poriadku alebo zákona o poplatkoch | LAW | CONFIRMED | SRC-062-003, SRC-062-004 |
| OUT-062-009 | Negatívny výsledok | Register zostáva nezmenený pri nepreukázanom delta,neoprávnenom žiadateľovi alebo SIS hite. | Bez účinku na aktuálne údaje | LAW | CONFIRMED | SRC-062-001 |
| OUT-062-010 | Zakázaný účinok | Žiadna zmena štátnej príslušnosti,prvotný zápis,výmaz,schválenie letovej spôsobilosti ani automatická zmena Mode S/ELT. | N/A | LAW | CONFIRMED | SRC-062-001, SRC-062-009 |
| OUT-062-011 | Aktuálne výstupy | Osvedčenie,pause,stop a tri finishing rozhodnutia pre generic/operator/owner-operator variant. | Obsahovo nepokrývajú všetkých sedem vetiev a obsahujú vzorové konštanty | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-022 až SRC-062-028 |

## 12. Integrácie a notifikácie

| ID | Typ | Systém/príjemca | Účel/obsah | Kritickosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- |
| INT-062-001 | INTEGRATION | Portál DÚ a ÚPVS | Výber existujúceho lietadla,vyplnenie/autorizácia delta,XML a prílohy. | HIGH | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-009, SRC-062-011, SRC-062-016 |
| INT-062-002 | INTEGRATION | Fabasoft a integračná platforma | Registratúrny záznam,spis,riešiteľ,dokumenty a spracovanie výstupov. | HIGH | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-011 |
| INT-062-003 | INTEGRATION | Platobný modul a PEP | Výber kódu,predpis a úhrada poplatku. | HIGH | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-003, SRC-062-014, SRC-062-018 |
| INT-062-004 | INTEGRATION | SIS cez CLK | Povinná kontrola lietadla a všetkých motorov pri každom delta. | CRITICAL | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-001, SRC-062-015, SRC-062-017, SRC-062-021 |
| NOT-062-001 | NOTIFICATION | Policajný zbor | Bezodkladné oznámenie jednoznačného SIS hitu. | CRITICAL | LAW | CONFIRMED | SRC-062-001 |
| INT-062-005 | INTEGRATION | Register lietadiel a verejný portál | Aplikácia presného delta a aktualizácia verejnej projekcie. | CRITICAL | CURRENT_IMPLEMENTATION | UNKNOWN | SRC-062-001, SRC-062-010, SRC-062-011 |
| INT-062-006 | INTEGRATION | Generovanie dokumentov | Podmienené osvedčenie a rozhodnutia pre exact delta,pause a stop. | HIGH | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-022 až SRC-062-028 |
| NOT-062-002 | NOTIFICATION | Žiadateľ | Výzva na doplnenie,výzva na percentuálny poplatok,rozhodnutie a podmienené nové osvedčenie. | HIGH | OFFICIAL_PROCEDURE | UNKNOWN | SRC-062-003, SRC-062-004, SRC-062-011 |

## 13. Alternatívne, chybové a opravné scenáre

| ID | Spúšťač | Očakávané správanie | Koncový stav | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| ALT-062-001 | Žiadosť je neúplná alebo delta nie je preukázané. | Úrad vyzve na odstránenie nedostatkov,prípadne konanie preruší a pri neodstránení zastaví. | Doplnené,prerušené alebo zastavené | LAW | CONFIRMED | SRC-062-004 |
| ALT-062-002 | Vlastník podá žiadosť po 30 dňoch. | Porušenie lehoty sa zaznamená,ale aktuálne zdroje nepreukazujú,že oneskorenie oprávňuje ponechať register vedome nesprávny. | Konanie pokračuje;ďalší následok UNKNOWN | LAW | UNKNOWN | SRC-062-001 |
| ALT-062-003 | Záložný veriteľ žiada zmenu mimo § 26 ods. 5 písm. e). | Úrad nevykoná neautorizované delta a vyžiada žiadosť vlastníka. | Nezmenené | LAW | CONFIRMED | SRC-062-001 |
| ALT-062-004 | Percentuálny poplatok nie je zaplatený po výzve. | Úrad úkon nevykoná a konanie zastaví; proti zastaveniu pre nezaplatenie sa nemožno odvolať. | Zastavené pre nezaplatenie | LAW | CONFIRMED | SRC-062-003 |
| ALT-062-005 | SIS potvrdí pátranie po lietadle alebo motore. | Úrad zmenu nevykoná a bezodkladne informuje Policajný zbor. | Nezmenené a oznámené PZ | LAW | CONFIRMED | SRC-062-001 |
| ALT-062-006 | SIS/CLK nie je dostupné alebo chýba dôkaz volania/odpovede. | Žiadne delta sa nesmie materializovať;retry,eskalácia a používateľský stav vyžadujú prijatý návrh. | Blokované pred zmenou | LAW | CONFIRMED | SRC-062-001, SRC-062-017 |
| ALT-062-007 | Mení sa údaj osvedčenia,ale pôvodné osvedčenie nie je vrátené. | Nové osvedčenie sa nevydá bez splnenia REQ-062-008; register nesmie vytvoriť dve súčasne platné osvedčenia. | Čaká na vrátenie | LAW | CONFIRMED | SRC-062-001 |
| ALT-062-008 | Mení sa značka. | Musí sa zachovať časová história starej značky,overiť nová značka a použiť poplatkový základ písm. e),nie automaticky MTOW. | Značka zmenená alebo riadený konflikt | LAW | CONFIRMED | SRC-062-002, SRC-062-003 |
| ALT-062-009 | Menia sa technické parametre formulárom F471. | Delta sa vedie pod MUDU-062 a musí sa posúdiť voči zdieľaným technickým procesom;chýbajúca presná route väzba zostane konfliktom. | Kandidát technickej zmeny alebo blokované | OFFICIAL_PROCEDURE | CONFLICT | SRC-062-006, SRC-062-008, SRC-062-031 |
| ALT-062-010 | MTOW je presne 5 701 kg a základom je písm. a). | Systém nesmie skryť konflikt základnej sadzby a implementačnej hranice. | Konflikt poplatku | LAW | CONFLICT | SRC-062-003, SRC-062-014 |
| ALT-062-011 | Počas spracovania sa zmení základný register rovnakého lietadla. | Kandidát sa nesmie aplikovať; vykoná sa nové zosúladenie a dopadová kontrola. | Stale-base konflikt | PROPOSAL | PROPOSED | SRC-062-012, SRC-062-031 |
| ALT-062-012 | Vybraný output nezodpovedá predmetu zmeny alebo obsahuje vzorový poplatok,dátum,číslo či nesprávny proces. | Dokument sa pred odoslaním zablokuje;nesmie sa ručne použiť ako dôkaz správneho delta. | Výstup blokovaný | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-024 až SRC-062-028 |
| ALT-062-013 | Dopravný úrad preukáže nesprávnosť registra bez žiadosti. | Vykoná samostatnú internú vetvu s dôkazom,poučením a auditom;elektronická MUDU-062 cesta sa nepredstiera ako žiadosť. | Ex-officio korekcia alebo otvorená interná medzera | LAW | UNKNOWN | SRC-062-001 |
| ALT-062-014 | Podaný rozklad v lehote. | Register a nové osvedčenie sa nesmú prezentovať ako nezvratne účinné iba podľa vytvorenia výstupu. | Rozkladové konanie | LAW | CONFIRMED | SRC-062-001, SRC-062-004 |

## 14. Väzby na iné procesy a dopad zmien

| ID | Smer | Proces/artefakt | Typ väzby | Dopad | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DEP-062-001 | IN | MUDU-061 | PREDECESSOR | MUDU-062 vyžaduje aktuálny zápis a nikdy nezakladá novú štátnu príslušnosť; zmena musí zachovať identitu predchodcu. | LAW | CONFIRMED | SRC-062-001, SRC-062-031 |
| DEP-062-002 | OUT | MUDU-063 | SUCCESSOR | Výmaz ukončuje celý zápis a nesmie sa modelovať ako hodnota `other` v MUDU-062. | LAW | CONFIRMED | SRC-062-001, SRC-062-002, SRC-062-009 |
| DEP-062-003 | BOTH | MUDU-060 | OUT_OF_SCOPE | Post-registračná zmena značky patrí MUDU-062;predbežné pridelenie pred prvým zápisom patrí MUDU-060. | LAW | CONFIRMED | SRC-062-001, SRC-062-002 |
| DEP-062-004 | BOTH | MUDU-091 | OUT_OF_SCOPE | Mód S/ELT používa spoločné lietadlo a značku,ale MUDU-062 ho automaticky neprerozdeľuje. | OBSERVATION | CONFIRMED | SRC-062-009, SRC-062-031 |
| DEP-062-005 | BOTH | MUDU-059 | SHARED_OUTPUT | Lietadlová kniha môže byť vráteným dokladom a položka 92 písm. f) poplatkovým základom;jej vydanie zostáva samostatný proces. | LAW | CONFIRMED | SRC-062-002, SRC-062-003, SRC-062-009 |
| DEP-062-006 | BOTH | EA Vehicle 9482 a Aircraft 9923 | SHARED_ENTITY | Zmena identifikátora,technických údajov alebo registračného stavu vyžaduje dopadovú kontrolu MUDU-051 až 063,065,066 a091 podľa konkrétneho atribútu. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-012, SRC-062-031 |
| DEP-062-007 | BOTH | EA Engine 9925 a Propeller 9929 | SHARED_ENTITY | Zmena súčastí ovplyvňuje registračné,SIS,záložné,technické a údržbové väzby;MUDU-062 realizuje iba schválené registračné delta. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-012, SRC-062-031 |
| DEP-062-008 | BOTH | EA Owner 13387,Operator 13406 a Lien 16820 | SHARED_ENTITY | Časové roly zdieľajú MUDU-060/061/062/063 a nesmú sa zlúčiť;predchádzajúca a nová relácia musia zostať auditovateľné. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-062-001, SRC-062-012, SRC-062-031 |
| DEP-062-009 | BOTH | EA RegistrationMark 20919 a RegistrationMarkInTime 20926 | SHARED_ENTITY | Zmena značky musí uzavrieť starú časovú reláciu a vytvoriť novú bez použitia MUDU-060. | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-012, SRC-062-031 |
| DEP-062-010 | BOTH | CLK/SIS | SHARED_INTEGRATION | Rovnaká zákonná kontrola patrí MUDU-061 a MUDU-062;MUDU-062 implementácia má ešte užší a neúplný scope. | LAW | CONFIRMED | SRC-062-001, SRC-062-015, SRC-062-017 |
| DEP-062-011 | BOTH | Šesť outputov ID62 | SHARED_OUTPUT | Output musí zodpovedať presnému delta a podmienenej výmene osvedčenia;tri finishing šablóny nepokrývajú všetkých sedem vetiev. | CURRENT_IMPLEMENTATION | CONFLICT | SRC-062-022 až SRC-062-028 |
| DEP-062-012 | IN | F471 technical-parameter form | DEPENDS_ON | Verejný formulár je relevantný variant,ale bez samostatného katalógového ID a bez presnej implementačnej väzby. | OFFICIAL_PROCEDURE | CONFLICT | SRC-062-006, SRC-062-008, SRC-062-009 |

## 15. Akceptačné scenáre

| ID | Given | When | Then | Pokrýva | Stav |
| --- | --- | --- | --- | --- | --- |
| AC-062-001 | Vlastník do 30 dní preukáže zmenu prevádzkovateľa,úhradu a čistú SIS kontrolu. | Úrad rozhodne a rozhodnutie nadobudne právoplatnosť. | Zmení sa iba prevádzkovateľ a auditovaná časová relácia;nové osvedčenie vznikne iba ak obsahuje tento údaj. | REQ-062-001,REQ-062-005,REQ-062-007,RULE-062-008 | DRAFT |
| AC-062-002 | Záložný veriteľ preukáže vznik alebo zmenu zabezpečenej pohľadávky. | Podá žiadosť bez vlastníka. | Zmenia sa iba záložné údaje a zápis nevytvorí záložné právo. | REQ-062-002,REQ-062-009,RULE-062-002 | DRAFT |
| AC-062-003 | Záložný veriteľ žiada zmenu vlastníka alebo technického údaja. | Úrad overí oprávnenie. | Neautorizované delta sa nevykoná. | ALT-062-003,RULE-062-002 | DRAFT |
| AC-062-004 | Mení sa údaj,ktorý nie je uvedený v osvedčení. | Register sa právoplatne zmení. | Nevydá sa automaticky nové osvedčenie. | REQ-062-007,RULE-062-005,OUT-062-005 | DRAFT |
| AC-062-005 | Mení sa údaj osvedčenia a pôvodné osvedčenie je vrátené. | Zmena je právoplatná. | Vydá sa nové osvedčenie a existuje najviac jedno aktuálne. | REQ-062-007,REQ-062-008,OUT-062-004 | DRAFT |
| AC-062-006 | Lietadlo alebo ktorýkoľvek aktuálny motor má jednoznačný SIS hit. | Úrad vyhodnotí kontrolu. | Žiadne delta sa nevykoná a PZ je bezodkladne informovaný. | REQ-062-005,REQ-062-006,RULE-062-004 | DRAFT |
| AC-062-007 | CLK je `MOŽNÁ`,selector nie je `other` alebo technický stav iba hovorí `odoslaná`. | Systém sa pokúsi dokončiť zmenu. | Dokončenie je zablokované,pretože zákonná kontrola lietadla a motorov nie je preukázaná. | RULE-062-003,ALT-062-006,INT-062-004 | DRAFT |
| AC-062-008 | Predmetom je zmena registrovej značky. | Určuje sa poplatok a delta. | Použije sa25 % sadzby písm. e),zachová sa časová história značky a MUDU-060 sa nespustí. | FEE-062-003,ALT-062-008,DEP-062-003 | DRAFT |
| AC-062-009 | Predmetom je registračný doklad s MTOW 2 750,2 751 alebo5 700 kg. | Určuje sa poplatok podľa písm. a). | Základný výsledok je25,125 alebo125 EUR pred elektronickým znížením. | FEE-062-002,FEE-062-005 | DRAFT |
| AC-062-010 | MTOW je presne5 701 kg a relevantný základ je písm. a). | Určuje sa poplatok. | Vznikne explicitný konflikt a nie tichý kód3039. | FEE-062-004,ALT-062-010 | DRAFT |
| AC-062-011 | Žiadateľ mení technické parametre cez F471. | Podanie sa mapuje na portál. | Ide o variant MUDU-062 s presným technickým delta;chýbajúca route väzba a dopad na zdieľané procesy musia byť vyriešené. | SCP-062-010,RULE-062-010,DEP-062-012 | DRAFT |
| AC-062-012 | Medzi načítaním a aplikáciou sa zmení vlastník,motor alebo značka. | Kandidát sa dokončuje. | Stale kandidát sa neaplikuje a vyžaduje nové zosúladenie. | PRE-062-010,ALT-062-011,RULE-062-012 | DRAFT |
| AC-062-013 | Vyberie sa generic/operator/owner-operator šablóna pre iný predmet zmeny. | Dokument sa validuje pred odoslaním. | Nesprávny alebo hardcoded output sa zablokuje. | ALT-062-012,DEP-062-011 | DRAFT |
| AC-062-014 | Úrad preukáže nesprávny údaj bez žiadosti. | Spustí opravu z vlastného podnetu. | Oprava má osobitný audit a nepredstiera externé MUDU-062 podanie. | REQ-062-003,SCP-062-006,ALT-062-013 | DRAFT |
| AC-062-015 | Po zmene sa žiada výmaz alebo Mode S/ELT delta. | Používateľ pokračuje. | Použije MUDU-063 alebo MUDU-091;MUDU-062 sa nerozširuje na iný právny účinok. | DEP-062-002,DEP-062-004 | DRAFT |

## 16. Mapovanie na EA, Petriflow a kód

| ID | Vrstva implementácie | Artefakt | Presná väzba | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| MAP-062-001 | Katalóg | katalog_sluzieb.csv ID62 | `portal_aircraft_change_data_aircraft_complete_form`,XML `vehicle`,elektronická aktívna služba pre existujúce lietadlo. | CONFIRMED | SRC-062-009 |
| MAP-062-002 | Petriflow | enum_change_subject | Sedem možností owner,operator,new_lien,delete_lien,registration_mark,exceptional_entry,other. | CONFIRMED | SRC-062-013 |
| MAP-062-003 | Petriflow/Groovy | vehicle.xml change transition | Na výbere vetvy ukončuje staré časové vzťahy,vytvára nové,prepína značku,výnimočný zápis alebo komentár. | CONFLICT | SRC-062-013 |
| MAP-062-004 | Petriflow | aircraft.xml part1 | Editovateľné type,model,year,MTOW,passengers,serial,actual placement;poplatky3037-3039 podľa MTOW. | CONFLICT | SRC-062-014 |
| MAP-062-005 | Petriflow | aircraft.xml part2 | Editovateľné motory,vrtule a polia rozhodnutia o výnimočnom zápise. | CONFIRMED | SRC-062-014 |
| MAP-062-006 | Poplatková konfigurácia | portal_spravne_poplatky.csv | ID62 je viazané na3037,3038,3039;ID61 je viazané na3034,200,3036,čo odporuje XML kódu3035. | CONFLICT | SRC-062-018 |
| MAP-062-007 | Konfigurácia | katalog_workflow.csv ID62 | Workflow `Poplatok + Lustrácie`. | CONFIRMED | SRC-062-020 |
| MAP-062-008 | Konfigurácia | lustracie_a_sluzby.csv ID62 | Lustrácia `MOŽNÁ`,CLK `X`,hoci zákon vyžaduje kontrolu pri každej zmene. | CONFLICT | SRC-062-001, SRC-062-021 |
| MAP-062-009 | Backoffice/Petriflow | backoffice_workflow_submission.xml | CLK cases sa vytvoria iba pre motory a iba pri selector `other`;aircraft case chýba. | CONFLICT | SRC-062-015 |
| MAP-062-010 | Petriflow | lustration.xml | SIS vetva má iba komentár o chýbajúcej integrácii,ale spoločný koniec nastaví čas a stav `odoslana`. | CONFLICT | SRC-062-017 |
| MAP-062-011 | Konfigurácia | prilohy_formularov.csv ID62 | Osem riadkov plošne vyžaduje change proof,insurance,declaration,logs,book,photos,certificate;iba operating agreement je označená podmienená. | CONFLICT | SRC-062-019 |
| MAP-062-012 | EA | Vehicle9482 a Aircraft9923 | Vehicle nesie register dates,identifier,number,lien,temp mark;Aircraft nesie technické,výnimočné,insurance a location údaje. | CONFIRMED | SRC-062-012 |
| MAP-062-013 | EA | Owner13387,Operator13406,Lien16820,RegistrationMark20919/20926 | Samostatné časové role a značka v čase;EA kardinality nevytvárajú právnu autoritu. | CONFIRMED | SRC-062-012 |
| MAP-062-014 | EA/CLK | Engine9925,Propeller9929,AircraftEngineResult40113 | Súčasti majú vlastnú platnosť a SIS výsledok;existencia modelu nie je vykonaná kontrola. | CONFLICT | SRC-062-012, SRC-062-017 |
| MAP-062-015 | Výstupná konfigurácia | word_templates.json ID62 | Šesť outputov:osvedčenie,pause,stop a tri finishing change rozhodnutia. | CONFIRMED | SRC-062-022 |
| MAP-062-016 | Výstupná šablóna | Osvedcenie_o_zapise_do_RLSR.docx | Zdieľaná registračná šablóna;má sa vydať iba pri zmene údajov osvedčenia. | CONFLICT | SRC-062-001, SRC-062-023 |
| MAP-062-017 | Výstupná šablóna | Prerusenie_konania_DCL_zmena_udajov.docx | Obsahuje neúplnú vetu,hardcoded záznam43110,poplatok20 EUR a zastaraný limit zníženia70 EUR. | CONFLICT | SRC-062-024 |
| MAP-062-018 | Výstupná šablóna | Zastavenie_konania_DCL_zmena_udajov.docx | Výrok je change,odôvodnenie hovorí o pridelení značky a podpisuje vedúci OLNS;obsahuje neoverenú refund logiku. | CONFLICT | SRC-062-025 |
| MAP-062-019 | Výstupná šablóna | Rozhodnutie_zmena_sidla_prevadzkovatela.docx | Text mení prevádzkovateľa,opakuje reference number a hardcoduje certifikát1105/04,poplatok45 EUR a dátum06.10.2023. | CONFLICT | SRC-062-026 |
| MAP-062-020 | Výstupná šablóna | Rozhodnutie_zmena_sidla_vlastnika_a_prevadzkovatela.docx | Text mení sídlo owner/operator a hardcoduje certifikát1114/05,poplatok45 EUR a dátum25.09.2023. | CONFLICT | SRC-062-027 |
| MAP-062-021 | Výstupná šablóna | Rozhodnutie_zmena_udajov.docx | Generic output v skutočnosti mení prevádzkovateľa a hardcoduje poplatok45 EUR a dátum06.10.2023. | CONFLICT | SRC-062-028 |
| MAP-062-022 | Official form | F471 technical parameter change | Jednostranový formulár pre aircraft/engine/propeller technické údaje a fotografie;bez samostatného katalógového ID alebo exact route. | CONFLICT | SRC-062-006, SRC-062-008, SRC-062-009 |
| MAP-062-023 | Knowledge transfer | Portal→ÚPVS→Fabasoft→Backoffice and output/finality flow | Elektronické/fyzické podanie,tree reconstruction,attachments,outputs a manuálne správoplatnenie. | CONFIRMED | SRC-062-011 |
| MAP-062-024 | SharePoint | Historical change form and expanded-data workbook | Starší input má širšie blanket prílohy;workbook je field-definition input,nie aktuálny register rows. | CONFIRMED | SRC-062-029, SRC-062-030 |
| MAP-062-025 | Test/mock inventory | Sealed17-repository mirror | Nula exact MUDU-062/selector testov;nula SIS/CLK integration modules or mocks in mudu-integrations. | UNKNOWN | SRC-062-032 |

## 17. Medzery, konflikty a otvorené rozhodnutia

| ID | Typ | Otázka/konflikt | Potrebné rozhodnutie | Vlastník | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| GAP-062-001 | SOURCE_CONFLICT | F470,F471,historický SharePoint formulár a osem attachment rows plošne vyžadujú technické údaje a dokumenty,ktoré § 2 viaže iba na konkrétny delta alebo vôbec neuvádza. | Prijať jednu change-subject maticu polí,dokladov,formy a prekladov podľa aktuálneho práva. | Vecný gestor + legislatíva | CONFLICT | SRC-062-002, SRC-062-007, SRC-062-008, SRC-062-019, SRC-062-029 |
| GAP-062-002 | SOURCE_CONFLICT | Stránka DÚ uvádza vyhlášku274/2004 namiesto274/2024 a blanket originál/overená kópia nezodpovedá § 5. | Opraviť obe verejné inštrukcie. | Dopravný úrad + legislatíva | CONFLICT | SRC-062-002, SRC-062-005, SRC-062-006 |
| GAP-062-003 | INTENT_QUESTION | F471 je verejný samostatný formulár,ale nemá samostatné katalógové ID ani preukázanú portálovú route. | Potvrdiť,že je variant MUDU-062,a zviazať exact selector/fields/attachments bez vytvorenia257.processu. | Vecný gestor + Netgrif | UNKNOWN | SRC-062-006, SRC-062-008, SRC-062-009 |
| GAP-062-004 | IMPLEMENTATION_GAP | Sedem selectorov nepokrýva explicitne všetky údaje § 26 ods. 5 a `other` nemá strojovo typovaný delta contract. | Zaviesť presný change contract s old/new value,reason,evidence and affected consumers. | Vecný gestor + Netgrif | UNKNOWN | SRC-062-001, SRC-062-013 |
| GAP-062-005 | IMPLEMENTATION_GAP | Zákon vyžaduje SIS pre každú zmenu,ale konfigurácia hovorí `MOŽNÁ`,BackOffice vytvára iba engine cases pre `other`,aircraft check chýba a SIS call nie je implementovaný. | Realizovať mandatory aircraft+all-engine request/result/hit/police gate pre každú vetvu a fail closed. | Netgrif + vecný gestor | CONFLICT | SRC-062-001, SRC-062-015, SRC-062-017, SRC-062-021 |
| GAP-062-006 | IMPLEMENTATION_GAP | Poplatok závisí od meneného dokladu,ale kód vyberá3037-3039 iba podľa MTOW a nerieši mark/book basis;presných5701 kg zostáva nejasných. | Zviazať selector/delta s položkou92(a,c,e,f),výpočtom,elektronickým znížením a testami. | Legislatíva + vecný gestor + Netgrif | CONFLICT | SRC-062-003, SRC-062-014, SRC-062-018 |
| GAP-062-007 | IMPLEMENTATION_GAP | MUDU-061 aircraft.xml používa3035 pre middle band,ale portal fee CSV viaže ID61 na200. | Autoritatívne určiť správny PEP code a zosúladiť zdroje bez tichej substitúcie. | Netgrif + prevádzkovateľ PEP | CONFLICT | SRC-062-014, SRC-062-018 |
| GAP-062-008 | IMPLEMENTATION_GAP | Output configuration nemá presný output pre owner,lien add/delete,mark,exceptional entry,technical delta a other;generic output hovorí o operator change. | Definovať exact-delta output coverage a obsahovú validáciu. | Vecný gestor + Netgrif | CONFLICT | SRC-062-022, SRC-062-026, SRC-062-027, SRC-062-028 |
| GAP-062-009 | IMPLEMENTATION_GAP | Pause/stop a finishing šablóny obsahujú broken text,wrong process/role,hardcoded certificate numbers,45EUR and2023 dates;pause uses obsolete70EUR cap. | Nahradiť vzorové konštanty a procesovo nesprávny text exact data bindingom. | Netgrif + vecný gestor | CONFLICT | SRC-062-024 až SRC-062-028 |
| GAP-062-010 | IMPLEMENTATION_GAP | Osvedčenie je vždy dostupný output,ale zákon ho vyžaduje iba pri zmene údajov osvedčenia. | Zaviesť deterministic certificate-impact predicate and old-certificate return gate. | Vecný gestor + Netgrif | CONFLICT | SRC-062-001, SRC-062-022, SRC-062-023 |
| GAP-062-011 | IMPLEMENTATION_GAP | Owner/operator/lien end dates default to previous day and exceptional date/number reset uses boolean types. | Zviazať účinnosť s accepted finality/event date and correct date/text types. | Vecný gestor + Netgrif | CONFLICT | SRC-062-013 |
| GAP-062-012 | INTENT_QUESTION | Ex-officio correction under § 26 ods. 9 has no exact internal route,authority/audit workflow or catalogue disposition. | Navrhnúť osobitnú internú vetvu bez predstierania external request. | Vecný gestor + Netgrif | UNKNOWN | SRC-062-001, SRC-062-009 |
| GAP-062-013 | IMPLEMENTATION_GAP | Atómová stale-base kontrola a concurrent owner/operator/mark/technical delta nebola preukázaná. | Definovať predecessor version,conflict policy,transaction,rollback and audit. | Vecný gestor + Netgrif | UNKNOWN | SRC-062-012, SRC-062-031 |
| GAP-062-014 | EVIDENCE_GAP | Neexistuje exact procesový test,fixture ani SIS/CLK mock/module v zachytených repozitároch. | Po akceptácii definície vytvoriť deterministic fixtures,third-party mocks,formal invariants and API/data/Playwright tests. | Netgrif | UNKNOWN | SRC-062-032 |
| GAP-062-015 | EVIDENCE_GAP | Nebol preukázaný end-to-end MUDU-062 beh cez všetkých sedem delta variantov,platbu,SIS,output,právoplatnosť,register,certificate predicate a public projection. | Overiť každý variant proti presne tejto definícii;ordinary bug nie je formal counterexample. | Netgrif + analytik | UNKNOWN | SRC-062-010, SRC-062-011, SRC-062-032 |
| Q-062-001 | INTENT_QUESTION | Aký je autoritatívny okamih účinku zmeny:skutočný event,právoplatnosť rozhodnutia alebo iný dátum pri jednotlivých typoch delta? | Prijať per-delta effective-date rule and temporal-history invariant. | Vecný gestor + legislatíva | UNKNOWN | SRC-062-001, SRC-062-013, SRC-062-022 |
| Q-062-002 | EVIDENCE_GAP | Vyriešené vo verzii 0.1.1: MUDU-063 je manuálne definované a recipročná kontrola potvrdila, že výmaz nie je `other` change variant, nevyžaduje SIS a musí zachovať históriu pri časovom uzavretí aktuálneho zápisu. | Bez ďalšieho rozhodnutia; obnoviť kontrolu pri zmene MUDU-060 až MUDU-063. | Codex | CONFIRMED | SRC-062-033 |

## 18. Schválenie a história zmien

| Verzia | Dátum | Zmena | Autorita | Stav |
| --- | --- | --- | --- | --- |
| 0.1.0 | 2026-09-01 | Prvý manuálny zdrojovo uzavretý návrh MUDU-062;zákonná change duty,applicant scope,SIS,conditional certificate,fee-by-document,seven UI variants,F470/F471,SharePoint,EA,Petriflow,outputs and tests/mocks were reconciled;MUDU-060/061/063/091 boundaries explicit. | UNCONFIRMED | DRAFT |
| 0.1.1 | 2026-09-01 | MUDU-063 uzavrelo prvý štvorprocesový fixed point; hranica change-versus-deregistration, rozdiel príloh, no-SIS výmaz a spoločné časové efekty sú recipročné a zostávajúce implementačné medzery explicitné. | UNCONFIRMED | DRAFT |

## 19. Register zdrojov

| ID | Typ | Názov/verzia | Lokátor | Ustanovenie/rozsah | SHA-256 | Účinnosť/pozorovanie |
| --- | --- | --- | --- | --- | --- | --- |
| SRC-062-001 | LAW | Zákon č.143/1998 Z.z.,časová verzia | https://static.slov-lex.sk/pdf/SK/ZZ/1998/143/ZZ_1998_143_20260101.pdf | § 26 ods.5-14;§ 55 | 0f0dc9039cabbd83e7096ff290bb0f555c8274f2160a8b307dff8a5cc3a754b3 | účinné od2026-01-01 |
| SRC-062-002 | LAW | Vyhláška č.274/2024 Z.z. | https://static.slov-lex.sk/static/SK/ZZ/2024/274/20241115.html | § 2;§ 5-7;úplný text§1-8 | c573893fcebc0ce4f5a095abfb98a6bf43b82a33974b8346fa9ea185f66a6152 | účinné od2024-11-15;zachytené2026-08-31 |
| SRC-062-003 | LAW | Zákon č.145/1995 Z.z.,časová verzia | https://static.slov-lex.sk/static/SK/ZZ/1995/145/20260901.html | § 6 ods.2;§ 8-9;sadzobník položka92 písm.a),c),e),f),g) | 6ee20746fa191be9ecfbd636770bb78d452fb392716e0e9e124d0e35ee0b8aed | účinné od2026-09-01;raw HTML zachytené2026-09-01 |
| SRC-062-004 | LAW | Zákon č.71/1967 Zb.,časová verzia | https://static.slov-lex.sk/pdf/SK/ZZ/1967/71/ZZ_1967_71_20180901.pdf | § 16-19;§ 27-30;§ 46-49;§ 54-61 | 39192cf3b53dbf90d859a1d08412054e8667de5e50366ee87eb933e2fbaec674 | účinné od2018-09-01;história skontrolovaná2026-08-31 |
| SRC-062-005 | OFFICIAL_PROCEDURE | DÚ — Register lietadiel SR | https://letectvo.nsat.sk/letova-sposobilost/register-lietadiel-slovenskej-republiky/ | verejný opis registra a legislatívy | a01d763383bb9ece8e2a3334f68ce480a9b5a2782474ea5afc939376fb53576f | pozorované2026-08-31 |
| SRC-062-006 | OFFICIAL_PROCEDURE | DÚ — Formuláre registra lietadiel | https://letectvo.nsat.sk/letova-sposobilost/register-lietadiel-slovenskej-republiky/formulare/ | applicant,attachment instructions,F470/F471 links | 9b5a43963f79a58dbfffad0b74ec3a4f9c128cbfeb9c19c398823d9aa3b669a4 | pozorované2026-08-31 |
| SRC-062-007 | OFFICIAL_FORM | DÚ F470-B/v1/OSL | https://letectvo.nsat.sk/wp-content/uploads/sites/2/2023/03/F470_B_v1_ZMENA-Z%C3%81PISU-DO-RL_FINAL.pdf | všetkých8 strán | 7332078c250f0e66f945186e0e75390c2cd52c3b8d509b2d82d96331b6306b28 | aktuálne prepojené DÚ;dokument2023;prečítané2026-09-01 |
| SRC-062-008 | OFFICIAL_FORM | DÚ F471-B/v1/OSL | https://letectvo.nsat.sk/wp-content/uploads/sites/2/2023/03/F471_B_v1_ZMENA-V-TECHNICK%C3%9DCH-PARAMETROCH_FINAL.pdf | celý1-stranový formulár | 5e73c827bdffc3c927ce73045852f23b13705047ddf617a44e1ab78f444460dd | aktuálne prepojené DÚ;zachytené a prečítané2026-09-01 |
| SRC-062-009 | CONFIGURATION | Katalóg služieb IS CRDÚ | not published in this repository | ID62 a susedné60/61/63/91;žiadna samostatná F471 identita | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-010 | CONFIGURATION | Aircraft registration EA/code context v2 | not published in this repository | ID60-63,EA14/108/13,CSV,XML,SharePoint,outputs,CLK | UNKNOWN | zachytené2026-08-31;private/project evidence reviewed internally;not redistributed |
| SRC-062-011 | KNOWLEDGE_TRANSFER | MUDU knowledge transfer | not published in this repository | submission channels,tree reconstruction,attachments,outputs,finality,CLK | UNKNOWN | lokálny zdroj prečítaný2026-09-01;private/project evidence reviewed internally;not redistributed |
| SRC-062-012 | EA | EA objects,attributes and relations for MUDU-062 | not published in this repository | 14 objektov,108 atribútov,13 vzťahov | UNKNOWN | offline snapshot2026-08-20;výber2026-09-01;private/project evidence reviewed internally;not redistributed |
| SRC-062-013 | PETRIFLOW | vehicle.xml | not published in this repository | ID62 transition,enum_change_subject and Groovy branches | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-014 | PETRIFLOW | aircraft.xml | not published in this repository | ID62 part1/part2 fields,engines,propellers and fee3037-3039 | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-015 | PETRIFLOW | backoffice_workflow_submission.xml | not published in this repository | service62 lustration creation branch | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-016 | PETRIFLOW | ziadost_sluzby.xml | not published in this repository | ID62 portal reconstruction/composition | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-017 | PETRIFLOW | lustration.xml | not published in this repository | SIS send branches and common sent-status tail | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-018 | CONFIGURATION | portal_spravne_poplatky.csv | not published in this repository | ID61/62 fee rows;3034/200/3036 versus3037/3038/3039 | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-019 | CONFIGURATION | prilohy_formularov.csv | not published in this repository | osem riadkov ID62 | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-020 | CONFIGURATION | katalog_workflow.csv | not published in this repository | ID62 Poplatok+Lustrácie | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-021 | CONFIGURATION | lustracie_a_sluzby.csv | not published in this repository | ID62 MOŽNÁ,CLK X | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-022 | CONFIGURATION | word_templates.json | not published in this repository | šesť outputov ID62 | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-023 | OUTPUT_TEMPLATE | Osvedcenie_o_zapise_do_RLSR.docx | not published in this repository | celý dokument | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-024 | OUTPUT_TEMPLATE | Prerusenie_konania_DCL_zmena_udajov.docx | not published in this repository | celý dokument,header/footer | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-025 | OUTPUT_TEMPLATE | Zastavenie_konania_DCL_zmena_udajov.docx | not published in this repository | celý dokument,header/footer | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-026 | OUTPUT_TEMPLATE | Rozhodnutie_zmena_sidla_prevadzkovatela.docx | not published in this repository | celý dokument,header/footer | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-027 | OUTPUT_TEMPLATE | Rozhodnutie_zmena_sidla_vlastnika_a_prevadzkovatela.docx | not published in this repository | celý dokument,header/footer | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-028 | OUTPUT_TEMPLATE | Rozhodnutie_zmena_udajov.docx | not published in this repository | celý dokument,header/footer | UNKNOWN | zachytená lokálna revízia;private/project evidence reviewed internally;not redistributed |
| SRC-062-029 | SHAREPOINT | Historická žiadosť o zmenu zápisu | not published in this repository | celý1-stranový input | UNKNOWN | zachytené2026-08-31;historický input;private/project evidence reviewed internally;not redistributed |
| SRC-062-030 | SHAREPOINT | Rozšírenie registra lietadiel.xlsx | not published in this repository | Hárok1 A1:BF2 | UNKNOWN | zachytené2026-08-31;field-definition input;private/project evidence reviewed internally;not redistributed |
| SRC-062-031 | SOURCE_DRAFT | MUDU-062 graph-neighbourhood dossier | not published in this repository | 57 direct relations and reverse consumers;navigation,not authority | UNKNOWN | snapshote3eb0e7e;created and manually reviewed2026-09-01;private/project evidence reviewed internally;not redistributed |
| SRC-062-032 | SOURCE_DRAFT | MUDU-062 test/mock inventory | not published in this repository | exact task/selector repository search and mudu-integrations modules | UNKNOWN | sealed repository mirror;reviewed2026-09-01;private/project evidence reviewed internally;not redistributed |
| SRC-062-033 | SOURCE_DRAFT | MUDU-063 process definition 0.1.0 DRAFT | not published in this repository | všetkých19 sekcií;change-versus-deregistration hranica | UNKNOWN | manuálne skontrolované2026-09-01;UNCONFIRMED;private/project evidence reviewed internally;not redistributed |
