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

---

## 2. Tipus d'autenticació

Podem autenticar una persona segons tres factors genèrics:

Sap

La persona sap alguna cosa (contrasenya).

Té

La persona té alguna cosa (claus).

És

La persona és alguna cosa (biomètric).

---

## 3. Política de contrasenyes

---

### 3.1. Apartat tècnic

- Característiques (longitud, tipus de caràcters, etc).
- Contrasenyes diferents per cada servei ([HaveIBeenPwned](https://haveibeenpwned.com/)).
- Caducitat.
- Bloqueig de compte (intents fallits).

---

### 3.2. Apartat procediment

- Alta.
- Modificació.
- Baixa.
- Pèrdua.
- Filtració.

---

### 3.3. Apartat normatiu

- Normativa a comunicar a cada tipus d'usuari.
- Com informar als usuaris.
- Sancions per incompliment.

---

## 4. Coses a tenir en compte

---

### 4.1. Generació de contrasenyes

Recomanacions:

- Longitud mínima: 8 caràcters.
- Combinació majúscules i minúscules.
- Combinació xifres i caràcters especials.

---

#### 4.1.1. Generació simple

1. Pensar en un parell de paraules: "moltdificil"
2. Majúscules al inici de mot: "MoltDificil"
3. l33t: "M0ltD1f1c1l"
4. Caràcters especials afegits: "#M0lt|D1f1c1l!"

Si es coneixen les transformacions, es pot generar per diccionari.

---

#### 4.1.2. Generació sense utilitzar paraules

1. Pensar en frase: "Aquesta contrasenya és molt difícil".
2. Utilitzar les dues primeres lletres: "Aqcoesmodi".
3. Aplicar procediment anterior: "#4qC03sm0d1!"

---

### 4.2. Clauers electrònics

Eines com KeePassX.

---

#### 4.2.1. Avantatges

- Tan sols recordar una contrasenya molt robusta.
- Integració amb altres aplicacions.
- Mesures extres de seguretat (p.e.: Eliminar portapapers).
- Gestió de caducitat.
- Generació automàtica de contrasenyes.

---

#### 4.2.2. Inconvenients

- Multiplataforma.
- Pèrdua de BBDD.
- Pèrdua de password principal.

Caldrà gestionar-ho bé.

---

### 4.3. Doble factor d'autenticació

Aporta molta més seguretat, sempre que es combinin dos tipus d'autenticació diferents.

---

### 4.4. Contrasenyes al navegador

Si hi ha accés al disc són molt fàcils de recuperar (sqllite).

Si s'auto completa el camp, es pot saber la contrasenya molt fàcilment (F12).
