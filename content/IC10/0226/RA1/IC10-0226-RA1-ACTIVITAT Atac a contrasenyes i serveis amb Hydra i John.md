---
publish: true
title: ACTIVITAT Atac a Linux
tags:
  - apunts
---

# Llicència

Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2026 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

# Objectius

- Prendre consciència de la necessitat d’utilitzar contrasenyes robustes.
- La utilitat d'altres configuracions defensives com limitar intents, bloqueig comptes, etc.
- Veure atacs de cracking de contrasenyes amb eines avançades.
- concepte _Hash_.
- Concepte _RainbowTables_.
- Conceptes de contrasenyes a Linux.

# Enunciat

## Atac a les comptes mitjançant SSH

Busqueu i instal·leu l'aplicació `hydra` (mitjançant repositoris o [web oficial](https://github.com/vanhauser-thc/thc-hydra)que serveix que realitzar atacs a contrasenyes de serveis remots com formularis web, ssh, ftp, email, smb, etc.

Tenim un servidor Debian, amb el servei SSH obert.  Farem un atac de diccionari/força bruta sobre aquest servei i l'usuari `pere`.

Per atacar per diccionari:
`hydra -l pere -P /usr/share/wordlists/rock-you.txt ssh://10.50.13.10`
On:

- `-l`: És el nom d'usuari a atacar.
- `-P`: Ruta al diccionari a utilitzar.
- `ssh://<IP>`: Servei a atacar, en aquest cas _ssh_ i la _IP_ objectiu.

Per un atac de força bruta:
`hydra -l pere -x 4:8:aA1! ssh://10.50.13.10`

On `-x` marca que farem un atac de _força bruta_ amb el patró:

- `4`: Longitud mínima.
- `8`: Longitud màxima.
- `aA1!`: a->minúscules, A->Majúscules, 1->números, !->caràcters especials.

## Atac a comptes mitjançant John

Ara que som a dis, tenim accés a dor arxius interessants: `/etc/passwd` i `/etc/shadow`.  Recordeu què contenen?

Veiem que les contrasenyes estàn emmagatzemades amb una [funció hash](https://ca.wikipedia.org/wiki/Funci%C3%B3_hash), i possiblement un [sal](https://lenciclopedia.org/wiki/Sal_\(criptografia\)).

Tenim dues vies:

- Buscar [Rainbow Tables](https://en.wikipedia.org/wiki/Rainbow_table) que resolguin el hash.
- Programa John the Ripper per craquejar les contrasenyes en local

## John the Ripper

Anem per parts.
q

# Recursos

Si us encalleu amb la contrasenya de `pere` proveu amb el diccionari: [Top 200 contrasenyes més utilitzades el 2025](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/2025-199_most_used_passwords.txt).

També recordeu que teniu disponibles.

- [SecLists](https://github.com/danielmiessler/SecLists): Github amb molts diccionaris de passwords comuns.
- [esGeek](https://esgeeks.com/formas-de-crear-diccionario-para-fuerza-bruta/): 5 formes de crear diccionaris.

# Muntatge servidor vulnerable

- Per defecte Debian tan sols deixa 6 intents per connexió, he pujat a 1000.
- LoginGraceTime ampliat a 30m.

# Tasques

- [ ] #2do #ic10/0226 Part de atac a /etc/shadow.
