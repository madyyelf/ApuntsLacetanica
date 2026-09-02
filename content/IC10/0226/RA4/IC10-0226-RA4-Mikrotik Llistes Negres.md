---
publish: true
title: Mikrotik Llistes Negres
tags:
  - apunts
  - ic10/0226
---

# Llicència

Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2026 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---

# Regles bàsiques

## Regles per defecte de llistes negres

Acceptem tots els paquets que prèviament no haguem descartat. Ho farem per a les tres cadenes del tallafocs: `INPUT OUTPUT FORWARD`.

- Input ACCEPT
- Output ACCEPT
- Forward ACCEPT

### Verificació

¿Podem fer ping des del router a _hosts_ de les tres xarxes?

## Regle NAT per accedir a Internet des de la xarxa Interna

Com ja vàrem vuere a M5, cal fer un _source nat_ per a modificar l'origen dels paquets que surten del nostre router cap a Internet, així sabràn com tornar.

### Verificació

Des desde un host de la _DMZ_ o _Xarxa Interna_ podem accedir a un host de Internet?

# Regles de llistes negres

## Bloqueig de IPs malicioses

Descobriu que algunes IPs de _Internet_ estàn intentant hackejar el vostre servidor web amb atacs DoS i de diccionari. La seva IP és `123.111.222.333`, per tant bloquejeu-la per a que no pugui accedir enlloc.

## Bloqueig de ports

Els treballadors de la vostra empresa estan fent servir la xarxa per a descarregar-se pelis amb emule. Esbrineu els ports que fa servir aquesta aplicació i eviteu qualsevol connexió desde les xarxes de l'empresa cap a _Internet_ d'aquests ports.

## Bloqueig selectiu

Esbrineu la IP de la web de `lacetanica.cat` i aconseguiu que des del host de la _Xarxa Interna_ no es pugui fer ping, però poder veure la pàgina web.

## Bloqueig de connexions de Internet

- No volem **noves** connexions provinents de _Internet_ arribin al _router_ excepte el `ICMP`.
- No volem que **noves** connexions provinents de _Internet_ arribin a la _Xarxa Interna_.

## Bloqueig de connexions de la DMZ

- No volem que **noves** connexions provinents de la _DMZ_ vagin enlloc, a excepció del protocol `ICMP`.
