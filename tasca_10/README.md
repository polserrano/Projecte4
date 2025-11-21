# 🖨️ Introducció a la tasca: Servidor d’Impressió Centralitzat amb CUPS

Molt bé, equip! 👋  

A **EverPia**, busquem optimitzar els recursos dels nostres clients, reduir costos i simplificar la gestió. Un dels punts més problemàtics és la **gestió d’impressores**: drivers incompatibles, tòner descontrolat i confusió sobre a quina impressora enviar les feines.  
La solució professional és un **Servidor d’Impressió Centralitzat**.

## 🏢 Cas client: DevOptimize Solutions
- Departaments amb **clients Linux (Zorin OS)** i **servidors Ubuntu Server**  
- Necessitat: centralitzar la impressió en tots els departaments  
- Requisit: demostració mitjançant una **Prova de Concepte (PoC)** abans de comprar hardware de xarxa costós

## 🎯 Objectiu de la PoC
Simular una impressora de xarxa utilitzant **cups-pdf**, que genera els documents en PDF en lloc de paper.  
El vostre objectiu és demostrar que un client pot enviar una feina d’impressió al servidor i comprovar que el PDF es genera correctament.

## 🛠️ Escenari de treball
- **Màquina 1 (Servidor)**: Ubuntu Server amb interfície NAT + Host-Only  
- **Màquina 2 (Client)**: Zorin OS Desktop amb mateixa configuració de xarxa

## ✅ Passos de la PoC
1. Instal·lació de **CUPS** al servidor  
2. Instal·lació de la **impressora virtual cups-pdf**  
3. Configuració de l’administració de CUPS i habilitar l’escolta per totes les interfícies  
4. Compartir la impressora des del **frontal web de CUPS**  
5. Afegir la impressora al client Zorin  
6. Realitzar proves d’impressió amb diversos documents  
7. Verificar al servidor que els PDFs s’han generat correctament  

Documenteu les **comandes utilitzades** i afegiu **captures de pantalla** per demostrar el correcte funcionament.

---

🔗 **Enllaços útils:**
- 📄 [Material propi: UD5. AA1. CUPS (Moodle)](https://moodle)  
