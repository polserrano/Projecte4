# DRP: Còpies de seguretat
Pol Serrano Aromí

## Introducció a la tasca

En aquesta tasca s’analitza com planificar i implementar un sistema de còpies de seguretat per a una empresa, seguint criteris de priorització, periodicitat i ubicació segons la regla 3-2-1. Es detallen quines dades són més crítiques, quina freqüència i tipus de còpia es recomana per a cada tipus d’informació, així com els mitjans i llocs més adequats per emmagatzemar-les.

L’objectiu és garantir la recuperació ràpida i segura de les dades davant qualsevol incident, minimitzant el risc de pèrdua d’informació essencial per al funcionament de l’organització.

---

## Índex

1. Introducció a la tasca
2. Què copiar? (Priorització)
3. Periodicitat i tipus de còpia
4. Mitjans i ubicació (Regla 3-2-1)
5. Conclusió

---

## 2. Què copiar? (Priorització)

### Dades més crítiques del servidor

* **Bases de Dades de Comptabilitat i Clients (20 GB)**
  Crítiques i d’ús diari; tenen un RTO de < 4 hores i RPO de 4 hores.

* **Documents de Projectes (300 GB)**
  Contenen plànols i especificacions tècniques. Tot i que el RPO permet fins a 24 hores de pèrdua, són dades molt importants.

* **Carpetes personals dels usuaris (100 GB)**
  Informació de treball diari; la seva pèrdua es pot tolerar fins a 24 hores.

### Còpia dels 10 equips clients

* Només cal copiar els fitxers locals importants dels equips clients (ex. informes tècnics temporals, documents de treball no sincronitzats amb el servidor).
* No cal fer còpia completa de tot el sistema dels clients, ja que la major part del treball es desa al servidor.

### Priorització resumida

1. Bases de Dades de Comptabilitat i Clients
2. Documents de Projectes
3. Carpetes personals dels usuaris
4. Fitxers locals crítics dels clients

---

## 3. Periodicitat i tipus de còpia

### Bases de Dades de Comptabilitat i Clients

* **Periodicitat**: Cada 4 hores (diari, amb backups intermedis cada 4h)
* **Tipus**: Incremental entre còpies completes
* **Còpia completa**: Setmanal

### Documents de Projectes i Carpetes Personals

* **Documents de Projectes**:
  Diari (incremental) + completa setmanal

* **Carpetes personals**:
  Diari (incremental) + completa setmanal o mensual segons creixement

* **Tipus general**: Incremental diari, completa setmanal

### Fitxers dels clients

* **Periodicitat**: Diari (preferiblement a la nit)
* **Tipus**: Incremental, amb còpia completa setmanal

### Calendari bàsic resumit

| Dia       | Bases de Dades | Documents Projectes | Carpetes Usuaris | Fitxers Clients |
| --------- | -------------- | ------------------- | ---------------- | --------------- |
| Dilluns   | Completa       | Completa            | Completa         | Completa        |
| Dimarts   | Incremental    | Incremental         | Incremental      | Incremental     |
| Dimecres  | Incremental    | Incremental         | Incremental      | Incremental     |
| Dijous    | Incremental    | Incremental         | Incremental      | Incremental     |
| Divendres | Incremental    | Incremental         | Incremental      | Incremental     |
| Dissabte  | Incremental    | Incremental         | Incremental      | Incremental     |
| Diumenge  | Completa       | Completa            | Completa         | Completa        |

---

## 4. Mitjans i ubicació (Regla 3-2-1)

### Mitjans recomanats

* **Discs durs externs**: Ràpids per restaurar dades crítiques.
* **NAS**: Ideal per còpies internes amb accés ràpid en xarxa.
* **Cloud**: Còpia fora del lloc físic (resiliència davant desastres).
* **Cintes**: Opcional per arxiu a llarg termini.

### Ubicació segons la Regla 3-2-1

* **3 còpies de les dades**: 1 al servidor, 1 al NAS, 1 al cloud o cinta externa.
* **2 mitjans diferents**: NAS + Cloud/cinta.
* **1 fora del lloc**: Cloud o cinta guardada en lloc segur extern.

### Exemple de configuració

* Còpia diària incremental al NAS
* Còpia setmanal completa al Cloud
* Arxiu mensual a cinta fora de l’empresa

---

## 5. Conclusió

Un pla de còpies de seguretat ben estructurat és essencial per assegurar la continuïtat del negoci. Prioritzar les dades més crítiques, establir una periodicitat adequada i aplicar correctament la regla 3-2-1 amb mitjans i ubicacions diferenciades permet protegir la informació davant pèrdues accidentals, fallades tècniques o desastres, garantint així la seguretat i disponibilitat de les dades empresarials.

---
- [Tornar Enrere](https://github.com/polserrano/Projecte4/tree/main/tasca_01)

