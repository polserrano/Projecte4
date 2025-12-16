# 🌍 DRP: Còpies de Seguretat

- **Autor:** Pol Serrano Aromí
- **Data:** 9/12/2025

## 💻 1. Introducció a la tasca:

A la tasca anterior heu dissenyat una política de còpies de seguretat pel nostre nou client "Muntatges i Serveis Tècnics SL". Ara toca passar a l’acció i portar a la pràctica l’estudi anterior. El client demana que s’elaborin unes guies tècniques amb proves de concepte per tal que el seu personal estigui qualificat per implantar el pla de còpies de seguretat.

## 📖 2. Índex:

**1. Introducció a la tasca**

**2. Índex**

**3. Configuracions Prèvies**

**4. Còpia seguretat equips clients Windows**

**5. Còpia seguretat servidor Linux**

**6. Conclusió de la tasca**

## 🌐 3. Configuracions Prèvies:

Començarem la pràctica creant les dues màquines, una de Windows y l'altre linux, en el meu cas he triat ubuntu. Hi posarem com diu l'enunciat un altre disc de **10GB** per guardar allà les còpies locals.

![imatge1_windows](/tasca_02/img/win1.png)
![imatge1_ubuntu](/tasca_02/img/ubuntu1.png)

---

## 🪟 4. Còpia seg. equips clients Windows:

Un cop haguem creat i iniciat les màquines, començarem amb la còpia de seguretat en l¡equip de **Windows**, quan iniciem l'equip, veurem que el disc no el reconeix, per això l'haurem de inicialitzar. farem un: **Ctrl+x > Administració de discos** i allà veurem que el disc antriorment posat desde el VirtualBox surt 'No assginat', llavors farem clic dret en el ratolí i l'icinialitzaren (li posarem particions).

![imatge2_windows](/tasca_02/img/win2.png)

En el cas nostre el formatarem amb format: **NTFS** i li posarem de nom **"Còpies"** perquè sen's fagui més fàcil a la hora de reconeixe el segon disc.

![imatge3_windows](/tasca_02/img/win3.png)

Un cop l'hàguim formatat, anirem al explorador de arxius i veurem que ara si que ens surt el segon disc.

![imatge4_windows](/tasca_02/img/win4.png)

Seguidament, el següent pas, és fer la instal·lació de l'eina **duplicati**, per això entrarem a: https://duplicati.com i farem l'instal·ació com un software normal; ens demanarà sistema operatiu i es fer 4 clics donant-li a següent.

![imatge5_windows](/tasca_02/img/win5.png)
![imatge_duplicati](/tasca_02/img/duplicati1.png)

Al iniciar l'aplicació per primer cop, ens demanarà que posem una **"Passphrase** això serveix per com diu a la imatge, si volem iniciar l'aplicació en un altre equip o localització que duplicati no coneix ens demanarà aquest "password" per confirmar que som nosaltres qui estem accedint.

![imatge6_windows](/tasca_02/img/win6.png)

Un cop instal·lada l'eina s'ens obrirà una pestanya en el nostre navegador predeterminat, com es mostra a la imatge. Podem veure que té una interficie molt bàsica i fàcil per la persona que l'està usant. Jo, en el meu cas, faré clic a **"Backups"** ja que com diu la pràctica haurem de fer una còpia de seguretat.

![imatge7_windows](/tasca_02/img/win7.png)

Un cop dins ens preguntarà quin nom li volem posar, tipus de encriptació, un password per guardar aquesta còpia ho més segur posible.

![imatge8_windows](/tasca_02/img/win8.png)

El següent pas és la destinació, on volem fer aquesta còpia, en el nostre cas triarem el **Disc C** ja que el **Disc de còpies** serà on desarem aquella còpia.

![imatge9_windows](/tasca_02/img/win9.png)

Seguidament, en l'apartat de: **Schedule"** allà és on podrem assginar una data o hora perquè és faguin les còpies automàticament. En aquests cas he assignat que la còpia és fagui cada hora de tots els dies de la setmana.

![imatge10_windows](/tasca_02/img/win10.png)

## 4.1 Còpia de seg. a Drive.

Un cop seguit tots els passos anterior tindrem feta correctament la còpia de l'equip local de windows i s'anirà actualitzant cada hora, que es com li hem assignat. Ara, el següent pas de la pràctica, serà realitzar una còpia com hem fet abans, pero en canvi de l'equip, fer-ho del drive, per fer això agafarem un compte que tenim de google o podem agafar un que tenim però que no fem servir.

Li posarem un nom al backup, una descripció (si volem), metode de encriptació i un password segur, jo no em vaig menjar molt el coco per posar una contrasenya segura ja que era per una pràctica, pero si es en un cas real, si que implementaria una contrasenya segura i difícil de descobrir.

![imatge11_windows](/tasca_02/img/win12.png)

El següent pas, serà com l'altre còpia, escollir on volem fer la còpia, gràcies a l'eina de **duplicati** ens deixà triar diferentes aplicación de cloud o no, i **Drive** sí que l'incorpora. Llavors escollirem Drive.

![imatge13_windows](/tasca_02/img/win13.png)

