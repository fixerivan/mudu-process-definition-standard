---
schema: mudu-process-definition/v1
process_id: MUDU-061
catalogue_id: "061"
catalogue_name: "Žiadosť o zápis lietadla do registra lietadiel"
canonical_name: "Zápis lietadla do registra lietadiel Slovenskej republiky"
definition_version: 0.1.3
definition_status: DRAFT
authority_status: UNCONFIRMED
source_selection: SELECTED
implementation_conformance: NONCONFORMANT
formal_verification: NOT_RUN
language: sk
source_baseline_date: 2026-09-01
supersedes: "MUDU-061@0.1.2"
related_processes: [MUDU-060, MUDU-062, MUDU-063, MUDU-091]
---

# MUDU-061 — Zápis lietadla do registra lietadiel Slovenskej republiky

> **Verejný pracovný príklad:** Verejné právne a oficiálne zdroje sú prepojené
> priamo. Interné projektové podklady sú iba opísané, nie zverejnené. Dokument
> zostáva `DRAFT / UNCONFIRMED` — vecný gestor ho ešte neschválil.

> Dopravný úrad na žiadosť vlastníka zapíše oprávnené lietadlo do registra
> lietadiel, pridelí mu registrovú značku, vydá osvedčenie o zápise a zápisom
> mu vznikne štátna príslušnosť Slovenskej republiky.

**Rýchly prehľad**

| Otázka | Odpoveď |
| --- | --- |
| Kto proces spúšťa? | Vlastník lietadla alebo preukázaný zástupca. |
| Čo úrad overuje? | Podmienky zápisu, údaje, prílohy, poplatok a povinnú kontrolu lietadla aj všetkých motorov v SIS. |
| Aký je úspešný výsledok? | Lietadlo sa zapíše, získa štátnu príslušnosť SR a značku; úrad vydá osvedčenie a zverejní zákonnú časť registra. |
| Čo sem nepatrí? | Predbežná značka je MUDU-060, neskoršia zmena MUDU-062 a výmaz MUDU-063. |
| Čo ešte treba rozhodnúť alebo opraviť? | Reálne volanie SIS, právoplatnosť a poradie účinkov, nesprávne šablóny a ochranu jedinečnosti pri súbehu. |
| Jednoduchý priebeh | [Otvoriť diagram procesu](graph.md) |

## 1. Identita a stav

| Pole | Hodnota |
| --- | --- |
| Katalógové ID | 061 |
| Katalógový názov | Žiadosť o zápis lietadla do registra lietadiel |
| Kanonický názov | Zápis lietadla do registra lietadiel Slovenskej republiky |
| Vecný gestor | Dopravný úrad, Divízia civilného letectva, register lietadiel |
| Typ procesu | REGISTRY_MUTATION |
| Definičný stav | DRAFT |
| Autorita | UNCONFIRMED |
| Jazyk | sk |

## 2. Účel, spúšťač a hranice

| ID | Typ | Tvrdenie | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| SCP-061-001 | PURPOSE | Zapísať lietadlo do registra lietadiel Slovenskej republiky, prideliť mu registrovú značku a vydať osvedčenie o zápise. | LAW | CONFIRMED | SRC-061-001 |
| SCP-061-002 | TRIGGER | Vlastník lietadla podá žiadosť o zápis lietadla do registra lietadiel. | LAW | CONFIRMED | SRC-061-001 |
| SCP-061-003 | IN_SCOPE | Posúdenie podmienok zápisu, údajov a príloh, povinná kontrola lietadla a motora v SIS, rozhodnutie, zápis, pridelenie značky, vydanie osvedčenia a zverejnenie verejnej časti údajov. | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| SCP-061-004 | IN_SCOPE | Zápis údajov o vlastníkoch, prevádzkovateľovi, lietadle, súčastiach, registrovej značke, dátume zápisu, výnimočnom povolení a prípadnom záložnom práve v zákonnom rozsahu. | LAW | CONFIRMED | SRC-061-001 |
| SCP-061-005 | OUT_OF_SCOPE | Predbežné pridelenie registrovej značky pred zápisom je MUDU-060. Platné predbežné pridelenie môže byť vstupom, ale samo lietadlo nezapisuje. | LAW | CONFIRMED | SRC-061-001 |
| SCP-061-006 | OUT_OF_SCOPE | Zmena údajov po zápise je MUDU-062 a výmaz lietadla je MUDU-063. | LAW | CONFIRMED | SRC-061-001, SRC-061-002, SRC-061-008 |
| SCP-061-007 | OUT_OF_SCOPE | Overenie alebo vydanie osvedčenia letovej spôsobilosti nie je právnym účinkom zápisu a patrí samostatným procesom letovej spôsobilosti. | LAW | CONFIRMED | SRC-061-001 |
| SCP-061-008 | OUT_OF_SCOPE | Pridelenie kódu módu S alebo kódu ELT je samostatný proces MUDU-091; zdieľané údaje o lietadle z neho nerobia súčasť zápisu. | OBSERVATION | CONFIRMED | SRC-061-008, SRC-061-025 |
| SCP-061-009 | OUT_OF_SCOPE | Bezpilotné lietadlo, ktorého projektový návrh podlieha certifikácii a zapisuje sa do registra podľa § 45b, sa nezapisuje týmto procesom. | LAW | CONFIRMED | SRC-061-001 |

## 3. Autorita a právny základ

| ID | Modalita | Normatívne pravidlo | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| REQ-061-001 | MUST | Lietadlo zapísané v registri lietadiel má štátnu príslušnosť Slovenskej republiky. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-002 | MUST | Do registra sa zapisuje lietadlo vo vlastníctve právnickej osoby so sídlom v SR alebo fyzickej osoby so štátnym občianstvom SR a trvalým pobytom v SR, alebo lietadlo prevádzkované takouto osobou. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-003 | MUST | Výnimočný zápis lietadla, ktoré nespĺňa REQ-061-002, vyžaduje povolenie ministerstva. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-004 | MUST_NOT | Lietadlo zapísané v registri cudzieho štátu sa nesmie zapísať do registra lietadiel SR. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-005 | MUST_NOT | Lietadlo patriace do registra certifikovaných bezpilotných lietadiel podľa § 45b sa nesmie zapísať týmto procesom. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-006 | MUST | Zápis vykoná Dopravný úrad na základe žiadosti vlastníka lietadla; samostatnú žiadosť iba o údaje záložného práva môže podať aj záložný veriteľ. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-007 | MUST | Zápisom sa lietadlu prideľuje registrová značka a Dopravný úrad vydáva osvedčenie o zápise. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-008 | MUST | Pred zápisom Dopravný úrad preverí v SIS lietadlo aj motor lietadla podľa nariadenia EÚ 2018/1862. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-009 | MUST_NOT | Pri jednoznačnom a nepochybnom pátraní v SIS Dopravný úrad zápis nevykoná a bezodkladne oznámi skutočnosť Policajnému zboru. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-010 | MUST | Žiadosť a jej prílohy musia spĺňať § 1 a § 5 vyhlášky č. 274/2024 Z. z. | LAW | CONFIRMED | SRC-061-002 |
| REQ-061-011 | MUST | Register obsahuje údaje podľa § 26 ods. 5; verejná časť sa zverejňuje iba v rozsahu § 26 ods. 6 a ostatné údaje zostávajú v neverejnej časti. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-012 | MUST_NOT | Zápis údajov o záložnom práve do registra sám osebe záložné právo nevytvára. | LAW | CONFIRMED | SRC-061-001 |
| REQ-061-013 | MUST | Na konanie sa vzťahuje správny poriadok a proti rozhodnutiu Dopravného úradu možno podať rozklad; rozhoduje o ňom predseda Dopravného úradu na návrh osobitnej komisie. | LAW | CONFIRMED | SRC-061-001, SRC-061-004 |
| REQ-061-014 | MUST_NOT | Úspešný zápis sa nesmie považovať za schválenie letovej spôsobilosti lietadla. | LAW | CONFIRMED | SRC-061-001 |

## 4. Aktéri a oprávnenia

