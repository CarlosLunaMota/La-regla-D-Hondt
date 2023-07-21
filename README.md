# La regla D'Hondt com mai te l'havien explicat!

Cada cop que hi ha eleccions passa el mateix: Mitjans de comunicació i divulgadors de tota mena s'afanyen a explicar les pintoresques peculiaritats de la [**regla D'Hondt**](https://ca.wikipedia.org/wiki/Regla_D%27Hondt), aquest sistema arcà que es fa servir per repartir els escons a molts països.

I cada cop l’expliquen malament. Així que anem a veure si podem explicar què és això de la regla D’Hondt d’una vegada per totes i, de pas, aclarir uns quants malentesos.

***

## Tenim un problema

La regla D’Hondt soluciona un problema molt concret:

> Donats uns partits polítics i una certa quantitat d’escons, volem repartir els escons entre els partits polítics de la manera més proporcional possible als vots que ha obtingut cada partit a les eleccions.

I, és clar, quan es parla de repartiment proporcional el primer que ens ve al cap és la [**regla de tres**](https://ca.wikipedia.org/wiki/Regla_de_tres). Amb això deu haver-hi prou, no?

Doncs no! La regla de tres només funciona per aquells problemes on pots tallar les coses a repartir com vulguis. Malauradament, els escons només els pots repartir sencers i aquesta petita diferència fa que calgui aplicar mètodes molt més complicats.

## Un primer intent

Malgrat no poder aplicar la regla de tres tal qual, és molt temptador mirar d’adaptar-la mitjançant el que es coneix com a [**mètode de Hamilton**](https://ca.wikipedia.org/wiki/M%C3%A8tode_de_Hamilton): Fas la regla de tres, arrodonint cap a baix i llavors acabes de repartir els escons que et quedin donant prioritat als partits que estaven més a prop d'aconseguir el següent escó abans de l’arrodoniment.

**Per exemple:** Volem repartir 10 escons entre els partits **A**, **B** i **C**.

| Partit | Vots	     | Regla de tres                  	 | Arrodoniment cap a baix | Repartiment final |
| :----: |----------:| ---------------------------------:| -----------------------:| -----------------:|
| **A**  |   600.000 | 600.000 · 10 / 1.400.000 = 4,2857 |                     	 4 |             	   4 |
| **B**  |   600.000 | 600.000 · 10 / 1.400.000 = 4,2857 |                   	   4 |             	   4 |
| **C**  |   200.000 | 200.000 · 10 / 1.400.000 = 1,4286 |                   	   1 |             	   2 |
| Total  | 1.400.000 |                           10,0000 |                   	   9 |            	  10 |

Després de l'arrodoniment **A** s'emporta 4 escons, **B** s'emporta 4 escons i **C** s'emporta 1 escó. Qui s'endurà l'escó que queda? Doncs el partit **C**, perquè és el partit que estava més a prop d'arribar al següent escó abans de l'arrodoniment.

Fàcil de fer i d'entendre... sembla que ja ho tindríem, oi? Doncs no!

## El primer intent falla

Resulta que el mètode de Hamilton va molt bé en molts casos, però falla estrepitosament en d'altres.

**Per exemple:** Suposem ara que en comptes de repartir 10 escons, en repartim 11.

| Partit | Vots	     | Regla de tres          	         | Arrodoniment cap a baix | Repartiment final |
| :----: |----------:| ---------------------------------:| -----------------------:| -----------------:|
| **A**  |   600.000 | 600.000 · 11 / 1.400.000 = 4,7143 |                   	   4 |             	   5 |
| **B**  |   600.000 | 600.000 · 11 / 1.400.000 = 4,7143 |                   	   4 |             	   5 |
| **C**  |   200.000 | 200.000 · 11 / 1.400.000 = 1,5714 |                   	   1 |             	   1 |
| Total  | 1.400.000 |                	         11,0000 |                   	   9 |            	  11 |

Com podeu veure, amb els mateixos resultats electorals, en repartir un escó més, el resultat pel partit **C** ha empitjorat. Això es coneix com la [**paradoxa d'Alabama**](https://en.wikipedia.org/wiki/Apportionment_paradox#Alabama_paradox) i és un dels motius pels quals s'acostuma a descartar el mètode de Hamilton.

## Un segon intent

El següent mètode més senzill possible per resoldre el problema del repartiment d’escons consisteix a fer servir la [llei de l’oferta i la demanda](https://ca.wikipedia.org/wiki/Oferta_i_demanda). Aquest principi econòmic ens diu que el preu d’un bé afecta les seves vendes i que hi ha un preu *just* que fa que se'n venguin, exactament, totes les unitats produïdes.

Aplicada al context electoral, aquesta llei implica que hi ha un preu (mesurat en vots) que fa que es venguin (s’assignin) exactament el nombre d’escons que volem repartir.

**Per exemple:** Volem repartir 12 escons entre quatre partits polítics.

| Partit | Vots 	    |
| :----: |-----------:|
| **A**  |  4.000.000 |
| **B**  |  3.500.000 |
| **C**  |  2.000.000 |
| **D**  |  1.500.000 |

Imagina que cada escó valgués 4.000.000 de vots. Quants es *vendrien*? Doncs només 1, el que podria comprar el partit **A**. És evident que cal *abaratir* el preu si en volem vendre 12.

I si valguessin 100.000 vots? Quants es *vendrien* ara? Doncs 110 escons: 40 pel partit **A**, 35 pel partit **B**, 20 pel partit **C** i 15 pel partit **D**. És evident que cal *encarir* el preu si només en podem vendre 12.

I quin és el preu *just* que fa que es venguin, exactament, 12 escons? Doncs anem a fer una taula per mirar de trobar-lo:

| Preu       | Escons venuts |
| ---------: | -------------:|
| 4.000.000  |             1 |
| 3.500.000  |             2 |
| 2.000.000  |             4 |
| 1.750.000  |             5 |
| 1.500.000  |             6 |
| 1.333.333  |             7 |
| 1.166.667  |             8 |
| 1.000.000  |            10 |
|   875.000  |            11 |
|   800.000  |        **12** |
|   750.000  |            13 |
|   700.000  |            14 |
|   666.667  |            16 |

Veient aquesta taula és evident que el preu que fa que es *venguin* exactament 12 escons és 800.000 vots/escó:

| Partit | Vots      | Escons que pot comprar     | Vots que desaprofita                |
| :----: | ---------:| --------------------------:| -----------------------------------:|
| **A**  | 4.000.000 |                          5 | 4.000.000 - (5 · 800.000) =       0 |
| **B**  | 3.500.000 |                          4 | 3.500.000 - (4 · 800.000) = 300.000 |
| **C**  | 2.000.000 |                          2 | 2.000.000 - (2 · 800.000) = 400.000 |
| **D**  | 1.500.000 |                          1 | 1.500.000 - (1 · 800.000) = 700.000 |

Ara bé, la pregunta és... Com he fet la taula anterior? O, més concretament, com he escollit els nombres que apareixen a la columna **Preu**?

## Oferta i demanda = regla D'Hondt

Doncs resulta que el que normalment s'entén per regla D'Hondt és, en realitat, un algorisme per resoldre el problema de trobar el preu just per *vendre* exactament els escons disponibles.

**Per exemple:** Fem una taula amb 4 columnes (una per cada partit) i 12 fileres (una per cada escó). A la filera N posem els vots de cada partit dividit per N. Aquest valor serà el preu màxim que podria pagar cada partit polític si volgués comprar N vots.

|        | **A**     | **B** 	    | **C**    | **D** 	   |
| :----: | :--------:| :--------:| :--------:| :--------:|
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

A continuació, queda't només amb amb els 12 números més grans de la taula. De tots aquests, el més petit (800.000) és el valor *just* que fa que es *venguin*, exactament, els 12 escons disponibles.

|        | **A**       | **B**   	   | **C**       | **D**   	   |
| :----: | :----------:| :----------:| :----------:| :----------:|
| **1**  | 4.000.000   | 3.500.000   | 2.000.000   | 1.500.000   |
| **2**  | 2.000.000   | 1.750.000   | 1.000.000   | ~~750.000~~ |
| **3**  | 1.333.333   | 1.166.667   | ~~666.667~~ | ~~500.000~~ |
| **4**  | 1.000.000   |   875.000   | ~~500.000~~ | ~~375.000~~ |
| **5**  | **800.000** | ~~700.000~~ | ~~400.000~~ | ~~300.000~~ |
| **6**  | ~~666.667~~ | ~~583.333~~ | ~~333.333~~ | ~~250.000~~ |
| **7**  | ~~571.429~~ | ~~500.000~~ | ~~285.714~~ | ~~214.286~~ |
| **8**  | ~~500.000~~ | ~~437.500~~ | ~~250.000~~ | ~~187.500~~ |
| **9**  | ~~444.444~~ | ~~388.889~~ | ~~222.222~~ | ~~166.667~~ |
| **10** | ~~400.000~~ | ~~350.000~~ | ~~200.000~~ | ~~150.000~~ |
| **11** | ~~363.636~~ | ~~318.182~~ | ~~181.818~~ | ~~136.364~~ |
| **12** | ~~333.333~~ | ~~291.667~~ | ~~166.667~~ | ~~125.000~~ |

Quan la gent veu aquesta taula
