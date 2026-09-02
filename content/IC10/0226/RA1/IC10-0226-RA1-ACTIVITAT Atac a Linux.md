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

# Introducció

En sistemes Linux si no es configura adequadament el sistema d'arrancada un atacant el pot fer servir per arrancar el sistema en mode monousuari i aconseguir accés total al sistema. El mode monousuari serveix perquè els administradors puguin realitzar gestions que no es poden fer si hi ha algun procés interferint. Però quan estem en aquest mode el sistema només té un sol usuari, el root, i per tant té el control total del sistema. Descarregueu l'última versió de Debian per realitzar la tasca.

# Atac

Actualment la majoria dels sistemes Linux venen amb GRUB o GRUB2 com a gestors d'arrencada. En aquest cas el que s'ha de fer és editar la línia d'arrencada del nucli simplement fent sortir el menú (prement `SHIFT` durant l'arrencada) i clicant la lletra `e` per editar: En la línia que especi�ca el nucli (comença per linux): `linux /boot/vmlinuz-3.2.0-24-generic root=UUID=bc6f8146-1523 ro quiet splash`

La forma més senzilla és afegir al final d’aquesta línia `rw init=/bin/bash`
que el que farà és invocar un terminal de bash en mode mono-usuari i muntar el sistema de fitxer en mode lectura/escriptura.

Reiniciem el sistema i tindrem accés al disc. Fins aquí podríem robar informació o cercar els hash del `/etc/shadow` en unes Rainbow Tables, crear usuaris, extreure info, instal·lar backdoors, etc. A partir d’aquí ha de ser trivial crear un nou usuari amb `adduser` i afegir-lo al grup de sudoers. O, simplement fer un passwd i canviar el password de l’usuari root o qualsevol altre.

Per si no recordeu com afegir un usuari al grup de sudoers farem les següents passes:

1. Modificar per si les mosques el editor per defecte del sistema per passar-l’ho a nano: `sudo update-alternatives --config editor`
2. Un cop tenim el editor per defecte configurat farem `visudo` per editar els sudoers.
3. Busquem la línia de root ALL=(ALL:ALL) ALL . Just a sota escribim el vostre /nou usuari/ ALL=(ALL:ALL) ALL . Per exemple: `pepito ALL=(ALL:ALL) ALL`
4. Guardem i sortirm i reiniciem la màquina. Comproveu que ja tenim un usuari creat amb permisos de SUDO per fer del sistema el que vulguem.

# Defensa

GRUB2 ofereix un sistema de protecció bàsic basat en usuari/contrasenya. D'aquesta forma es pot definir un grup d'usuaris i quines entrades poden modificar o executar. Les contrasenyes i els usuaris es defineixen en el fitxer `/etc/grub.d/40_custom` (es pot afegir en altres llocs):

```shell
set superusers="admin"
password admin patata
```

Tenir la contrasenya en text pla en el fitxer de configuració no és un procediment gaire segur (es podria recuperar o modificar simplement amb un LiveCD) de manera que també s'ofereix la possibilitat de que la contrasenya estigui xifrada. Per fer-ho s'ofereix la comanda
`grub-mkpasswd-pbkdf2` . El que surti d'aquesta comanda serà la contrasenya que s'ha de definir a l'usuari. D’aquesta manera ens quedarà l’arxiu `/etc/grub.d/40_custom` de la següent manera:

```shell
set superusers="admin"
password_pbkdf2 admin grub.pbkdf2.sha512.10000.FC58373BCA1...
```

# Webgrafia

- [Hacking linux grub mode](https://www.linkedin.com/pulse/hacking-linux-machine-grub-mode-kiran-vijay)