Iniciarem sessió en el compte de Google on volem fer la còpia del drive, ja que així duplicati obtindra el **"AuthID"** on és una serie de lletres que autoritzan que la teva conta tingui accés duplicati. I en l'apartat de

![imatge14_windows](/tasca_02/img/win14.png)
![imatge15_windows](/tasca_02/img/win15.png)

I posarem la data de cuan es volen fer les còpies i com diu la pràctica ho farem **1 cop cada dia de la setmana a les 18:00 hores**.

![imatge16_windows](/tasca_02/img/win17.png)

## 4.1 Comprovacions:

Un cop fetes les dues còpies, tant de Windows com de Drive, farem comprovacións per comprovar que funcionen correctament els backups, per fer-ho creare un arxiu **.txt** en l'apartat de documents.

![imatge17_windows](/tasca_02/img/win18.png)

Comprovem que s'ha creat correctament i l'eliminem.

![imatge18_windows](/tasca_02/img/win19.png)

Un cop eliminat entrarem al duplicati escollirem el backup local de windows creat anterioment, localitzarem els tres puntets que surten just al cantó de cada backup, i li farem clic a **"Restore"**.

![imatge19_windows](/tasca_02/img/win20.png)

Seguidament ens preguntarà quin arxius o directoris volem restaurar, nosaltres com hem creat l'arixu a **usuari_21 > documents** escollirem aquella localització.

![imatge20_windows](/tasca_02/img/win21.png)

Un cop fet això, veurem que els arixus o arxiu que tenim s'aniran restaurant, això depent molt dels arxius que tinguem, si estem recuperant molts arxius tardarà molt, pero en el nostra cas com era un **.txt** sense res dins, va tardar poc.

Veurem que l'arxius s'haurà restaurat correctament, i si anem al segon disc, això no vaig fer captura, però veurem que s'han creat logs o registres de duplicati.

![imatge21_windows](/tasca_02/img/win22.png)

I si fem tots els mateixos passos a drive, veurem que l'arxiu s'ha recuperat correcament i els logs s'han cargat correctament.

![imatge21_windows](/tasca_02/img/logs_drive.png)

---

## 🐧 5. Còpia seg. servidor Linux:

Començarem la segona pràctica fent la corresponent instal·lació del sistema operatiu, posteriorment, veurem quin nom ens a donat el Linux al nostre disc, en el meu cas el nom que m'ha donat a sigut:

```bash
/dev/sdb
```

Llavors un cop sapigut el disc de 10GB continuarem amb la pràctica.

![imatge2_ubuntu](/tasca_02/img/ubuntu2.png)

Seguidament farem la instal·lació del servei duplicity, amb la comanda:

```bash
sudo apt install xfsprogs duplicity -y
```

![imatge3_ubuntu](/tasca_02/img/ubuntu3.png)

Seguidament comprovem que el servei està instal·lat correctament amb un version:

```bash
duplicity --version
```

Podem veure que ens dona una versió instal·lada del servei (vol dir que està instal·lat).

![imatge4_ubuntu](/tasca_02/img/ubuntu4.png)

Seguidament amb la comanda que apareix en la imatge el que estem fent es formatar el disc, bàsicament el que farà serà:

- S'esborraran totes les dades existents a /dev/sdb.
- S'inicialitzarà l'estructura del sistema de fitxers XFS perquè el disc pugui ser muntat i usat.

![imatge5_ubuntu](/tasca_02/img/ubuntu5.png)

Ara crearem el repositori base:

```bash
sudo mkdir -p /media/backup
```

i un cop creat el muntarem en el disc dins de:

```bash
/media/backup
```

![imatge6_ubuntu](/tasca_02/img/ubuntu6.png)

I amb la següent comanda:

```bash
df | grep /media/backup
```

El que fem es mostrar l’ús d’espai del punt de muntatge, amb això podriem comprovar si cuan l'hem formatat abans a sortit bé o malament.

![imatge7_ubuntu](/tasca_02/img/ubuntu7.png)

Ara pasarem a la part de la creació dels usuaris com diu la tasca, amb la comanda:

```bash
sudo adduser usuari1
```

Per configuracions de Linux li podrem configurar numero de telefon, nom complert del usuari, numero de habitació i molt més, com la pràctica a realitzar és una cosa molt bàsica a configurar no he volgut argumentar ni configurar a fons cada usuari.

![imatge8_ubuntu](/tasca_02/img/ubuntu8.png)

Ara volia acabar de assegurar-me de que els usuaris s'havien creat correctament, i així és, es podria fer amb la comanda:

```
ls -l /home
```

![imatge9_ubuntu](/tasca_02/img/ubuntu9.png)

Seguidament crearem els arxius com demana la pràctica, recordeu de no crear-los amb **"touch"** ja que no podreu configurar-los una mida i amb **"truncate"** si que li podrem assignar la mida que volguem al arxiu o arxius que estiguem creant.

```bash
truncate -s 10M ~/fitxer1.bin
```

![imatge10_ubuntu](/tasca_02/img/ubuntu10.png)

Com abans he volgut assegurar-me de que els usuaris estaven ben creats, ara he volgut assegurar-me amb el arxius per això he fet un:

