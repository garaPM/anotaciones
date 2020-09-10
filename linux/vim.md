# Vim

## 1. Configuraciones

- **crear un archivo o acceso** `vim +[número_linea] archivo.txt`
- **Permite descargar el diccionario en español** `set spelllang=es`
- **habilita el corrector ortografico** `set spell`
- **deshabilita el corrector ortografico** `nospell`
- **mostrar los números de linea** `set number`
- **no muestra los números de las lineas** `set nonumber`
- **habilita y deshabilita los números de la lineas** `set number!`
- **permite selecionar un esquema de colores** `colorscheme esquema`
- **Permite visualizar la linea del cursor** `set cursorline`
- **Cambiar el color de linea del cursor** `highlight CursorLine guidb=lightblue ctermbg=blue`
- **Crea un linea del curso en la columna** `set cursorcolumn`
- **Permite deshabilitar vi para reemplazar con las opciones de vim** `set nocompatible`
- **Permite el retroceso, la sangria y el inicio de inserción** `set backspace= indent, eol, start`
- **Establece un numero mayor de comando ejecutados es el historial** `set history=1000`
- **Muestra los comandos en parte inferior escrito en teclado** `set showcmd`
- **Muestra el modo actual en la parte inferior** `set showmode`
- **Vuelve a leer automáticamente los archivos** `set autoread`
- **Ocultas los buffers sin que se escriban en el disco duro, solo se recuerdan y se ven en el historial** `set hidden`
- **Habilita el número de líneas** `set nu`
- `jumps | :ju`


## 2. Abrir, modificar Archivos

- **Permite abrir muchos archivos pero se debe utilizar buffers** `vim [archivo 1] [archivo n]`
- **Permite abrir muchos archivos en ventanas verticales** `vim -o [archivo 1] [archivo n]`
- **Permite abrir muchos archivos en ventanas horizontales** `vim -O  [archivo 1] [archivo n]`
- **Abrir el último documento editado** `Ctrl + o + o`
- **Apretando escape entra modo comando** `Esc`
- **Deshacer cambio** `u`
- **Rehacer cambios** `Ctrl + r`
- **copiar contenido** `y`
- **pegar contenido** `p`
- **cortar contenido** `c`
- **el primero guarda, guarda y termina y el ultimo realizar termino con fuerza** `:w, :wq, :q!`
- **Permite eliminar los espacio o tabulaciones de la sangria en todo el bloque o documento hacia la izquierda del cursor** `=G`

## 3. Abrir multiples archivos

- `vim [archivo 1] [archivo n]`  **Permite abrir muchos archivos pero se debe utilizar buffers**
- `vim -o [archivo 1] [archivo n]`  **Permite abrir muchos archivos en ventanas verticales**
- `vim -O  [archivo 1] [archivo n]`  **Permite abrir muchos archivos en ventanas horizontales**
- **Permite ir saltando en pestañas** `CTRL-w w`
- **Permite ir hacia arriba en las pestañas** `CTRL-w k`
- **Permite ir hacia abajo en las pestañas** `CTRL-w j`
- **Permite ir hacia izquierda en las pestañas** `CTRL-w h`
- **Permite ir hacia derecha en las pestañas** `CTRL-w l`

## 4. Read

- **Inserta el texto el archivo seleccionado** `:r [nombre archivo]`
- **Inserta en el archivo la primera línea del archivo seleccionado.** `:0r [nombre archivo]`
- **Inserta las líneas 2 y 8 del archivo seleccionado en el documento actual.** `:r !sed -n 2,8p [nombre archivo]`
- **Insertar el resultado de comandos, por ejemplo** `:r ![comando]`

### 4.1. Ejemplos

- `:r !ls` **inserta en el documento el resultado y mostrara el resultado del directorio.**

## 5. Guardar

- **Guardar como** `:sav [nuevo archivo]`
- **Sobreescribir un archivo** `:w! [nombre archivo]`
- **guarda un archivo el buffer o el documento ha sido modificado** `:up[date] [nombre archivo]`

* * *

## 6. Modo Comando (Ex)

- **Entra en modo Ex** `!` **y puede ejecutar comando en **linux ****
- **representa el bang para corre comando bash o terminal** `!`
- **Representa el archivo actual** `%`

### 6.1. Ejercicios

- **ordená las cadenas de los archivos** `sort -u`
- **v es invertir e i que aplique modo case sensitive** `grep -vi`
- **filtra todas las lineas que no contenga Content-Security** `grep -V Content-Security`
- **Lista los archivos y directorios** `!ls`
- **Filtra todas las línes que posean el patrón asignado** `!grep -V (patron)`

