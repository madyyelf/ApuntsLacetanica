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
- Veure atacs de cracking de contrasenyes amb eines avançades (_hydra-thq_ i \*John The Ripper).
- concepte _Hash_.
- Concepte _RainbowTables_.
- Conceptes de contrasenyes a Linux.
- Com es veuen els atacs als registres del sistema.

# ATENCIÓ

**RECORDEU QUE AQUESTES PRÀCTIQUES TAN SOLS ES PODEN FER UTILITZANT ELS SISTEMES I INSTRUCCIONS DONATS PER EL PROFESSOR.  QUALSEVOL ALTRE ACTIVITAT ÉS IL·LEGAL I PENAL!**

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

### John the Ripper

Anem per parts.
Primer combinarem els dos arxius de `/etc/passwd/`i `/etc/shadow/`per generar un arxiu base de hash que utilitzarem amb `john`.

Creeu un arxiu anomenat `passwd.txt`amb el contingut de `/etc/passwd` i un `shadow.txt`amb el contingut de `/etc/shadow`.  Ho podeu fer amb _copy/paste_ o per `scp`.

Els combinarem utiltizant la comanda `unshadow passwd-txt shadow.txt > hashes.txt`

#### Atac de diccionari

Si volem fer un atac de diccionari farem: `john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt`.  Els paràmetres són evidents ja a aquestes alçades.

#### Atac de força bruta

Si no trobem les contrasenyes amb el diccionari, podem optar per generar un diccionari personalitzar o fer un atac de força bruta, aprofitant que l'estem fent en local.

Llancem `john`per crackejar les contrasenyes utilitzant força bruta mitjançant la comanda: `john --incremental=All hashes.txt`

On:

- `--incremental=All`: Indica que el conjunt de caràcters és l'alfabet complet, incloent minúscules, majúscules, dígits i caràcters especials.

#### Veure contrasenyes

Un cop acabat podem veure els passowords amb: `john --show hashes.txt`

## Registres de l'atac

Ara que ja esteu dins i teniu accés, consulteu el _logs_ de _ssh_ amb la comanda `journalctl -u ssh`.

- Com d'evident és que hem estat atacats?
- Sabem l'atacant?
- Podem arribar a esbrinar si han aconseguit entrar finalment?

# Recursos

Si us encalleu amb la contrasenya de `pere` proveu amb el diccionari: [Top 200 contrasenyes més utilitzades el 2025](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/2025-199_most_used_passwords.txt).

També recordeu que teniu disponibles.

- [SecLists](https://github.com/danielmiessler/SecLists): Github amb molts diccionaris de passwords comuns.
- [esGeek](https://esgeeks.com/formas-de-crear-diccionario-para-fuerza-bruta/): 5 formes de crear diccionaris.

# Muntatge servidor vulnerable

- Per defecte Debian tan sols deixa 6 intents per connexió, he pujat a 1000.
- LoginGraceTime ampliat a 30m.
- `chmod o+r /etc/shadow`
- `chmod o+r /etc/passwd`

# Tasques

- [x] #2do #ic10/0226 Part de atac a /etc/shadow. ✅ 2026-09-30
- [x] #2do #ic10/0226 Part veure registres. ✅ 2026-09-30
