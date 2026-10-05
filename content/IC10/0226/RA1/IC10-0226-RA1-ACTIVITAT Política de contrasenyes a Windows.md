---
publish: true
title: ACTIVITAT Política de contrasenyes a Windows
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

- Veure les eines de Windows per implementar una política de contrasenyes a nivell tècnic.
- Destacar limitacions i particularitats.
- Adonar-se de com reacciona el sistema en un canvi de política de contrasenyes (què passa amb usuaris antics, etc).
- Acostumar-se a fer verificacions tant funcionals com no-funcionals (coses que SI ha de fer el sistema i coses que NO ha de fer el sistema).

# Introducció

Aquesta activitat busca

# Activitat

1. En una màquina virtual en Windows definiu-hi tres usuaris amb contrasenyes simples: “12345”, “1Ab”, “patata” (en cas que existeixi una política de contrasenyes vigent, elimineu-la per a poder crear aquests comptes amb contrasenyes poc segures).
2. Definiu una política de contrasenyes que obligui als usuaris a:
   - Tenir contrasenyes de 9 o més caràcters amb complexitat (números, lletres i símbols).
   - Que caduquin cada any.
   - Que guardi un historial de les darreres tres contrasenyes.
   - Que bloquegi el compte si l'usuari falla la contrasenya tres vegades seguides i que calgui esperar-se 5 minuts per tornar a intentar entrar.
3. Reinicieu el sistema
4. Intenteu entrar amb un dels usuaris creats anteriorment. Què fa el sistema?
5. Intenteu crear un usuari nou amb una contrasenya senzilla que no compleixi la política i comproveu que el sistema no el deixa crear.
6. Amb un usuari qualsevol intenteu entrar en el sistema fallant la contrasenya 4 vegades. Què passa?
7. Busqueu com podeu fer per, com administrador, desbloquejar un compte bloquejat (que no calgui esperar els 5 minuts).
8. Entreu amb un dels usuaris del sistema i canvieu la contrasenya 4 vegades. Comproveu que no podeu posar una de les anteriors.
9. Finalment, avanceu la data del sistema un any i escaig, reinicieu i verifiqueu que les contrasenyes han caducat i el sistema demana renovació.

# Webgrafía