* * *

## 7. Modo insertar (i)

- **insertar datos** `i`
- En modo inserción presionar `ctrl+o` y ejecutar el comando `5j` => esto volvera modo normal y el cursor volvera hacia atras 5 veces en modo *insertar*
- **Modo inserción en el mismo espacio del carácter posicionado** `i`
- **Insertara texto al principio de la línea posicionada** `I`
- **Insertara texto después de un carácter** `a`
- **Insertara texto al final de la línea.** `A`
- **Insertara texto debajo de la posición actual creando un salto de línea** `o`
- **Insertara texto arriba de la posición actual creando un salto de línea** `O`

### 7.1. Ejercicios

- **En modo inserción presionar** `ctrl+o` **y ejecutar el comando** `5j` **Esto volverá modo normal y el cursor volverá hacia atrás 5 veces en modo** *insertar*

* * *

## 8. Modo Copiar (y)

- **Copia la línea completa** `yy` o `Y`
- **Copia una palabras hacia delante** `yw`
- **Copia desde la posición del cursor hacia inicio de la línea** `y0`
- **Copia desde la posición del cursor hacia el final de la línea** `y$`

### 8.1. Ejercicio
- **Copia toda la linea actual** `yy`
- **copia la línea de la 8 a la 10 y la pega 17** `:8,10co17`

* * *

## 9. Modo visual (v)

- **Entra en modo visual.** `v`
- **Entra en modo bloque visual, permite seleccionar de forma independiente** `Ctrl-v`

### 9.1. Ejercicio

- **Podrá seleccionar un párrafo** `vap`

* * *

## 10. Modo Borrar (d)

- **Borra la línea completa.** `dd`
- **Borra cuatro palabras** `d4w`
- **Borra desde la posición al principio de la línea** `d0`
- **Borra desde donde esta el curso hacia el final de línea** `d$`
- **Borra desde la posición hacia atrás** `dgg`
- **Borra desde la posición hacia delante** `dG`
- **Borra en modo normal y actual como un delete** `x`
- **Borra en modo normal y actuá como una backdelete** `X`
- **apretar letra c barra invertirá borrara hasta la palabra descrita y podrá reescribir** `c/[palabra]`
- **podrá cambiar hasta la letra asignada** `ct [letra]`
- **podrá borrar la palabra en posición actual** `ce"`
- **Eliminar hasta el final de línea** `d$`
- **Eliminar la palabra donde esté el cursor** `diw`
- **apretar letra c barra invertirá borrara hasta la palabra descrita y podrá reescribir** '' `c/`*palabra* ''
- **podrá cambiar hasta la letra asignada** ''` ct`*letra* ''
- **podrá cambiar lo que esta adentro de la *"*** ''` ci"` ''
- **podrá borrar la palabra en posición actual** ''` ce"` ''
- **Eliminar hasta el final de línea** ''` d$` ''
- **Eliminar la palabra donde esté el cursor** ''` diw`  ''
- **Elimina una palabra y entra en modo inserción** `s`
- **Elimina una palabra hacia delante** `x`
- **Elimina una palabra en reversa del cursor** `X`
- **Eliminar tag de html rapido aplicar** `cit`


### 10.1. Ejercicios

- **Borrar rangos con regex** `/v/[expresion_regular]/d`
- **Elimina la línea de la 8 a la 10** `:8,10d`
- **Eliminar tag de html rapido aplicar** `cit` **sobre una etiqueta html**

* * *

## 11. modo Pegar(p)

- **Pega hacia delante de la posición del cursor** `p`
- **Pega hacia atrás de la posición del cursor** `P`
- **Pegar n números de veces** `[n]p`

### 11.1. Ejercicios

- **pega nueve veces** `9p`
- **Pega la línea de la 8 a la 10** `:8,10p`

* * *

## 12. Modo Búsqueda (/ o ?)

- **Buscar una palabra** `/*palabra por buscar*/`
- **Buscar de manera inversa** `?*palabra por buscar*/` =>
- **Realiza la búsqueda de la palabra en el documento** `/*palabra_buscar*`
- **Realiza la búsqueda de la palabra al principio de la línea** `/^*palabra_buscar*`
- **Realiza la búsqueda de la palabra al final de la línea** `/*palabra_buscar*$`
- **Realiza la búsqueda de forma inversa de la palabra en el documento** `?*palabra_buscar*`
- **Realiza la búsqueda de forma inversa la palabra al principio de la línea** `?^*palabra_buscar*`
- **Realiza la búsqueda de forma de la palabra al final de la línea**`?*palabra_buscar*$`
- **Salta a la siguiente coincidencia** `n`
- **Salta a la anterior coincidencia** `N`
- **Buscar la palabras cosa y casa** `/c[ao]sa`
- **Buscar la palabras que comienza con c y cualquier letra de la a hasta z** `/c[a-z]`
- **Buscar la palabras que comienza con c o C y cualquier letra de la a hasta z** `/[cC][a-z]`

