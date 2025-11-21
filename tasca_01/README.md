# Introducció al Projecte de Còpies de Seguretat

Aquest projecte té com a objectiu dissenyar i implementar una **política de còpies de seguretat** per a l’empresa **"Muntatges i Serveis Tècnics SL"**, una petita empresa dedicada a la instal·lació i manteniment d’equips industrials. La tasca es desenvolupa en tres fases (individual, per parelles i en grup) amb l’objectiu d’assegurar la protecció de les dades crítiques i garantir la **continuïtat del negoci** en cas d’incidències.

## Context

L’empresa disposa de la següent infraestructura tècnica:

- **Servidor de Fitxers (Ubuntu Server):**
  - Documents de Projectes: Plànols i especificacions tècniques (300 GB, creixement moderat).
  - Bases de Dades (Comptabilitat i Clients): Crítiques i d'ús diari (20 GB, canvi constant).
  - Carpetes Personals dels Usuaris: Fitxers de treball diari (100 GB).

- **10 Equips Clients (Windows 10/11):** Els tècnics treballen principalment amb fitxers del servidor, però alguns guarden temporalment arxius importants localment.

- **Connexió a Internet:** Fibra òptica simètrica de 600 Mbps.

## Requisits de Recuperació

- **RTO (Temps de Recuperació):** Les dades de Comptabilitat i Clients han d’estar disponibles en menys de 4 hores.
- **RPO (Pèrdua de Dades Admesa):** Les dades de Comptabilitat i Clients no poden perdre més de 4 hores; per la resta de dades, es permet una pèrdua màxima de 24 hores.
- **Retenció:** Les dades han de mantenir-se amb un historial mínim d’un mes.

## Objectiu de la Tasca

Durant el desenvolupament del projecte, es treballarà de la següent manera:

1. **Fase 1 - Treball Individual:** Identificar quines dades són crítiques, definir periodicitat i tipus de còpia, i seleccionar mitjans i ubicació.
2. **Fase 2 - Treball per Parelles:** Comparar respostes individuals, consensuar i dissenyar un esquema de còpia basat en la **Regla 3-2-1** (3 còpies, 2 mitjans, 1 fora de lloc).
3. **Fase 3 - Treball en Grup:** Debat de propostes, selecció de la millor estratègia i elaboració de la **Política de Còpies de Seguretat Definitiva** per a l’empresa.

L’objectiu final és garantir que les dades crítiques estiguin protegides, accessibles i recuperables de manera eficient davant qualsevol incident.

---
## Documentació a entregar:

- [Còpies de seguretat. Estudi cas client, INDIVIDUAL](https://github.com/polserrano/Projecte4/blob/main/tasca_01/DRP%3A%20c%C3%B2pies%20de%20seguretat.%20Estudi%20cas%20client%20(INDIVIDUAL).md)
- [Còpies de seguretat. Estudi cas client, PARELLES](https://github.com/polserrano/Projecte4/blob/main/tasca_01/DRP%3A%20c%C3%B2pies%20de%20seguretat.%20Estudi%20cas%20client%20(PARELLES).md)
- [Còpies de seguretat. Estudi cas client, GRUP](https://github.com/polserrano/Projecte4/blob/main/tasca_01/DRP%3A%20c%C3%B2pies%20de%20seguretat.%20Estudi%20cas%20client%20(GRUP).md)

---

- [Tornar Enrere](https://github.com/polserrano/Projecte4/tree/main)
