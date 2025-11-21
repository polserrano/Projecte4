# DRP: Còpies de seguretat (Parelles)

## Introducció a la tasca

En aquesta tasca analitzarem la importància de mantenir còpies de seguretat de les dades crítiques d’una empresa seguint l’esquema **3-2-1**. Aquest mètode és essencial per protegir la informació davant possibles pèrdues, errors humans o desastres naturals.

A través de la seva aplicació, es garanteix que les dades més rellevants de l’organització es mantinguin disponibles, segures i recuperables en tot moment, minimitzant l’impacte que podria tenir una pèrdua d’informació en la continuïtat del negoci.

---

## Índex

1. Introducció a la tasca
2. Índex
3. Esquema 3-2-1 de còpies
4. Explicació del 3-2-1
5. Conclusió

---

## Esquema 3-2-1 de còpies

| Element             | Proposta de la parella                                            | Justificació                                                                                                                            |
| ------------------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Dades crítiques     | Bases de dades de clients, factures, inventari, registres legals  | Són dades que, si es perden, afectarien greument l’operativa i la seguretat legal i financera de l’empresa.                             |
| Periodicitat (BD)   | Diària                                                            | Les dades crítiques canvien sovint i la seva pèrdua pot ser molt costosa. Algunes empreses poden optar per còpies horàries o contínues. |
| Tipus de còpia (BD) | Completa + incremental                                            | Una còpia completa setmanal + còpies incrementals diàries permet optimitzar espai i recuperar ràpidament la informació.                 |
| Mitjà 1 (Local)     | Servidor de còpies dins de l’empresa (NAS o disc dur extern)      | Permet recuperació ràpida i accessible per a petites incidències.                                                                       |
| Mitjà 2 (Extern)    | Núvol o centre de dades remot                                     | Protegeix davant desastres locals (robatoris, inundacions) i garanteix continuïtat del servei.                                          |
| 1 Fora de lloc      | Còpia en cinta o disc dur desconnectat fora de les instal·lacions | Assegura recuperació encara que falli la infraestructura local i externa.                                                               |

---

## Explicació del 3-2-1

* **3 còpies de les dades**: 1 còpia principal + 2 còpies de seguretat.
* **2 mitjans diferents**: Evitar la dependència d’un sol tipus de dispositiu.
* **1 fora de lloc**: Garantir la recuperació en cas de desastres locals.

---

## Conclusió

L’esquema 3-2-1 és una estratègia eficaç i pràctica per assegurar la protecció de les dades crítiques de qualsevol empresa. Disposar de tres còpies de les dades, utilitzar almenys dos tipus de mitjans i mantenir una còpia fora de lloc permet reduir significativament els riscos associats a la pèrdua d’informació i garantir la continuïtat del negoci.

---
- [Tornar Enrere](https://github.com/polserrano/Projecte4/tree/main/tasca_01)

