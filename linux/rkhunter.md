# rkhunter
Anti rootkit en Linux con rkhunter

**Rootkit Hunter** (**rkhunter**) es una herramienta de línea de comandos para Unix y Linux que realiza varias funciones de escaneado en el sistema con el fin de encontrar **rootkits**, **exploits**, **backdoors**, **malware**, modificaciones de comandos y librerías, scripts de arranque, configuración de red, etc.

## 1. Descarga de Rootkit Hunter

Última versión estable:

wget "http://downloads.sourceforge.net/project/rkhunter/rkhunter/1.4.2/rkhunter-1.4.2.tar.gz -O rkhunter-1.4.2.tar.gz

tar -xzvf rkhunter-1.4.2.tar.gz

## 2. Instalación de rkhunter

Tenemos varias opciones de instalación:

### 2.1. Instalación integrada en el sistema con todas las opciones por defecto

Simplemente ejecutamos como root el siguiente comando dentro de la carpeta descomprimida:

\# ./installer.sh --install

La salida de la instalación debería ser la siguiente en caso de ir todo bien:

    Checking system for:
     Rootkit Hunter installer files: found
     A web file download command: wget found
    Starting installation:
     Checking installation directory "/usr/local": it exists and is writable.
     Checking installation directories:
      Directory /usr/local/share/doc/rkhunter-1.4.2: creating: OK
      Directory /usr/local/share/man/man8: exists and is writable.
      Directory /etc: exists and is writable.
      Directory /usr/local/bin: exists and is writable.
      Directory /usr/local/lib64: exists and is writable.
      Directory /var/lib: exists and is writable.
      Directory /usr/local/lib64/rkhunter/scripts: creating: OK
      Directory /var/lib/rkhunter/db: creating: OK
      Directory /var/lib/rkhunter/tmp: creating: OK
      Directory /var/lib/rkhunter/db/i18n: creating: OK
      Directory /var/lib/rkhunter/db/signatures: creating: OK
     Installing check_modules.pl: OK
     Installing filehashsha.pl: OK
     Installing stat.pl: OK
     Installing readlink.sh: OK
     Installing backdoorports.dat: OK
     Installing mirrors.dat: OK
     Installing programs_bad.dat: OK
     Installing suspscan.dat: OK
     Installing rkhunter.8: OK
     Installing ACKNOWLEDGMENTS: OK
     Installing CHANGELOG: OK
     Installing FAQ: OK
     Installing LICENSE: OK
     Installing README: OK
     Installing language support files: OK
     Installing ClamAV signatures: OK
     Installing rkhunter: OK
     Installing rkhunter.conf: OK
    Installation complete

En este tipo de instalación ya tenemos el binario rkhunter en el path así que podemos invocarlo desde cualquier ruta del servidor. El archivo de configuración se encuentra en «**/etc/rkhunter.conf**«:

```sh
\# whereis rkhunter
```
    rkhunter: /etc/rkhunter.conf /usr/local/bin/rkhunter

Este modelo de instalación puede personalizarse cambiando rutas y otros parámetros:

    --examples       : Show layout examples.
    --layout  : Choose installation template.
                     The templates are:
                      \- default: (FHS compliant; the default)
                      \- /usr
                      \- /usr/local
                      \- oldschool: old version file locations
                      \- custom: supply your own installation directory
                      \- RPM: for building RPM's. Requires $RPM\_BUILD\_ROOT.
                      \- DEB: for building DEB's. Requires $DEB\_BUILD\_ROOT.
                      \- TGZ: for building Slackware TGZ's. Requires $TGZ\_BUILD\_ROOT.
                      \- TXZ: for building Slackware TXZ's. Requires $TXZ\_BUILD\_ROOT.
    --striproot      : Strip path from custom layout (for package maintainers).
    --install        : Install according to chosen layout.
    --overwrite      : Overwrite the existing configuration file.
                     (Default is to create a separate configuration file.)

### 2.2. Instalación en modo standalone

Este modo de instalación permite **instalar rkhunter en un único directorio**, es decir, sin separar binarios, archivos de configuración, logs, etc.

Si quisiéramos instalar todo en la ruta /opt/rkhunter:

```sh
\# ./installer.sh --layout custom /opt/rkhunter/ --install
```

