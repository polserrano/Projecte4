# 🌐 T06: ACCÉS REMOT

- **Autor:** Pol Serrano Aromí
- **Data:** 11/12/2025


## 📖 1. Índex:

- **1/ Índex**
- **2/ Introducció a la tasca**
- **3/ Tasca accés remot**
- **4/ Connexió remota de Zorin OS > Windows**
- **5/ Connexió remota de Windows > Zorin OS**
- **6/ Conclusió**

## 💥 2. Introducció a la tasca:

En aquesta activitat es treballarà la configuració i utilització de connexions d’escriptori remot entre dos sistemes operatius: Windows i Linux (amb entorn d’escriptori Gnome, com ara Zorin OS o Ubuntu). L’objectiu principal és comprendre i aplicar els mecanismes que permeten l’accés remot a una màquina, així com garantir que ambdues estacions de treball poden comunicar-se correctament dins d’una mateixa xarxa.

Per tal d’assolir aquests objectius, primer es verificarà que tots dos equips disposen de connectivitat. A continuació, es documentarà el procés de configuració necessari tant en Windows com en Linux perquè cada màquina pugui acceptar connexions remotes de manera segura. Finalment, es realitzarà la connexió d’un equip a l’altre i es comprovarà el correcte funcionament del servei d’escriptori remot.

## 💻 3. Tasca accés remot:

Primer de tot haurem de instal·lar i configurar les màquines, tant la de **Windows** com la de **Zorin**, el punt important és que haurem de posar 2 adaptadors a les dues màquines, **NAT** (perquè tinguin connexió) i **Amfitrió** (perquè es puguin veure entre si).

![imatge1](/tasca_06/img/1.png)
![imatge2](/tasca_06/img/2.png)

## 🔗 4. Connexió remota de Zorin OS > Windows:

Seguidament un cop tinguem les dues màquines farem un:

```bash
sudo apt upgrade && apt upgrade -y
```

Despres anirem a la configuració de el nostre Windows: **Sistema > Escritorio Remoto** i activarem la primera opció com es pot mostrar a la imatge, un cop activada la opció veurem el nom del nostre PC ja que ens servirà per fer la configuració

![imatge3](/tasca_06/img/3.png)

Un cop tinguem la opció activada, sabem quin es el nostre nom de el PC, entrarem a la tercera opció de la imatge anterior: **"Usuarios de escritorio remoto"**, aqui assignarem i li donarem permisos als usuaris amb els que podem fer la connexió. Llavors aquí afegirem el nom que tenim en la màquina del **Windows** i en la del **Zorin**.

![imatge4](/tasca_06/img/4.png)

Un cop haguim agregat el usuari en el Windows tindrem la part de Windows configurada (fins el moment), ara entrarem en el Zorin i obrirem l'aplicació **"Remmina"** que per defecte ja be instal·lat amb el Zorin. Bàsicament remmina és un client d'escriptori remot de Linux, el que estem fent és "simular" una cosa que ens podria passar a la nostra vida real, treballant remot amb un client.

Llavors un cop obreta l'aplicació, introdüirem en el buscador d'adalt com s'observa a la imatge, posarem el nom del **PC de Windows** i un .local al final, en el meu cas ha sigut:

```bash
pcpolserrano.local
```

Seguidament li donem al **Enter**

![imatge5](/tasca_06/img/5.png)

Seguidament ens donarà informació de un certificat entre les connexións de cada màquina, li donem a: **Yes** ja que si no l'accepten no podrem seguir la pràctica.

![imatge6](/tasca_06/img/6.png)

Ara ens apareixera un 'pop-up' amb les credencials RDP, on haurem de posar el usuari i contrasenya del PC de Windows. Un cop ho tinguem la autentificació feta, li donarem a: **"OK"**.

![imatge7](/tasca_06/img/7.png)

I si tots els passos els hem seguit tots correctament, la connexió remota sortirà bé i podrem veure podem veure i fer servir el ordenador amb el que estem fent la connexió. Podem veure en l'imatge, que posa: **"usuari_21"** vol dir que estem en el PC correcte, que la connexió està ben feta.

![imatge8](/tasca_06/img/8.png)

## 🔗 5. Connexió remota de Windows > Zorin OS:

Un cop haguim fet la connexió de Zorin a Windows, seguirem amb part dos que consisteix fer el mateix perà al revès. de **Windows > Zorin**

Per començar aquesta part, entrarem a **Configuració > Sistema > Activar opcions: 'Escriptori Compartit' i 'Control Remot'**. Sobretot has de saber que Zorin et posa una contrasenya predeterminada que són paraules random, jo recomano cambiarla per una vostre més senzilla però segura.

![imatge9](/tasca_06/img/9.png)

Aquesta imatge us la mostro, ja que en el Zorin, en la configuració com us e ensenyat abans, podrem configurar tant el **nom del usuari** com la **contrasenya** ja que com us he dit més endevant quan fem la connexió ens demanarà tant el usuari com la contrasenya.

![imatge11](/tasca_06/img/11.png)

Seguidament, un cop activades les opcions i cambiada la contrasenya, anirem al Windows, on haurem de buscar: **"Conexió a Exriptori Remot"**, aquí no haurem de tocar res ja que allò sen's posarà automàticament, li donarem a **"Connectar"**.

![imatge10](/tasca_06/img/10.png)

Seguidament ens demanarà les credencials de la conta de Windows, perquè pugui verificar que estem fent una connexió segura amb equips nostres o de client, no amb algú random.

![imatge13](/tasca_06/img/13.png)

Un 

![imatge14](/tasca_06/img/14.png)

a

![imatge15](/tasca_06/img/15.png)

## 💾 4. Conclusió de la tasca:

La realització d’aquesta activitat m’ha permès comprendre de manera pràctica el funcionament de les connexions d’escriptori remot entre sistemes operatius diferents, així com els requisits de configuració específics per a Windows i Linux. Considero que ha estat una tasca útil, ja que no només he après a habilitar i gestionar aquestes connexions, sinó també a identificar possibles problemes de xarxa i a assegurar una comunicació correcta entre màquines.

Personalment, opino que aquesta experiència és molt valuosa perquè reflecteix situacions reals d’entorns professionals, on sovint cal administrar equips remotament i combinar diferents plataformes. Haver pogut provar el procés pas a pas m’ha ajudat a entendre millor la importància de la configuració adequada, la seguretat i la verificació contínua del sistema. En general, considero que l’activitat ha estat enriquidora i m’ha aportat coneixements pràctics que podré aplicar en futurs projectes tècnics.

---

# Gràcies per la vostra atenció
- [Tornar enrere](./.)
