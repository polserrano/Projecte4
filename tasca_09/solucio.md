# 📁 Servidor Fitxers de Linux NFS

- **Autor:** Pol Serrano Aromí
- **Data:** 9/12/2025

---
## 💬 1. Introducció a la tasca:

En aquest projecte abordarem una de les necessitats més habituals dels nostres clients: la centralització de dades en entorns Linux. A partir del cas real de DevOptimize Solutions, una startup amb dificultats per gestionar el seu codi i els seus actius digitals, preparem una demostració pràctica d’un servidor NFSv3 i un client Linux. L’objectiu és mostrar com aquesta solució pot unificar la gestió de fitxers, millorar l’eficiència del treball en equip i evidenciar tant els avantatges com les limitacions d’un entorn sense autenticació centralitzada.

## 📖 2. Índex:

**1/ Introducció a la tasca**

**2/ Índex**

**3/ Fase 1: Preparació de l'entorn**

**4/ Fase 2: Preparació del servidor**

**5/ Fase 3: L'Exportació d'Administració**

**6/ Fase 4: L'Exportació de Desenvolupament**

**7/ Fase 5: Muntatge Automàtic amb /etc/fstab**

**8/ Conclusió**


---

## 🌍 3. Fase 1: Preparació de l'entorn

Primer de tot crearem i iniciarem les dues màquines, tant la del **server** com **client**, hi posarem que hi haguin a les dues màquines, 2 adaptadors, x1 de **NAT** (per tenir xarxa) i x1 de **Amfitrió** (perquè es veguin entre si).

![imatge](/tasca_09/img/1.png)
![imatge](/tasca_09/img/2.png)

Actualitzarem els paquets que solen estar desactualitzats just cuan iniciem les màquines amb la comanda:

```bash
sudo apt update && apt upgrade -y
```

Això ho realitzarem amb les dues màquines, tant el servidor com el client.

![imatge](/tasca_09/img/3.png)

Verfiquem que el segon adaptador en les dues màquines que està activat i donant-nos ip. Si no ens esta donant adaptador, hauriem de entrar a:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

Y posarem en el **enp0s8** true.

![imatge](/tasca_09/img/4.png)
![imatge](/tasca_09/img/5.png)

Seguidament fem un ping:

- Del servidor --> client
- Del client --> servidor

Per comprovar que ambudes màquines es veuen entre sí, si no es veuen no podrem seguir la pràctica.

![imatge](/tasca_09/img/6.png)
![imatge](/tasca_09/img/7.png)

---
## 📡 4. Fase 2: Preparació del servidor

Seguidament continuarem amb la creació de les carpetes y assginarem els permisos pertinents, com podem veure estem creant la carpeta: **dev_projectes** i **admin_tools** i assignarem els permisos 777, que es tradueixen en:

**7 per al propietari** → lectura, escriptura i execució
**7 per al grup** → lectura, escriptura i execució
**7 per a altres (tots)** → lectura, escriptura i execució

![imatge](/tasca_09/img/8.png)
![imatge](/tasca_09/img/9.png)
![imatge](/tasca_09/img/10.png)

Ara crearem els dos grups amb un id, amb la comanda:

```bash
sudo groupadd -g id nom_grup
```

![imatge](/tasca_09/img/11.png)

seguidament crearem els usuaris, on com abans, assignarem un id per a cada un i els posarem dins la carpeta. Comanda:

```bash
sudo useradd -m -s id nom_carpeta nom_usuari
```

![imatge](/tasca_09/img/12.png)
![imatge](/tasca_09/img/13.png)

Seguidament un cop tinguem creat els usuaris i grups i assignar-los a id, instal·larem el servei **nfs** al servidor amb la comanda:

```bash
sudo apt intall nfs-kernel-server
```

![imatge](/tasca_09/img/14.png)

I ara, un cop el tinguem instal·lat l'iniciarem:

```bash
systemctl start nfs-kernel-server
```

![imatge](/tasca_09/img/15.png)

Seguidament entrarem al arxiu:

```bash
sudo nano /etc/exports
```

Aqui afegirem les dues següents liníes, per poder habilitar les carpetes i poguer-les exportales.

![imatge](/tasca_09/img/17.png)

Ara, amb la comanda:

```bash
sudo exportfs -u
```

Podrem comprovar si les carpetes exportades en l'arxiu del pas enterior estan correctament configurats i exportats. Com podeu veure surten les dues carpetes, les que hem introduit abans.

![imatge](/tasca_09/img/16.png)

Abans de anar cap al zorin en l'arxiu de: 

```bash
sudo nano /etc/exports
```

Podrem afegir al final de les dues línies posades abans: **"no_root_squash"**, bàsicament és una opció de NFS que serveix per no limitar els privilegis de l’usuari root del client. Un cop fet, ho guardarem i pasarem cap al client.

