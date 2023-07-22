# La regla D'Hondt com mai te l'havien explicat!

Cada cop que hi ha eleccions passa el mateix, els mitjans de comunicació s'afanyen a explicar amb taules i diagrames les pintoresques peculiaritats de la [**regla D'Hondt**](https://ca.wikipedia.org/wiki/Regla_D%27Hondt), aquest sistema arcà que es fa servir per repartir els escons a molts països.

**I gairebé sempre l’expliquen malament**, així que anem a veure si podem posar una mica de *llum a la foscor* i, de pas, aclarir uns quants malentesos.

***

## Tenim un problema

La regla D’Hondt soluciona un problema molt concret:

> Donats uns partits polítics i una certa quantitat d’escons, volem repartir els escons entre els partits polítics de la manera més proporcional possible als vots que ha obtingut cada partit a les eleccions.

I, és clar, quan es parla de repartiment proporcional, el primer que ens ve al cap és la [**regla de tres**](https://ca.wikipedia.org/wiki/Regla_de_tres). Amb això deu haver-hi prou, no?

Doncs no! La regla de tres només funciona per aquells problemes on pots tallar les coses com vulguis i, malauradament, els escons només els pots repartir sencers. Aquesta petita diferència fa que calgui aplicar mètodes molt més complicats.

## Un primer intent

Malgrat no poder aplicar la regla de tres tal qual, és molt temptador mirar d’adaptar-la mitjançant el que es coneix com a [**mètode de Hamilton**](https://ca.wikipedia.org/wiki/M%C3%A8tode_de_Hamilton): Fas la regla de tres, truncant els decimals, i llavors acabes de repartir els escons que et quedin donant prioritat als partits que estaven més a prop d'aconseguir el següent escó abans de l’arrodoniment, és a dir, als que tenen un major residu decimal.

**Per exemple:** Volem repartir 10 escons entre els partits **A**, **B** i **C**.

| Partit | Vots      | Regla de tres                        | Part entera | Residu decimal | Escons  |
| :----: | :-------: | :----------------------------------: | :---------: | :------------: | :-----: |
| **A**  |   600.000 |   600.000 · 10 / 1.400.000 =  4,2857 |           4 |         0,2857 |       4 |
| **B**  |   600.000 |   600.000 · 10 / 1.400.000 =  4,2857 |           4 |         0,2857 |       4 |
| **C**  |   200.000 |   200.000 · 10 / 1.400.000 =  1,4286 |           1 |     **0,4286** | 1+**1** |
| Total  | 1.400.000 | 1.400.000 · 10 / 1.400.000 = 10,0000 |           9 |              1 |      10 |

Després del truncament **A** s'emporta 4 escons, **B** s'emporta 4 escons i **C** s'emporta 1 escó. Qui s'endurà l'escó que queda? Doncs el partit **C**, perquè és el partit amb un major residu decimal.

Fàcil de fer i d'entendre… sembla que ja ho tindríem, oi? Doncs no!

## El primer intent falla

Resulta que el mètode de Hamilton va molt bé en molts casos, però falla estrepitosament en d'altres.

**Per exemple:** Suposem ara que en comptes de repartir 10 escons, en repartim 11.

| Partit | Vots      | Regla de tres                        | Part entera | Residu decimal | Escons  |
| :----: | :--------:| :----------------------------------: | :---------: | :------------: | :-----: |
| **A**  |   600.000 |   600.000 · 11 / 1.400.000 =  4,7143 |           4 |     **0,7143** | 4+**1** |
| **B**  |   600.000 |   600.000 · 11 / 1.400.000 =  4,7143 |           4 |     **0,7143** | 4+**1** |
| **C**  |   200.000 |   200.000 · 11 / 1.400.000 =  1,5714 |           1 |         0,5714 |       1 |
| Total  | 1.400.000 | 1.400.000 · 11 / 1.400.000 = 11,0000 |           9 |         2,0000 |      11 |

Com podeu veure, amb els mateixos resultats electorals, en repartir un escó més, el resultat pel partit **C** ha empitjorat. Això es coneix com la [**paradoxa d'Alabama**](https://en.wikipedia.org/wiki/Apportionment_paradox#Alabama_paradox) i és un dels motius pels quals s'acostuma a descartar el mètode de Hamilton.

## Un segon intent

El següent mètode més senzill possible per resoldre el problema del repartiment d’escons consisteix a fer servir la [llei de l’oferta i la demanda](https://ca.wikipedia.org/wiki/Oferta_i_demanda). Aquest principi econòmic ens diu que el preu d’un bé afecta les seves vendes i que hi ha un preu *just* que fa que se'n venguin, exactament, totes les unitats produïdes.

Aplicada al context electoral, aquesta llei implica que hi ha un preu (mesurat en vots) que fa que es venguin (s’assignin) exactament el nombre d’escons que volem repartir.

**Per exemple:** Volem repartir 12 escons entre quatre partits polítics.

| Partit | Vots      |
| :----: | :-------: |
| **A**  | 4.000.000 |
| **B**  | 3.500.000 |
| **C**  | 2.000.000 |
| **D**  | 1.500.000 |

Imaginem que cada escó valgués 1.000.000 de vots. Quants es *vendrien*? Doncs només 10, 4 pel partit **A**, 3 pel partit **B**, 2 pel parit **C** i 1 pel partit **D**. És evident que cal *abaratir* el preu si en volem vendre 12.

I si valguessin 500.000 vots? Quants es *vendrien* ara? Doncs 22 escons: 8 pel partit **A**, 7 pel partit **B**, 4 pel partit **C** i 3 pel partit **D**. És evident que cal *encarir* el preu si només en podem vendre 12.

I quin és el preu *just* que fa que es venguin, exactament, 12 escons? Doncs anem a fer una taula per mirar de trobar-lo:

| Preu        | Escons *venuts* |
| :---------: | :-------------: |
| 4.000.000   |               1 |
| 3.500.000   |               2 |
| 2.000.000   |               4 |
| 1.750.000   |               5 |
| 1.500.000   |               6 |
| 1.333.333   |               7 |
| 1.166.667   |               8 |
| 1.000.000   |              10 |
|   875.000   |              11 |
| **800.000** |          **12** |
|   750.000   |              13 |
|   700.000   |              14 |
|   666.667   |              16 |
|   583.333   |              17 |
|   571.429   |              18 |
|   500.000   |              22 |

Veient aquesta taula és evident que el preu que fa que es *venguin* exactament 12 escons és 800.000 vots/escó:

| Partit | Vots      | Escons que pot comprar | Vots desaprofitats                  |
| :----: | :-------: | :--------------------: | :---------------------------------- |
| **A**  | 4.000.000 |                      5 | 4.000.000 - (5 · 800.000) =   0     |
| **B**  | 3.500.000 |                      4 | 3.500.000 - (4 · 800.000) = 300.000 |
| **C**  | 2.000.000 |                      2 | 2.000.000 - (2 · 800.000) = 400.000 |
| **D**  | 1.500.000 |                      1 | 1.500.000 - (1 · 800.000) = 700.000 |

Ara bé, ja hem vist que calcular quants escons es reparteixen a un preu donat és fàcil… però la pregunta és: com podem trobar ràpidament el preu *just* que ens permetrà vendre exactament els escons disponibles? D'on han sortit els *preus* de la taula anterior?

## Regla D'Hondt = Llei de l'oferta i la demanda

Doncs resulta que **el que normalment s'entén per regla D'Hondt és, en realitat, un algorisme per resoldre el problema de trobar el preu just per *vendre* exactament els escons disponibles fent servir la llei de l'oferta i la demanda.**

Recordem com funcionava: Cal fer una taula amb 4 columnes (una per cada partit) i 12 fileres (una per cada escó). A la filera N posem els vots de cada partit dividits per N. **Aquest valor serà el preu màxim que podria pagar cada partit polític si volgués comprar N vots**.

|        | **A**     | **B**     | **C**     | **D**     |
| :----: | :-------: | :-------: | :-------: | :-------: |
| **1**  | 4.000.000 | 3.500.000 | 2.000.000 | 1.500.000 |
| **2**  | 2.000.000 | 1.750.000 | 1.000.000 |   750.000 |
| **3**  | 1.333.333 | 1.166.667 |   666.667 |   500.000 |
| **4**  | 1.000.000 |   875.000 |   500.000 |   375.000 |
| **5**  |   800.000 |   700.000 |   400.000 |   300.000 |
| **6**  |   666.667 |   583.333 |   333.333 |   250.000 |
| **7**  |   571.429 |   500.000 |   285.714 |   214.286 |
| **8**  |   500.000 |   437.500 |   250.000 |   187.500 |
| **9**  |   444.444 |   388.889 |   222.222 |   166.667 |
| **10** |   400.000 |   350.000 |   200.000 |   150.000 |
| **11** |   363.636 |   318.182 |   181.818 |   136.364 |
| **12** |   333.333 |   291.667 |   166.667 |   125.000 |

A continuació, cal quedar-nos amb els 12 números més grans de la taula (perquè tenim 12 escons a repartir). El més petit d'aquests, 800.000, serà el valor *just* que fa que es *venguin*, exactament, els 12 escons disponibles.

|        | **A**       | **B**       | **C**       | **D**       |
| :----: | :---------: | :---------: | :---------: | :---------: |
| **1**  | 4.000.000   | 3.500.000   | 2.000.000   | 1.500.000   |
| **2**  | 2.000.000   | 1.750.000   | 1.000.000   |             |
| **3**  | 1.333.333   | 1.166.667   |             |             |
| **4**  | 1.000.000   |   875.000   |             |             |
| **5**  | **800.000** |             |             |             |


Ara podem entendre d'on han sortit els *preus* de la taula **Preu / Escons *venuts***, són els nombres que apareixen a la taula de la regla D'Hondt i tenen la propietat de ser els valors que marquen el límit entre assignar K escons i assignar-ne K+1.

**Per exemple:** Mirant la taula anterior és fàcil veure que si el *preu* fos 800.001 vots, es *vendrien* 11 escons mentre que si és 800.000, se'n *vendran* 12. També podem veure casos on el salt és més gran: si el *preu* és 1.000.000 vots, es *vendran* 8 escons, mentre que, si el preu baixa a 1.000.000, se'n vendran 10. Aquests salts són molt poc probables a la pràctica, on és gairebé impossible que un mateix nombre aparegui diverses vegades a la taula.

## Conseqüències de fer servir la llei de l'oferta i la demanda

En contra del que sovint es creu, **amb aquest mètode tots els partits estan comprant els escons al mateix preu** (800.000 vots, en l'exemple). El que passa és que gairebé tots els partits (tots menys el que té el *preu just* a la seva columna) desperdicien part dels seus vots en fer-ho. Aquest efecte és més acusat com més minoritari és el partit polític, perquè els vots desperdiciats en termes absoluts suposaran un major percentatge del seu pes electoral en termes relatius.

També és fàcil observar que aquest mètode de repartiment d'escons penalitza les coalicions formades *a posteriori*. El partit **B** té 3.500.000 vots i la coalició **C+D** també, però el partit **B** pot aprofitar els 400.000 vots que desperdicia **C** i els 700.000 vots que desperdicia **D** per comprar un altre escó, obtenint-ne 4 en total, mentre que **C+D** s'ha de conformar amb 3 perquè han concorregut a les eleccions per separat.

Tots dos efectes combinats acostumen a justificar la creença que la regla D'Hondt afavoreix als partits majoritaris, però en realitat són una conseqüència bàsica de la llei de l'oferta i la demanda i les [**economies d'escala**](https://ca.wikipedia.org/wiki/Economia_d%27escala). Això té més rellevància a les circumscripcions petites, on el [**vot útil**](https://ca.wikipedia.org/wiki/Vot_%C3%BAtil) pot suposar una gran diferència i val la pena donar un cop d'ull a quin partit està més a prop d'aconseguir un altre escó.

**Per exemple:** Qui està en millors condicions de robar-li el cinquè escó al partit **A** és el partit més minoritari de tots, **D**, que només necessitaria 100.001 vots més per fer-ho. Això va en contra de la creença popular que la regla D'Hondt fa que votar a partits minoritaris sigui inútil.
