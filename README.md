# Návrhy procesov MUDU na vecnú kontrolu

Tento repozitár overuje praktický spôsob, ako môže LLM pripraviť prvý návrh
procesu tak, aby ho analytik alebo vecný gestor vedel priamo skontrolovať.

LLM môže interne prečítať veľké množstvo zdrojov, ale človeku ukáže iba:

- čo podľa zdrojov proces robí;
- čo do procesu patrí a nepatrí;
- jednoduchý navrhovaný priebeh;
- najdôležitejšie pravidlá;
- rozpory a konkrétne otázky;
- presne to, čo potrebuje potvrdiť.

Nejde o implementačnú dokumentáciu ani o náhradu Petriflow. Po vecnom potvrdení
návrhu sa rovnaký priebeh spracuje ako skutočný Petriflow model a následne sa
rozšíri o formuláre, integrácie, automatické testy a dôkazy.

## Príklady

| Proces | Návrh na kontrolu |
| --- | --- |
| MUDU-060 — Predbežné pridelenie registrovej značky | [Otvoriť](examples/MUDU-060/definition.md) |
| MUDU-061 — Zápis lietadla do registra | [Otvoriť](examples/MUDU-061/definition.md) |
| MUDU-062 — Zmena údajov registra | [Otvoriť](examples/MUDU-062/definition.md) |
| MUDU-063 — Výmaz lietadla z registra | [Otvoriť](examples/MUDU-063/definition.md) |

Všetky štyri sú `DRAFT / UNCONFIRMED`. Sú to návrhy toho, čo sme pochopili zo
zdrojov, nie schválené procesy.

## Pracovný postup

Pri obnove existujúcich procesov:

`zdroje + dnešný Petriflow + implementácia → LLM návrh → analytik opraví a odpovie → gestor prijme → detailný Petriflow a overovanie`

Po prvom prijatí procesu:

`ľudská požiadavka na zmenu → LLM navrhne zmenu → kontrola dopadov → ľudské prijatie → nový Petriflow a nové overovanie`

Formát návrhu určuje [`STANDARD.md`](STANDARD.md). Postup pre ľubovoľný schopný
LLM je v [`SKILL.md`](SKILL.md).