* * *

## 13. Modo Sustituir o Reemplaza

- **Buscar y reemplazar una palabra** `%s/origen/cambio/g`
- **Buscar y reemplazar** `%s/origen/cambio/gc`
- `DW`
- **Elimina una palabra y entra modo inserción** `cw`
- **Elimina la línea y entra modo inserción** `cc`
- **Elimina de la posición hacia final de la línea y entra modo inserción** `C`
- **podrá cambiar lo que esta adentro de un símbolo** `ci[símbolo]`

### 13.1. Ejercicio
- **Reemplaza el patron por ejemplo "o" en las lineas** `:g/patron/normal ( @o | @q )`
- **Permite invertir de mayúsculas a minúsculas viceversa la línea** `g ~~`
- **comentar la línea usando el #** `:g/patron/s/#/g`
- **Cambiar lo que se encuentre en el paréntesis** `ci(`
- **cambiar las lineas de primera hasta el final del documento** `1,$s/lock/string/g`

* * *

## 14. Modo mover o unir

- **unir diferentes líneas de una sola** `J`

### 14.1. Ejercicios

- **Mover las línea de la 8 a la 10 y la traslada pega 17** `:8,10m17`
- **Une las línea de la 8 a la 10 en una separadas por un espacio** `:8,10j17`

* * *

## 15. Buffers

Permite ver las diferentes archivos cargados en el sistema

- **Irá a la pestaña siguiente.** `:n`
- **Ira a la pestaña siguiente.** `:N`
- **Entrega una listado de los archivos abierto con vim con números** `:buffers`
- **Se activa y visualizar el archivo contenido en el buffer** `:buffer [0-9]` o `:b [0-9]`
- **Irá al principio de la pestañas del buffer** `:bf`
- **Irá al final de las del buffer** `:bl`
- **Irá al siguiente archivo del listado del buffer** `:bn`
- **Irá al anterior archivo del listado del buffer** `:bp`
- **Irá al archivo especifico del listado del buffer** `:b [0-9]`
- **Cerrara la pestaña de archivo actual** `:bw`
- **Cerrara la pestaña archivo actual** `:bd`
- **Abrirá un archivo adicional para editar y agregara** `:e`

* * *

## 16. Funciones

crear funciones en **VIM** para citar, por ejemplo :

```
function !EchoQuote(quote)
    echo a:quote
endfunction
```

* * *

## 17. Plugins

### 17.1. NerdCommenter

 Es un plugin para realizar comentarios en vim, se debe realizar la siguiente configuración.
```js
 let mapleader ","
 set timeout timeoutlen = 1500
```
* **,cc** : Para activar el comentario se debe teclear
* **,ci** : descomentar la línea
* **,c+<tecla_espaciadora>** : permite alternar los sacar o colocar comentario
* **,cu** sirve igual para descomentar lineas

la Configuracion es la siguiente:
```zsh
 zsh
" Add spaces after comment delimiters by default

let g:NERDSpaceDelims = 1

"
Use compact syntax for prettified multi-line comments
let g:NERDCompactSexyComs = 1

" Align line-wise comment delimiters flush left instead of following code indentation
let g:NERDDefaultAlign = 'left'
```

### 17.2. NERDTREE Plugin

es un visualizador de archivos de vim

- lo activo mendiante F2 abrir o cerrar el menu
- con la letra **m** se podra

### 17.3. Plugin RIPGREP
Instalar en opensuse
`sudo zypper install ripgrep`