| ID | Aktér | Typ | Oprávnenie a zodpovednosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| ACT-061-001 | Vlastník lietadla | Externý žiadateľ | Podáva žiadosť, preukazuje vlastníctvo, uvádza zákonné údaje a po zápise zodpovedá za oznamovanie zmien. | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| ACT-061-002 | Spoluvlastníci lietadla | Externé dotknuté osoby | Sú zapísaní v zákonnom rozsahu; oprávnenie jedného konať za ostatných musí vyplývať zo zastúpenia alebo predložených listín. | LAW | CONFIRMED | SRC-061-001, SRC-061-002, SRC-061-004 |
| ACT-061-003 | Prevádzkovateľ lietadla | Externá dotknutá osoba | Jeho údaje a právny titul na prevádzkovanie sa preukazujú, ak nie je vlastníkom; jeho slovenský status môže založiť spôsobilosť lietadla na zápis. | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| ACT-061-004 | Splnomocnený zástupca | Externý zástupca | Koná za vlastníka v rozsahu preukázaného splnomocnenia; aktuálna stránka DÚ výslovne pripúšťa podanie oprávneným zástupcom. | OFFICIAL_PROCEDURE | CONFIRMED | SRC-061-004, SRC-061-006 |
| ACT-061-005 | Záložný veriteľ | Externá dotknutá osoba | Môže podať žiadosť o zápis alebo zmenu údajov záložného práva; nie je všeobecným žiadateľom o zápis lietadla. | LAW | CONFIRMED | SRC-061-001 |
| ACT-061-006 | Dopravný úrad | Orgán verejnej moci | Vedie register, posudzuje žiadosť, vykonáva SIS kontrolu, rozhoduje, zapisuje lietadlo, prideľuje značku, vydáva osvedčenie a zverejňuje verejné údaje. | LAW | CONFIRMED | SRC-061-001 |
| ACT-061-007 | Ministerstvo dopravy SR | Iný orgán verejnej moci | Povoľuje výnimočný zápis, ak lietadlo nespĺňa bežné podmienky § 25 ods. 3. | LAW | CONFIRMED | SRC-061-001 |
| ACT-061-008 | Policajný zbor | Iný orgán verejnej moci | Prijíma bezodkladné oznámenie pri jednoznačnom a nepochybnom výsledku pátrania v SIS. | LAW | CONFIRMED | SRC-061-001 |
| ACT-061-009 | Referent registra lietadiel | Interná rola | V aktuálnom riešení spracúva podanie a pripravuje výstupy; presná hranica oprávnení voči schvaľovateľovi nie je autoritatívne doložená. | CURRENT_IMPLEMENTATION | UNKNOWN | SRC-061-009, SRC-061-010 |
| ACT-061-010 | Predseda Dopravného úradu a osobitná komisia | Odvolací orgán | Predseda rozhoduje o rozklade na návrh osobitnej komisie. | LAW | CONFIRMED | SRC-061-001 |

## 5. Vstupy a predpoklady

| ID | Podmienka alebo vstup | Povinnosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| PRE-061-001 | Lietadlo spĺňa podmienku vlastníka alebo prevádzkovateľa podľa REQ-061-002, alebo existuje povolenie ministerstva podľa REQ-061-003. | REQUIRED | LAW | CONFIRMED | SRC-061-001 |
| PRE-061-002 | Lietadlo nie je zapísané v registri cudzieho štátu a nepatrí do vylúčeného registra podľa § 45b. | REQUIRED | LAW | CONFIRMED | SRC-061-001 |
| PRE-061-003 | Vlastník a lietadlo sú jednoznačne identifikované; ak je prevádzkovateľ iný, je doložený jeho právny titul. | REQUIRED | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| PRE-061-004 | K dispozícii sú všetky povinné a podmienene povinné prílohy DOC-061-001 až DOC-061-008. | REQUIRED | LAW | CONFIRMED | SRC-061-002 |
| PRE-061-005 | Navrhovaná registrová značka zodpovedá kategórii lietadla a nie je v konflikte s platným pridelením. | REQUIRED | LAW | CONFIRMED | SRC-061-002 |
| PRE-061-006 | Platné rozhodnutie MUDU-060 o predbežnom pridelení značky je voliteľný vstup; ak bola MUDU-061 podaná v jeho jednoročnej lehote, predbežné pridelenie nestráca platnosť. | CONDITIONAL | LAW | CONFIRMED | SRC-061-001 |
| PRE-061-007 | Údaje lietadla a každého motora potrebné na povinnú SIS kontrolu sú dostupné a kontrola sa dá preukázateľne vykonať. | REQUIRED | LAW | CONFIRMED | SRC-061-001 |
| PRE-061-008 | Správny poplatok je zaplatený pri podaní alebo v lehote po výzve. | REQUIRED | LAW | CONFIRMED | SRC-061-003 |
| PRE-061-009 | Pri elektronickom podaní je žiadateľ identifikovaný a podanie aj žiadateľom vytvorené prílohy sú autorizované v požadovanej forme. | CONDITIONAL | LAW | CONFIRMED | SRC-061-002 |
| PRE-061-010 | Pri portálovej ceste existuje XML podania a technická väzba na spis/záznam a riešiteľa vo Fabasofte; nejde o zákonnú podmienku listinného podania. | CONDITIONAL | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-010 |

## 6. Údaje formulára

| ID | Údaj | Typ | Kardinalita | Zdroj/hodnota | Validácia | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| FLD-061-001 | Vlastník alebo spoluvlastníci | Štruktúrovaná identita | 1..* | Rozsah § 26 ods. 5 písm. a) | Podľa FO, FOP alebo PO; musí zodpovedať dokladu vlastníctva | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| FLD-061-002 | Prevádzkovateľ | Štruktúrovaná identita | 1 | Rozsah § 26 ods. 5 písm. a) | Ak sa líši od vlastníka, vyžaduje DOC-061-002 | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| FLD-061-003 | Telefón a email vlastníka, spoluvlastníkov a prevádzkovateľa | Kontakt | 1..* | § 1 ods. 1 písm. a) | Neprázdny údaj pre každú uvedenú osobu v rozsahu vyhlášky | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-004 | Záložný veriteľ, záložné právo a zabezpečená pohľadávka | Štruktúrované údaje | 0..* | Pri existencii záložného práva | Vyžaduje DOC-061-003; zachovať oddelenie od vlastníka a prevádzkovateľa | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| FLD-061-005 | Návrh registrovej značky | Text alebo referencia | 1 | Značka podľa kategórie lietadla | RULE-061-004 a RULE-061-005; zohľadniť PRE-061-006 | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-006 | Typ lietadla | Číselník alebo text | 1 | Typ lietadla | Neprázdny; určuje formát značky a rozsah súčastí | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-007 | Výrobné číslo lietadla | Text | 1 | Výrobný identifikátor | Neprázdne; kontrola proti existujúcemu registru | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| FLD-061-008 | Rok výroby lietadla | Rok | 1 | Rok výroby | Platný kalendárny rok | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-009 | Maximálna vzletová hmotnosť | Hmotnosť v kg | 1 | MTOW | Kladná hodnota; určuje FEE-061-001 až FEE-061-004 | LAW | CONFIRMED | SRC-061-002, SRC-061-003 |
| FLD-061-010 | Maximálny schválený počet osôb na palube | Celé číslo | 1 | Schválený počet | Nezáporné celé číslo | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-011 | Druh pohonnej jednotky | Číselník alebo text | 1 | Pohonná jednotka lietadla | Konzistentné s typom lietadla | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-012 | Typ a výrobné číslo motora | Opakovateľná štruktúra | 0..* | Každý motor, ak je súčasťou lietadla | Každý motor musí byť samostatne identifikovateľný a zahrnutý do SIS kontroly | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| FLD-061-013 | Typ a výrobné číslo vrtule | Opakovateľná štruktúra | 0..* | Každá vrtuľa, ak je súčasťou lietadla | Samostatná identita súčasti | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| FLD-061-014 | Výrobca lietadla | Text | 1 | Označenie výrobcu | Neprázdne | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-015 | Základné letisko alebo osobitné letisko | Referencia alebo text | 1 | Názov a miestny identifikačný kód, ak bol pridelený | Názov povinný; kód podmienený jeho pridelením | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-016 | Dátum a miesto vyhotovenia žiadosti | Dátum a text | 1 | Žiadateľ | Platný dátum a neprázdne miesto | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-017 | Podpis žiadateľa | Podpis alebo elektronická autorizácia | 1 | Listinný podpis alebo elektronická autorizácia | Podpis je výslovne povinný pri listinnej forme; elektronická forma podľa § 5 ods. 2 | LAW | CONFIRMED | SRC-061-002 |
| FLD-061-018 | Číslo a dátum povolenia ministerstva | Referencia na rozhodnutie | 0..1 | Iba výnimočný zápis | Vyžaduje REQ-061-003 | LAW | CONFIRMED | SRC-061-001 |
| FLD-061-019 | Predchádzajúca značka, model lietadla a skutočné umiestnenie | Zložené údaje | 0..1 | F468 a aktuálny Petriflow | Model je v Petriflow povinný a skutočné umiestnenie nepovinné; presný aktuálny právny alebo prijatý účel nie je úplne zviazaný | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-007, SRC-061-012, SRC-061-013 |
| FLD-061-020 | Údaje verejnej a neverejnej časti registra | Odvodená projekcia | 1 | § 26 ods. 5-8 | Zverejniť iba zákonný verejný rozsah; ostatné údaje nepublikovať | LAW | CONFIRMED | SRC-061-001 |

## 7. Dokumenty a prílohy

