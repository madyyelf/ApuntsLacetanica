---
{"publish":true,"title":"ACTIVITAT Atac a windows","tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2026 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)
# Introducció

En un sistema Windows hi ha una sèrie de programes que s'inicien abans de que l'usuari entri en el sistema. Si un atacant aconseguir canviar el programa que s'executa per defecte per un altre que permeti executar comandes podria entrar en el sistema sense conèixer cap compte d'usuari.

Però a més tindrà els privilegis de l'usuari amb el que Windows executa el programa. En temps d'arrencada normalment és l'usuari `SYSTEM`, que és un usuari privilegiat de Windows, i que permet fer qualsevol tasca en el sistema operatiu com per exemple canviar la contrasenya de l'administrador.

Amb una tècnica com aquesta un usuari limitat del sistema podrà incrementar els seus privilegis d'accés al sistema i aconseguir fer coses a les que no està autoritzat. O simplement un hacker sense cap mena d'informació sobre els usuaris pot modificar el compte d'administració i accedir-hi o crear-se el seu propi usuari…. o simplement accedir al sistema i fer el que vulgui.

Les _StickyKeys_ són una característica d'accessibilitat per usuaris amb problemes per mantenir dues o més tecles premudes alhora. Quan cal una combinació de tecles per aconseguir accés a determinades opcions, com CTRL+P permet prémer les tecles una a una en comptes de requerir que es premin de forma simultània.

Utilitzarem això com a via d'entrada al sistema.

# Activitat

Imaginem que ens han contractat en una petita empresa que funciona amb [aquest servidor Windows](https://drive.google.com/file/d/1SLLDgLqo1NtJEQ9h115LIMfzLBFC0lQI/view?usp=drive_link). El problema que ens trobem el primer dia és que l'informàtic anterior el van acomiadar i va marxar de males maneres, i per venjança ha modificat tots els passwords del sistema. Lògicament no podem formatar el servidor, ja que perdriem totes les dades… però hi tenim accés físic, així que en principi tenim moltes vies per accedir a la informació i/o hackerjar-l'ho directament, que és el que et proposses fer…

## Preparació de l'activitat

1. Descarregueu la OVA del Windows Server.

![sticky_downloadOVA.png](https://educaciodigital.cat/inslacetania/moodle/pluginfile.php/331443/mod_resource/content/1/sticky_downloadOVA.png)

1. Importeu-la a _VirtualBox_.

![sticky_importaOVA.png](https://educaciodigital.cat/inslacetania/moodle/pluginfile.php/331443/mod_resource/content/1/sticky_importaOVA.png)

1. Descarregueu l'última ISO de Ubuntu.

## Atac

> **ATENCIÓ:** Cal que _Windows Server_ s'apagui correctament, sinó bloqueja el sistema de fitxers i per tant des de Ubuntu no podrem fer els canvis necessaris. Si teniu Windows apagat malament, la forma més simple és eliminar la màquina virtual i tornar-la a importar.

Arranqueu una màquina virtual de Windows amb un _LiveCD_, situeu-vos al sistema de fitxers de Windows i dins de `C:\Windows\System32` i substituïu el programa `SETHC.exe` per `CMD.exe`. Per fer-ho:

1. Simularem un USB amb l'Ubuntu tot afegint la seva ISO al CD de la màquina virtual. ![sticky_livecd.png](https://educaciodigital.cat/inslacetania/moodle/pluginfile.php/331443/mod_resource/content/1/sticky_livecd.png)
2. Triarem idioma, teclat etc al assistent de Ubuntu, i sobretot triarem l'opció **Try Ubuntu**!
3. Anirem al explorador de fitxers i buscarem el disc de Windows, el reconeixerem per la mida i per les carpetes que conté. ![sticky_filesystem.png](https://educaciodigital.cat/inslacetania/moodle/pluginfile.php/331443/mod_resource/content/1/sticky_filesystem.png)
4. Navegarem fins a `c:/Windows/System32`.
5. Renombrarem `sethc.exe` a `sethc_OLD.exe` per no perdre l'arxiu. (per entorn gràfic o per terminal)
6. Farem una còpia de `cmd.exe` i la renombrarem a `sethc.exe`.
7. Apaguem la _VM_ i treiem la ISO de Ubuntu del CD.
8. Inicieu el Windows Server i comprovareu que el sistema arranca normalment
9. Premeu cinc vegades la tecla SHIFT i veureu que se us obre un terminal amb privilegis de l'**usuari SYSTEM**! ![sticky_hack.png](https://educaciodigital.cat/inslacetania/moodle/pluginfile.php/331443/mod_resource/content/1/sticky_hack.png)
10. Crearem un usuari nou, per no tocar l'`Administrador`, i l'assignarem permissos de `Admin` amb l'eina de gestió d'usuaris.
    
        netplwiz
    
    ![sticky_netplwiz.png](https://educaciodigital.cat/inslacetania/moodle/pluginfile.php/331443/mod_resource/content/1/sticky_netplwiz.png)
    
11. Inicieu el sistema normalment i comproveu que l'usuari que heu creat pot entrar en el sistema. Sou capaços de crear un usuari amb privilegis d'administració?
12. Penseu en el temps que trigarieu amb una mica de pràctica per a hackerjar el sistema.

## Defensa

Un cop acabat investigueu:

1. Descobriu com es poden desactivar les Sticky Keys en Windows.
2. Altres idees per evitar l’atac?
3. Linux també pot ser vulnerable?
4. Encara que no puguessim fer l'atac, amb el _LiveCD_ hem tingut accés al disc… Què podriem fer com a atacants i com podem evitar-ho com administradors?

# Webgrafía

- [https://hardmicro.net/es/art%25C3%25ADculos/199-truco-de-las-stickykeys](https://hardmicro.net/es/art%25C3%25ADculos/199-truco-de-las-stickykeys)