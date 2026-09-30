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

## 2. Objectius

- Prendre consciència de la necessitat d’utilitzar contrasenyes robustes.
- Veure atacs de cracking de contrasenyes.
- Extrapolar possibles defenses, especialment en serveis.

## 3. Enunciat

## Atac a les comptes mitjançant SSH

Busuque i instal·leu l'aplicació de crack de contrasenyes.

Tenim un servidor Debian, amb el servei SSH obert.  Farem un atac de força bruta o diccionari sobre aquest servei i l'usuari `pere`.

Per atacar per diccionari:
`hydra -l pere -P diccionari ssh://<IP>`

Podeu utilitzar el [Top 200 contrasenyes més utilitzades el 2025](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/2025-199_most_used_passwords.txt).
Nota: Per defecte Debian tan sols deixa 6 intents per connexió. LoginGraceTime ampliat a 30m.

Per un atac de força bruta:
`hydra -l pere -x 4:8:aA1! ssh://<IP>`

On:

- `4`: Longitud mínima.
- `8`: Longitud màxima.
- `aA1!`: a->minúscules, A->Majúscules, 1->números, !->caràcters especials.

## Atac a comptes mitjançant Jhon

/etc/passwd
/etc/shadow
funcions hash
Rainbowtables
Jhon the Ripper

## 4. Recursos

- [SecLists](https://github.com/danielmiessler/SecLists): Github amb molts diccionaris de passwords comuns.
- [esGeek](https://esgeeks.com/formas-de-crear-diccionario-para-fuerza-bruta/): 5 formes de crear diccionaris.
