# 🌍 DRP: Còpies de Seguretat

- **Autor:** Pol Serrano Aromí
- **Data:** 9/12/2025

## 💻 1. Introducció a la tasca:

A la tasca anterior heu dissenyat una política de còpies de seguretat pel nostre nou client "Muntatges i Serveis Tècnics SL". Ara toca passar a l’acció i portar a la pràctica l’estudi anterior. El client demana que s’elaborin unes guies tècniques amb proves de concepte per tal que el seu personal estigui qualificat per implantar el pla de còpies de seguretat.

## 📖 2. Índex:

1. Introducció a la tasca
2. Índex
3. Configuracions Prèvies
4. Còpia seguretat equips clients Windows
5. Còpia seguretat servidor Linux
6. Conclusió de la tasca

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

## 4.4 Còpia de seg. a Drive.

Un cop seguit tots els passos anterior tindrem feta correctament la còpia de l'equip local de windows i s'anirà actualitzant cada hora, que es com li hem assignat. Ara, el següent pas de la pràctica, serà realitzar una còpia com hem fet abans, pero en canvi de l'equip, fer-ho del drive, per fer això agafarem un compte que tenim de google o podem agafar un que tenim però que no fem servir.

![imatge11_windows](/tasca_02/img/win12.png)
![imatge12_windows](/tasca_02/img/win13.png)
![imatge13_windows](/tasca_02/img/win14.png)
![imatge14_windows](/tasca_02/img/win15.png)
![imatge15_windows](/tasca_02/img/win16.png)
![imatge16_windows](/tasca_02/img/win17.png)
![imatge17_windows](/tasca_02/img/win18.png)
![imatge18_windows](/tasca_02/img/win19.png)
![imatge19_windows](/tasca_02/img/win20.png)
![imatge20_windows](/tasca_02/img/win21.png)
![imatge21_windows](/tasca_02/img/win22.png)
![imatge22_windows](/tasca_02/img/win23.png)

---

## 🐧 5. Còpia seg. servidor Linux:

![imatge2_ubuntu](/tasca_02/img/ubuntu2.png)
![imatge3_ubuntu](/tasca_02/img/ubuntu3.png)
![imatge4_ubuntu](/tasca_02/img/ubuntu4.png)
![imatge5_ubuntu](/tasca_02/img/ubuntu5.png)
![imatge6_ubuntu](/tasca_02/img/ubuntu6.png)
![imatge7_ubuntu](/tasca_02/img/ubuntu7.png)
![imatge8_ubuntu](/tasca_02/img/ubuntu8.png)
![imatge9_ubuntu](/tasca_02/img/ubuntu9.png)
![imatge10_ubuntu](/tasca_02/img/ubuntu10.png)
![imatge11_ubuntu](/tasca_02/img/ubuntu11.png)
![imatge12_ubuntu](/tasca_02/img/ubuntu12.png)
![imatge13_ubuntu](/tasca_02/img/ubuntu13.png)
![imatge14_ubuntu](/tasca_02/img/ubuntu14.png)
![imatge15_ubuntu](/tasca_02/img/ubuntu15.png)
![imatge16_ubuntu](/tasca_02/img/ubuntu16.png)
![imatge17_ubuntu](/tasca_02/img/ubuntu17.png)
![imatge18_ubuntu](/tasca_02/img/ubuntu18.png)
![imatge19_ubuntu](/tasca_02/img/ubuntu19.png)
![imatge20_ubuntu](/tasca_02/img/ubuntu20.png)
![imatge21_ubuntu](/tasca_02/img/ubuntu21.png)
![imatge22_ubuntu](/tasca_02/img/ubuntu22.png)
![imatge23_ubuntu](/tasca_02/img/ubuntu23.png)
![imatge24_ubuntu](/tasca_02/img/ubuntu24.png)
![imatge25_ubuntu](/tasca_02/img/ubuntu25.png)

---
## 🎯 6. Conclusió tasca:


---
# Gràcies per la vostra atenció!
- [Tornar enrere](./.)
