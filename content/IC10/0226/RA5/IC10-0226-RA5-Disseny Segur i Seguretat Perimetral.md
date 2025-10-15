---
{"publish":true,"title":"Disseny Segur i Seguretat Perimetral","tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
# Disseny Segur i Seguretat Perimetral
---
## Evolució d'una xarxa empresarial
---
### Inicis

Pocs equips + router

---
### Creixement de l'empresa

Molts equips + router. Necessitat de compartir recursos + facilitar la gestió.

- Servidors interns
- Impressores en xarxa
- Gestió centralitzada (AD)
---
### Presència a Internet

Necessitat de presencia a Internet i oferir serveis externs / telemàtics.

- Servidors Web / email / VPN, etc.
- Wifis.

**POSSIBILITAT HACKING!!!**

- Necessitat de segmentar la xarxa per nivells de confiança -> DMZ.
---
## Concepte de perímetre

Tot element o zona que estigui en contacte amb elements aliens a l'empresa.

---
### Elements típics del perímetre

- Enrutadors
- Tallafocs
- Punts d'accés wifi
- Servidors exposats a Internet.
- Xarxa convidats / reparació.
- Equips itinerants.
---
## Seguretat perimetral
---
### Regla d'or: Mínima superfície d'atac

- Minimitzar infraestructura
- Minimitzat serveis exposats
- Port knocking.
---
### Ofuscació

- Ocultació
- Des-informació
---
### Segmentació de xarxa

- Física
- Lògica
- Virtual
- SDN
---
### Control pas subxarxes

- Tallafocs
- NIDS
- Autenticació Usuaris
---
### Control dins subxarxes

- NIDS
- Honeypots
- SOC
- Theath hunting
---
## DMZ

- Xarxa dividida per confiança
- Serveix externs separats
---
### Estructura 1

[Estructura DMZ 1](https://www.ionos.es/digitalguide/fileadmin/DigitalGuide/Screenshots/dmz-network-diagram-1.png)

---
### Estructura 2

[Estructura DMZ 2](https://www.ionos.es/digitalguide/fileadmin/DigitalGuide/Screenshots/dmz-network-diagram-2.png)

---
## Tot i assegurar el perímetre

- Monitoratge (SOC)
- Manteniment i millora
- Avanç en la disciplina
- Insiders
- Evació del perímetre