Este es el proceso normal de instalación, todo correcto a excepción de un aviso que nos indica que la ruta no se encuentra en el path así que si no lo modificamos manualmente no podremos invocar el comando sin utilizar el path completo:

    Note: Directory /opt/rkhunter//bin is not in your PATH

    Checking system for:
     Rootkit Hunter installer files: found
     A web file download command: wget found
    Starting installation:
     Checking installation directory "/opt/rkhunter/": it exists and is writable.
     Checking installation directories:
      Directory /opt/rkhunter//share/doc/rkhunter-1.4.2: creating: OK
      Directory /opt/rkhunter//share/man/man8: creating: OK
      Directory /opt/rkhunter//etc: creating: OK
      Directory /opt/rkhunter//bin: creating: OK
      Directory /opt/rkhunter//lib64: creating: OK
      Directory /opt/rkhunter//var/lib: creating: OK
      Directory /opt/rkhunter//lib64/rkhunter/scripts: creating: OK
      Directory /opt/rkhunter//var/lib/rkhunter/db: creating: OK
      Directory /opt/rkhunter//var/lib/rkhunter/tmp: creating: OK
      Directory /opt/rkhunter//var/lib/rkhunter/db/i18n: creating: OK
      Directory /opt/rkhunter//var/lib/rkhunter/db/signatures: creating: OK
     Installing check_modules.pl: OK
     Installing filehashsha.pl: OK
     Installing stat.pl: OK
     Installing readlink.sh: OK
     Installing backdoorports.dat: OK
     Installing mirrors.dat: OK
     Installing programs_bad.dat: OK
     Installing suspscan.dat: OK
     Installing rkhunter.8: OK
     Installing ACKNOWLEDGMENTS: OK
     Installing CHANGELOG: OK
     Installing FAQ: OK
     Installing LICENSE: OK
     Installing README: OK
     Installing language support files: OK
     Installing ClamAV signatures: OK
     Installing rkhunter: OK
     Installing rkhunter.conf: OK
    Installation complete

Este método de instalación es interesante si vamos a **probar la herramienta y no queremos integrarla en el sistema**, así la podremos borrar fácilmente (eliminar directorio y listo). En el resto de casos, para eliminar rkhunter usaremos el parámetro –remove del instalador:

```sh
\# ./installer.sh --remove
```

## 3. Utilización/Modo de uso

En el caso de que vayamos a utilizar rkhunter de forma proactiva, es necesario **generar una base de datos** en la que indiquemos a la herramienta el estado inicial (y correcto) del sistema sobre el cual comparar futuros análisis. El comando para generar la base de datos es el siguiente:

