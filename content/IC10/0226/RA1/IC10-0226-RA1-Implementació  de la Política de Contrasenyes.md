---
publish: true
title: Implementació de Política de contrasenyes
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

# Windows

- "Igual" en local com en domini.
- Opcions poc configurables.
- No es poden afegir altres mètodes.
- No activar xifrat reversible.
- Windows HOME no té política de contrasenyes.
- `gpedit.msc`

---

## Directiva de contrasenyes

![[IC10/0226/RA1/Pasted image 20261005084401.png]]

---

## Directiva de bloqueig de compta

## ![[IC10/0226/RA1/Pasted image 20261005084432.png]]

# Linux

## Mòduls PAM

- Modulars
- Configurables
- Arxius molt sensibles! (errors, ordre)

---

## Complexitat (pwquality)

- `/etc/security/pwquality.conf`
  - `enforce_for_root`
- `/etc/pam.d/common-password`

![[IC10/0226/RA1/Pasted image 20261005084511.png]]

Figure 1: Configuració pwquality.conf

![[IC10/0226/RA1/Pasted image 20261005084518.png]]

Figure 2: Configuració /etc/pam.d/common-password (primer línia)

---

### Verificació complexitat

Cal que en introduir una contrasenya que no compleix aparegui el missatge: ![[IC10/0226/RA1/Pasted image 20261005084553.png]] Si apareix "VUELVA A ESCRIBIR LA CONTRASENYA" no està funcionant!

---

## Intents fallits (`pam_faillock`)

- `/etc/pam.d/common-auth`

![[IC10/0226/RA1/Pasted image 20261005084613.png]]

Figure 3: Vigilar l'ordre dins l'arxiu

---

### Verificació bloqueig

Cal que aparegui un missatge clar del bloqueig del compte.\
![[IC10/0226/RA1/Pasted image 20261005084629.png]]
![[IC10/0226/RA1/Pasted image 20261005084636.png]]

---

## Caducitat

- Per tot els comptes nous: `/etc/login.defs`

![[IC10/0226/RA1/Pasted image 20261005084701.png]]

- Per comptes individuals: `chage` (un a un)

---

### Verificació caducitat

- Canviant data sistema.
- `cat /etc/shadow`

![[IC10/0226/RA1/Pasted image 20261005084720.png]]