| ID | Dokument/príloha | Povinnosť | Forma | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| DOC-061-001 | Doklad preukazujúci vlastnícke právo k lietadlu | REQUIRED | Listinne originál alebo úradne osvedčená kópia; elektronicky podľa § 5 ods. 2 | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-002 | Doklad preukazujúci užívacie právo alebo dohoda o prevádzkovaní | CONDITIONAL | Ako DOC-061-001; iba ak prevádzkovateľ nie je vlastník | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-003 | Zmluva alebo iný doklad o zriadení záložného práva | CONDITIONAL | Ako DOC-061-001; iba pri záložnom práve na lietadle, motore alebo vrtuli | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-004 | Doklad o poistení zodpovednosti za škodu spôsobenú prevádzkou lietadla | REQUIRED | Listinne kópia; elektronicky podľa § 5 ods. 2 | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-005 | Potvrdenie cudzieho orgánu o výmaze z cudzieho registra | CONDITIONAL | Listinne kópia; úradný preklad okrem češtiny alebo angličtiny | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-006 | Potvrdenie cudzieho orgánu, že prvýkrát registrované lietadlo nie je zapísané v cudzom registri | CONDITIONAL | Listinne kópia; úradný preklad okrem češtiny alebo angličtiny | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-007 | Individuálne povolenie na používanie frekvencií pre lietadlovú stanicu | REQUIRED | Listinne originál alebo úradne osvedčená kópia; elektronicky podľa § 5 ods. 2 | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-008 | Exportné osvedčenie o letovej spôsobilosti nie staršie ako 60 dní | CONDITIONAL | Listinne kópia; úradný preklad okrem češtiny alebo angličtiny; iba ak sa na lietadlo nevzťahuje určený rozsah nariadenia EÚ 2018/1139 | LAW | CONFIRMED | SRC-061-002 |
| DOC-061-009 | Plná moc | CONDITIONAL | Forma spôsobilá preukázať zastúpenie | OFFICIAL_PROCEDURE | CONFIRMED | SRC-061-004, SRC-061-006 |
| DOC-061-010 | Colné potvrdenie, vyhlásenie o súkromnom používaní, fotografie štítkov a doklad o zaplatení | CONDITIONAL | Podľa F468 | OFFICIAL_PROCEDURE | CONFLICT | SRC-061-002, SRC-061-007 |
| DOC-061-011 | Osem nakonfigurovaných príloh MUDU pre ID 61 | CONDITIONAL | Elektronicky, poštou alebo osobne podľa konfigurácie | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-002, SRC-061-014 |
| DOC-061-012 | Výpis z obchodného alebo živnostenského registra | NOT_APPLICABLE | Aktuálna stránka DÚ uvádza, že ho netreba prikladať; identita sa však musí preukázať zákonným spôsobom. | OFFICIAL_PROCEDURE | CONFIRMED | SRC-061-006 |

## 8. Poplatky, lehoty a časové pravidlá

| ID | Typ pravidla | Hodnota | Spúšťač/začiatok | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| FEE-061-001 | Správny poplatok | 100 EUR pri MTOW do 2 750 kg vrátane | Podanie žiadosti | LAW | CONFIRMED | SRC-061-003 |
| FEE-061-002 | Správny poplatok | 500 EUR pri MTOW od 2 751 kg do 5 700 kg vrátane | Podanie žiadosti | LAW | CONFIRMED | SRC-061-003 |
| FEE-061-003 | Správny poplatok | 1 000 EUR pri MTOW nad 5 701 kg | Podanie žiadosti | LAW | CONFIRMED | SRC-061-003 |
| FEE-061-004 | Správny poplatok | Presná sadzba pre MTOW 5 701 kg nie je textom položky 92 písm. a) jednoznačne pokrytá; MUDU používa 1 000 EUR od 5 701 kg vrátane. | Podanie žiadosti s MTOW presne 5 701 kg | LAW | CONFLICT | SRC-061-003, SRC-061-013 |
| FEE-061-005 | Elektronické zníženie | 50 % zo sadzby, najviac o 50 EUR; iba ak sú prílohy elektronické | Elektronické podanie spĺňajúce § 6 ods. 2 | LAW | CONFIRMED | SRC-061-003 |
| TIM-061-001 | Splatnosť pevného poplatku | Pri podaní; ak nebol zaplatený, do 15 dní od doručenia písomnej výzvy | Podanie alebo doručenie výzvy | LAW | CONFIRMED | SRC-061-003 |
| TIM-061-002 | Rozhodnutie správneho orgánu | Bezodkladne v jednoduchých veciach, inak do 30 dní; vo zvlášť zložitých prípadoch do 60 dní, ak osobitný predpis neustanoví inak | Úplné a rozhodnuteľné podanie; lehoty neplynú počas zákonného prerušenia | LAW | CONFIRMED | SRC-061-004 |
| TIM-061-003 | Rozklad | 15 dní od oznámenia rozhodnutia, ak osobitný predpis neurčuje inak | Doručenie rozhodnutia | LAW | CONFIRMED | SRC-061-001, SRC-061-004 |
| TIM-061-004 | Platnosť exportného osvedčenia | Najviac 60 dní staré | Deň podania žiadosti | LAW | CONFIRMED | SRC-061-002 |
| TIM-061-005 | Zachovanie predbežnej značky | Predbežné pridelenie nestratí platnosť | Podanie MUDU-061 vlastníkom počas jedného roka od právoplatnosti MUDU-060 | LAW | CONFIRMED | SRC-061-001 |
| TIM-061-006 | Aktuálne správoplatnenie výstupu | Konfigurácia používa režim 15 dní, ale automatická úloha je vypnutá a ukončenie sa vykonáva manuálne | Aktuálne spracovanie výstupu vo Fabasofte a module Backoffice | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-010, SRC-061-015, SRC-061-017 |

## 9. Rozhodovacie pravidlá a invarianty

| ID | Modalita | Pravidlo/invariant | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| RULE-061-001 | MUST | Pred zápisom musí platiť práve jedna z vetiev: bežná spôsobilosť podľa REQ-061-002 alebo doložené povolenie výnimočného zápisu podľa REQ-061-003. | LAW | CONFIRMED | SRC-061-001 |
| RULE-061-002 | MUST_NOT | Zápis sa nevykoná, kým lietadlo zostáva zapísané v cudzom registri alebo patrí do registra podľa § 45b. | LAW | CONFIRMED | SRC-061-001 |
| RULE-061-003 | MUST | SIS kontrola zahŕňa lietadlo a každý motor uvedený v žiadosti; technický stav „odoslaná“ bez integračného dôkazu kontrolu nepreukazuje. | LAW | CONFIRMED | SRC-061-001, SRC-061-016 |
| RULE-061-004 | MUST | Letún, rotorové lietadlo a ornitoptéra používajú registrovú značku z troch veľkých písmen latinskej abecedy. | LAW | CONFIRMED | SRC-061-002 |
| RULE-061-005 | MUST | Klzák, vzducholoď, voľný balón a pripútaný balón používajú štyri arabské číslice s výnimkami podľa § 6 ods. 2. | LAW | CONFIRMED | SRC-061-002 |
| RULE-061-006 | MUST_NOT | Rovnaká aktívna registrová značka ani rovnaká identita lietadla nesmú byť súčasne zapísané ako dve rozdielne aktuálne lietadlá. | PROPOSAL | PROPOSED | SRC-061-009, SRC-061-011 |
| RULE-061-007 | MUST | Zápis údajov o záložnom práve je deklaratórny a nesmie byť interpretovaný ako vznik záložného práva. | LAW | CONFIRMED | SRC-061-001 |
| RULE-061-008 | MUST | Po úspešnom zápise musia zostať vzájomne konzistentné lietadlo, vlastník, prevádzkovateľ, prípadný záložný veriteľ, motory, vrtule, registrová značka, dátum zápisu a vydané osvedčenie. | LAW | CONFIRMED | SRC-061-001 |
| RULE-061-009 | MUST | Do verejnej časti sa projektujú iba údaje povolené § 26 ods. 6; neverejné údaje sa nesmú zverejniť ako súčasť verejného registra. | LAW | CONFIRMED | SRC-061-001 |
| RULE-061-010 | MUST | Ak je preukázaný jednoznačný a nepochybný SIS hit, zápis sa nevykoná a nasleduje bezodkladné oznámenie Policajnému zboru. | LAW | CONFIRMED | SRC-061-001 |
| RULE-061-011 | MUST | Platná predbežná značka MUDU-060 sa pri včas podanej MUDU-061 zachová; MUDU-061 však musí samostatne splniť všetky podmienky zápisu. | LAW | CONFIRMED | SRC-061-001 |
| RULE-061-012 | MUST_NOT | Vytvorenie rozhodnutia, osvedčenia alebo technického registrového záznamu nesmie samo osebe predstierať právoplatnosť, zverejnenie ani úspešný SIS dopyt. | LAW | CONFIRMED | SRC-061-001, SRC-061-004, SRC-061-010 |

## 10. Procesný tok

