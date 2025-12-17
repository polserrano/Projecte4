# T10: Servidor impressió Linux. CUPS

- **Autor:** Pol Serrano Aromí
- **Data:** 16/12/2025

 ## 1. Introducció a la tasca:

En aquesta tasca es planteja el disseny i la proposta d’implementació d’un Servidor d’Impressió Centralitzat per a l’empresa DevOptimize Solutions, amb l’objectiu de posar fi a la complexitat actual en la gestió d’impressores. L’entorn de l’empresa presenta una combinació de clients Linux (Zorin OS) i servidors Ubuntu Server, fet que requereix una solució robusta, compatible i fàcilment administrable des d’un punt central.

A través d’aquesta proposta, EverPia pretén optimitzar els recursos tecnològics de l’organització, reduir costos operatius (especialment en consumibles com el tòner), simplificar la gestió de drivers i millorar l’experiència dels usuaris finals. La centralització de la impressió permetrà un millor control, més seguretat i una administració més eficient, alineada amb les bones pràctiques professionals en entorns corporatius moderns.

 ## 2. Índex:

**1. Introducció a la tasca:**

**2. Índex:**

**3. Pràctica:**

 ## 3. Pràctica:

Començarem primer de tot creant les dues màquines, en el meu cas en el client he fet un **ubuntu server** i en el client un **Zorin** i finalment com diu la tasca, en ambdues màquines posarem només 1 adaptador de **Xarxa NAT**

![imatge1](/tasca_10/img/1.png)
![imatge2](/tasca_10/img/2.png)

Farem una actualització dels paquets que es troben desactualitzats o no instal·lats:

```bash
sudo apt upgrade && apt update -y
```

![imatge3](/tasca_10/img/3.png)

Ara seguidament instal·larem el servei amb el que realitzarem la pràctica, cups:

```bash
sudo apt install cupds-pdf -y
```

![imatge4](/tasca_10/img/4.png)

Seguidament instal·larem el cups pero la versió per PDF, ho instal·larem amb la comanda:

```bash
sudo apt install cupds-pdf -y
```

![imatge5](/tasca_10/img/5.png)

Seguidament un cop instal·lat el servei, entrarem al arxiu de configuració:

```bash
sudo nano /etc/cups/cupsd.conf
```

Aqui modificarem diverses línies com: el port on volem obrir el cups, veure les impresores compratides en una xarxa local, el accés al servidor i finalment el accés a les pàgines del administració:

![imatge6](/tasca_10/img/6.png)
![imatge7](/tasca_10/img/7.png)

Seguidament reiniciem el servei perque s'apliquin tots el canvis i veiem el estat del servei per veure si esta malament configurat.

```bash
sudo systemctl restart cups && systemctl status cups
```

![imatge8](/tasca_10/img/8.png)

Continuarem fent un:

```bash
ip a
```

Per veure la ip la que posarem al buscador del client per entrar a la configuració del nostre cups.

![imatge9](/tasca_10/img/9.png)

Un cop dins ens apareixarà aquests menú, seguidament anirem a: **Administarion**

![imatge10](/tasca_10/img/10.png)

Ens demanarà les credencials del servidor, això ho fa, ja que a la hora de entrar en la pestanya de **"Administarion"** estarem modificant i editant paràmetres importants i d'administrador, per això cups vol confirmar que som nosaltres.

![imatge11](/tasca_10/img/11.png)

El primer cop en iniciar sessió en la pestanya **"Administarion"** ens dira que necessitem donar-li el permís al usuaris per accederir a la pestanya **"Administarion"**.

![imatge12](/tasca_10/img/12.png)

Per habilitar l'accés del pas anterior, anirem al servidor i farem que l'usuari: **"server21"** tingui accés de superusuari. Ho farem amb la comanda:

```bash
sudo usermod -aG lpadmin server21
```

![imatge13](/tasca_10/img/13.png)

Un cop hàguim posat el usuari del nostre servidor com a un superusuari, tornarem a iniciar la sessió dins del cups en l'aprtat de **"Administarion"** i veurem que tenim accés. Un cop dins crearem la impresora.

![imatge14](/tasca_10/img/14.png)

Sobretot hi posarem que sigui una **impresora local**.

![imatge15](/tasca_10/img/15.png)

Seguidament posarem la localització, que serà el nom del nostre servidor, i habilitarem el boto de compartir aquesta impresora (perquè els arxius que imprimim es copin al servidor).

![imatge16](/tasca_10/img/16.png)

Seguidament ens dirà de quina marca volem crear la impresora, li direm que volem del tipus **Generic** i seguidament li donarem a **Add printer** per activar la impresora.

![imatge17](/tasca_10/img/17.png)
![imatge18](/tasca_10/img/18.png)
![imatge19](/tasca_10/img/19.png)
![imatge20](/tasca_10/img/20.png)
![imatge21](/tasca_10/img/21.png)
![imatge22](/tasca_10/img/22.png)
![imatge22](/tasca_10/img/23.png)

---
# Gràcies per la vostra atenció!
- [Tornar enrere](./.)
