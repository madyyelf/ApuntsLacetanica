---
{"publish":true,"title":"Càpsula Google","tags":["apunts","ic10/tutoria"],"cssclasses":""}
---

# Llicència
Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---
# Càpsula Google
## Esmolant la destral

Tot sovint ens oblidem d'*esmolar la destral*; millorar en les coses utilitàries que fem tot sovint dia a dia. Tanmateix la millora d'aquestes tasques repetitives i ús d'eines que utilitzem molts cops cada dia ens farà poder treballar molt millor, ser més efectius, més ràpids i dedicar el temps guanyat a esmolar encara més la nostra destral!

Una d'aquestes habilitats que utilitzem tot sovint és cercar informació a Internet. Afinar aquesta habilitat ens permetrà trobar molt més ràpidament la informació que busquem i fins i tot trobar "joies" (informació molt rellevant i singular) dins de tot l'oceà d'informació que és Internet.

## Opcions de cerca de Google

Per utilitzar les opcions de cerca cal anar a l'apartat de [cerca avançada](https://www.google.com/advanced_search) o simplement conèixer i utilitzar les opcions en el quadre de cerca normal (que acostuma a ser més ràpid).

**" "**

Les cometes són literals i forçarem a que aparegui la paraula o que sigui la frase exacta indicada. (p.e.: `"debian 12"`)

**+**

Força a que aparegui aquella paraula en els resultats. També es pot utilitzar per concatenar (ajuntar) paraules a buscar.

**site**

Limitarem les cerques a un lloc web o domini concret (p.e.: `site:lacetaniaca.cat`).

**-**

Excloure (p.e.: `-github`).

**intitle**

Text al títol (p.e.: `intitle:"index of"`).

**filetype**

Per buscar tipus concrets d'arxius (p.e.: `filetype:pdf`).

**ext**

Ídem que `filetype`.

**OR**

Qualsevol d'aquests termes (p.e.: `site:.es OR site:.cat`).

**0..10**

Per marcar un rang numèric. (p.e.: `intext:nota 0..10`)

**intext**

El terme es cercarà dins del cos del text. (p.e.: `intext:password intext:admin`)

**inurl**

El terme es cercarà a la URL de la web. (p.e.: `inurl:login`)

**allinanchor**

Cerquem als enllaços. (p.e.: `allinanchor:lacetania.cat`)

### Opcions de cerca avançada sense "paraula clau"

Algunes opcions no disposen de "paraula clau" i tan sols les podem utilitzar activant les `eines` (la forma ràpida si utilitzem paraules clau en la consulta) o anat a l'apartat de `cerca avançada`. Aquestes opcions són:

**Idioma**

Si volem un idioma concret com el espanyol.

**Regió**

Si volem un país concret.

**Darrera actualització**

SUPER ÚTIL per cercar informació actualitzada o d'última fornada.

**Drets d'utilització**

SUPER ÚTIL per cercar imatges que puguem utilitzar en els nostres projectes sense infringir drets d'autor.

## Altres tipus de cerca

**Per veu**

Interessant com a mans lliures, o per cercar una cançó en base la seva lletra.

**Per imatge**

Molt útil per cercar imatges semblants, productes que desconeixem el seu nom o _OSINT_.

## Tips i exemples

Per cercar informació concreta ens hem d'imaginar on apareixerà (lloc, tipus d'arxiu, etc) i el seu format, així com paraules clau que apareixeran.

- Podem cercar pàgines espanyoles per limitar els resultats a empreses locals utilitzant `site:.es`.
- Llocs espanyols que regulen com fer-ne bug bounty: `site:.es inurl:"security.txt"`
- Cercar servidors que estiguin compartint ISO: `intitle:"index of" intext:".." intext:".iso"`
- Documents d'una organització: `site:gencat.cat filetype:pdf OR filetype:xlsx OR filtetype:docx`
- Excels amb usuaris de gmail i passwords: `intext:user intext:password intext:"*@gmail.com" ext:xls`
- Logs que continguin l'usuari "admin" i password: `intext:user intext:password intext:"admin" ext:log`
- Comptes de paypal: `intext:paypal intext:password ext:xls -github`
- Còpies de seguretat SQL que continguin passwords: `inurl:backup ext:sql -github intext:password`
- Pàgines de login de tots els subdominis de Coca-Cola: `site:*.coca-cola.com intext:login`