| ID | Poradie | Stav pred | Činnosť | Aktér | Podmienka | Stav po | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| STEP-061-001 | 1 | Neexistuje konanie | Vlastník alebo jeho zástupca podá žiadosť s údajmi a prílohami. | ACT-061-001 alebo ACT-061-004 | REQ-061-006, REQ-061-010 | Konanie začaté | LAW | CONFIRMED | SRC-061-001, SRC-061-002, SRC-061-004 |
| STEP-061-002 | 2 | Konanie začaté | Dopravný úrad overí oprávnenie žiadateľa, úplnosť podania a formu príloh; odstrániteľné nedostatky rieši podľa správneho poriadku. | ACT-061-006 | PRE-061-003 a PRE-061-004 | Podanie úplné alebo vyžaduje doplnenie | LAW | CONFIRMED | SRC-061-002, SRC-061-004 |
| STEP-061-003 | 3 | Podanie prijaté | Určí sa poplatok podľa MTOW, uplatní sa prípadné elektronické zníženie a overí sa úhrada. | ACT-061-006 | FLD-061-009 | Poplatok splnený alebo čaká na úhradu | LAW | CONFIRMED | SRC-061-003 |
| STEP-061-004 | 4 | Podanie úplné a poplatok splnený | Posúdia sa podmienky vlastníka alebo prevádzkovateľa, zahraničný register, výnimočné povolenie a vylúčenie registra § 45b. | ACT-061-006 | RULE-061-001 a RULE-061-002 | Lietadlo spôsobilé alebo nespôsobilé na zápis | LAW | CONFIRMED | SRC-061-001 |
| STEP-061-005 | 5 | Lietadlo spôsobilé na zápis | Dopravný úrad vykoná a vyhodnotí SIS kontrolu lietadla a každého motora. | ACT-061-006 | PRE-061-007 | SIS bez jednoznačného hitu alebo SIS hit | LAW | CONFIRMED | SRC-061-001 |
| STEP-061-006 | 6 | SIS bez jednoznačného hitu | Dopravný úrad posúdi údaje, prílohy, navrhnutú alebo predbežne pridelenú značku a údaje registra. | ACT-061-006 | REQ-061-010 a RULE-061-004 až RULE-061-011 | Vec pripravená na rozhodnutie | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| STEP-061-007 | 7 | Vec pripravená na rozhodnutie | Dopravný úrad vydá rozhodnutie o zápise alebo negatívne rozhodnutie s náležitosťami správneho rozhodnutia. | ACT-061-006 | Výsledok dokazovania | Rozhodnutie oznámené | LAW | CONFIRMED | SRC-061-001, SRC-061-004 |
| STEP-061-008 | 8 | Rozhodnutie o zápise je právoplatné | Dopravný úrad zapíše zákonné údaje, pridelí značku, vytvorí verejnú a neverejnú projekciu a vydá osvedčenie. | ACT-061-006 | RULE-061-008, RULE-061-009 a RULE-061-012 | Lietadlo zapísané a osvedčenie vydané | LAW | CONFIRMED | SRC-061-001 |
| STEP-061-009 | 9 | Lietadlo zapísané | Dopravný úrad zverejní zákonný rozsah verejnej časti registra. | ACT-061-006 | REQ-061-011 | Verejný register aktualizovaný | LAW | CONFIRMED | SRC-061-001 |
| STEP-061-010 | A1 | Jednoznačný nález v SIS | Dopravný úrad bezodkladne oznámi nález Policajnému zboru a zápis nevykoná. | ACT-061-006 | RULE-061-010 | Nezapísané; oznámené Policajnému zboru | LAW | CONFIRMED | SRC-061-001 |
| STEP-061-011 | A2 | Rozhodnutie oznámené | Oprávnená osoba môže podať rozklad; právoplatnosť a vykonanie sa určia podľa správneho poriadku a osobitného zákona. | ACT-061-001 alebo ACT-061-004 | TIM-061-003 | Rozkladové konanie alebo právoplatné rozhodnutie | LAW | CONFIRMED | SRC-061-001, SRC-061-004 |
| STEP-061-012 | I1 | Elektronická žiadosť odoslaná | Portál vytvorí XML a prílohy, ÚPVS/Fabasoft vytvorí záznam a modul Backoffice ho prevezme s väzbou na spis a riešiteľa. | Systém CRDÚ a Fabasoft | Portálový kanál | Podanie v module Backoffice | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-008, SRC-061-010, SRC-061-012 |
| STEP-061-013 | I2 | Podanie v module Backoffice | Konfigurácia spustí poplatok a lustráciu CLK; dnešná vetva SIS však nemá integračné volanie a nesmie byť použitá ako dôkaz STEP-061-005. | Systém CRDÚ | Pracovný postup ID 61 | Technické podprocesy vytvorené | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-015, SRC-061-016 |
| STEP-061-014 | I3 | Rozhodnutie pripravené | Modul Backoffice vytvorí a odošle výstup do Fabasoftu; registrové záznamy sa správoplatňujú podľa výstupného postupu, pričom automatická 15-dňová úloha je vypnutá. | ACT-061-009 a systém CRDÚ | Konfigurovaný výstup | Manuálne dokončenie alebo prerušenie/zastavenie | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-010, SRC-061-017 |

## 11. Výstupy, právne účinky a koncové stavy

| ID | Typ | Výstup/účinok | Právoplatnosť/platnosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| OUT-061-001 | Rozhodnutie | Rozhodnutie o zápise lietadla do registra lietadiel. | Účinok podľa právoplatnosti rozhodnutia a vykonania zápisu; obyčajné vytvorenie dokumentu nestačí | LAW | CONFIRMED | SRC-061-001, SRC-061-004 |
| OUT-061-002 | Register mutation | Zápis údajov podľa § 26 ods. 5 a vznik štátnej príslušnosti SR. | Po účinnom zápise | LAW | CONFIRMED | SRC-061-001 |
| OUT-061-003 | Registrová značka | Pridelenie registrovej značky, ktorá sa vyznačí za značkou štátnej príslušnosti. | Súčasť účinného zápisu | LAW | CONFIRMED | SRC-061-001, SRC-061-002 |
| OUT-061-004 | Osvedčenie | Osvedčenie o zápise lietadla do registra lietadiel. | Vydané Dopravným úradom k zápisu | LAW | CONFIRMED | SRC-061-001 |
| OUT-061-005 | Verejná publikácia | Zverejnenie verejnej časti údajov podľa § 26 ods. 6. | Po účinnom zápise; iba zákonný rozsah | LAW | CONFIRMED | SRC-061-001 |
| OUT-061-006 | Záložné údaje | Zápis údajov o záložnom práve, veriteľovi a pohľadávke. | Deklaratórny; nevytvára záložné právo | LAW | CONFIRMED | SRC-061-001 |
| OUT-061-007 | List právoplatnosti | Konfigurovaný list právoplatnosti zápisu. | Bez vlastného typu správoplatnenia v konfigurácii | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-017, SRC-061-020 |
| OUT-061-008 | Nálepky | Konfigurovaná šablóna nálepiek s registračnými údajmi. | Technický výstup; právny účinok nepreukázaný | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-017, SRC-061-023 |
| OUT-061-009 | Prerušenie | Rozhodnutie o prerušení konania bez zápisu lietadla. | Lehoty počas zákonného prerušenia neplynú | LAW | CONFIRMED | SRC-061-004 |
| OUT-061-010 | Zastavenie | Rozhodnutie o zastavení konania bez zápisu lietadla. | Podľa dôvodu a správneho poriadku alebo zákona o poplatkoch | LAW | CONFIRMED | SRC-061-003, SRC-061-004 |
| OUT-061-011 | Negatívny výsledok | Lietadlo zostáva nezapísané pri nesplnení podmienok alebo SIS hite. | Bez vzniku štátnej príslušnosti a bez osvedčenia | LAW | CONFIRMED | SRC-061-001 |
| OUT-061-012 | Zakázaný účinok | Zápis nevydáva osvedčenie letovej spôsobilosti ani neprideľuje kód módu S alebo ELT. | N/A | LAW | CONFIRMED | SRC-061-001, SRC-061-008 |

## 12. Integrácie a notifikácie

| ID | Typ | Systém/príjemca | Účel/obsah | Kritickosť | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- |
| INT-061-001 | INTEGRATION | Portál DÚ a ÚPVS | Elektronické vyplnenie, autorizácia, odoslanie XML a príloh. | HIGH | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-008, SRC-061-010, SRC-061-012 |
| INT-061-002 | INTEGRATION | Fabasoft a integračná platforma | Registratúrny záznam, spis, riešiteľ, dokumenty podania a spracovanie výstupov. | HIGH | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-010 |
| INT-061-003 | INTEGRATION | Platobný modul a centrálny systém poplatkov | Predpis, úhrada a stav správneho poplatku. | HIGH | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-003, SRC-061-013, SRC-061-015 |
| INT-061-004 | INTEGRATION | Schengenský informačný systém cez CLK | Povinná kontrola lietadla a motorov pred zápisom. | CRITICAL | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-001, SRC-061-016 |
| NOT-061-001 | NOTIFICATION | Policajný zbor | Bezodkladné oznámenie jednoznačného a nepochybného SIS hitu. | CRITICAL | LAW | CONFIRMED | SRC-061-001 |
| INT-061-005 | INTEGRATION | Register lietadiel v module Backoffice a verejný portál | Uloženie aktuálneho záznamu a zverejnenie iba verejnej projekcie. | CRITICAL | CURRENT_IMPLEMENTATION | UNKNOWN | SRC-061-001, SRC-061-009, SRC-061-010 |
| INT-061-006 | INTEGRATION | Generovanie dokumentov | Rozhodnutie, osvedčenie, list právoplatnosti, nálepky, prerušenie a zastavenie. | HIGH | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-017 až SRC-061-023 |
| NOT-061-002 | NOTIFICATION | Žiadateľ | Výzva na doplnenie, výzva na úhradu, oznámenie rozhodnutia a doručenie osvedčenia. | HIGH | OFFICIAL_PROCEDURE | UNKNOWN | SRC-061-003, SRC-061-004, SRC-061-010 |
| NOT-061-003 | NOTIFICATION | Ministerstvo dopravy SR | Overenie alebo použitie povolenia výnimočného zápisu; technický integračný mechanizmus nie je doložený. | MEDIUM | LAW | UNKNOWN | SRC-061-001 |

