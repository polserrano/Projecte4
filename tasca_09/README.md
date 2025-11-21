# 📁 Introducció a la tasca: Centralització de dades amb NFS

Molt bé, equip de consultors júniors! 👋  

En aquesta activitat ens enfrontem a un **requisit molt habitual dels clients Linux**: la **centralització de dades** per millorar l’eficiència i evitar conflictes de versions.

## 🏢 Cas client: DevOptimize Solutions
- Startup de desenvolupament de programari, **tot Linux**  
- Problema crític: codi font i documents descontrolats, amb còpies locals disperses  
- Objectiu: **implementar un servidor de fitxers centralitzat** utilitzant **NFS (Network File System)**  
- Limitació: sense autenticació centralitzada, com ha demanat el client

## 🎯 Objectius de la prova
Crear una **demostració funcional** que mostri:

1. Servidor NFS (NFSv3) operatiu  
2. Client Linux que consumeixi els recursos compartits  
3. Creació d’usuaris i grups per simular l’entorn del client  
4. Control d’accés mitjançant:
   - Opcions d’exportació (`/etc/exports`)  
   - Permisos del sistema de fitxers (`chmod`, `chown`)  

L’objectiu és mostrar com quedarà la solució, així com les seves limitacions en l’entorn actual del client.

---

🔗 **Enllaços útils:**
- 📄 [Descripció completa de la tasca al repositori GitHub](https://github.com/SMX2n/Projecte04-NFS)  
