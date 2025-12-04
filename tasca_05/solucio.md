# 🌐 **T05: Accés Remot via SSH**  
- **Autor:** Pol Serrano Aromí
- **Data:** 4/12/2025
---

## 🪄 1. **Introducció a la tasca:**

La tasca consisteix a crear una Prova de Concepte (PoC) que servirà com a base per a la futura documentació interna de la consultora sobre gestió remota segura. Atès que els servidors dels clients i els interns estan en CPDs o al núvol, l’eina principal per administrar-los és SSH, l’estàndard segur per gestionar sistemes, especialment Linux.  
L’objectiu és elaborar una guia impecable destinada als futurs becaris perquè puguin connectar-se de manera segura als sistemes de l’empresa sense necessitat d’una formació inicial extensa.

S’ha de documentar el procés de connexió SSH utilitzant màquines virtuals, tant des de clients Linux com des de clients Windows, seguint els punts indicats a la pràctica SSH. En definitiva, aquesta guia permetrà que qualsevol nou tècnic pugui ser operatiu des del primer dia.

---

## 🗒️ 2. **Índex:**

**1\. Introducció a la tasca**

**2\. Índex**

**3\. Configuracions prèvies (server)**

**4\. instalación del ssh**

**5\. Configuracions prèvies (client)**

**6\. Primeres connexions**

**7\. Configuracions SSH**

**8\. Túnel amb redirecció dinàmica**

**9\. Túnel amb redirecció dinàmica (WireShark)**

**10\. Log in amb SSH Keys**

**11\. Servidor OpenSSH

**12\. Conclusió de la tasca**

---

## 🖥️ 3. **Configuracions prèvies (server):**

Primer de tot configurarem la vm del servidor, on hi posarem **2** adaptadors: un **NAT** i l’altre **amfitrió** perquè es pugui fer la connexió via ssh amb el client com diu la pràctica.

![imatge](/tasca_05/img/imatge_1.png)

Seguidament, entrarem amb arxiu de configuració de xarxa:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

Per habilitar el **2n adaptador**, sinó el habilitem no funcionara el 2n adaptador, és com si no el tinguéssim activat.

![imatge](/tasca_05/img/imatge_2.png)

Un cop habilitat el segon adaptador, introduirem un 

```bash
sudo netplan apply
```

I revisarem si l’hem configurat correctament, i així és, si ens dona una ip voldrà dir que està correctament configurat i funcionant.

![imatge](/tasca_05/img/imatge_3.png)

Seguidament farem uns updates i upgrades: 

```bash
sudo apt update && apt upgrade -y
```

En els paquets que es troben desactualitzats en el sistema.

![imatge](/tasca_05/img/imatge_4.png)
![imatge](/tasca_05/img/imatge_5.png)

---

## 📌 4. **instalación del ssh**

Un cop haguim configurat l’equip i actualitzat, instal·larem el servei **ssh**.

![imatge](/tasca_05/img/imatge_6.png)

Un cop instal·lat, comprovem el seu estat si està activat amb un status:

```bash
systemctl status ssh
```

![imatge](/tasca_05/img/imatge_7.png)

## 🖥️ 5. **Configuracions prèvies (client)**

Un tinguem al servidor, tot actualitzat, els adaptadors **habilitats** i configurats i l’ssh **instal·lat**, pasarem a crear una altre vm simulada a un client, en aquests cas ho farem amb windows 11. També recordem, posar els adaptador igual que el server. **1r adaptador nat i el segon amfitrió**.

![imatge](/tasca_05/img/imatge_8.png)


## 🧲 6. **Primeres connexions**

El següent pas, obrirem **PowerShell** i intentarem connectar-nos amb el servidor via **ssh**. En la primera connexió com no ens reconeix la clau pública ens demana que li confirmem l’autenticitat.

![imatge](/tasca_05/img/imatge_9.png)

Un cop confirmada l’autenticitat i posada la contrasenya del servidor **estarem dins**.

![imatge](/tasca_05/img/imatge_10.png)

## 📟 7.  **Configuracions SSH:**

Seguidament entrarem amb arxiu que es troba a: 

```bash
sudo nano /etc/ssh/sshd_config
```

On aqui podem permetre o no connexions de root canviar el port de connexió, en el meu cas com diu la tasca he tocat només el permís de iniciar sessió com a root.

![imatge](/tasca_05/img/imatge_11.png)

Després com ens diu la tasca, **crearem un nou usuari** amb el nom de **usuari2**.

![imatge](/tasca_05/img/imatge_12.png)

Seguidament, configurarem perquè l’usuari **server21** pugui entrar a ssh com a usuari, pero **usuari2** tingui el permís denegat, més endavant veurem com els canvis s'apliquen correctament.

![imatge](/tasca_05/img/imatge_13.png)

Farem un: 

```bash
sudo systemctl restart shh
```

també un: 

```bash
sudo systemctl reload ssh
```