## 13. Alternatívne, chybové a opravné scenáre

| ID | Spúšťač | Očakávané správanie | Koncový stav | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| ALT-061-001 | Podanie nemá predpísané náležitosti alebo trpí odstrániteľnými nedostatkami. | Úrad pomôže nedostatky odstrániť alebo vyzve na doplnenie; podľa okolností konanie preruší a pri neodstránení postupuje podľa správneho poriadku. | Doplnené, prerušené alebo zastavené | LAW | CONFIRMED | SRC-061-004 |
| ALT-061-002 | Poplatok nebol zaplatený pri podaní. | Úrad doručí výzvu; ak poplatok nie je zaplatený do 15 dní, úkon nevykoná a konanie zastaví bez možnosti odvolania proti tomuto zastaveniu. | Zastavené pre nezaplatenie | LAW | CONFIRMED | SRC-061-003 |
| ALT-061-003 | Vlastník ani prevádzkovateľ nespĺňa § 25 ods. 3 a chýba povolenie ministerstva. | Zápis sa nevykoná. | Nezapísané | LAW | CONFIRMED | SRC-061-001 |
| ALT-061-004 | Lietadlo je stále zapísané v cudzom registri alebo patrí do registra podľa § 45b. | Zápis sa nevykoná. | Nezapísané | LAW | CONFIRMED | SRC-061-001 |
| ALT-061-005 | SIS kontrola jednoznačne a nepochybne potvrdí pátranie po lietadle alebo motore. | Zápis sa nevykoná a Policajný zbor sa bezodkladne informuje. | Nezapísané a oznámené PZ | LAW | CONFIRMED | SRC-061-001 |
| ALT-061-006 | SIS/CLK nie je dostupné alebo nie je preukázané reálne odoslanie a odpoveď. | Zápis sa nesmie vykonať, kým nebude zákonná kontrola preukázateľne dokončená; opakovanie, eskalácia a používateľský stav vyžadujú prijatý návrh. | Blokované pred zápisom | LAW | CONFIRMED | SRC-061-001, SRC-061-016 |
| ALT-061-007 | Chýba podmienene povinné potvrdenie z cudzieho registra, prevádzkové oprávnenie, záložný doklad alebo exportné osvedčenie. | Úrad vyzve na presne príslušný dokument; nesmie automaticky požadovať navzájom sa vylučujúce zahraničné potvrdenia. | Čaká na doplnenie alebo nezapísané | LAW | CONFIRMED | SRC-061-002, SRC-061-004 |
| ALT-061-008 | MTOW je presne 5 701 kg. | Systém ani referent nesmú konflikt sadzobníka a implementácie skryť; potrebné je autoritatívne určenie sadzby. | Konflikt poplatku pred rozhodnutím | LAW | CONFLICT | SRC-061-003, SRC-061-013 |
| ALT-061-009 | Navrhovaná značka je neprípustná alebo už aktívne použitá. | Úrad vyžiada prípustnú značku alebo rozhodne bez vytvorenia duplicitného aktuálneho pridelenia. | Čaká na opravu alebo nezapísané | PROPOSAL | PROPOSED | SRC-061-002, SRC-061-009 |
| ALT-061-010 | Podaný rozklad v lehote. | Vec sa nesmie prezentovať ako nezvratne právoplatne ukončená; postupuje sa podľa § 55 ods. 3 leteckého zákona a správneho poriadku. | Rozkladové konanie | LAW | CONFIRMED | SRC-061-001, SRC-061-004 |
| ALT-061-011 | Prerušenie alebo zastavenie sa generuje aktuálnou všeobecnou šablónou. | Šablóna nesmie uvádzať, že predmetom MUDU-061 je iba predbežné pridelenie značky; výstup treba odmietnuť alebo opraviť pred použitím. | Výstup blokovaný ako vecne nesprávny | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-021, SRC-061-022 |
| ALT-061-012 | Súbežné žiadosti sa týkajú rovnakého lietadla alebo značky. | Potrebné je atómovo zabrániť dvom aktuálnym zápisom a zachovať auditnú stopu rozhodnutia. | Jeden konzistentný výsledok alebo explicitný konflikt | PROPOSAL | PROPOSED | SRC-061-009, SRC-061-011 |

## 14. Väzby na iné procesy a dopad zmien

| ID | Smer | Proces/artefakt | Typ väzby | Dopad | Vrstva | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DEP-061-001 | IN | MUDU-060 | PREDECESSOR | Ak existuje platné predbežné pridelenie, MUDU-061 ho spotrebuje ako vstup a včasným podaním zachová jeho platnosť; MUDU-060 nie je povinný pre každý zápis. | LAW | CONFIRMED | SRC-061-001 |
| DEP-061-002 | OUT | MUDU-062 | SUCCESSOR | Všetky neskoršie zmeny zapísaných údajov zostávajú samostatným procesom; zmena schémy alebo účinku zápisu sa musí skontrolovať proti MUDU-062. | LAW | CONFIRMED | SRC-061-001, SRC-061-002, SRC-061-008 |
| DEP-061-003 | OUT | MUDU-063 | SUCCESSOR | Výmaz ukončuje registráciu a vyžaduje samostatné podmienky a výstupy; MUDU-061 ho neobsahuje. | LAW | CONFIRMED | SRC-061-001, SRC-061-002, SRC-061-008 |
| DEP-061-004 | OUT | MUDU-091 | OUT_OF_SCOPE | Mód S alebo ELT je samostatná služba so zdieľaným lietadlom a značkou; úspech MUDU-061 nie je dôkazom pridelenia kódu. | OBSERVATION | CONFIRMED | SRC-061-008, SRC-061-025 |
| DEP-061-005 | BOTH | EA Vehicle 9482 a Aircraft 9923 | SHARED_ENTITY | Zmenu identity, technických údajov, registrového stavu alebo dátumov treba preveriť proti MUDU-051 až MUDU-063, MUDU-065, MUDU-066 a MUDU-091 podľa konkrétneho atribútu. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-011, SRC-061-025 |
| DEP-061-006 | BOTH | EA `Engine` 9925 a `Propeller` 9929 | SHARED_ENTITY | Zmeny identity súčastí ovplyvňujú registračné, zmenové, výmazové, technické a SIS väzby; v MUDU-061 sú v rozsahu iba registračné, záložné a SIS účinky. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-011, SRC-061-025 |
| DEP-061-007 | BOTH | EA Owner 13387, Operator 13406 a Lien 16820 | SHARED_ENTITY | Role sa nesmú zlúčiť; rovnaké entity zdieľajú MUDU-060/061/062/063, ale oprávnenia sú procesovo rozdielne. | CURRENT_IMPLEMENTATION | CONFIRMED | SRC-061-001, SRC-061-011, SRC-061-025 |
| DEP-061-008 | BOTH | EA RegistrationMark 20919 a RegistrationMarkInTime 20926 | SHARED_ENTITY | Značka spája predbežné pridelenie, zápis, zmenu a výmaz; verzovanie musí zachovať časový životný cyklus a zabrániť súbežnému aktívnemu použitiu. | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-011, SRC-061-025 |
| DEP-061-009 | BOTH | CLK/SIS | SHARED_INTEGRATION | Rovnaká zákonná kontrola patrí MUDU-061 a MUDU-062; MUDU-060 ju zákon nevyžaduje a MUDU-063 ju nemá nakonfigurovanú. | LAW | CONFIRMED | SRC-061-001, SRC-061-016 |
| DEP-061-010 | IN | MUDU-070 a MUDU-075 | OUT_OF_SCOPE | Grafové odkazy iba používajú kontext registrovaného lietadla; nevytvárajú podmienku ani vstup MUDU-061. | OBSERVATION | CONFIRMED | SRC-061-025 |
| DEP-061-011 | BOTH | Šesť výstupov ID 61 | SHARED_OUTPUT | Rozhodnutie, osvedčenie, list, nálepky, prerušenie a zastavenie musia byť zviazané s rovnakou definíciou a nesmú používať text MUDU-060. | CURRENT_IMPLEMENTATION | CONFLICT | SRC-061-017 až SRC-061-023 |