###  Google Dorks

Els _Google Dorks_ són cerques perfetes que busquen certs resultats prefixats. Tenim llocs com [Exploit-DB](https://www.exploit-db.com/google-hacking-database) on podem trobar tot de _dorks_ ja creats per trobar informació molt específica com dispositius, logs amb errors, usuaris i passwords, etc.

### Demanar que s'indexi un lloc web

Si Google encara no ha indexat la nostra web de nova creació (o actualització) podem crear una sol·licitud per a que ho faci amb les eines administratives ([Tutorial](https://developers.google.com/search/docs/crawling-indexing/ask-google-to-recrawl)).

### robots.txt

L'entrada de `domini/robots.txt` serveix per indicar als crawlers (les eines dels cercadors que recorren Internet cercant continguts nous) com volem que recorrin el nostre domini. És interessant ja que aquí els administradors poden "vetar" algunes webs o carpetes per a que no siguin indexades, fer que no es guardi una versió de cache, etc.

### Alertes de Google

Si volem podem crear una alerta que ens envii un email directament quan el crawler de Google indexi una nova web que compleixi amb el nostre criteri de cerca. Útil per tenir controlada la informació pròpia que apareix a Internet o per ser dels primers en detectar els canvis en una web corporativa.

## Hacking amb Google

Dins de la disciplina de cyberseguretat tenim un conjunt de tècniques anomenades _OSINT_ (Open Source INTelligence) que tracta precisament de cercar informació sensible de l'objectiu a fonts públiques. No cal dir que una de les eines principals és utilitzar Google i trobar tota info possible, com logs, excels, metadades en PDFs, cercar les fotos dels treballadors per localitzar-los en altres indrets, etc.

És molt interessant ja que per un costat s'arriba a trobar informació molt important i que facilita molt el hacking posterior, i per l'altre perque són tècniques totalment legals i que es poden fer sense por a ser denunciats.

OSINT utilitza moltes eines per a cercar de forma específica tipus d'informació i/o portals. Podem trobar un recull d'eines a [OSINT Framework](https://osintframework.com/) molt interessant. També existeixen eines com MALTEGO que combinen fonts i resultats per fer-ne una cerca més profunda i ordenada.

Tanmateix cal coneixer webs especialitzades com per exemple [la DGT](https://www.dgt.es/nuestros-servicios/tu-vehiculo/tus-vehiculos/informe-de-un-vehiculo/) ofereix informació sobre un vehicle, podent saber-ne la titularitat i altres dades. També al BOE es publiquen les multes de trànsit

### Google traductor

- Útil per no deixar rastre en els logs del servidor que visitem.
- Útil per saltar-se proxys que ens filtrin per domini.

## Altres cercadors

**Bing**

Alternativa de Microsoft, i que a vegades dona resultats diferents… és interessant contrastar.

**DuckDuckGo**

Cercador que no utilitza les teves dades personals, per tant el resultats són "genèrics" però al menys no estàs alimentant al monstre.

**WayBackMachine**

Web que conté snapshots de un lloc web al llarg del temps, és interessant pq hi pot ….

**Shodan**

Cercador de serveis, no de continguts.

## Webgrafía

- [Ajuda de Google](https://support.google.com/websearch/answer/35890?hl=ca&co=GENIE.Platform%3DDesktop#zippy=%2Cde-p%C3%A0gines-web-i-fitxers)
- [BrigadaOSINT](https://www.brigadaosint.com/)