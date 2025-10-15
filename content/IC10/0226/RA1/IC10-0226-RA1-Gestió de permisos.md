---
{"publish":true,"title":"Gestió de permisos","tags":["apunts","ic10/0226"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
# Gestió de permisos
---
## Permisos a sistemes de fitxers

Permisos típics de lectura, escriptura i execució.

> **RECORDAR**: Sempre MÍNIMS permisos.
---
### Com gestionar-los

- Mínims permisos possibles.
- Agrupacions d'usuaris per grups.
- Particularitats del sistema de fitxers.
---
## Gestió de permisos a Windows

![permisosWindows.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF1/permisosWindows.png)

---
### Pestanya Seguretat

- Gestiona els permisos del sistema de fitxers local.
- Tot usuari que hi accedeixi quedarà filtrat (tant si accedeix localment com remot).
- Cal ser el més restrictiu possible.
- _Denegar_ preval sobre _Permetre_.
- _Herència_ a _opcions avançades_.
---
### Pestanya Compartir

- Gestiona els permisos de les carpetes compartides (accedides remotament).
- Han de ser més restrictius que la pestanya _Seguretat_, sinó no té sentit.
- _Denegar_ preval sobre _Permetre_.
- _Herència_ a _opcions avançades_.
---
### ALERTA!

Coses a recordar:

- _Seguretat_ preval per sobre _Compartir_.
- _Denegar_ preval sobre _Permetre_.
- Propietats heretades.
---
## Gestió de permisos a Linux

![permisosLinux.jpg](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF1/permisosLinux.jpg)

---
### Comandes per gestionar Grups

Amb les comandes:

- `grupadd`:  Crear un grup nou.
- `grupdel`:  Eliminar grup.
- `grupmod`: Modificar grup.
- `cat /etc/group`:  LListar grups existents.
- `getent`:  Saber els membres (usuaris) d'un grup.
---
### Comandes per gestionar Usuaris

Amb les comandes:

- `adduser`: Crear usuaris.
- `usermod`:  Modificar un usuari (afegir-lo a un grup per exemple).
- `userdel`: Eliminar usuari.
- `groups`:  Veure grups de l'usuari.
---
### Comandes per gestionar Permisos

Amb les comandes:

- `ls -l`:  Llistar el directori i mostrant permisos.
- `chmod`:  Canvi de permisos.
- `chown`:  Canvi propietari.
- `chgrp`:  Canvi grup.