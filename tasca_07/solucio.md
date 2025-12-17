# 💻 T07: Serveis d’assistència remota (RUSTDESK)

- **Autors:** Pol Serrano i Pau Constanseu
- **Data:** 17/12/2025

## 📖 1. Introducció a la tasca:

A EverPia, una part essencial de la nostra feina és el suport directe a l’usuari final (Helpdesk). Per resoldre incidències habituals de manera ràpida i eficient, necessitem una eina d’assistència remota sota demanda que sigui senzilla d’utilitzar, segura i compatible amb diferents sistemes operatius.

Per aquest motiu, la direcció ha decidit estandarditzar una eina oficial d’assistència remota. En aquesta tasca, treballant en parelles, haureu d’analitzar diverses solucions del mercat, seleccionar la més adequada i crear la documentació necessària tant per als tècnics d’EverPia com per als clients finals.

## 📚 2. Índex:

**1. Introducció a la tasca**

**2. índex**

**3. Anàlisi i comparativa**

**4. Fase pràctica**

**5. Conclusió de la tasca**

## 📋 3. Anàlisi i comparativa:

Ara analitzarem diferents eines d’assistència remota disponibles al mercat i seleccionar la més adequada per a EverPia, tenint en compte la **facilitat d’ús per al client**, la **disponibilitat en sistemes operatius** i el **model de preu per a ús comercial**.

### Eines Analitzades
Les quatre solucions seleccionades són:
1. **TeamViewer**
2. **AnyDesk**
3. **Google Remote Desktop**
4. **RustDesk**

---

### Taula Comparativa

| Criteri | TeamViewer | AnyDesk | Google Remote Desktop | RustDesk |
|-------|-----------|---------|----------------------|----------|
| **Facilitat d’ús** | Requereix instal·lació (o versió QuickSupport). L’ID i contrasenya són fàcils de compartir. | Portable disponible. ID curt i fàcil de comunicar. Molt intuïtiu. | Requereix compte Google i configuració prèvia. Menys flexible per a assistència puntual. | Portable disponible. Connexió mitjançant ID o codi. Interfície senzilla per a usuaris no tècnics. |
| **Disponibilitat (SO)** | Windows, macOS, Linux, Android, iOS | Windows, macOS, Linux, Android, iOS | Windows, macOS, Linux (via navegador Chrome) | Windows, macOS, Linux, Android, iOS |
| **Model de Preu** | No gratuït per a ús comercial. Cost elevat per tècnic. | No gratuït per a ús comercial. Cost mitjà per llicència. | Gratuït, però amb funcionalitats molt limitades per a entorns professionals. | Gratuït i **open-source**. Opció d’autoallotjament sense cost de llicència. Versions de pagament opcionals amb suport. |
| **Limitacions principals** | Cost elevat, detecció agressiva d’ús comercial. | Llicència obligatòria per a ús professional continuat. | No pensat per a suport tècnic professional (sense ID temporal). | Requereix configuració inicial si s’autoallotja el servidor. |

---

### Recomanació:

Després de l’anàlisi comparativa, **RustDesk** és la millor opció per a EverPia pels motius següents:

- **Equilibri entre cost i funcionalitat**: és gratuït per a ús comercial i no imposa limitacions artificials.
- **Compatibilitat:** (Windows, macOS i Linux), un requisit clau per a EverPia.
- **Facilitat per al client**: permet connexions ràpides mitjançant ID o versió portable, ideal per a usuaris no tècnics.
- **Control i seguretat**: en ser open-source, permet a EverPia autoallotjar el servidor i tenir control total sobre les dades.

## 🌐 4. Fase pràctica:

Començarem primer de tot instal·lant els dos entorns/màquines, en aquests cas us mostro la màquina que estarem usant per el tècnic, pero el client seria el mateix, **Windows 11** (en el nostre cas) i un adaptador en **NAT** (per tenir connexió a internet i poguer fer la instal·lació de rustdesk.

![imatge1](/tasca_07/img/1.png)

Seguirem amb la instal·lació de l'eina, ho farem en les **dues màquines**, en el nostre cas, com estem utilitzan l'eina de rust desk entrarem a: https://rustdesk.com/ i farem la instal·lació com es mostra a la imatge.

![imatge2](/tasca_07/img/2.png)
![imatge3](/tasca_07/img/3.png)
![imatge4](/tasca_07/img/4.png)

Un cop fets els passos i com es mostra a la imatge veurem que tindrem el **RustDesk** completament instal·lat, aquesta captura és la del tècnic, però en el client li sortirà el mateix. Haig de recordar que el tècnic pot usar el software de **RustDesk** per fer la pràctica.

![imatge5](/tasca_07/img/5.png)

Un cop instal·lat en ambdues màquines, com es mostra en aquesta caputra del client haurem de copiar o passar-nos el codi i la contrasenya al tècnic. El codi i la contrasenya és troben on les fletxes de la imatge.

![imatge6](/tasca_07/img/6.png)

Un cop en el entorn del client hàguim posat les credencials del client li farem clic al botó: **Conectar**.

![imatge7](/tasca_07/img/7.png)
![imatge8](/tasca_07/img/8.png)
![imatge9](/tasca_07/img/9.png)
![imatge10](/tasca_07/img/10.png)
![imatge11](/tasca_07/img/11.png)
![imatge12](/tasca_07/img/12.png)

## 💥 5. Conclusió de la tasca:

Jo crec que RustDesk és una molt bona opció per a EverPia per oferir assistència remota. Tot i que només he fet servir aquesta eina, m’ha semblat fàcil d’utilitzar tant per al tècnic com per a l’usuari final, compatible amb diferents sistemes operatius i prou segura per a tasques de Helpdesk. A més, el fet de ser de codi obert i no requerir costos elevats la fa especialment adequada per al suport remot ràpid i eficient.

---
# Gràcies per la vostra atenció
- [Tornar enrere](./.)