```sh
\# **rkhunter --propupd**
```

    \[ Rootkit Hunter version 1.4.2 \]
    File created: searched for 171 files, found 118

    Para hacer un análisis básico del sistema, utilizamos el parámetro «-c» (**check**). Podemos personalizar el modo de análisis añadiendo o quitando diferentes tests. Actualmente, los test disponibles son los siguientes:

    Current test names:
        additional\_rkts all apps attributes avail\_modules deleted_files
        filesystem group\_accounts group\_changes hashes hidden\_ports hidden\_procs
        immutable known\_rkts loaded\_modules local_host malware network
        none os\_specific other\_malware packet\_cap\_apps passwd_changes ports
        possible\_rkt\_files possible\_rkt\_strings promisc properties rootkits running_procs
        scripts shared\_libs shared\_libs\_path startup\_files startup_malware strings
        suspscan system\_commands system\_configs trojans

    Grouped test names:
        additional\_rkts => possible\_rkt\_files possible\_rkt_strings 
        group\_accounts  => group\_changes passwd_changes 
        local\_host      => filesystem group\_changes passwd\_changes startup\_malware system_configs 
        malware         => deleted\_files hidden\_procs other\_malware running\_procs suspscan 
        network         => hidden\_ports packet\_cap_apps ports promisc 
        os\_specific     => avail\_modules loaded_modules 
        properties      => attributes hashes immutable scripts 
        rootkits        => avail\_modules deleted\_files hidden\_procs known\_rkts loaded\_modules other\_malware possible\_rkt\_files possible\_rkt\_strings running_procs suspscan trojans 
        shared\_libs     => shared\_libs_path 
        startup\_files   => startup\_malware 
        system\_commands => attributes hashes immutable scripts shared\_libs_path strings 

    Current languages:
        cn de en tr tr.utf8 zh zh.utf8

    Rootkits checked for:
        55808 Trojan - Variant A, AjaKit, aPa Kit, Adore, Apache Worm, Ambient (ark),
        Balaur, BeastKit, beX2, BOBKit, Boonana (Koobface.A), cb,
        CiNIK Worm (Slapper.B variant), CX, Danny-Boy's Abuse Kit, Devil, Dica, Dreams,
        Duarawkz, Enye LKM, Flea Linux, FreeBSD, Fu, Fuck`it,
        GasKit, Heroin LKM, HjC Kit, ignoKit, iLLogiC, Inqtana-A,
        Inqtana-B, Inqtana-C, IntoXonia-NG, Irix, Jynx, KBeast,
        Kitko, Knark, ld-linuxv.so, Li0n Worm, Lockit/LJK2, Mood-NT,
        MRK, Ni0, Ohhara, Optic Kit (Tux), OSXRK, Oz,
        Phalanx, Phalanx2, Portacelo, R3dstorm Toolkit, RH-Sharpe's, RSHA's,
        Scalper Worm, Shutdown, SHV4, SHV5, Sin, SInAR,
        Slapper, Sneakin, Solaris Wanuk, Spanish, Suckit, SunOS / NSDAP,
        SunOS Rootkit, Superkit, TBD (Telnet BackDoor), TeLeKiT, Togroot, T0rn,
        trNkit, Trojanit Kit, Turtle2, Tuxtendo, URK, Vampire,
        VcKit, Volc, w00tkit, weaponX, Xzibit, X-Org SunOS,
        zaRwT.KiT, ZK

De primeras, y ante la duda sobre tan abrumadora lista de pruebas, podemos lanzar un escaneo completo con todos los tests, así que lo ejecutamos:

```sh
\# rkhunter -c --enable all
```

Es el  momento para «disfrutar» de la salida por pantalla (o temblar con incertidumbre jaja). Es todo muy «gráfico», en verde lo OK y en rojo los problemas. No os voy a poner aquí la salida completa del informe pero sí alguna parte para que veáis los chequeos que hace. Después de cada sección solicita pulsar «Enter» para continuar, así podemos revisar con tranquilidad.

Análisis de archivos de sistema, binarios, librerías…

    Checking system commands...

      Performing 'strings' command checks
        Checking 'strings' command                               \[ OK \]

      Performing 'shared libraries' checks
        Checking for preloading variables                        \[ None found \]
        Checking for preloaded libraries                         \[ None found \]
        Checking LD\_LIBRARY\_PATH variable                        \[ Not found \]

      Performing file properties checks
        Checking for prerequisites                               \[ OK \]
        /usr/local/bin/rkhunter                                  \[ OK \]
        /usr/sbin/adduser                                        \[ OK \]
        /usr/sbin/chkconfig                                      \[ OK \]
        /usr/sbin/chroot                                         \[ OK \]
        /usr/sbin/depmod                                         \[ OK \]
        /usr/sbin/fsck                                           \[ OK \]
        /usr/sbin/groupadd                                       \[ OK \]
        /usr/sbin/groupdel                                       \[ OK \]
        /usr/sbin/groupmod                                       \[ OK \]
        /usr/sbin/grpck                                          \[ OK \]
        /usr/sbin/ifdown                                         \[ Warning \]
        /usr/sbin/ifup                                           \[ Warning \]

    \[...\]

Búsqueda de rootkits en todo el sistema:

    Checking for rootkits...

      Performing check of known rootkit files and directories
        55808 Trojan - Variant A                                 \[ Not found \]
        ADM Worm                                                 \[ Not found \]
        AjaKit Rootkit                                           \[ Not found \]
        Adore Rootkit                                            \[ Not found \]
        aPa Kit                                                  \[ Not found \]
        Apache Worm                                              \[ Not found \]

    \[...\]

Chequeos adicionales de rootkits, malware y específicos de Linux:

      Performing additional rootkit checks
        Suckit Rookit additional checks                          \[ OK \]
        Checking for possible rootkit files and directories      \[ None found \]
        Checking for possible rootkit strings                    \[ None found \]

      Performing malware checks
        Checking running processes for suspicious files          \[ Skipped \]
        Checking for login backdoors                             \[ None found \]
        Checking for suspicious directories                      \[ None found \]
        Checking for sniffer log files                           \[ None found \]
        Suspicious Shared Memory segments                        \[ None found \]
        Checking for Apache backdoor                             \[ Not found \]

      Performing Linux specific checks
        Checking loaded kernel modules                           \[ OK \]
        Checking kernel module names                             \[ OK \]

    \[...\]

Pruebas e inspeccion de la red y el host local: arranque de sistema, hostname, archivos de arranque en runlevels, malware en scripts de arranque, revisión de cuentas de usuario y grupos (passwd, shadow), usuarios sin password, configuración de ssh, filesystems…

    Checking the network...
    Performing checks on the network ports
     Checking for backdoor ports \[ Skipped \]
    Performing checks on the network interfaces
     Checking for promiscuous interfaces \[ None found \]
    Checking the local host...
    Performing system boot checks
     Checking for local host name \[ Found \]
     Checking for system startup files \[ Found \]
     Checking system startup files for malware \[ None found \]
    Performing group and account checks
     Checking for passwd file \[ Found \]
     Checking for root equivalent (UID 0) accounts \[ None found \]
     Checking for passwordless accounts \[ None found \]

    Versión de aplicaciones críticas:

    Checking application versions...

    Checking version of GnuPG                                \[ OK \]
    Checking version of OpenSSL                              \[ OK \]
    Checking version of OpenSSH                              \[ OK \]

Y por fin el resumen final con el resultado de los chequeos. Junto a las estadísticas se muestra la ruta al fichero de log con toda la información almacenada para su revisión:

System checks summary
=====================

    File properties checks...
        Files checked: 119
        Suspect files: 4

    Rootkit checks...
        Rootkits checked : 296
        Possible rootkits: 0

    Applications checks...
        Applications checked: 3
        Suspect applications: 0

    The system checks took: 6 minutes and 50 seconds

    All results have been written to the log file: /var/log/rkhunter.log

En este punto, lo importante es revisar cualquier problema que haya podido saltar en el análisis. Información extendida aparecerá en el log «**/var/log/rkhunter.log**»

### 3.1. Actualización de las bases de datos

Con el parámetro «–update» revisamos si hay actualizaciones (y actualizamos en caso afirmativo) referente a la información de rootkits, backdoors, malware, etc:

```sh
\# rkhunter --update
\[ Rootkit Hunter version 1.4.2 \]