## 15. Akceptačné scenáre

| ID | Given | When | Then | Pokrýva | Stav |
| --- | --- | --- | --- | --- | --- |
| AC-061-001 | Vlastník je slovenská oprávnená osoba, lietadlo nie je v cudzom registri, podanie je úplné, poplatok zaplatený a SIS je bez hitu. | Úrad dokončí konanie. | Vznikne jeden konzistentný zápis, pridelená značka, osvedčenie a zákonná verejná projekcia. | REQ-061-001 až REQ-061-012, OUT-061-001 až OUT-061-005 | DRAFT |
| AC-061-002 | Vlastník nespĺňa slovenské podmienky, ale prevádzkovateľ ich spĺňa a jeho právny titul je doložený. | Úrad posúdi § 25 ods. 3 písm. b). | Žiadosť sa neodmietne iba pre zahraničný status vlastníka. | REQ-061-002, ACT-061-003, DOC-061-002 | DRAFT |
| AC-061-003 | Vlastník ani prevádzkovateľ nespĺňa bežné podmienky. | Žiadateľ doloží povolenie ministerstva. | Zápis pokračuje iba ako výnimočný a číslo/dátum povolenia sa zapíšu. | REQ-061-003, FLD-061-018, RULE-061-001 | DRAFT |
| AC-061-004 | Lietadlo je stále zapísané v cudzom registri. | Žiadateľ požiada o zápis. | Zápis sa nevykoná, kým nie je splnená zákonná podmienka. | REQ-061-004, ALT-061-004 | DRAFT |
| AC-061-005 | Lietadlo alebo motor má jednoznačný a nepochybný SIS hit. | Úrad vyhodnotí kontrolu. | Zápis sa nevykoná a Policajný zbor je bezodkladne informovaný. | REQ-061-008, REQ-061-009, ALT-061-005, NOT-061-001 | DRAFT |
| AC-061-006 | CLK vetva iba nastaví technický stav odoslania bez volania a odpovede. | Systém sa pokúsi ukončiť zápis. | Ukončenie je zablokované, pretože zákonná kontrola nie je preukázaná. | RULE-061-003, ALT-061-006, INT-061-004 | DRAFT |
| AC-061-007 | Lietadlo má platné predbežné pridelenie MUDU-060 a MUDU-061 bola podaná v jednoročnej lehote. | Prebieha zápis. | Predbežné pridelenie zostane platné a značka sa spracuje bez tvrdenia, že MUDU-060 už vykonal zápis. | TIM-061-005, RULE-061-011, DEP-061-001 | DRAFT |
| AC-061-008 | Prevádzkovateľ nie je vlastník alebo existuje záložné právo. | Žiadosť sa validuje. | Vyžadujú sa iba príslušné podmienené doklady a role zostanú oddelené. | DOC-061-002, DOC-061-003, RULE-061-007 | DRAFT |
| AC-061-009 | MTOW je 2 750 kg, 2 751 kg alebo 5 700 kg. | Vypočíta sa poplatok. | Výsledok je postupne 100 EUR, 500 EUR a 500 EUR pred prípadným elektronickým znížením. | FEE-061-001, FEE-061-002, FEE-061-005 | DRAFT |
| AC-061-010 | MTOW je presne 5 701 kg. | Vypočíta sa poplatok. | Systém vystaví explicitný konflikt právneho textu a implementačnej hranice, nie tichú sadzbu. | FEE-061-004, ALT-061-008 | DRAFT |
| AC-061-011 | Žiadosť je elektronická, ale niektorá príloha nie je v elektronickej podobe. | Uplatňuje sa zníženie poplatku. | Znížená sadzba sa neuplatní iba na základe elektronického formulára. | FEE-061-005, PRE-061-009 | DRAFT |
| AC-061-012 | Úspešné rozhodnutie je vygenerované, ale nebola preukázaná právoplatnosť. | Systém vytvorí register alebo osvedčenie. | Výstupy sa nesmú prezentovať ako účinný zápis iba na základe času vytvorenia dokumentu. | RULE-061-012, STEP-061-008, OUT-061-001 | DRAFT |
| AC-061-013 | Pre MUDU-061 sa vyberie aktuálna šablóna prerušenia alebo zastavenia. | Dokument sa pred odoslaním validuje. | Text o predbežnom pridelení podľa § 26 ods. 4 je označený ako vecne nesprávny a dokument sa neodošle bez opravy. | ALT-061-011, DEP-061-011 | DRAFT |
| AC-061-014 | Dve súbežné podania požadujú tú istú značku alebo identitu lietadla. | Obe sa pokúsia dokončiť zápis. | Vznikne najviac jeden aktuálny zápis; druhé podanie má výslovný konflikt a auditnú stopu. | RULE-061-006, ALT-061-012 | DRAFT |
| AC-061-015 | Po zápise sa zmenia údaje alebo sa žiada výmaz či Mode S/ELT. | Používateľ pokračuje. | Použije samostatne MUDU-062, MUDU-063 alebo MUDU-091; MUDU-061 sa nerecykluje ako rodinný proces. | SCP-061-006, SCP-061-008, DEP-061-002 až DEP-061-004 | DRAFT |

## 16. Mapovanie na EA, Petriflow a kód

| ID | Vrstva implementácie | Artefakt | Presná väzba | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- |
| MAP-061-001 | Katalóg | `katalog_sluzieb.csv`, ID 61 | `portal_aircraft_new_aircraft_complete_form`, XML `vehicle`, elektronická aktívna služba, účel zápisu do registra. | CONFIRMED | SRC-061-008 |
| MAP-061-002 | Petriflow | `vehicle.xml` | Prechod `portal_aircraft_new_aircraft_complete_form`; kompozícia `Vehicle` na `Aircraft` časti 1 a 2, `Owner`, `Operator`, `Lien` a `RegistrationMark`. | CONFIRMED | SRC-061-012, SRC-061-009 |
| MAP-061-003 | Petriflow | `aircraft.xml` časť 1 | Povinné typ, model, rok, výrobca, výrobné číslo, MTOW, počet osôb a základné letisko; predchádzajúca značka a skutočné umiestnenie majú odlišnú povinnosť. | CONFLICT | SRC-061-013 |
| MAP-061-004 | Petriflow | `aircraft.xml` časť 2 | Opakovateľné motory a vrtule a ich údaje; presná kompozícia na `engine.xml` a `propeller.xml`. | CONFIRMED | SRC-061-013, SRC-061-009 |
| MAP-061-005 | Petriflow/Groovy a poplatková konfigurácia | Výpočet poplatku podľa MTOW a `portal_spravne_poplatky.csv` | `aircraft.xml` používa kód 3034 pri MTOW do 2 750 kg, 3035 pri 2 751 až 5 700 kg a 3036 od 5 701 kg; CSV však viaže ID 61 na kódy 3034, 200 a 3036. | CONFLICT | SRC-061-003, SRC-061-013, SRC-061-026 |
| MAP-061-006 | Konfigurácia | `katalog_workflow.csv`, ID 61 | Pracovný postup `Poplatok + Lustrácie`. | CONFIRMED | SRC-061-015 |
| MAP-061-007 | Konfigurácia | `lustracie_a_sluzby.csv`, ID 61 | Lustrácia `ANO`, CLK `X`. | CONFIRMED | SRC-061-016 |
| MAP-061-008 | Konfigurácia | `prilohy_formularov.csv`, ID 61 | Osem riadkov príloh; vlastníctvo, frekvencie a poistenie sú označené ako povinné, ostatné ako nepovinné bez úplnej podmienkovej logiky vyhlášky. | CONFLICT | SRC-061-014 |
| MAP-061-009 | EA | Vehicle 9482 a Aircraft 9923 | Vehicle drží registračné dátumy, značku, číslo, záložné právo a dočasnú značku; Aircraft drží technické a vzťahové údaje. | CONFIRMED | SRC-061-011 |
| MAP-061-010 | EA | `Engine` 9925, `Propeller` 9929, `RegistrationMark` 20919 a `RegistrationMarkInTime` 20926 | Súčasti a časový životný cyklus značky zdieľajú MUDU-060/061/062/063 a ďalšie technické služby. | CONFLICT | SRC-061-011, SRC-061-025 |
| MAP-061-011 | EA | Owner 13387, Operator 13406 a Lien 16820 | Samostatné role a vzťahy k lietadlu; ich zlúčenie by porušilo § 25 a § 26. | CONFIRMED | SRC-061-001, SRC-061-011 |
| MAP-061-012 | EA/CLK | AircraftEngineResult 40113 | Výsledkový model kontroly motora; existencia modelu nie je dôkazom vykonanej kontroly. | CONFLICT | SRC-061-011, SRC-061-016 |
| MAP-061-013 | Výstupná konfigurácia | `word_templates.json`, ID 61 | Šesť výstupov: rozhodnutie, osvedčenie, list právoplatnosti, nálepky, prerušenie a zastavenie. | CONFIRMED | SRC-061-017 |
| MAP-061-014 | Výstupná šablóna | Rozhodnutie_Zapis_do_RL.docx | Vecne opisuje zápis a osvedčenie po právoplatnosti, ale obsahuje vzorový poplatok 100 EUR a dátum 03.12.2024. | CONFLICT | SRC-061-018 |
| MAP-061-015 | Výstupná šablóna | Osvedcenie_o_zapise_do_RLSR.docx | Osvedčenie o zápise s registračnými údajmi. | CONFIRMED | SRC-061-019 |
| MAP-061-016 | Výstupná šablóna | List_pravoplatnost_zapis_do_RL.docx | List právoplatnosti zápisu. | CONFIRMED | SRC-061-020 |
| MAP-061-017 | Výstupná šablóna | `Prerusenie_konania_DCL.docx` | Konfigurovaná pre ID 61, ale text označuje konanie o pridelenie značky podľa § 26 ods. 4. | CONFLICT | SRC-061-021 |
| MAP-061-018 | Výstupná šablóna | `Zastavenie_konania_DCL.docx` | Konfigurovaná pre ID 61, ale text označuje zastavenie konania o pridelenie značky. | CONFLICT | SRC-061-022 |
| MAP-061-019 | Výstupná šablóna | Nalepky.docx | Technická šablóna nálepiek; normatívny účel nebol samostatne potvrdený. | UNKNOWN | SRC-061-023 |
| MAP-061-020 | Integrácia | Tok podania a výstupov podľa dokumentu o odovzdaní znalostí | Elektronické a fyzické podanie cez Fabasoft, prílohy, `caseRef`, `taskRef`, výstupy a manuálne správoplatnenie pri vypnutej 15-dňovej úlohe. | CONFIRMED | SRC-061-010 |
| MAP-061-021 | Starší register | Schéma MDB | Schéma rozlišuje pridelenie, zápis, zmenu a výmaz; tento návrh nepreukazuje úplnosť ani aktuálnosť riadkov historickej databázy. | UNKNOWN | SRC-061-009, SRC-061-024 |
| MAP-061-022 | SharePoint | Vzor žiadosti, rozhodnutia, osvedčenia, listu právoplatnosti a rozšírenia registra | Historický projektový kontext použitý na porovnanie, nie na prebitie aktuálneho zákona a vyhlášky. | CONFIRMED | SRC-061-024 |

