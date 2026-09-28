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

Per veure com de senzill és crackejar una contrasenya no robusta el que heu de fer és utilitzar un dels dos tipus d’atacs per aconseguir accedir als arxius que hi han comprimits en [aquest arxiu ZIP](file:///run/media/rgimenezh/36167eda-1ffc-44d1-9e8e-ebbe470f63ff/Docs/www/apunts/SMX/MP06/UF1/Geheim.zip).

Recordeu que bàsicament per crackejar una contrasenya existeixen bàsicament dos tipus d’atacs:

Atac de força bruta

On establim longituds mínimes i màximes a provar així com conjunt de caràcters i el que fem és intentar accedir amb cadascuna de les combinacions possibles. Aquests atacs són extremadament efectius igual que extremadament lents, cosa que els normalment inviables.

Atac de diccionari

Aquí simplement intentarem entrar amb un conjunt determinat de passwords (uns milers o milions normalment) que anomenem diccionari. Aquest atac és força ràpid donat el conjunt limitat de intents però no sempre és efectiu.

Un cop aconseguit reflexionem sobre:

- Quin tipus d’atac esteu fent servir?
- Existeixen més coses susceptibles a ser atacades de la mateixa manera?
- Quins mètodes podem emprar per evitar aquest atac?

## 4. Recursos

- [SecLists](https://github.com/danielmiessler/SecLists): Github amb molts diccionaris de passwords comuns.
- [esGeek](https://esgeeks.com/formas-de-crear-diccionario-para-fuerza-bruta/): 5 formes de crear diccionaris.
