# DRP: Còpies de seguretat (GRUP)
Aran Perez, Pau Lopez, Pau Constanseu i Pol Serrano

## Introducció

Aquest document descriu l’estratègia de còpia de seguretat i recuperació de dades del nostre entorn IT, amb l’objectiu de garantir la disponibilitat i integritat de la informació crítica. S’han identificat les dades a protegir, la freqüència de les còpies, els mitjans i ubicacions utilitzats, així com els procediments de recuperació davant incidències.

La metodologia segueix la **Regla 3-2-1** i assegura que les dades de comptabilitat i clients compleixin els requisits de **RPO** i **RTO** de 4 hores, garantint així la continuïtat del negoci davant qualsevol eventualitat.

---

## Índex

1. Introducció
2. Índex
3. Dades objectes de còpia
4. Cronograma setmanal detallat
5. Elecció de mitjans i ubicació
6. Estratègies de recuperació
7. Conclusió

---

## Dades objectes de còpia

S’ha optat per un format taula per facilitar la visualització i comprensió de la informació:

| Categoria | Dades                          | Freqüència           | Notes              |
| --------- | ------------------------------ | -------------------- | ------------------ |
| Servidor  | Base de dades de Comptabilitat | Diària (incremental) | Crítica            |
| Servidor  | Base de dades de Clients       | Cada 4 hores         | Crítica (RPO ≤ 4h) |
| Servidor  | Fitxers compartits interns     | Setmanal             | No crítica         |
| Clients   | Documents locals de treball    | Diària               | No crítica         |
| Clients   | Configuracions locals          | Setmanal             | No crítica         |
| Altres    | Logs de sistema                | Setmanal             | No crítica         |

S’han separat les dades de **Servidor/Clients** i **Crítiques/No crítiques** per prioritzar correctament la recuperació.

---

## Cronograma setmanal detallat

| Dia       | Dades                  | Tipus de còpia | Mitjà        |
| --------- | ---------------------- | -------------- | ------------ |
| Dilluns   | BD Comptabilitat       | Incremental    | NAS Local    |
| Dilluns   | BD Clients             | Incremental    | NAS Local    |
| Dimarts   | Fitxers compartits     | Completa       | NAS Local    |
| Dimarts   | Logs sistema           | Completa       | NAS Local    |
| Dimecres  | BD Comptabilitat       | Incremental    | NAS Local    |
| Dimecres  | BD Clients             | Incremental    | NAS Local    |
| Dijous    | Fitxers compartits     | Incremental    | NAS Local    |
| Divendres | BD Comptabilitat       | Incremental    | NAS Local    |
| Divendres | BD Clients             | Incremental    | NAS Local    |
| Dissabte  | BD Comptabilitat       | Completa       | Cloud Extern |
| Dissabte  | BD Clients             | Completa       | Cloud Extern |
| Diumenge  | Fitxers compartits     | Completa       | Cloud Extern |
| Diumenge  | Configuracions clients | Completa       | Cloud Extern |

---

## Elecció de mitjans i ubicació

| Mitjà            | Descripció                         | Ubicació                   | Responsable                           |
| ---------------- | ---------------------------------- | -------------------------- | ------------------------------------- |
| Mitjà 1 (Local)  | NAS amb discos RAID 5 de 10 TB     | Sala de Servidors          | Administrador IT local                |
| Mitjà 2 (Extern) | Cloud Storage (Azure Blob Storage) | Data Center extern d’Azure | Administrador IT                      |
| Fora de lloc     | Còpia externa diària al Cloud      | Data Center remot          | Administrador IT amb accés restringit |

---

## Regla 3-2-1

* **3 còpies**: 1 original + 2 còpies de seguretat.
* **2 mitjans diferents**: NAS local i Cloud.
* **1 fora de lloc**: Cloud Azure per protecció davant desastres físics.

---

## Estratègies de recuperació

| Tipus de dada      | RPO      | RTO      | Estratègia                                                                                                                          |
| ------------------ | -------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Comptabilitat      | 4 hores  | 4 hores  | Còpies incrementals cada 4h. Restauració prioritària des del NAS local. En cas de fallida completa, recuperació des de Cloud Azure. |
| Clients            | 4 hores  | 4 hores  | Còpies incrementals cada 4h. Restauració automatitzada amb software de backup centralitzat.                                         |
| Fitxers compartits | 24 hores | 24 hores | Recuperació menys prioritària, des NAS o Cloud segons disponibilitat.                                                               |

* El **RPO de 4 hores** es garanteix amb còpies incrementals cada 4 hores.
* El **RTO de 4 hores** s’assegura amb restauracions prioritàries locals i accés immediat a còpia Cloud en cas de desastre.

---

## Conclusió

L’estratègia proposada proporciona un pla de backup robust i escalable, combinant còpies locals i externes per minimitzar riscos. La definició clara de freqüències, tipus de còpia i responsabilitats assegura que les dades crítiques estiguin protegides i recuperables dins dels límits establerts.

Mitjançant aquesta planificació, l’empresa disposa d’un sistema de recuperació fiable que garanteix la continuïtat operativa, redueix la possibilitat de pèrdua de dades i compleix amb els requisits de seguretat i normativa vigent.

---
- [Tornar Enrere](/Projecte4/tasca_01)

