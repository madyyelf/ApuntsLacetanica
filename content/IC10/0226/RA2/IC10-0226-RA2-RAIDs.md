---
{"publish":true,"title":"RAIDs","tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**
![by-nc-sa-eu_.png](http://alquimiabinaria.cat/by-nc-sa-eu_.png)

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

## 2025 Raul Gimenez Herrada
(raul.gimenez@lacetania.cat)
[lacetanica.at](https://lacetanica.cat/)

[![Ko-fi Raul Gimenez Herrada](https://alquimiabinaria.cat/kofi.png)](https:/ko-fi.com/raulgimenezherrada)
# RAIDs
---
## Què és un RAID?

Conjunt de discos que treballen plegats i es mostren com una sola unitat lògica.

Avantatges possibles:

- Velocitat
- Unió de capacitats
- Tolerància a errors (físics)
- Millora integritat (verificar que no hi han modificacions incontrolades)
---
## Muntatge de RAIDs

 **Per software**: Opció pobre, ja que carrega al S.O. de funcions extres.

**Per hardware**: Mitjançant opcions de placa base o controladora.

---
## Tipus de RAIDs

De cada tipus de RAID cal analitzar:

- Capacitat total
- Capacitat de la unitat lògica resultant.
- Tolerància a errors
- Quants discos màxims poden fallar sense comprometre el sistema.
- Augment de velocitat
- Quants capçals es poden utilitzar per llegir informació útil alhora.

Suposarem discos de 1TB per fer càlculs simples.

### RAID 0

![RAID0.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF2/RAID0.png)

---
#### Característiques RAID 0

- Mínim 2 discos
- Velocitat (2 capçals)
- Unió de capacitats 100% (2TB)
---
### RAID 1 (Mirall)

![RAID1.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF2/RAID1.png)

---
####  Característiques RAID 1

- Mínim 2 discos
- Integritat
- Tolerància a errors (1 disc)
- Capacitat 50% (1TB)
---
### RAID4

![RAID4.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF2/RAID4.png)

---
#### Càlcul de paritat

La paritat "fa que" el recompte de 1s sigui parell per cada posició d'informació en els 3 discos.

  
| DISC 1 | DISC 2 | DISC 3 |
| ------ | ------ | ------ |
| 1001   | 1101   | P=0110 |

Permet recuperar la informació d'un disc en cas de fallida, verificar integritat i fins i tot treballar sense un disc.

---
#### Característiques RAID 4

- Mínim 3 discos
- Velocitat (2 capçals)
- Unió capacitats 66% (2TB)
- Tolerància a errors (1 disc)
- Integritat
---
### RAID 5

![RAID5.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF2/RAID5.png)

---
#### Característiques RAID 5

- Mínim 3 discos
- Velocitat (3 capçals)
- Unió capacitats 66% (2TB)
- Tolerància a erros (1 disc)
- Integritat
---
### RAID 1+0

![RAID1+0.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF2/RAID1+0.png)

---
#### Característiques RAID 1+0

- Mínim 4 discos
- Velocitat (4 capçals)
- Unió capacitats 50% (2TB)
- Tolerància a errors (2 discos, però depèn de quins!)
- Integritat
---
### RAID 0+1

![RAID0+1.png](file:///home/rgimenezh/Escriptori/lacetanica/apunts/SMX/MP06/UF2/RAID0+1.png)

---
#### Característiques RAID 0+1

Iguals al RAID 1+0