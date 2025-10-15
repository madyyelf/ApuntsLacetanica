---
{"publish":true,"title":"Treball de còpies de seguretat","tags":["apunts","ic10/0226"],"cssclasses":""}
---

# Imatges

Aquestes són les imatges del Servidor Moodle necessàries per fer les còpies i per desprès, un cop fetes, verificar que són suficients per recuperar el sistema en cas d'error crític.

- [OVA Servidor Moodle (FUNCIONAL)](https://drive.google.com/file/d/1lWmpLkiIcMtZMTEIveSafkyeTK2jydI7/view). Mateixa imatge però des del [ROBUST](https://robust.infla.cat/~rgimenez/VM/moodleBackup.ova) del institut.
- [OVA Servidor Moodle (AMB ERROR, ON CAP RECUPERAR EL MOODLE AMB LES CÒPIES FETES)](https://drive.google.com/file/d/1xBcV26LrgdKtxHzkA8huRdxOgqpTl6kF/view). (versió [ROBUST](https://robust.infla.cat/~rgimenez/VM/moodleBackup-RECUPERACIO.ova))

# Credencials

Els usuaris/contrasenyes de les màquines són:

- S.O.: root/L4c3t4n14! i rgimenezh/moltdificil
- MariaDB: root/L4c3t4n14!
- Usuari de MariaDB per Moodle: moodleuser/L4c3t4n14!
- Moodle: admin/L4c3t4n14!

# Modificacions prèvies

Pel que fa a la xarxa, perquè la VM funcioni correctament i pugueu veure el Moodle que hi té instal·lar cal:

- Modificar `/etc/network/interfaces` i col·locar-hi una IP estàtica del vostre rang personal.
- Modificar l'arxiu de `hosts` del vostre equip perquè l’adreça `moodlebackup.cat` apunti a la IP estàtica que heu assignat a Moodle.
    - A Linux: `/etc/hosts`
    - A Windows: `C:\Windows\System32\drivers\etc\hosts`

# Què cal fer?

El document és molt gran, per a donar-vos una idea ràpida de què cal que feu i entregueu a la memòria, és bàsicament:

- Implementació: Tot l'apartat d'implementació.
- Simulacre: Utilitzar l'OVA del servidor Moodle amb error i volcar-hi la còpia generada. Verificar que tot ha anat bé i podeu accedir al Moodle. En cas de que no hi pugueu accedir, **analitzeu i documenteu** les causes i com ho arranjarieu-ho.

# Planificació

## Estudi del sistema

  
|DADES|MIDA|FREQÜÈNCIA CANVIS|
|---|---|---|
|/var/www/html|277 Mb|Anual / bianual|
|/var/www/moodledata|19Mb->60 Gb|Diària|
|Base de dades|1,4Mb|Diària|
|/etc|5Mb|Anual|

### Relacions (integritat):

Les tres primeres són del Moodle i per tant s'han de tractar igual.

Tot i que _etc_ ho podem tractar separat, donat que ocupa tant poc, o inclourem amb la resta de dades del Moodle.

## Requisits del sistema de còpies

### Marge de recuperació

Tenir còpies de 24 hores abans.

### Històric

A nivell legislatiu necessitem guardar notes del curs anterior, per tant esborrarem dades de 18 messos d'antiguitat (a partir del Gener eliminem dades del curs anterior començant per Setembre).

### Emmagatzematge de còpies

Servidor de còpies (Debian) simuli un servior extern i on farem la transferència utilitzant el servei SSH amb la comanda `scp`.

## Temporització

### Finestra de còpies

Farem còpies a partir de les 2:00 AM per evitar les hores típiques de treball i entrega d'activitats.

### Esquema de còpies

Completa

Primer dia de mes.

Diferencials

Cada divendres.

Incrementals

Diàries.

Eliminar arxius >= 18 messos d'antiguitat.

# Implementació

**IMPORTANT**: Aquesta és la part que heu de resoldre vosaltres de forma autònoma. El "cap" us ha donat les instruccions de fer el sistema de còpies del Moodle especificat abans, i vosaltres heu d'implementar-ho.

## Srv Moodle

En el servidor del Moodle crearem i progrararem uns scripts per fer les còpies de seguretat, que desrpés seràn recollides pel _servidor de còpies_ mitjançant `scp`.

### MySQLDump

Recordeu que per fer còpia de la base de dades no podem copiar els arxius sinó que cal fer una còpia amb la comanda `mysqldump`. La sintàxis és:

```
mysqldump [opcions] <bbdd> > <arxiu_sortida>
```

Per exemple:
```
mysqldump -u root -pL4c3t4n14! moodle > backup_bbdd-$(date +%Y-%m-%d).sql
```

**NOTA**: Fixeu-vos en el detall que no hi ha espai entre l'opció *-p* i el password.
**NOTA**: Remireu l'apartat de _Dates automàtiques_ de l'apartat dedicat a _TAR_.

### TAR

Els noms dels arxius resultatns han de ser:

- completa-ANY-MES-DIA.tar.gz
- diferencial-ANY-MES-DIA.tar.gz
- incremental-ANY-MES-DIA.tar.gz

Totes les dates han de ser automatitzades (agafades el sistema).

> **IMPORTANT**: Assegureu-vos de que els `tar` estàn funcionant correctament i fan còpies completes, diferencials i incrementals de forma respectiva. Això vol dir que **cal que feu proves** ja que si en corregir això no funciona el sistema de còpies no servirà de res i per tant la pràctica estarà mal feta!!!

> **NOTA**: Recordeu que `tar` funciona diferent a altres comandes, el primer paràmetre és el destí i el segon (i següents) els origens de dades per fer el TAR.

1. TAR Complert  
    
    Simplement fent un tar.
    
2. TAR Diferencial  
    
    Amb el paràmetre `-N` seguit de la data de l'última complerta. Aquesta data ha de ser automàtica (no pot ser fixa).
    
3. TAR Incremental  
    
    La incremental utilitza el paràmetre `-g` seguit d'un arxiu on es guardarà ua _snapshot_ de l'estat del fitxers. Quan tornem a llançar un tar amb el mateix paràmetre i mateix arxiu, compararà els arxius a comprimir amb la _snapshot_ i tan sols copiarà els que s'hagin modificat.
    
4. Dates automàtiques  
    
    Per posar noms i dates que s'actualitzin de forma automàtica amb la data i hora del sistema heu d'utilitzar la comanda `date` amb els paràmetres adients per a que us mostri (mireu el tutorial per tenir exemples).
    
    Si volem incloure el valor retornat dins d'un text (per exemple el nom d'un arxiu) haurem de posar la comanda entre accents oberts `$(date)`.
    

### Script final

Caldrà generar scripts per als tres tipus de còpies. El que cal que facin és:

1. Eliminar les còpies anteriors (ja estàn teòricament al servidor de còpies).
2. Fer còpia de la base de dades amb `mysqldump`.
3. Fer la còpia corresponent amb `tar`.

### CRON

Caldrà programar l'execució dels scripts seguint l'esquema de còpies.

> **IMPORTANT**: Vigileu de nou en entendre com esteu programant l'execució dels scripts amb el _CRON_ i verifiqueu que realment esteu programant seguint l'esquema de còpies plantejat.

## Srv Còpies

Cal muntar un servidor de còpies per emmagatzemar tots els arxius i simular que tenim un servidor en un altre edifici on tindrem les còpies segures. Aquest servidor tan sols cal que siguin un _Debian_ amb el servei _SSH_.

Serà l'encarregat de connectar-se al servidor de Moodle, recollir els arxius de backup i eliminar els backups superiors a 18 messos.

### SCP

La comanda `scp` serveix per fer còpies entre ordinadors remots sempre que l'ordinador remot tingui un servidor ssh com `openssh-server`. La comanda és tal com:
```
scp <origen> <destí>
```
On:

- **origen**: Si és el servidor remot SSH (enm aquest cas el servidor de Moodle) indicarem l'origen de la còpia de la següent forma: ```<usuari>@<srvremot>:<pathdestí> (p.e.: root@10.34.12.22:/tmp/backup*)```.
- **destí**:  Path cap a la carpeta destí con copiarem les dades (p.e.: _backup_).

1. SSHPASS  
    
    La comanda `scp` demanarà password cada cop que s'executi, per automatitzar-ho del tot l'haurem de combinar amb `sshpass` que té el format: `sshpass -p <password> <comanda SSH/SCP>` i per tant la comanda final serà quelcom semblant a:
    
 ```
 sshpass -p moltdificil scp /tmp/complerta-*.tar rgimenezh@10.34.22.33:/backup/
```    

### Eliminar arxius anteriors als 18 messos

A partir d'aquí creeu uns _scripts_ en aquest servidor que, mitjançant la comanda `scp`, s'endugui les còpies fetes, les elimini un cop copiades del servidor de Moodle i finalment elimini de si mateix els arxius més antics de 18 messos.

Per fer-ho caldrà utilitzar la comanda `find` amb els paràmetres `-mtime` i `-delete` tal que així:
```
find /backup/* -mtime +5 -delete
```
On:
- **/backup/***:  És el directori i els arxius a eliminar.
- **-mtime**: Són els dies d'antiguitat dels arxius, en el exemple +5 significa 5 dies d'antiguitat.
- **-delete**:  Eliminar els arxius.

### Scripts i CRON

Cal automatitzar que unes hores després de fer les còpies, el servidor de còpies les reculli i també elimini els arxius d'històric sobrants. Per tant:

1. Fer un `scp` per recollir les còpies del servidor de Moodle.
2. Eliminar les còpies més antigues de 18 messos.

# Procediments

## Gestió i emmagatzematge de còpies

Les còpies es gestionaràn totalment amb l'usuari _root_ i per tant tan sols l'administrador del sistema en tindrà accés i control.

A nivell d'emmagatzematge, el servidor de còpies estarà en una sala distanciada del servidor de Moodle, a l'aula 1.33 (Coordinació Informàtica). A aquesta sala tan sols hi tindrà accés el personal de la Coordianció de la mateixa forma que a l'armari on hi ha el servidor de còpies.

El Servidor de còpies tan sols tindrà el compte _root_ habilitat, que disposarà de contrasenya l'administrador del sistema.

## Recuperació de còpies

Per a realitzar una recuperació parcial ho podrà solicitar el propietari de la infomració en qüestió, o en el seu defecte el Cap de Departament de l'àrea associada.

Per a una recuperació total, caldrà el vist i plau de l'administrador i del director del centre.

## Simulacres

> **ATENCIÓ**: Aquesta part també cal fer-la al treball!

Es realitzarà un simulacre de recuperació a principis d'any, no més tard del 31 de Març. Per fer-ho es recuperaràn les dades del dia anterior sobre un servidor de característiques de HW similars a les del Servidor Moodle actual.

Aquest simulacre el realitzarà el Administrador, junt amb el personal de la Coordinació Informàtica i es registraràn temps de recuperació així com qualsevol incidència de cara a millorar el sistema de còpies.

Aquí el que cal és utilitzar la OVA de RECUPERACIÓ (la podeu trobar al principi del document) i fer els passos següents:

- Configurar la màquina amb `Adaptador Pont` des de _VirtualBox_ si encara no ho està.
- Configurar la mateixa `IP` que heu assignat al Moodle original. D'aquesta forma aconseguim que des del nostre _Host_, i utilitzant el navegador web, puguem accedir a [http://moodlebackup.cat](http://moodlebackup.cat) i veure si el _Moodle_ funciona. **IMPORTANT**: Cal que el Moodle original estigui apagat, tan sols la VM de _MoodleBackup-RECUPERACIO_ ha d'estar encès!
- Des del _servidor de còpies_, enviar els TAR i el mysqldump cap a _MoodleBackup-RECUPERACIO_.
- Al _MoodleBackup-RECUPERACIO_, descomprimir els TAR al les carpetes originals i carregar el _mysqldump_ al _MySQL Server_ amb la comanda `mysql -u root -p moodle < backup_BBDD-2024-11-20.sql`.
- Reiniciar el servidor _MoodleBackup-RECUPERACIO_.
- Verificar visitant la web [http://moodlebackup.cat](http://moodlebackup.cat) que el Moodle torna a funcionar correctament.

# Entrega

La memòria del treball ha de contenir:

- Implementació del sistema de copies amb proves de funcionament.
- Simulacre de recuperació, tot transferint com a mínim la copia completa al moodleBackup-RECUPERACIO i verificant que s'ha restaurat el servei de Moodle.

# Webgrafía

Recursos per repassar els conceptes de M2 i cerca ajuda de forma autònoma:

- [Nebul4ck](https://nebul4ck.wordpress.com/2015/03/20/backups-con-tar-full-backups-e-incrementales/): Tutorial en castellà sobre com utilitzar la comanda `tar` per fer els diferents tipus de còpies (completa, diferencial i incremental).
- [GeekyTheory](https://geekytheory.com/programar-tareas-en-linux-usando-crontab/): Explicació de com programar tasques amb `crontab`.
- [CronTab Guru](https://crontab.guru/): Web on podeu posar la vostra configuració de la temporització de `crontab` i verificar que fa el que espereu. També conté explicacions, exemples i trucs.
- [ExplainShell](https://explainshell.com/): Aquí podeu escriure una comanda concreta de la _shell_ de Linux i us explica paràmetre a paràmetre que fa cada cosa.
- [Redhat](https://www.redhat.com/sysadmin/ssh-automation-sshpass): Petit tutorial d'ús de `sshpass`.
- [LinuxTotal](https://www.linuxtotal.com.mx/index.php?cont=info_admon_021): Tutorial de com utilitzar `mysqldump`.
- [ubunlog](https://ubunlog.com/date-comando-conceptos-opciones-basicos/): Exemples d'ús de la comanda `date`, però no hi ha com aniuar-la amb els accents oberts.
- [StackExchange](https://unix.stackexchange.com/questions/194863/delete-files-older-than-x-days): Com eliminar arxius més antics que X dies amb la comanda `find`.