---
{"publish":true,"title":"ACTIVITAT Diagnòstic de Dispositius d'Emmagatzematge","tags":["apunts"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**
![by-nc-sa-eu_.png](http://alquimiabinaria.cat/by-nc-sa-eu_.png)

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

## 2025 Raul Gimenez Herrada
(raul.gimenez@lacetania.cat)
[lacetanica.cat](https://lacetanica.cat/)

[![Ko-fi Raul Gimenez Herrada](https://alquimiabinaria.cat/kofi.png)](https:/ko-fi.com/raulgimenezherrada)
# ACTIVITAT Diagnòstic de Dispositius d'Emmagatzematge
## Objectius

L’objectiu d’aquesta activitat és conèixer i practicar algunes de les eines disponibles actualment per a realitzar bancs de proves de rendiment del discos durs i consultes i automatitzacions de les propietats SMART d’aquests.

## Enunciat

Aquestes eines permetran detectar futurs errors ja que s'estima que el 60% dels errors dels disc durs són previsibles. El que heu de fer és utilitzar un benchmark i un visualitzador de propietats SMART per **veure l’estat del disc dur de la vostra màquina real**.

Les eines que utilitzarem seràn: Per Windows:

- Benchmark: [ASS SSD Benchmark](https://www.techspot.com/downloads/6014-as-ssd-benchmark.html).
- SMART: [CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/).

I per Linux:

- Benchmark: [hdparm](https://blog.desdelinux.net/medir-rendimiento-de-hdd-hdparm/).
- SMART: [smartmontools](https://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu).

Primer farem un benchmark anotant les velocitat de lectura i escriptura seqüencials.

Seguidament veurem les propietats SMART. En tots dos casos (windows/linux) investigueu com podeu automatitzar la lectura de les propietats SMART i establir alarmes o missatges per automatitzar-ne el monitorage. Sobre les SMART anoteu els següents valors:

- Velocitat de lectura.
- Velocitat d’escriptura.
- Temperatura.
- Sectors reassignats / cicles d’escriptura.
- Hores en funcionament.
- Velocitat de rotació.
- Mode ATA (o velocitat de transferència del ATA).

Un cop finalitzades les proves, intenteu treure conclusions. Per fer-ho:

- Busqueu la documentació tècnica específica del vostre disc dur i compareu les característiques teòriques que us indiquen amb les reals que heu obtingut.
- Compareu els vostres resultats amb els obtinguts per companys amb discs "similars".
- Compareu els vostres resultats amb els obtinguts per companys amb discs "tecnològica-ment diferents".

Com creieu que està el vostre disc dur?

## Valoració

L’activitat es valorarà mitjançant un test, tant a nivell de continguts teòrics com pràctics.

## Ampliació i millora

- Apreneu a utilitzar les eines de “l’altre sistema operatius”.
- Podeu consultar els següents enllaços:
    - [https://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](https://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)
    - [https://www.youtube.com/watch?v=bL_X3OZh0zw](https://www.youtube.com/watch?v=bL_X3OZh0zw)
    - [https://androidpc.es/blog/2014/01/06/comprueba-el-estado-y-rendimiento-de-tu-disco-duro/](https://androidpc.es/blog/2014/01/06/comprueba-el-estado-y-rendimiento-de-tu-disco-duro/)
    - [https://es.wikipedia.org/wiki/S.M.A.R.T](https://es.wikipedia.org/wiki/S.M.A.R.T).