## 17. Medzery, konflikty a otvorené rozhodnutia

| ID | Typ | Otázka/konflikt | Potrebné rozhodnutie | Vlastník | Stav | Zdroje |
| --- | --- | --- | --- | --- | --- | --- |
| GAP-061-001 | SOURCE_CONFLICT | Aktuálne prepojený F468 z roku 2023 a prílohová konfigurácia MUDU nezodpovedajú presne rozsahu a podmienkam vyhlášky č. 274/2024 Z. z. | Prijať jednu aktuálnu maticu údajov, príloh, podmienok, formy a prekladov; zosúladiť formulár aj konfiguráciu. | Vecný gestor + legislatíva | CONFLICT | SRC-061-002, SRC-061-007, SRC-061-014 |
| GAP-061-002 | SOURCE_CONFLICT | Stránka DÚ odkazuje na vyhlášku č. 274/2004, hoci platná vyhláška je č. 274/2024 Z. z. | Opraviť oficiálnu stránku a potvrdiť aktuálny zdroj. | Dopravný úrad | CONFLICT | SRC-061-002, SRC-061-005 |
| GAP-061-003 | SOURCE_CONFLICT | Formulárová stránka DÚ zjednodušene vyžaduje originály alebo overené kópie okrem dvoch potvrdení, kým § 5 vyhlášky rozlišuje viac kategórií a elektronickú konverziu. | Zosúladiť verejnú inštrukciu s § 5 a odstrániť nejednoznačnosť. | Dopravný úrad + legislatíva | CONFLICT | SRC-061-002, SRC-061-006 |
| GAP-061-004 | SOURCE_CONFLICT | Položka 92 písm. a) uvádza 1 000 EUR pri MTOW nad 5 701 kg, takže presných 5 701 kg nie je textovo pokrytých; kód používa hranicu od 5 701 kg. | Autoritatívne určiť sadzbu presne pre 5 701 kg a následne zjednotiť zákonnú interpretáciu, konfiguráciu a testy. | Legislatíva + vecný gestor | CONFLICT | SRC-061-003, SRC-061-013 |
| GAP-061-005 | IMPLEMENTATION_GAP | Vetva CLK/SIS nemá integračné volanie, ale spoločný koniec nastaví čas a stav odoslania. | Realizovať preukázateľnú kontrolu lietadla a každého motora, výsledok, vetvu pre nález a oznámenie Policajnému zboru; falošný stav odoslania nesmie odomknúť zápis. | Netgrif + vecný gestor | CONFLICT | SRC-061-001, SRC-061-016 |
| GAP-061-006 | IMPLEMENTATION_GAP | Šablóny prerušenia a zastavenia ID 61 opisujú MUDU-060 a § 26 ods. 4. | Vytvoriť a zviazať procesovo správne šablóny MUDU-061; pridať obsahovú kontrolu. | Netgrif + vecný gestor | CONFLICT | SRC-061-021, SRC-061-022 |
| GAP-061-007 | IMPLEMENTATION_GAP | Rozhodnutie o zápise obsahuje vzorový dátum a príklad poplatku 100 EUR, ktorý nezodpovedá všetkým hmotnostným pásmam. | Odstrániť konštanty a viazať dátum aj poplatok na overené údaje konkrétneho podania. | Netgrif | CONFLICT | SRC-061-018 |
| GAP-061-008 | IMPLEMENTATION_GAP | Automatická 15-dňová úloha je vypnutá a manuálne dokončenie nie je v definícii zviazané s doručením, rozkladom a skutočnou právoplatnosťou. | Definovať a implementovať stavový automat právoplatnosti s dôkazom doručenia a opravného prostriedku. | Vecný gestor + Netgrif | CONFLICT | SRC-061-004, SRC-061-010, SRC-061-015 |
| GAP-061-009 | IMPLEMENTATION_GAP | Dočasná značka je v EA zachytená ako Vehicle flag a starší model ju klonoval pri Aircraft; nie je dokázaná jedna autoritatívna časová reprezentácia. | Prijať model predbežnej značky, jej rezervácie, prechodu do zápisu, expirácie a súbehu MUDU-060/061. | Vecný gestor + Netgrif | CONFLICT | SRC-061-011, SRC-061-025 |
| GAP-061-010 | INTENT_QUESTION | Presné interné roly referenta, schvaľovateľa, podpisujúcej osoby, notifikácie a lehoty na doplnenie nie sú zviazané s prijatým postupom. | Doplniť alebo prijať oprávnenia bez preberania rolí iba z aktuálneho technického postupu. | Vecný gestor | UNKNOWN | SRC-061-004, SRC-061-009, SRC-061-010 |
| GAP-061-011 | IMPLEMENTATION_GAP | Atómová jedinečnosť lietadla a registrovej značky proti súbežným podaniam nebola preukázaná. | Definovať kľúče identity, okamih rezervácie alebo zápisu, riešenie konfliktu, návrat transakcie a auditnú stopu. | Vecný gestor + Netgrif | UNKNOWN | SRC-061-009, SRC-061-011 |
| GAP-061-012 | EVIDENCE_GAP | Nebol vykonaný aktuálny úplný beh portál → Fabasoft/FBB → Backoffice → SIS → rozhodnutie → právoplatnosť → register → osvedčenie → verejná projekcia. | Po prijatí definície vytvoriť testovacie vstupy, náhrady tretích strán, formálne invarianty a dôkazy Playwright/API/dáta pre presne túto verziu. | Netgrif + analytik | UNKNOWN | SRC-061-009, SRC-061-010 |
| GAP-061-013 | IMPLEMENTATION_GAP | `aircraft.xml` vyberá pre stredné pásmo MTOW kód PEP 3035, ale `portal_spravne_poplatky.csv` viaže ID 61 na kód 200. | Oprávnená osoba musí určiť správny kód a zosúladiť XML, CSV, PEP a testy bez tichej náhrady. | Netgrif + prevádzkovateľ PEP | CONFLICT | SRC-061-013, SRC-061-026 |
| Q-061-001 | INTENT_QUESTION | Je model lietadla a skutočné umiestnenie povinným alebo voliteľným biznis údajom nad rámec vyhlášky, alebo iba technickou položkou? | Prijať význam, kardinalitu, verejnosť a validačné pravidlo, alebo údaje odstrániť. | Vecný gestor | UNKNOWN | SRC-061-002, SRC-061-007, SRC-061-013 |
| Q-061-002 | INTENT_QUESTION | Aký presný právny/prevádzkový účel majú nálepky a kedy sa vydávajú? | Zviazať ich s prijatým účelom a výstupovým stavom alebo ich vyradiť. | Vecný gestor | UNKNOWN | SRC-061-017, SRC-061-023 |
| Q-061-003 | EVIDENCE_GAP | Vyriešené vo verzii 0.1.2: MUDU-063 je manuálne definované a kontrola štyroch procesov potvrdila oddelenie zápisu, zmeny a výmazu, hranicu výmazu bez SIS, zachovanie histórie a spoločné časové medzery. | Bez ďalšieho rozhodnutia; kontrolu obnoviť pri zmene ktoréhokoľvek MUDU-060 až MUDU-063. | Sémantický autor | CONFIRMED | SRC-061-027 |