```
ls -l
```

![imatge11_ubuntu](/tasca_02/img/ubuntu11.png)

Ara he volgut crear una carpeta dins de la carpeta de backup perquè si a futur vull fer diferents backups, on allà creariem cada cop un carpeta per cada backup que volguessim fer.

Seguidament el que fem amb la comanda:

```bash
sudo -E duplicity /home file:///media/backup/backup_carpeta
```

El que fem és una còpia de seguretat incremental de **/home** guardant-la a **file:///media/backup/backup_carpeta**, executada amb permisos de superusuari

![imatge12_ubuntu](/tasca_02/img/ubuntu12.png)

Fem un **"ls"** a la carpeta on hem desat localment la còpia i podrem veure que hi han arxius de **duplicity**, això confirma que ha pogut fer part o tota la còpia i que ha dasat correctament la còpia on li hem dit.

![imatge13_ubuntu](/tasca_02/img/ubuntu13.png)

Seguidament amb la comanda tant llarga:

```bash
sudo duplicity collection-status file:///media/baclup/backup_carpeta
```

El que estem fent és mostra l’estat de la col·lecció de còpies de seguretat guardades a **/media/backup/backup_carpeta**, incloent quines còpies existeixen i els seus intervals, aquesta comanda ens serveix per veure si la còpia s'ha fet i podem veure que detecta que s'ha fet una còpia de **"full"**, bàsicament s'està referin a la de **/home** feta anteriorment.

![imatge14_ubuntu](/tasca_02/img/ubuntu14.png)

Seguidament toca la part de comprovar el funcionament d'aquests servei, per això eliminarem un arxiu per despres recuperar-lo, per eliminar el arxiu:

```bash
sudo rm ~/fitxer1.bin
```

I despres amb un **"ls"** comprovem que s'ha borrat,

![imatge15_ubuntu](/tasca_02/img/ubuntu15.png)

Ara un cop borrat l'arxiu tocarà la part de usar el servei, començarem amb la comanda:

```bash
sudo -E duplicity restore \
```

I seguidament jo afageixo tres comandes:

```bash
--path-to-restore home/usuari21/fitxer1.bin
```
Indica el camí dins la còpia de seguretat del fitxer que volem restaurar.

```bash
file:///media/backup/backup_carpeta
```
És la ubicació on es troba la còpia de seguretat (en aquest cas, una carpeta local).

```bash
/home/usuari21/fitxer1.bin
```
És el camí on es restaurarà el fitxer al sistema actual.

![imatge16_ubuntu](/tasca_02/img/ubuntu16.png)

Finalment fem un **"ls"** al home del usuari nostre i podrem veure que l'arxiu s'ha recuperat correctament, això si, com a root, ja que a la hora de posar les comandes li hem donat el permís **"sudo"**

![imatge17_ubuntu](/tasca_02/img/ubuntu17.png)

Seguidament crearem un arxiu per fer la còpia incremental, per això crearem un arxiu amb el **"truncate"** explicat anteriorment amb una mida de **4M**.

![imatge18_ubuntu](/tasca_02/img/ubuntu18.png)

Ara amb la comanda:

```bash
sudo -E duplicity incremental /home file:///media/backup/backup_carpeta
```

El que estem fent aquí és una còpia incremental del directori /home a la carpeta /media/backup/backup_carpeta amb permísos de root.

![imatge19_ubuntu](/tasca_02/img/ubuntu19.png)

Ara comprovem que la còpia incremental s'ha fet correctament i s'ha desat en el directori correctamen amb la comanda:

```bash
sudo duplicity collection-status file:///media/backup/backup_carpeta
```

![imatge20_ubuntu](/tasca_02/img/ubuntu20.png)

El següent pas serà desmontar el directori **/media/backup**:

```bash
sudo umount /media/backup
```

![imatge21_ubuntu](/tasca_02/img/ubuntu21.png)

Seguidament crearem un script amb el nom de: **"fullbackup.sh"** a **/usr/local/bin**. El que fa aquests script és una còpia de seguretat completa del directori **/home** amb cap a **/media/backup/homebackup**, registra el procés en un log i desmunta el disc.

![imatge22_ubuntu](/tasca_02/img/ubuntu22.png)

Quan exetucem el crontab o alguna comanda que relacioni el crontab ens apareixara un menú, per root. on haurem de seleccionar un editor.

![imatge23_ubuntu](/tasca_02/img/ubuntu23.png)

Seguidament entrarem a:

```bash
sudo nano /tmp/crontab.wap0Wu/crontab
```

Allà afegirem la línia:

```bash
0 23 * * 0 /usr/local/bin/fullbackup.sh
```

El que estem fent aquí és programant que el script **fullbackup.sh** faci una còpia de seguretat **cada diumenge a les 23:00** de manera automàtica.

![imatge24_ubuntu](/tasca_02/img/ubuntu24.png)
![imatge25_ubuntu](/tasca_02/img/ubuntu25.png)

---
## 🎯 6. Conclusió tasca:


---
# Gràcies per la vostra atenció!
- [Tornar enrere](./.)
