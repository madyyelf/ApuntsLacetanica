---
publish: true
tags:
  - apunts
---

# Llicència

Aquest document es publica sota llicència **[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)**

**2025 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[![[Meta/Plantilles/buymeacoffee.png]]](https://ko-fi.com/raulgimenezherrada)

---

# ACTIVITAT: Analitzar els cyberatacs en temps real

## Mapes en temps real

Actualment hi han varies empreses, principalment proveïdors d'antivirus i solucions de seguretat, que publiquen en temps real els atacs que detecten.

Analitza els que mostra [Kaspersky](https://cybermap.kaspersky.com/), també en el apartat d'[estadístiques](https://cybermap.kaspersky.com/stats), i reflexiona sobre varis punts:

-  Com saben els atacs que s'estan donant en temps real?
-  Pq hi han països amb més cyberatacs? Quins son?
-  El gruix d'atacs provenen de /hackers/ o de governs?
-  Aquests atacs s'estan realitzant "a mà" o s'automatitzen d'alguna manera?
-  Quins són els tipus d'atacs més numerosos? Son també els més perillosos?
-  Hi ha algun tipus d'infecció que destaqui sobre els altres? De quin tipus és?

## Honeypots

Com hem vist anteriorment un dels elements que podem utilitzar per veure les activitats de hacking real són els _honeypots_.  Aquests ens proporcionen les següents avantatges:

- Alerta preventiva.
- Anàlisi de comportament.
- Anàlisi d'eines utilitzades

Quan intentem classificar els _honeypots_ podem distingit tres nivells d'interacció, amb les seves avantatges e inconvenients:

- Baixa interacció: Normalment tan sols obren el port i permeten tan sols una primera interacció (com un intent de login).
- Mitjana interacció: Simulen un servei real, però en realitat l'atacant no està interactuant amb el servei.  La dificultat resideix en com de be "simulen el servei".
- Alta interacció: Es munta un servei real i l'atacant hi interactua lliurement.  Cal afegir grans mesures de seguretat i tenir-ho extremadament controlat.

Així doncs, tal com veieu, els més interessants són els de mitjana interacció.  Un dels més interessants i que ha aparegut recentment és [Beelzebub](https://github.com/mariocandela/beelzebub) que bàsicament és un _honeypot de interacció mitja_ que pot utilitzar models LLM per a interactuar amb l'atacant i simular les respostes del servei.

### Anàlisi dades Beelzebub

Aquest honeypot s'ha tingut en servei vàries hores i algunes dades que podem extreure i analitzar són:

#### IPs d'origen

```
584	134.199.196.232	(US, United States)
581	129.212.188.139	(US, United States)
287	129.212.181.186	(US, United States)
128	209.38.121.136	(IN, India)
55	null	(can't resolve hostname ( null )
can't resolve hostname ( null ))
49	204.76.203.83	(NL, Netherlands)
38	91.215.85.88	(RU, Russian Federation)
28	::1	(can't resolve hostname ( ::1 )
can't resolve hostname ( ::1 ))
20	115.190.21.38	(CN, China)
18		(can't resolve hostname (  )
can't resolve hostname (  ))
15	193.32.162.146	(RO, Romania)
11	45.140.17.88	(RU, Russian Federation)
11	125.243.25.84	(KR, Korea, Republic of)
9	45.135.232.92	(RU, Russian Federation)
7	207.54.149.118	(US, United States)
6	91.92.241.59	(NL, Netherlands)
5	91.202.233.33	(TM, Turkmenistan)
5	45.140.17.124	(RU, Russian Federation)
5	103.144.246.218	(HK, Hong Kong)
4	80.94.92.182	(RO, Romania)
4	61.245.11.87	(PH, Philippines)
4	216.227.138.122	(US, United States)
4	210.177.143.61	(HK, Hong Kong)
2	92.118.39.95	(US, United States)
2	62.36.107.20	(ES, Spain)
2	45.135.232.177	(RU, Russian Federation)
2	213.209.143.51	(DE, Germany)
1	60.173.147.52	(CN, China)
1	27.71.229.14	(VN, Vietnam)
```

Coses que poden ser interessants d'analitzar:

- Paisos i geopolítica.
- Màquines compromeses o atacs directes?
- Reputació de IPs.

#### Usuaris i passwords utilitzats

Usuaris:

```
   343 root
     75 admin
     55 null
     49 1234
     31 user
     31 guest
     30 
     24 gitlab
     20 postgres
     19 test
     19 ftp
     18 rgimenezh
     18 hadoop
     17 user2
     17 nginx
     17 minecraft
     17 ftpuser
     17 esuser
     17 dmdba
     16 ubuntu
     16 es
     16 elastic
     16 debian
     15 opc
     15 mysql
     14 tom
     14 centos
     14 alex
     13 www
     13 wang
     13 uftp
     13 server
     13 lighthouse
     13 kingbase
     13 deploy
     12 testuser
     12 steam
     11 user1
     11 niaoyun
     11 jfedu1
     11 git
     11 dolphinscheduler
     11 dev
      9 oracle
      9 mehdi
      9 gitlab-runner
      9 ec2-user
      9 developer
      9 administrator
      8 elasticsearch
      7 sol
      7 jenkins
      6 support
      6 solana
      6 pi
      5 mongo
      5 docker
      5 apache
      4 sonar
      4 solv
      4 node
      3 zrybs
      3 yealink
      3 x2goprint
      3 www-data
      3 worker
      3 webuzo
      3 webserv
      3 vmail
      3 vagrant
      3 user6
      3 user50
      3 user5
      3 user3
      3 update
      3 trytan
      3 tools
      3 test2
      3 technician
      3 tbds
      3 systemx
      3 system
      3 sys
      3 suporte
      3 student
      3 srikanth
      3 splunk
      3 spamfilter
      3 smtest
      3 shutdown
      3 sem6
      3 sem5
      3 sem4
      3 selvananthi
      3 sadmin
      3 runner
      3 rtelekom
      3 root2
      3 ranger
      3 pufferpanel
      3 proxy
      3 plexserver
      3 plex
      3 pfd
      3 paas
      3 oscar
      3 operator
      3 openvpn
      3 omsagent
      3 odoo15
      3 o3-root
      3 nobody
      3 nexus
      3 newuser
      3 netdata
      3 nagios
      3 master
      3 maps
      3 manager
      3 man
      3 main
      3 linux
      3 kubernetes
      3 klepetko
      3 keycloak
      3 kafka
      3 jfletcher
      3 isabakir
      3 init
      3 hive
      3 hestiaweb
      3 hestiamail
      3 hennadii
      3 hdfs
      3 hapubws
      3 gpuadmin
      3 gpadmin
      3 gitlab-psql
      3 g
      3 flask
      3 fastmail
      3 factorio
      3 esearch
      3 downloader
      3 dogeman
      3 devmon
      3 devadmin
      3 data
      3 cxvqo
      3 cseadmin
      3 cp_postgres
      3 cp_extensions
      3 cloud-user
      3 cloudendure
      3 cloud
      3 ciuser
      3 chetana
      3 cbm
      3 bob
      3 bitrix
      3 bin
      3 bigdata
      3 backup
      3 azureuser
      3 astra_user
      3 asterisk
      3 appuser
      3 app
      3 aporaudio
      3 ansible
      3 amrita
      3 amp
      3 amir
      3 amavis
      3 amandabackup
      3 alisson
      2 zabbix
      2 yarn
      2 wso2
      2 weblogic
      2 vscode
      2 vncuser
      2 uucp
      2 username
      2 user4
      2 upmpdcli
      2 unl0
      2 ubnt
      2 tty0
      2 ts
      2 tomcat
      2 titu
      2 testuser1
      2 test3
      2 test1
      2 teamspeak
      2 systemd
      2 sysadmin
      2 supermap
      2 super
      2 stream
      2 stptbdd
      2 ssm-user
      2 solr
      2 slurm
      2 sem8
      2 sem7
      2 sem3
      2 sem2
      2 samba
      2 root1
      2 rocky
      2 registry
      2 redis
      2 rancher
      2 rajesh
      2 priyanka
      2 potok
      2 postgresql
      2 polkitd
      2 peer
      2 palworld
      2 packer
      2 orangepi
      2 odoo18
      2 odoo17
      2 odoo16
      2 odoo14
      2 odoo
      2 observer
      2 nxautomation
      2 nvidia
      2 nova
      2 nil
      2 news
      2 neo4j
      2 myuser
      2 mssql
      2 media
      2 mail
      2 lvuser
      2 lsfadmin
      2 lscpd
      2 lp
      2 list
      2 libuuid
      2 library-koha
      2 liberty-bridge
      2 labuser
      2 kipt
      2 jyvtc
      2 jumpserver
      2 joakima
      2 jms
      2 jiffyexp-usr
      2 jiffyapp-usr
      2 jack
      2 irc
      2 hysteria
      2 hiddify-panel
      2 hiddify-cli
      2 grml
      2 grid
      2 gnats
      2 gitlab-prometheus
      2 games
      2 flink
      2 fivem
      2 fastuser
      2 esroot
      2 emregover
      2 emqx
      2 emps
      2 elsearch
      2 ecs-user
      2 ec2
      2 dton
      2 dspace
      2 docubeapp-usr
      2 digital
      2 devops
      2 deployer
      2 demo
      2 default
      2 debian-spamd
      2 david
      2 daemon
      2 cyberpanel
      2 cowrie
      2 cephadm
      2 brute
      2 bot
      2 beaver
      2 basit
      2 ball
      2 backuply
      2 arpwatch
      2 argebarikat
      2 applmgr
      2 angel
      2 almalinux
      2 alexis
      2 aes-admin
      2 adminuser
      2 adminbnt
      2 admin123
      2 admin1
      2 a
      2 33sqn
      1 zyfwp
      1 validator
      1 telecomadmin
      1 t128
      1 router
```

Contrasenyes:

```
   450 
    120 123456
     62 root
     59 1234
     55 null
     20 admin
     16 password
     16 123
     10 123456789
      9 toor
      9 111111
      8 user
      8 admin123
      8 1
      6 ubuntu
      6 support
      6 administrator
      5 qwerty
      5 passw0rd
      5 docker
      5 default
      5 debian
      5 1q2w3e4r
      5 12345
      4 www
      4 root@123
      4 redhat
      4 raspberry
      4 P@ssw0rd
      4 Password1
      4 passwd
      4 oracle
      4 node
      4 nginx
      4 mysql
      4 linux
      4 centos
      4 apache
      4 Admin@123
      4 1qaz2wsx
      4 1234567890
      4 12345678
      4 123321
      3 zrybs
      3 yealink
      3 x2goprint
      3 www-data
      3 worker
      3 webuzo
      3 webserv
      3 wang
      3 vmail
      3 vagrant
      3 user6
      3 user50
      3 user5
      3 user3
      3 user1
      3 update
      3 uftp
      3 ubnt
      3 trytan
      3 tools
      3 tom
      3 testuser
      3 test2
      3 test
      3 technician
      3 tbds
      3 systemx
      3 system
      3 sys
      3 suporte
      3 student
      3 srikanth
      3 splunk
      3 spamfilter
      3 solana
      3 smtest
      3 shutdown
      3 sem6
      3 sem5
      3 sem4
      3 selvananthi
      3 sadmin
      3 runner
      3 rtelekom
      3 rootroot
      3 root2
      3 root123
      3 root1
      3 ranger
      3 QWERTY123
      3 qwerty123
      3 !Q@W3e4r
      3 qQ123456
      3 !Qaz@Wsx
      3 !qaz@WSX
      3 !Q2w3e4r
      3 pufferpanel
      3 P@ssword
      3 p@ssw0rd
      3 proxy
      3 plexserver
      3 plex
      3 pi
      3 pfd
      3 paas
      3 P@55w0rd
      3 oscar
      3 oracle123
      3 operator
      3 openvpn
      3 opc
      3 omsagent
      3 odoo15
      3 o3-root
      3 nobody
      3 nginx123
      3 nexus
      3 newuser
      3 netdata
      3 nagios
      3 master
      3 maps
      3 manager
      3 man
      3 main
      3 lighthouse
      3 letmein
      3 kubernetes
      3 klepetko
      3 keycloak
      3 kafka
      3 jfletcher
      3 isabakir
      3 init
      3 hive
      3 hestiaweb
      3 hestiamail
      3 hennadii
      3 hdfs
      3 hapubws
      3 hadoop123
      3 guest123
      3 guest
      3 gpuadmin
      3 gpadmin
      3 gitlab-psql
      3 gitlab
      3 git
      3 g
      3 ftpuser
      3 ftp
      3 flask
      3 fastmail
      3 factorio
      3 esuser
      3 esearch
      3 es
      3 elasticsearch
      3 downloader
      3 dolphinscheduler
      3 dogeman
      3 devmon
      3 developer
      3 devadmin
      3 dev123456
      3 deploy
      3 data
      3 cxvqo
      3 cseadmin
      3 cp_postgres
      3 cp_extensions
      3 cloud-user
      3 cloudendure
      3 cloud
      3 ciuser
      3 chetana
      3 cbm
      3 broadguam1
      3 bob
      3 bitrix
      3 bin
      3 bigdata
      3 backup
      3 azureuser
      3 astra_user
      3 asterisk
      3 appuser
      3 app
      3 aporaudio
      3 apache123
      3 ansible
      3 amrita
      3 amp
      3 amir
      3 amavis
      3 amandabackup
      3 alisson
      3 alex
      3 admin1234
      3 admin1
      3 abc123
      3 Ab123456
      3 a123456A
      3 1Q2W3E4R
      3 1234qwer
      2 zabbix
      2 yarn
      2 wso2
      2 welcome
      2 weblogic
      2 wang123
      2 vscode
      2 vncuser
      2 uucp
      2 username
      2 user4
      2 user2
      2 upmpdcli
      2 unl0
      2 tty0
      2 ts
      2 tomcat
      2 titu
      2 testuser1
      2 test3
      2 test123
      2 test1
      2 teamspeak
      2 systemd
      2 sysadmin
      2 supermap
      2 super
      2 stream
      2 stptbdd
      2 steam123
      2 steam
      2 ssm-user
      2 sonar123
      2 sonar
      2 solv
      2 solr
      2 sol
      2 slurm
      2 server
      2 sem8
      2 sem7
      2 sem3
      2 sem2
      2 samba
      2 rocky
      2 registry
      2 redis
      2 rancher
      2 rajesh
      2 Qwerty
      2 Qq123456
      2 qq123456
      2 !QAZ2wsx
      2 P@ssword123
      2 priyanka
      2 potok
      2 postgresql
      2 postgres123
      2 postgres
      2 polkitd
      2 peer
      2 password123
      2 Password
      2 Passw0rd
      2 palworld
      2 packer
      2 Pa$$w0rd
      2 P
      2 orangepi
      2 odoo18
      2 odoo17
      2 odoo16
      2 odoo14
      2 odoo
      2 observer
      2 nxautomation
      2 nvidia
      2 nova
      2 niaoyun
      2 news
      2 neo4j
      2 myuser
      2 mssql
      2 minecraft
      2 media
      2 mail
      2 lvuser
      2 lsfadmin
      2 lscpd
      2 lp
      2 list
      2 libuuid
      2 library-koha
      2 liberty-bridge
      2 labuser
      2 kipt
      2 kingbase
      2 jyvtc
      2 jumpserver
      2 joakima
      2 jiffyexp-usr
      2 jiffyapp-usr
      2 jenkins
      2 jack
      2 irc
      2 hysteria
      2 hiddify-panel
      2 hiddify-cli
      2 hadoop
      2 grml
      2 grid
      2 gnats
      2 gitlab-runner
      2 gitlab-prometheus
      2 games
      2 ftpuser123
      2 ftp123
      2 flink
      2 fivem
      2 fastuser
      2 esroot
      2 es123456
      2 emregover
      2 emqx
      2 emps
      2 elsearch
      2 elastic
      2 ecs-user
      2 ec2-user
      2 ec2
      2 dton
      2 dspace
      2 dolphinscheduler123
      2 docubeapp-usr
      2 docker123
      2 dmdba
      2 digital
      2 devops
      2 dev
      2 deployer
      2 demo
      2 debian-spamd
      2 david
      2 daemon
      2 cyberpanel
      2 cowrie
      2 changeme
      2 cephadm
      2 brute
      2 bot
      2 beaver
      2 basit
      2 ball
      2 backuply
      2 arpwatch
      2 argebarikat
      2 applmgr
      2 angel
      2 almalinux
      2 alexis
      2 aes-admin
      2 adminuser
      2 adminbnt
      2 adminadmin
      2 Admin123
      2 Ac123456
      2 aB123456
      2 Aa123456
      2 aA123456
      2 aa123456
      2 A123456a
      2 a
      2 888888
      2 654321
      2 33sqn
      2 1qazxsw2
      2 1qazXSW@
      2 1qaz@WSX
      2 1qaz@wsx
      2 1Q2w3e4r
      2 123qwe
      2 123abc
      2 123123
      2 000000
      2 !@#$%^&*
      1 web
      1 vps
      1 validator
      1 temp
      1 sshd
      1 solana123
      1 solana@123
      1 sol321
      1 sol123
      1 sol@123
      1 rootpass
      1 root1234
      1 root$
      1 root@
      1 root&
      1 root%
      1 root#
      1 root!
      1 PrOw!aN_fXp
      1 pass
      1 pasddd
      1 paco
      1 lpRPtj7rAL5nAabr
      1 host
      1 ------fuck------
      1 alpine
      1 alcatel
      1 admintelecom
      1 adminroot
      1 adminpass
      1 admin12345
      1 admin123!
      1 admin@123
      1 admin$
      1 Admin
      1 admin@
      1 admin&
      1 admin%
      1 admin#
      1 admin!@#
      1 abcd1234
      1 321
      1 1q2w3e
      1 128tRoutes
```

Coses interessants a analitzar:

- Llistats utilitzats reals (i per tant amb números de funcionar).
- Tecnologies que s'estan apuntant, trending.

#### Clients

```
   1354 SSH-2.0-Go
    447 
     55 null
     12 SSH-2.0-OpenSSH_10.2p1 Debian-2
     11 SSH-2.0-libssh2_1.11.1
      8 SSH-2.0-OpenSSH_10.0
      1 SSH-2.0-libssh_0.9.3
```

Coses interessants a analitzar:

- Llibreries i llenguatges més utilitzats.
- Son bots o és un atac manual?

#### Comandes executades

```
/bin/./uname -s -v -n -r -m
cat /proc/cpuinfo
curl ipinfo.io/org
echo 123456 > /tmp/d.log
echo "cat /proc/1/mounts && ls /proc/1/; curl2; ps aux; ps" | sh
echo Hi | cat -n
ifconfig
/ip cloud print
locate D877F783D5D3EF8Cs
ls
ls -la ~/.local/share/TelegramDesktop/tdata /home/*/.local/share/TelegramDesktop/tdata /dev/ttyGSM* /dev/ttyUSB-mod* /var/spool/sms/* /var/log/smsd.log /etc/smsd.conf* /usr/bin/qmuxd /var/qmux_connect_socket /etc/config/simman /dev/modem* /var/config/sms/*
lscpu | egrep "Model name:" | cut -d ' ' -f 14-
lspci | egrep VGA | grep Radeon | wc -l | head -c 1
lspci | egrep VGA && lspci | grep 3D
nproc 
null
nvidia-smi -q | grep "Product Name"
nvidia-smi -q | grep "Product Name" | awk '{print $4, $5, $6, $7, $8, $9, $10, $11}' | wc -l | head -c 1
ps | grep '[Mm]iner'
ps -ef | grep '[Mm]iner'
pwd
scp -qt "/var/tmp/lyITzxyy"
uname -a
uname -m
uname -m | awk '{printf $1}'
uname -n | awk '{printf $1}'
uname -r | awk '{printf $1}'
uname -s -v -n -r -m
uptime | grep -ohe 'up .*' | sed 's/,//g' | awk '{ print $2" "$3 }'
```

Coses interessants a analitzar:

- Comandes i eines utilitzades.
- Motivació dels atacants.
- Primers passos després d'entrar.
- Aplicacions descarregades.
