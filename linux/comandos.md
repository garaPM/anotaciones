# comandos

Comandos en Linux


## 1. Xsel

Permite copiar y pegar sin necesidad de utilizar el raton del mouse contenido

### 1.1. Ejemplos

Permite copiar el contenido de un archivo `cat foo.txt bar.txt | xsel -i`  o `ls | xsel -i`

Con `xsel -o` retorna o devuelve el contenido copiado con `xsel -i` 

`xsel -b` con este comando permite pegar el contenido copiado en clipboard o portapapeles de lo archivos selecionado y copiados

`xsel -b | vim -` Permite pegar el contenido en un editor de vim

[Fuente 1](https://fernandobasso.dev/shell/copy-paste-from-command-line-xclip-xsel-clipboard.html)


## 2. Xclip

` | xclip ` esto permite copiar el contenido de entrada

`xclip -o` Permite copiar el contenido del portapapeles o copiado


## 3. lsof
muestras todos los puertos estan escuchandos por los usuario activos

`lsof -Pan -i tcp -i udp`

## 4. 7Zip

Comando para comprimir y descromprimir en linuz

### 4.1. CREAR UN ARCHIVO 7Z
`7z a [nombre_archivo_salida].7z [archivo_a_comprimir]`

### 4.2. EXTRAER UN ARCHIVO 7Z

`7z e [nombre_archivo].7z`

### 4.3. CREAR OTROS FORMATOS DE ARCHIVO

```
7z a -t[formato] [nombre_Archivo] [archivo_a_comprimir]
# Ejemplo
7z a -ttar  comprimido comandos7Z.mp4
```

[Fuente + comandos](https://esgeeks.com/crear-extraer-7zip-linux-ejemplos-comandos/)

## 5. Zenity

Sirve para crear dialogos en linux

`zenity --password --title="sudo password prompt" --timeout=10`

[Ejemplo con contraseña](http://linux.dokry.com/cmo-solicito-la-contrasea-mediante-la-request-de-gui-mientras-uso-sudo-en-el-script.html)

