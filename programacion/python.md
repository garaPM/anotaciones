# python

[Curso HCanalesMX](https://www.twitch.tv/videos/751871964?t=0h29m51s)

## 1. Variables

es una locación de memoria el cual es dar un nombre a un espacio de memoria.

- int
- float
- Dict (Diccionario)
- Boolean (Boleanos)
- List (Listas) []
- Tuples (Tuplas)

### 1.1. Listas

```py
n = [1,2,3,4]
for n in g:
   print(n)
```

### 1.2. Diccionario

hh = { "key1": "value1", "key2": "value2" }
for key, value in hh.items():
print(key, value)
>>> ('key2', 'value2')
>>> ('key1', 'value1')

### 1.3. Tuplas

No se puede modificar

### 1.4. Set Conjuntos





### 1.5. Asignacion(=) vs comparacion(==)

El = sirve para asignar vairables en cambio == sirve para comparar las variables

## 2. bucles 

### 2.1. For

```py
ll = [1,2,3,4,5,6,7,8,9]

for idx in ll:
    print(idx)
```

```py
ff = 5
ll = [1,2,3,4,5,6,7,8,9,10]

for idx in ll:
	print(5 * ll)
```

```py
hh = [{"nombre": "Gonzalo", "apellido": "Ruiz"}, {"nombre": "jose", "apellido": "Perez"}]

for idx in hh:
	print(idx["nombre"])
```

```py
hh = [{"nombre": "Gonzalo", "apellido": "Ruiz"}, {"nombre": "jose", "apellido": "Perez"}]

for idx in hh:
	print(idx["nombre"])

for idx in hh:
	print(idx["apellido"])
```



## 3. Tips

### 3.1. Sumar el ultimo registro de una lista
En el siguiente permite sumar el ultima registro de la lista es decir `2+2=4` ya que `lst[-1](2) += lst.pop()(2)`

```py
lst = [0,1,2]
lst[-1] += lst.pop()
lst
>>> [0, 4]
```
### 3.2. Unir dos lista con itertools
En este truco permite que dos lista se unan y se transforme en una lista con dos tuplas a través del módulo **itertools** con el método *zip_longest*, comos se puede ver en el ejemplo

```py
from itertools import zip_longest
x = [1,2]; y=[3]
list(zip_longest(x,y))
>>> [(1, 3), (2, None)]
```

### 3.3. Usar * para imprimir más separador

Con el * antes del nombres la variable extraer el contenido de la lista y unir el contenido de un a traves  separandolo en espacios y dando un resultado string o texto unido. con el comando **sep** permite definir el separador del resultado.

```py
letras = ['a','b','c','d','e']
numeros = [1,2,3,4,5]
print(letras)
>>> ['a', 'b', 'c', 'd', 'e']
print(*letras, sep=", ")
>>> a, b, c, d, e
print(numeros)
>>> [1, 2, 3, 4, 5]
print(*numeros, sep="-")
>>> 1-2-3-4-5
```

### 3.4. usar divmod para separar años y meses

Con la función **divmod** permite convertir los meses en años y meses respectivos.

```py
divmod(1,12)
>>> (0, 1) # 0 años y 1 mes
divmod(12,12)
>>> (1, 0) # 1 año y 0 meses
divmod(55,12)
>>> (4, 7) # 4 años y 7 meses
```

### 3.5. Crear un archivo zip

Con esto permite crear un archivo zip y comprimir los archivos data.csv y test.log.

```py
from zipfile import ZipFile
with ZipFile('my.zip','w') as zip_ref:
    zip_ref.write('data.csv')
    zip_ref.write('test.log')
```

### 3.6. Formas de mostrar un resultado en REPL

En dos líneas
```py
>>> q = 3.5 * 1.5
>>> q
5.25
```

En una segunda expresión
```py
>>> q = 3.5 * 1.5;q
5.25
```
Forma Walrus
```py
>>> (q := 3.5 * 1.5)
5.25
```
Invisible no se mostrara el resultado en el REPL de python
```py
>>> q = 3.5 * 1.5
```