Per aplicar els canvis correctament, jo recomano per si algun cas reiniciar les dues màquines, tant client com server, per acabar d’assegurar que els canvis s’han desat.

![imatge](/tasca_05/img/imatge_14.png)

Un cop reiniciat el servei, i reiniciades les màquines intentarem connectar-nos amb els dos usuaris: **server21** i **usuari2**, i un cop fetes les comprovacions veiem que el que ens diu l’enunciat s’ha complert correctament, ja que amb usuari2 ens denega el permís (no podem entrar) i amb server21 sí que ens deixa gràcies a afegir-lo com a usuari vàlid en el arxiu de configuració d’ssh.

![imatge](/tasca_05/img/imatge_15.png) 
![imatge](/tasca_05/img/imatge_16.png)

## 🕳️ 8. **Túnel amb redirecció dinàmica:**

Ara configurarem un **túnel amb redirecció dinàmica** que utilitzarem per redirigir el trànsit.

![imatge](/tasca_05/img/imatge_17.png)

Un cop posada la comanda, haurem de fer-ho manualment desde windows, entrarem a: **Panel de control > redes e internet > Propiedades de internet > Conexiones > Configuración de LAN > (deshabilitar l’opció ‘Detectar la configuración automáticamente’) Opciones avançades****. 

![imatge](/tasca_05/img/imatge_18.png)

## 📡 9. **Túnel amb redirecció dinàmica (WireShark):**

Primer de tot entrarem a: [wireshark.org](http://wireshark.org), instal·larem el wireshark.

![imatge](/tasca_05/img/imatge_19.png)

I comprovarem amb el wireshark que tot el trànsit que generem surt via ****SSH cap al servidor SSH****. En aquests cas he escollit [amazon.es](http://amazon.es) per fer les proves.

![imatge](/tasca_05/img/imatge_20.png)

## ⌨️ 10. **Log in amb SSH Keys:**

En l’últim pas de la pràctica haurem de intentar iniciar sessió remota (ssh) sense utilitzar el password de l’equip que ens volem connectar. Això ens pot ajudar a **l’automatització de gestió de màquines remotes**.

Per fer-ho generarem una ****key pública****.

![imatge](/tasca_05/img/imatge_21.png)

Ara, introduirem la següen comanda, que intenta copiar la clau pública SSH **(id_rsa.pub)** des de la màquina local al servidor. 

![imatge](/tasca_05/img/imatge_22.png)

Seguidament veurem amb un **cat**, si la clau que hem copiat abans de la màquina local al servidor s’ha copiat correctament, i així és.

![imatge](/tasca_05/img/imatge_23.png)

Finalment veiem que si intentem fer un ssh amb el servidor desde el client, no ens demanara ningún password, sino que se'ns iniciarà sessió automàticament.

![imatge](/tasca_05/img/imatge_24.png)

----
## 🖱️ 11. Servidor OpenSSH

Seguidament habilitarem el servidor **OpenSSH**, que per defecte be desactivat. Per això haurem de anar desde el windows a **Aplicaciones y caracteristicas > características opcionales > Agregar una caracteristica > Servidor OpenSSH**

![imatge](/tasca_05/img/imatge_25.png)

Ara habilitarem amb el servei amb la comanda:

```bash
Start-Service sshd
```

![imatge](/tasca_05/img/imatge_26.png)

I ara indiquem que el servei arranqui automaticament amb la comanda:

```bash
Set-Service -Name sshd -StartupType 'Automatic'
```

![imatge](/tasca_05/img/imatge_27.png)

Ara introduïm aquesta comanda per deshabilitar el firewall:

```bash
New-NetFirewallRule -Name "OpenSSH-Server" -DisplayName "OpenSSH Server (sshd)" -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

I seguidament introduïrem la comanda:

```bash
Restart-Service sshd
```

Per aplicar tots el canviis anteriorment fets. Despres iniciarem un ssh amb el servidor des d'un altre equip, ja sigui Linux o Windows.

![imatge](/tasca_05/img/imatge_28.png)

Finalment, un cop validat, tenim una sessió remota.

![imatge](/tasca_05/img/imatge_28.png)

----
## 🔥 12. Conclusió de la tasca:

En aquesta pràctica s’ha configurat un entorn de connexió remota segur entre un servidor Linux i un client Windows mitjançant SSH. S’han configurat correctament els adaptadors de xarxa, instal·lat i verificat el servei SSH, i aplicat restriccions d’accés per usuari. També s’ha creat un túnel SSH amb redirecció dinàmica i s’ha comprovat el seu funcionament amb Wireshark. Finalment, s’ha implementat l’autenticació per claus SSH, permetent iniciar sessió sense contrasenya. En conjunt, la pràctica ha servit per comprendre i aplicar els elements essencials de la gestió de connexions remotes segures.

---
# Gràcies per la vostra atenció!
- [Tornar Enrere](./.)