Checking rkhunter data files...
  Checking file mirrors.dat                                  \[ No update \]
  Checking file programs_bad.dat                             \[ No update \]
  Checking file backdoorports.dat                            \[ No update \]
  Checking file suspscan.dat                                 \[ No update \]
  Checking file i18n/cn                                      \[ No update \]
  Checking file i18n/de                                      \[ No update \]
  Checking file i18n/en                                      \[ No update \]
  Checking file i18n/tr                                      \[ No update \]
  Checking file i18n/tr.utf8                                 \[ No update \]
  Checking file i18n/zh                                      \[ No update \]
  Checking file i18n/zh.utf8                                 \[ No update \]
```

### 3.2. Falsos positivos y personalización

Como es lógico, pueden aparecer falsos positivos. Para ello tenemos el archivo de configuración «/etc/rkhunter.conf» donde se pueden personalizar todos los parámetros, por ejemplo añadiendo scripts o binarios en lista blanca (SCRIPTWHITELIST), configurar alertas por correo electrónico (MAIL-ON-WARNING), configuraciones de SSH (ALLOW\_SSH\_ROOT_USER), etc.

**Después de cada cambio en la configuración hay que volver a actualizar la base de datos** de rkhunter, sino aparecerán alertas y errores:

```sh
\# rkhunter --propupd
```

### 3.3. Automatización de análisis

Para automatizar los análisis, simplemente añadimos una entrada en el [cron](https://rm-rf.es/crontab-modo-de-uso-ejemplos/ "crontab: modo de uso y ejemplos") de root que ejecute periódicamente el análisis según nuestros requerimientos. Podemos añadir el parámetro «–quiet» y «–cronjob» para evitar ruido al ser una ejecución desatendida. En este caso lo ejecutamos a las 8 de la mañana todos los días junto con un update por si hay actualizaciones:

```sh
crontab -u root -e

0 08 * * * /usr/bin/rkhunter --cronjob --update --quiet; /usr/bin/rkhunter --cronjob -c --enable all --quiet
```
Por supuesto, en lugar de añadirlo así al cron se puede crear un script más optimizado que realice el update y el chequeo según nuestros requerimientos. Después, basta con invocar ese script en el cron.

Como información adicional, os recomiendo realizar una revisión con las herramientas propias de sistema, por ejemplo una revisión de integridad de todos los paquetes instalados en el sistema. En RHEL, CentOS, Fedora, etc podéis [verificar la integridad y seguridad de ficheros con RPM](https://rm-rf.es/verificar-la-integridad-y-seguridad-de-ficheros-con-rpm/ "Verificar la integridad y seguridad de ficheros con RPM"). Y eso es todo por hoy. Suerte y espero que no tengáis mucha basurilla por vuestros sistemas ;)