## 18. Schválenie a história zmien

| Verzia | Dátum | Zmena | Autorita | Stav |
| --- | --- | --- | --- | --- |
| 0.1.0 | 2026-09-01 | Prvý manuálny zdrojovo uzavretý návrh MUDU-061; oddelené právo, oficiálny postup, historické projektové zdroje, EA, Petriflow, konfigurácia, výstupy a explicitné konflikty; skontrolovaná hranica MUDU-060/062/063/091. | UNCONFIRMED | DRAFT |
| 0.1.1 | 2026-09-01 | Krížová kontrola pri MUDU-062 odhalila rozpor medzi kódom PEP 3035 a kódom CSV 200 a uzavrela vzájomnú hranicu MUDU-061/062; MUDU-063 ešte nebolo spracované. | UNCONFIRMED | DRAFT |
| 0.1.2 | 2026-09-01 | Kontrola štyroch procesov vytvorila prvý vzájomne konzistentný stav: MUDU-061 vytvára aktuálny zápis, MUDU-062 ho mení a MUDU-063 ho právoplatne ukončuje pri zachovaní histórie; otvorené implementačné konflikty zostávajú výslovné. | UNCONFIRMED | DRAFT |
| 0.1.3 | 2026-09-01 | Doplnený ľudský rýchly prehľad a jazykové spresnenia bez zmeny vecných pravidiel procesu. | UNCONFIRMED | DRAFT |

## 19. Register zdrojov

| ID | Typ | Názov/verzia | Lokátor | Ustanovenie/rozsah | Účinnosť/pozorovanie |
| --- | --- | --- | --- | --- | --- |
| SRC-061-001 | LAW | Zákon č. 143/1998 Z. z., časová verzia | https://static.slov-lex.sk/pdf/SK/ZZ/1998/143/ZZ_1998_143_20260101.pdf | § 25; § 26 ods. 1-15; § 55 | účinné od 2026-01-01 |
| SRC-061-002 | LAW | Vyhláška č. 274/2024 Z. z. | https://static.slov-lex.sk/static/SK/ZZ/2024/274/20241115.html | § 1; § 5-7; úplný text § 1-8 | účinné od 2024-11-15; zachytené 2026-08-31 |
| SRC-061-003 | LAW | Zákon č. 145/1995 Z. z., časová verzia | https://static.slov-lex.sk/static/SK/ZZ/1995/145/20260901.html | § 6 ods. 2; § 8 až 9; sadzobník, položka 92 písm. a) | účinné od 2026-09-01; text HTML zachytený 2026-09-01 |
| SRC-061-004 | LAW | Zákon č. 71/1967 Zb., časová verzia | https://static.slov-lex.sk/pdf/SK/ZZ/1967/71/ZZ_1967_71_20180901.pdf | § 16-19; § 27-30; § 46-49; § 54-61 | účinné od 2018-09-01; história skontrolovaná 2026-08-31 |
| SRC-061-005 | OFFICIAL_PROCEDURE | DÚ — Register lietadiel SR | https://letectvo.nsat.sk/letova-sposobilost/register-lietadiel-slovenskej-republiky/ | verejný opis registra a podmienok | pozorované 2026-08-31 |
| SRC-061-006 | OFFICIAL_PROCEDURE | DÚ — Formuláre registra lietadiel | https://letectvo.nsat.sk/letova-sposobilost/register-lietadiel-slovenskej-republiky/formulare/ | žiadateľ, zástupca a pravidlá príloh | pozorované 2026-08-31 |
| SRC-061-007 | OFFICIAL_FORM | DÚ F468-B/v1/OSL | https://letectvo.nsat.sk/wp-content/uploads/sites/2/2023/03/F468_B_v1_Z%C3%81PIS-LIETADLA-DO-RL_FINAL.pdf | všetkých 8 strán | aktuálne prepojené DÚ; dokument z 2023; pozorované 2026-08-31 |
| SRC-061-008 | CONFIGURATION | Katalóg služieb IS CRDÚ | nezverejnené v tomto repozitári | riadok ID 61 a susedné ID 60/62/63/91 | zachytená lokálna revízia |
| SRC-061-009 | CONFIGURATION | Kontext registra lietadiel v EA a kóde v2 | nezverejnené v tomto repozitári | ID 60 až 63, EA, CSV, XML, SharePoint, výstupy a CLK | zachytené 2026-08-31 |
| SRC-061-010 | KNOWLEDGE_TRANSFER | Odovzdanie znalostí MUDU | nezverejnené v tomto repozitári | elektronické a fyzické podania, Fabasoft, kompozícia, prílohy, výstupy, správoplatnenie a CLK | lokálny zdroj prečítaný 2026-09-01 |
| SRC-061-011 | EA | Objekty, atribúty a vzťahy EA pre MUDU-061 | nezverejnené v tomto repozitári | 14 objektov, 108 atribútov, 13 vzťahov | offline snímka 2026-08-20; výber 2026-09-01 |
| SRC-061-012 | PETRIFLOW | `vehicle.xml` | nezverejnené v tomto repozitári | prechod `portal_aircraft_new_aircraft_complete_form` a kompozícia | zachytená lokálna revízia |
| SRC-061-013 | PETRIFLOW | `aircraft.xml` | nezverejnené v tomto repozitári | prechody častí 1 a 2; polia a poplatkové akcie 3034 až 3036 | zachytená lokálna revízia |
| SRC-061-014 | CONFIGURATION | `prilohy_formularov.csv` | nezverejnené v tomto repozitári | osem riadkov ID 61 | zachytená lokálna revízia |
| SRC-061-015 | CONFIGURATION | `katalog_workflow.csv` | nezverejnené v tomto repozitári | riadok ID 61, `Poplatok + Lustrácie` | zachytená lokálna revízia |
| SRC-061-016 | CONFIGURATION | `lustracie_a_sluzby.csv` a CLK Petriflow | nezverejnené v tomto repozitári | CLK pre ID 61; vetva SIS a spoločný koniec v balíku zdrojov | zachytená lokálna revízia |
| SRC-061-017 | CONFIGURATION | `word_templates.json` | nezverejnené v tomto repozitári | šesť výstupov ID 61 | zachytená lokálna revízia |
| SRC-061-018 | OUTPUT_TEMPLATE | Rozhodnutie_Zapis_do_RL.docx | nezverejnené v tomto repozitári | celý dokument | zachytená lokálna revízia |
| SRC-061-019 | OUTPUT_TEMPLATE | Osvedcenie_o_zapise_do_RLSR.docx | nezverejnené v tomto repozitári | celý dokument | zachytená lokálna revízia |
| SRC-061-020 | OUTPUT_TEMPLATE | List_pravoplatnost_zapis_do_RL.docx | nezverejnené v tomto repozitári | celý dokument | zachytená lokálna revízia |
| SRC-061-021 | OUTPUT_TEMPLATE | Prerusenie_konania_DCL.docx | nezverejnené v tomto repozitári | celý dokument | zachytená lokálna revízia |
| SRC-061-022 | OUTPUT_TEMPLATE | Zastavenie_konania_DCL.docx | nezverejnené v tomto repozitári | celý dokument | zachytená lokálna revízia |
| SRC-061-023 | OUTPUT_TEMPLATE | Nalepky.docx | nezverejnené v tomto repozitári | celý dokument | zachytená lokálna revízia |
| SRC-061-024 | SHAREPOINT | Súbor podkladov registra lietadiel | nezverejnené v tomto repozitári | žiadosť, vzor rozhodnutia, osvedčenie, list právoplatnosti, rozšírenie registra a schéma databázy | zachytené 2026-08-31 |
| SRC-061-025 | SOURCE_DRAFT | Prehľad grafového okolia MUDU-061 | nezverejnené v tomto repozitári | 53 priamych kontextov a priami konzumenti; navigácia, nie autorita | vytvorené a manuálne skontrolované 2026-09-01 |
| SRC-061-026 | CONFIGURATION | `portal_spravne_poplatky.csv` | nezverejnené v tomto repozitári | riadky ID 61 s kódmi 3034, 200 a 3036; porovnanie so zdrojmi MUDU-062 | zachytená lokálna revízia; skontrolované 2026-09-01 |
| SRC-061-027 | SOURCE_DRAFT | Definícia procesu MUDU-063 vo verzii 0.1.0 | nezverejnené v tomto repozitári | všetkých 19 sekcií; vzájomná hranica registra | manuálne skontrolované 2026-09-01; `UNCONFIRMED` |
