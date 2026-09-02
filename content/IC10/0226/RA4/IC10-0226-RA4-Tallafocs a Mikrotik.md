---
publish: true
title: Mikrotik DMZ
tags:
  - apunts
  - ic10/0226
---

# Llicència

Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---

# Funcionament Tallafocs a Mikrotik

- Cadenes: Punts d'inspecció del paquet.
- Taules (pestanyes): Agrupació per tipus de regles.

---

## El flux d'un paquet al Kernel de Linux

![IPtables esquema simple](https://www.redeszone.net/app/uploads-redeszone.net/2022/05/iptables_esquema_sencillo.png)

---

## Les taules i cadenes

![Taules i cadenes](https://ranxing.wordpress.com/wp-content/uploads/2014/11/untitled.png)

---

# Juguines amb les que jugar

![jugant firewall](https://www.networkstraining.com/wp-content/uploads/2020/10/firewall-management-tools.jpg)

---

## Cadenes

Les cadenes són els punts on podem intervenir, i tocarem:

- **INPUT**: Paquets que van dirigits (IP destí) al tallafocs (router).
- **OUTPUT**: Paquets que es generen (IP origen) al tallafocs (router).
- **FORWARD**: Paquets que passen (Ni la IP d'origen ni destí són el tallafocs) per el tallafocs (router).
- **PREROUTING** : Paquets que entren, just abans de processar-los.
- **POSTROUTING**: Paquets just abans d'alliberar-los a la xarxa.

---

## Taules

Les taules són agrupacions de regles per "temàtica d'accions".

- **FILTER**: Per filtrar paquets (decidir què passa i què no).
- **NAT**: Modificar capçaleres dels paquets (normalment IP/Port origen/destí).

---

## Accions

Les accions són, un cop seleccionat un paquet, què farem amb ell:

- **ACCEPT**: Deixem passar el paquets.
- **DROP**: No deixem passar el paquet.
- **REJECT**: Idem però avisant al client que no el deixem passar.
- **SRC\_NAT**: Modifiquem IP i/o port d'origen del paquet.
- **DST\_NAT**: Modifiquem IP i/o port de destí del paquet.

---

# Estructura de les regles

Les regles les definirem seguint sempre un patró semblant a:
\`ip firewall <taula> add chain=<cadena> <opcions de filtratge de paquet> action=\<acció> comment=<comentaris>

---

# Bones pràctiques

Recordar que el tallafocs intentarà aplicar una per una cada regla al paquet analitzar, i ==aplicarà la primera vàlida==.

- Les regles per defecte sempre les últimes.
- Les regles més genèriques (que afectaran a més transit) primeres.
- No barrejar mai llistes blanques i negres (utilitzar de forma creativa les negacions).
