# Trucos o tips

## 1. Convertir un archivo JAR en un ejecutable Linux - /dev/blog

With Java programs it’s quite common to combine several classes into one [JAR archive](https://en.wikipedia.org/wiki/JAR_(file_format)). Java libraries are typically distributed this way as well.  
On Linux platforms, people are quite used to using command line programs, but sometimes it’s handy to distribute a java program as an executable file that can be run by a simple double-click instead of opening a terminal and typing `java -jar FancyProgram.jar`. Of course, one could always configure the desktop environment to associate JAR files with the corresponding executable from the Java Runtime Environment, but adding the JAR archive as a payload to a common shell script is much more universal.

Here’s a small stub of code that will launch the Java interpreter (i.e. the binary called `java`) with itself as the JAR file to run.

```sh
#!/bin/sh
MYSELF= which "$0" 2> /dev/null
[ $? -gt 0 -a -f` `"$0"` `] && MYSELF= "./$0" java=java
if test -n "$JAVA_HOME"; then
    java=``"$JAVA_HOME/bin/java"
fi
exec "$java" $java_args -jar $MYSELF "$@"
exit 1
```

To add the original JAR archive as payload and make the resulting file executable, run

```shell
cat stub.sh FancyProgram.jar > FancyProgram && chmod +x FancyProgram
```

Como resultado saldra un ejecutable llamado `./FancyProgram`.

Binary payloads in shell scripts also allow you do distribute entire software packages that could easily consist of hundreds of files as a single shell script, as described in a [great article from linuxjournal.com](http://www.linuxjournal.com/content/add-binary-payload-your-shell-scripts). To wrap JAR archives in native Windows executables, have a look at [http://launch4j.sourceforge.net](http://launch4j.sourceforge.net/).

Recursos:
[Fuente](https://coderwall.com/p/ssuaxa/how-to-make-a-jar-file-linux-executable)

## 2. Sacar cabeceras HTTP con cURL

Una entrada rápida y concisa para aprender cómo **extraer todas las cabeceras de una petición HTTP con cURL**. Lo único que hay que hacer es especificar el parámetro `-I` en la ejecución del comando:

```sh
curl -I URL

Ejemplo:

```shell
$ curl -I https://google.es
HTTP/2 301 
location: https://www.google.es/
content-type: text/html; charset=UTF-8
date: Sun, 31 May 2020 16:09:12 GMT
expires: Tue, 30 Jun 2020 16:09:12 GMT
cache-control: public, max-age=2592000
server: gws
content-length: 219
x-xss-protection: 0
x-frame-options: SAMEORIGIN
alt-svc: h3-27=":443"; ma=2592000,h3-25=":443"; ma=2592000,h3-T050=":443"; ma=2592000,h3-Q050=":443"; ma=2592000,h3-Q049=":443"; ma=2592000,h3-Q048=":443"; ma=2592000,h3-Q046=":443"; ma=2592000,h3-Q043=":443"; ma=2592000,quic=":443"; ma=2592000; v="46,43"
```

Por supuesto hay otras formas de sacar las cabeceras, incluso con el mismo cURL, pero al pasar el parámetro `-I` únicamente recibimos por salida estándar la información que necesitamos.