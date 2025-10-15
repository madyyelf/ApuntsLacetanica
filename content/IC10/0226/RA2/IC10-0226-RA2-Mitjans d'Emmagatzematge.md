---
{"publish":true,"title":"Mitjans d'Emmagatzematge","tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**
![by-nc-sa-eu_.png](http://alquimiabinaria.cat/by-nc-sa-eu_.png)

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

## 2025 Raul Gimenez Herrada
(raul.gimenez@lacetania.cat)
[lacetanica.at](https://lacetanica.cat/)

[![Ko-fi Raul Gimenez Herrada](https://alquimiabinaria.cat/kofi.png)](https:/ko-fi.com/raulgimenezherrada)

---
# Mitjans d'Emmagatzematge

---
## Tecnología

Les característiques dels mitjans d'emmagatzematge depenen bàsicament de la tecnologia emprada.

---
### Magnètics

- Econòmic (capacitat / preu)
- Parts mecàniques
- Molts cicles d'escriptura / lectura.
- Lectura seqüencial
- Sensible camps magnètics / elèctrics.

---
### Estat Sòlid

- Molt portable.
- Sense parts mòbils.
- Lectura aleatòria.
- Car (capacitat / preu)

---
### Òptics

- En desús.
- Extremadament pocs cicles d'escriptura
- Sensible calor / ratllades.
- Lectura seqüencial.
- Unitats d'emmagatzematge independents del lector.

---
### Magneto-òptics

Combinacióó magnètics i òptics.

- En desús.
- Millora els òptics amb millor capacitat i més re-escriptures.

---
## Localització

---

### Local

- Control i propietat de dades.
- Inversió necessària.

---
### Núvol

- Escalabilitat.
- Especialització a baix cost.
- Pèrdua de control.

---
### Portable

- Portabilitat
- Perill pèrdua / fuga informació.

---
## Distribució
---
### Distribuït

- Dades repartides en varis llocs (nodes).
- Es busca resiliència de les dades.
---
#### Centralitzat

- Equips amb rols separats.
- Rol central de gestor de la xarxa.
- Rol de node (treballador).
---
#### Des-centralitzat

- No hi han rols, tots iguals.
- Millora resiliència de la xarxa.
- Millora anonimat.
- Empitjora rendiment.
---
### No-Distribuït

- Dades concentrades en un node (equip o servidor).
- Més fàcil de mantenir (inversions, gestió, etc).
- Equip crític.
---
## Redundància

- Una mateixa informació està en varis nodes.
- Es guanya resiliència.
- A cost d'emmagatzematge.
---
## Exemples
---
### Dades als equips de les empreses

- Distribuïdes / local.
- Empresa resistent a errades d'un equip.
- Difícil de gestionar (seguretat, còpies, permisos).
---
### Dades en servidor de dades (carpetes compartides)

- Centralitzat / local.
- Equip crític.
- Fàcil de gestionar (seguretat, còpies, permisos).
- Cal invertir.
---
### P2P

- Distribuït / Centralitzat (clients + tracker).
- Resiliència de dades.
- Poc control.
---
### TOR / I2P / FreeNet

Son tres xarxes de compartició de continguts i serveis (_hidden services_).

De menys anònim a més:

- TOR
- I2P
- FreeNet
---
### CEPH
- Llicència LGPL
- Distribuït, descentralitzat amb replicació de dades.