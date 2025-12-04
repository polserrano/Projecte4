# **T05: Accés Remot via SSH**  
- **Autor:** Pol Serrano Aromí
- **Data:** 4/12/2025
---

# 1. **Introducció:**

La tasca consisteix a crear una Prova de Concepte (PoC) que servirà com a base per a la futura documentació interna de la consultora sobre gestió remota segura. Atès que els servidors dels clients i els interns estan en CPDs o al núvol, l’eina principal per administrar-los és SSH, l’estàndard segur per gestionar sistemes, especialment Linux.  
L’objectiu és elaborar una guia impecable destinada als futurs becaris perquè puguin connectar-se de manera segura als sistemes de l’empresa sense necessitat d’una formació inicial extensa.

S’ha de documentar el procés de connexió SSH utilitzant màquines virtuals, tant des de clients Linux com des de clients Windows, seguint els punts indicats a la pràctica SSH. En definitiva, aquesta guia permetrà que qualsevol nou tècnic pugui ser operatiu des del primer dia.

---

# 2. **Índex:**

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

**11\. Conclusió de la tasca**

---

# 3. **Configuracions prèvies (server):**

Primer de tot configurarem la vm del servidor, on hi posarem 2 adaptadors: un NAT i l’altre amfitrió perquè es pugui fer la connexió via ssh amb el client com diu la pràctica.

![][image1]

Seguidament, entrarem amb arxiu de configuració de xarxa per habilitar el 2n adaptador, sinó el habilitem no funcionara el 2n adaptador, és com si no el tinguéssim activat.

![][image2]

Un cop habilitat el segon adaptador, introduirem un ‘sudo netplan apply’ i revisarem si l’hem configurat correctament, i així és, si ens dona una ip voldrà dir que està correctament configurat i funcionant.

![][image3]

Seguidament farem uns updates i upgrades en els paquets que es troben desactualitzats en el sistema.

![][image4]  
![][image5]

---

# 4. **instalación del ssh**

Un cop haguim configurat l’equip i actualitzat, instal·larem el servei ssh.

![][image6]

Un cop instal·lat, comprovem el seu estat si està activat.

![][image7]

# 5. **Configuracions prèvies (client)**

Un tinguem al servidor, tot actualitzat, els adaptadors habilitats i configurats i l’ssh instal·lat, pasarem a crear una altre vm simulada a un client, en aquests cas ho farem amb windows 11\. També recordem, posar els adaptador igual que el server. 1r adaptador nat i el segon amfitrió.

![][image8]

# 6. **Primeres connexions**

El següent pas, obrirem PowerShell i intentarem connectar-nos amb el servidor via ssh. En la primera connexió com no ens reconeix la clau pública ens demana que li confirmem l’autenticitat.

![][image9]

Un cop confirmada l’autenticitat i posada la contrasenya del servidor estarem dins.

![][image10]

# 7.  **Configuracions SSH:**

Seguidament entrarem amb arxiu que es troba a: /etc/ssh/sshd\_config. On aqui podem permetre o no connexions de root  canviar el port de connexió, en el meu cas com diu la tasca he tocat només el permís de iniciar sessió com a root.

![][image11]

Després com ens diu la tasca, crearem un nou usuari amb el nom de usuari2.

![][image12]

Seguidament, configurarem perquè l’usuari server21 pugui entrar a ssh com a usuari, pero usuari2 tingui el permís denegat, més endavant veurem com els canvis s'apliquen correctament.

![][image13]

Farem un: sudo systemctl restart shh, també un reload, per aplicar els canvis correctament, jo recomano per si algun cas reiniciar les dues màquines, tant client com server, per acabar d’assegurar que els canvis s’han desat.

![][image14]

Un cop reiniciat el servei, i reiniciades les màquines intentarem connectar-nos amb els dos usuaris: server21 i usuari2, i un cop fetes les comprovacions veiem que el que ens diu l’enunciat s’ha complert correctament, ja que amb usuari2 ens denega el permís (no podem entrar) i amb server21 sí que ens deixa gràcies a afegir-lo com a usuari vàlid en el arxiu de configuració d’ssh

![][image15]  
![][image16]

# 8. **Túnel amb redirecció dinàmica:**

Ara configurarem un túnel amb redirecció dinàmica que utilitzarem per redirigir el trànsit.

![][image17]  
Un cop posada la comanda, haurem de fer-ho manualment desde windows, entrarem a panel de control \> redes e internet \> Propiedades de internet \> Conexiones \> Configuración de LAN \> (deshabilitar l’opció ‘Detectar la configuración automáticamente’) Opciones avanzades. 

![][image18]

# 9. **Túnel amb redirecció dinàmica (WireShark):**

Primer de tot entrarem a: [wireshark.org](http://wireshark.org), instal·larem el wireshark.

![][image19]

I comprovarem amb el wireshark que tot el trànsit que generem surt via SSH cap al servidor SSH. En aquests cas he escollit [amazon.es](http://amazon.es) per fer les proves.

![][image20]

# 10. **Log in amb SSH Keys:**

En l’últim pas de la pràctica haurem de intentar iniciar sessió remota (ssh) sense utilitzar el password de l’equip que ens volem connectar. Això ens pot ajudar a l’automatització de gestió de màquines remotes.

Per fer-ho generarem una key pública.

![][image21]

Ara, introduirem la següen comanda, que intenta copiar la clau pública SSH (id\_rsa.pub) des de la màquina local al servidor. 

![][image22]

Seguidament veurem amb un cat, si la clau que hem copiat abans de la màquina local al servidor s’ha copiat correctament, i així és.

![][image23]

Finalment veiem que si intentem fer un ssh amb el servidor desde el client, no ens demanara ningún password, sino que se'ns iniciarà sessió automàticament.

![][image24]