Agregar en plugin en vim como en [github.com/BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep#installation) `Plug 'BurntSushi/ripgrep'`

Esto sirve para utilizar con el comando **CocSearch** palabras dentro del archivo que uno quiera buscar y necesita este paquete y plugin para usarlo. Paginas de ejemplo que utilizan este paquete son:

- [medium.com/@michael.j.fettis](https://medium.com/@michael.j.fettis/vim-and-rg-ripgrep-af1c1e72d502)
- [Julia Evans](https://jvns.ca/blog/2017/09/10/vim-sessions/)


### 17.4. Plugin Coc

**Conquer of Completion(coc)** para instalar este plugin se tiene que tener instalado node en el pc y se puede agregar como `Plug 'neoclide/coc.nvim' , { 'branch' : 'release' }`, tiene la intelligent completion que permite el autocompletado y mostrar los errores que pueden surgir en el codigo de diversos lenguajes, la configuración que recomienda es esta.

```
" GoTo code navigation.
nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)
```

Se puede encontrar en [github.com/neoclide](https://jvns.ca/blog/2017/09/10/vim-sessions/)

### 17.5. Vim Sesssion 

Buscando info [julia evans](https://jvns.ca/blog/2017/09/10/vim-sessions/)



* * *

## 18. Tips con VIM

- `/v/`*expresion_regular*`/d`  **Borrar rangos con regex**
- `vap`  **podra seleccionar un parrafo**
- `Ctrl + o + o`  **abre el último documento editado**
- `J`  **Permite unir una selección de frase o palabras de diferentes líneas de una sola**
- `Shift + 5`  **Pemite saltar de un simbolo de apertura hacia el simbolo de cierre y viceversa**
- **Listar 1000 número de lineas** `:0put=range(1,1000)`
- **Reemplazar palabras** `1,$s/lock/string/g`
- **Reemplazo de espacios a sangria** `=G` Permite corregir de espacio a sangria en todo el bloque o documento hacia abajo del cursor.
- **Usar vim en la consola** `set -o vi`
- **remueve los separadores** `ls | awk -F' ' '{print $4}'`

### 18.1. Listar variable con número
i1 <Esc>
`Y999p` # Copia la linea y la pega 999 veces más
`VG` # Seleciona la linea y se va a la ultima línea.
`g<C-a>` # Seleciona en modo global para aplicar el efecto de autoincremento.

### 18.2. Calculadora

1. **debes presionar** `Ctrl+r` (en modo inserción)
2. **Después presionar el (=) más  el valor y presionar enter**

### 18.3. Como remover las ultimas caracteres

*primer método*

1.- `shift-A`
2.- `x`
3.- `.` (repite)

*segundo método*

1.- `/\.$` => borrara todos los puntos hasta el final

*tercer método*

1.- `:%s//`
2.- `:%s///`
3.- `*` // (buscara el ultimo palabra buscada )
4.-  `*`  %!xargs => buscara

### 18.4. Filtrar datos con filtros en awk

- `:%awk -F'FOO' '{print $3}` **Esto permite mostrar filtrar y mostrar en el documento el resultado filtrado borrando el resto de datos del documento, FOO es el campo separador**
- `:%awk -F':' '{print $3}` **ejercicios**

### 18.5. Abreviaciones

Las abreviaturas son **una forma rápida de escribir en un texto una palabra larga o un grupo de palabras que se repite muchas veces, sin necesidad de escribirla entera, simplemente una abreviación** que nosotros determinemos.

Esa abreviación, la podemos establecer solo para el documento actual y que no sea persistente una vez que lo cerremos, o la podemos establecer permanentemente en cualquier documento que abramos, **veamos cómo hacerlo.** Pongamos un ejemplo:

Podemos **crear una abreviatura para que cuando simplemente escribamos fsf en modo de insertar texto nos añada automáticamente en el texto “automágicamente”** el texto Free Software Foundation.

Para ello vamos a crear la abreviatura mediante el comando **:ab &lt;abreviatura&gt; &lt;texto&gt;** de la siguiente manera en nuestro ejemplo: `:ab fsf Free Software Foundation`

Si queremos que esa abreviatura este siempre activa, simplemente escribiremos ese mismo comando en nuestro fichero de configuración .vimrc. **Si no es así quedará activa sólo para el documento actual y mientras no lo cerremos, cuando lo cerremos se perderá.**

- `:iab estubo estuvo` Se puede establecer todas las abreviaturas que queramos para que nuestro trabajo sea más rápido, o podemos usarlas **para corregir errores comunes que tengamos.** De esta manera si escribimos por error estubo, Vim nos lo cambiará a la palabra correcta.
- `:ab` Podemos ver un listado de las abreviaturas que tenemos configuradas, para ello pulsamos y pulsamos enter y nos dará un listado de las que tenemos establecidas.
- `:una fsf` **Podemos borrar alguna** mediante el comando **:una** si ya no queremos usarla. Para ello hacemos lo siguiente:
- **Existen tres tipos de abreviaturas.** Las que hemos visto **:ab** que están activas tanto para el modo de insertar como de comandos. **:iab** activas en el modo insertar o **:cab** en el modo de comandos.

**Recursos**
[** Carla Schrode - Linux.com.**](https://www.linux.com/learn/intro-to-linux/2017/3/vim-shortcuts-and-text-searches)