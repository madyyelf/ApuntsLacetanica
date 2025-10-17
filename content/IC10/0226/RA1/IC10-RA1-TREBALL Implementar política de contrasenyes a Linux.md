---
{"publish":true,"tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
# ISOs i recursos

- [ISO Debian 11 al ROBUST. (intern INS Lacetània)](http://robust.infla.cat/~rgimenez/ISO/debian-11.5.0-amd64-DVD-1.iso)
- [ISO Debian 11 al Drive.](https://drive.google.com/file/d/1rlXpNqd20gGQ2c25mNmxwQdQXuyR4oHm/view?usp=sharing)

## Repositoris

Els repositoris (Arxiu `/etc/apt/sources.list`) de Debian 11 han de ser:

S'ha de comentar, la línia del `cdrom`.

> deb [http://ftp.caliu.cat/debian/](http://ftp.caliu.cat/debian/) bullseye main
> 
> deb-src [http://ftp.caliu.cat/debian/](http://ftp.caliu.cat/debian/) bullseye main
> 
> deb [http://security.debian.org/debian-security](http://security.debian.org/debian-security) bullseye-security main contrib
> 
> deb-src [http://security.debian.org/debian-security](http://security.debian.org/debian-security) bullseye-security main contrib
> 
> deb [http://ftp.caliu.cat/debian/](http://ftp.caliu.cat/debian/) bullseye-updates main contrib
> 
> deb-src [http://ftp.caliu.cat/debian/](http://ftp.caliu.cat/debian/) bullseye-updates main contrib

# Objectius

- Implementació de política de contrasenyes a Linux.
- Hàbit d'interpretar la sortida del sistema.
- Hàbit de fer verificacions de funcionalitat i no-funcionalitat.

# Enunciat

Com hem vist, la implementació d'una política de contrasenyes a Linux és més complexa alhora que més flexible i personalitzable. Podem fer-nos una idea de la de coses que podem remenar simplement executant `apt-cache search libpam` i veient tots els paquets relacionats amb el sistema d'autenticació de Linux.

En aquesta pràctica buscarem tant aprendre com configurar les contrasenyes a Linux com acostumar-nos a fer verificacions, ser curosos amb els arxius de configuració i interpretar les respostes del sistema. Tot això habilitats imprescindibles per a un informàtic.

## Recordatoris generals

> **ALERTA**
> 
> - Aquesta pràctica la podeu fer amb entorn gràfic si voleu, però és MOLT recomanable fer totes les configuracions i verificacions per terminal.
> - Que el sistema es queixi, no vol dir que no ho deixi fer.
> - Interpreteu sempre els missatges del sistema, molts cops us guiaràn cap a la solució.
> - Si quelcom no funciona i no sabem el motiu, cal consultar els registres (/var/log/syslog).
> - Si cal afegir línies en un fitxer PAM el lloc en el que es posen les línies és molt important. Fer-ho malament pot fer que no es pugui entrar més en el sistema o que es pugui entrar sempre…
> - Mireu la webgrafia.

## Mòduls PAM

### Pam Pwquality

El mòdul _pam_ pwquality_ ofereix la possibilitat de forçar als usuaris a tenir **contrasenyes complexes**. Per fer-ho es poden afegir tota una sèrie de paràmetres que indiquen la llargada mínima, la complexitat de la contrasenya (quantes majúscules, minúscules, números i símbols ha de tenir la contrasenya) i com han de diferir les contrasenyes.

Primer de tot caldrà instal·lar el mòdul amb `apt install libpam-pwquality`. Després tan sols cal buscar el fitxer `/etc/security/pwquality.conf` i modificar-ho de forma que s'adeqüi al que volem aconseguir.

### Pam Faillock

El mòdul _pam_ faillock_ és el responsable de **bloquejar els comptes** dels usuaris que han fallat un número determinat de vegades les contrasenyes. Generalment està instal·lat per defecte i per configurar-lo només cal “afegir” unes línies en un arxiu del `/etc/pam.d/common-auth`. Caldrà afegir:

> auth required pam_ faillock.so preauth audit deny=3 fail_ interval=60 unlock_ time=300

Abans de la línia `auth [success=1 default=ignore] pam_unix.so nullok`.

I també les línies:

> auth [default=die] pam_ faillock.so authfail audit deny=3 fail_ interval=60 unlock_ time=300
> 
> auth sufficient pam_ faillock.so authsucc audit deny=3 fail_ interval=60 unlock_ time=300

Abans de la línia `auth requisite pam_deny.so`.

> - **ALERTA**: No feu copy/paste, ja que per format hi han uns espais que "sobren" despres de "_".
> - **ALERTA**: Ja que us pauto aquest apartat, caldrà que a la memòria expliqueu molt bé què fa cadascun els paràmetres que apareixen en aquestes línies de configuració. I també per a que serveix cada línia.

### Login.defs

La **caducitat per defecte de les contrasenyes** es poden definir en l'arxiu `/etc/login.defs`. Aquestes modificacions afectaràn a tots els usuaris.

# Activitat

L'activitat consta de reproduïr la política de contrasenyes vista en l'activitat anterior, però en aquest cas en una Debian 11:

1. En una màquina virtual amb Debian 11 definiu-hi tres usuaris amb contrasenyes simples: “12345”, “1Ab”, “patata” (en cas que existeixi una política de contrasenyes vigent, elimineu-la per a poder crear aquests comptes amb contrasenyes poc segures).
2. Definiu una política de contrasenyes que obligui als usuaris a:
    - Tenir contrasenyes de 9 o més caràcters amb complexitat (números, lletres i símbols).
    - Que caduquin cada any.
    - Que bloquegi el compte si l'usuari falla la contrasenya tres vegades seguides i que calgui esperar-se 5 minuts per tornar a intentar entrar.
3. Reinicieu el sistema
4. Intenteu entrar amb un dels usuaris creats anteriorment. Què fa el sistema?
5. Intenteu crear un usuari nou amb una contrasenya senzilla que no compleixi la política i comproveu que el sistema no el deixa crear.
6. Amb un usuari qualsevol intenteu entrar en el sistema fallant la contrasenya 4 vegades. Què passa?
7. Busqueu com podeu fer per, com administrador, desbloquejar un compte bloquejat (que no calgui esperar els 5 minuts).
8. Finalment, creeu un nou usuari i verifiqueu al `/etc/shadow` que la data de caducitat del nou compte és d'aquí 365 dies.

# Entrega

L'entrega ha de constar d'un PDF amb portada i índex, respectant la normativa de treballs i demostrant qualitat de documentació tècnica a nivell professional.

Hi han de mostrar-se **captures** a un tamany suficient per ser llegibles de les **configuracions** i de les **proves** de bon funcionament.

> **IMPORTANT**: Cal captura completa del resultat de la comanda. No retalleu!

En aquest treball serà especialment important realitzar **explicacions de les configuracions** fetes, així com **interpretar els resultats** de les proves.

# Valoració

Aquest treball computa com **QUATRE** activitats normals. La valoració del treball es realitzarà sobre la rúbrica que podeu consultar en l'entrega.

> **IMPORTANT**: En aquest treball es valoraràn especialment:
> 
> - Les bones explicacions de les configuracions, especialment de l'apartat **Faillock**.
> - Les interpretacions de les proves fetes.

# FAQs

## No puc instal·lar el paquet…

- Et va `ping 8.8.8.8`?
- Et va `ping google.com`?
- Has configurat els _repositoris en xarxa_ durant la instal·lació?

## Tot i configurar l'arxiu `/etc/security/pwquality.conf` al crear un usuari nou ignora la configuració

- Has configurat l'arxiu però no instal·lat el paquet `libpam-pwquality`.

## Al configurar el `faillock` ja no puc entrar al sistema

- Al configurar el `faillock` segurament t'has equivocat en escriure quelcom o ho has escrit en una línia (posició) que no toca.

## Com verifico la caducitat de la contrasenya?

- Recorda que afecta als usuaris creats posteriorment a la modificació de la configuració.
- La caducitat es pot veure a `/etc/shadow` tal com es va explicar a la teoria.

# WebGrafia

- Fer que caduquin manualment (per fer proves): [rm-rf](https://rm-rf.es/comando-chage-tiempo-de-vida-de-claves-y-usuarios-en-gnulinux/)
- Complexitat: [Server-World](https://www.server-world.info/en/note?os=Debian_11&p=pam&f=1).
- Bloqueig d’intents fallits: [KifarUnix](https://kifarunix.com/lock-linux-user-account-after-multiple-failed-login-attempts/).
- Error típic de deixar saltar política a usuaris "super": [rosehosting](https://www.rosehosting.com/blog/how-to-enforce-password-quality-in-linux/) A l'últim comentari.