![imatge](/tasca_09/img/18.png)

Seguidament desmuntarem la carpeta admin_tools, amb la comanda:

```bash
sudo umount /mnt/admin_tools
```

I seguidament, muntarem un recurs NFS que està al servidor remot al nostre propi sistema local, ho farem amb:

```bash
sudo mount -t nfs 192.168.56.109:/srv/nfs/admin_tools /mnt/admin_tools
```

![imatge](/tasca_09/img/19.png)

Seguidament farem un **"ls"** per veure si la carpeta admin_tools està copiada correctament i està l'arxiu comprovant que verifica que està copiada.

```bash
ls -l /mnt/admin_tools/test_no_root_squash.txt
```
![imatge](/tasca_09/img/20.png)

Seguidament i últim pas de aquesta part, instal·larem el NFS en la màquina del client. Per fer-ho ho farem mitjançant la comanda:

```bash
sudo apt install nfs-common
```

![imatge](/tasca_09/img/21.png)

---
## 🗄️ 5. Fase 3: L'Exportació d'Administració

Ara pasarem a la part de la exportació dels usuaris d'adminstració, llavors amb la comanda: 

```bash
showmount -e 192.168.56.109
```

El que estem fent es consultar el servidor NFS i mostra la llista de directoris exportats i qui hi pot accedir, que serien **admin_tools** i **dev_projects**.

![imatge](/tasca_09/img/22.png)

Seguidament amb la comanda:

```bash
mount | grep admin_tools
```

El que faig és consultar tots els sistemes de fitxers que tinc muntats al client i filtrar només aquells que contenen admin_tools.

![imatge](/tasca_09/img/24.png)

I en aquesta part final comprovo que els arxius creats abans estàn correctament exportats en la seva carpeta pertinent.

![imatge](/tasca_09/img/25.png)
![imatge](/tasca_09/img/26.png)

---
## ⚙️ 6. Fase 4: L'Exportació de Desenvolupament

Seguidament començarem la part de exportació de desenvolupament, on començarem entrant al arxiu:

```bash
sudo nano /etc/exports
```

Afegirem les comandes, en el meu cas:

```bash
/srv/nfs/admin_tools 192.168.56.0/24(rw,sync,no_subtree_check,no_root_squash)
/srv/nfs/admin_tools 192.168.56.100(ro,sync,no_subtree_check,no_root_squash)
```

Les afegim ja que serveixen per definir permisos més específics sobre el mateix directori NFS.

![imatge](/tasca_09/img/27.png)

Simplement aquí comprovem que estan correctament exportades, que no hi ha ningún error.

![imatge](/tasca_09/img/28.png)

Ara entrarem o iniciarem sessió en el perfil de: **dev01** i crearem un arxiu i veiem que ens el deixa crear sense cap tipus de problema.

![imatge](/tasca_09/img/30.png)

Pasarem al arxiu de configuració de xarxa:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

i posarem que la nostra ip acabi amb **.100** ja que si recordem abans, hem introduit en el arxiu: **etc/exports** haviem introduit dues noves exportacions, una ip que acabava en **.0** (xarxa) i una altre **.100** (màquina) i com els hi haviem posat només permisos de **lectura** en la màquina comprovarem si els canvis que hem fet están correctament, es a dir que si intentem crear un arxiu un cop configurada la xarxa no ens hauria de deixar.

![imatge](/tasca_09/img/31.png)

Comprovem amb un:

```bash
ip a
```

Que la ip cambiada està correctament.

![imatge](/tasca_09/img/32.png)

I ara com hem dit, iniciarem sessió a: **dev01** i com podrem veure si intentem crear un arxiu sortirà que tindrem permisos denegats (ja que només tenim de lectura), això ens confirma que està correctament introduida la comanda.

![imatge](/tasca_09/img/36.png)

---
## 🔗 7. Fase 5: Muntatge Automàtic amb /etc/fstab

![imatge](/tasca_09/img/37.png)

---
## 🔥 8. Conclusió de la tasca

Després de completar aquesta demostració, considero que la implantació d’un servidor NFSv3 és una solució molt adequada per a DevOptimize Solutions, ja que permet centralitzar els fitxers i reduir els conflictes de versions que afectaven el seu flux de treball. Tot i així, penso que la manca d’un sistema d’autenticació centralitzada limita el potencial de la infraestructura i pot generar riscos de seguretat o problemes de gestió a llarg termini. Malgrat això, la configuració actual és un bon primer pas que els permet millorar l’organització interna i estableix una base sòlida per a futures ampliacions.

---
# Gràcies per la vostra atenció!
- [Tornar enrere](./.)
