# JavaScript - ECMASCRIPT

Programación Javascript

* * *


## 1. condificional IF

condicional if simple puede usarse de la siguiente forma

```javascript
const x = 10;

if (x === 10) {
	console.log('x es diez');
}
```
Tambien puede usarse el palabra **else** en el caso que no se cumpla una condicion

```javascript
const x = '10';

if (x === 10) {
	console.log('x es diez');
} else {
	console.log('x es menor a 10');
}
```

Tambien existe el **else if** para cuando se desee buscar otras condiciones

```javascript
const x = 4;

if (x === 10) {
	console.log('x es diez');
} else if(x > 10) {
	console.log('x es mayor a 10');
} else {
	console.log('x es menor a 10');
}
```

## 2. Condicional logico OR ||

el *or*(**||**) se ejecuta cuando una de las condiciones escritas es verdadera el resultado sera verdadero, en caso que no se cumpla ninguna de las dos sera falso.

```javascript
const x = 6;
const y = 10;

if (x > 5 || y > 10) {
	console.log('si x es mayor que 5 o si y es mayor que 10');
}
```

## 3. Condicional logico and &&

el *and*(**&&**) a diferencia del *or* solo ejectura verdadero cuando todas las condiciones escritas sean verdaderas.

```javascript
const x = 6;
const y = 11;

if (x > 5 && y > 10) {
	console.log('si x es mayor que 5 o si y es mayor que 10');
}
```
esta setencia es lo mismo que definir

```javascript
if(x <5) {
	if(y > 10) {
	}
}
```
* * *

## 4. If Ternario

El *if ternario* se cuando se utiliza una condición en una sola linea de codigo, `(condicion) ? verdadero : falso`

```javascript
const x = 11;
const color = x > 10 ? 'red' : 'blue';
console.log(color);
```

Como se ve en el codigo de arriba vemos si x es menor a 10 el valor sera red(*verdadero*) y en caso contrario sera blue(*falso*).

## 5. Condicional switch

El condicional **switch**, permite buscar una condición mediante multiples opciones hasta dar con la correcta y en caso contrario el default se activará al no encontrar.

```javascript
const x = 9;
const color = x > 10 ? 'red' : 'blue';

switch (color) {
	case 'red':
		console.log('color is red');
		break;
	case 'blue':
		console.log('color is blue');
		break;
	default:
		console.log('color no es red o blue');
		break;
}
```
* * *

## 6. Funciones en javascript

Las funciones se ocupan con la palabra **function** y permite devolver o retornar una acción.

```javascript
function addNums(num1= 1, num2= 1) {
	return num1 + num2;
}
console.log(addNums(5,5));
```
Desde la nueva actualización de ECMAscript las funciones se pueden utilizar de esta forma con arrow functions(*funciones flecha*)

```javascript
const addNums = (num1= 1, num2= 1) => {
	return num1 + num2;
}
console.log(addNums(5,5));
```

Tambien se puede simplificar  el arrya cuando cuenta con solo una línea de codigo no usando el **return** y dara como resultado cuando sea llamado la función `const addNums = (num1= 1, num2= 1) => num1 + num2;` o de esta forma llamando al **console.log** `const addNums = (num1= 1, num2= 1) => console.log(num1 + num2);`.

Cuando solo se posea un solo parametro se puede sacar los parantesis

```javascript
const addNums = num1  => num1 + 5;
console.log(addNums(5));
```

***
**TIPS** `todos.forEach((todo) => console.log(todo));`, esto permitira imprimir todo lo que contenga el objeto **todos**.
***

## 7. Creacion de objetos con funciones

```javascript
// constructor function
function Person(firstName, lastName, dob) {
	this.firstName = firstName;
	this.lastName = lastName;
	this.dob = new Date(dob);
}

// instanciar un objeto
const person1 = new Person('Pedro', 'las', '4-3-1980');
const person2 = new Person('Maria', 'Salas', '3-4-1974');

console.log(person1.firstName);
console.log(person2.firstName);
console.log(person2.dob.getFullYear() );
console.log(person1.dob.getFullYear() );
```

```javascript
function Person(firstName, lastName, dob) {
	this.firstName = firstName;
	this.lastName = lastName;
	this.dob = new Date(dob);
	this.getBirthYear = function() {
		return this.dob.getFullYear();
	}
	this.getFullName = function() {
		return `${this.firstName} ${this.lastName}`
	}
}

// instanciar un objeto
const person1 = new Person('Pedro', 'las', '4-3-1980');
const person2 = new Person('Maria', 'Salas', '3-4-1974');

console.log(person1.getBirthYear());
console.log(person1.getFullName());
```

* * *

## 8. Prototipos (prototypes en ingles)

Los **prototipos** son aquellas funciones o métodos genericos que permiten integrarse a un objeto como una función propia de este sin tener que ser instanciado y permite disminuir la memoria por que no se instancia por cada objeto creado. Los prototipos son similares a los metodos de las clases las cuales se aplican para todos los objetos instanciados por igual.

Como se puede puede ver en el ejemplo el objeto *Person* ya tiene dos prototipos creados reservando que la funcion que retorna la fecha y la otra que sirve para devolver el nombre completo son algo generico y por lo tanto se puede compartir con los demas objetos.

```javascript
function Person(firstName, lastName, dob) {
	this.firstName = firstName;
	this.lastName = lastName;
	this.dob = new Date(dob);
}

Person.prototype.getBirthYear = function() {
	return this.dob.getFullYear();
}

Person.prototype.getFullName = function() {
	return `${this.firstName} ${this.lastName}`
}

// instanciar un objeto
const person1 = new Person('Pedro', 'las', '4-3-1980');
const person2 = new Person('Maria', 'Salas', '3-4-1974');

console.log(person2.getFullName());
console.log(person1.getFullName());
console.log(person1);
```

* * *

## 9. Clases

En comparación a lo que era antes de ECMASCRIPT JS6, no contenia clases desde estas nuevas versiones de javascript se puden utilizar y tienen un codigo mas legible a la hora de escribir.

Como se puede apreciar en comparación de escribir codigo se ve más legible y permite de tener un codigo más organizado
```javascript
class Person {
	constructor(firstName, lastName, dob) {
		this.firstName = firstName;
		this.lastName = lastName;
		this.dob = new Date(dob);

	}

	getFullYear() {
		return this.dob.getFullYear();
	}

	getFullName() {
		return `${this.firstName} ${this.lastName}`
	}
}

// instanciar un objeto
const person1 = new Person('Pedro', 'las', '4-3-1980');
const person2 = new Person('Maria', 'Salas', '3-4-1974');

console.log(person2.getFullName());
console.log(person1.getFullName());
console.log(person1);
```
* * *

## 10. DOM

Aqui se podra ir modificando el Document Object Model de la página de javascript, se podra seleccionar algunos o todos los elementos del objecto windows

```javascript
// single element
const  form = document.getElementById('my-form')
console.log(document.getElementById('my-form'));
console.log(document.querySelector('h1'));
console.log(document.querySelector('.container'));

// multiple element
console.log(document.querySelectorAll('.item'));
// esta es una mejor opción para poder selecionar solo las clases
console.log(document.getElementsByClassName('item'));
console.log(document.getElementsByTagName('li'));
```
Tambien esta `console.log(document.getElementsByTagName('li'));`

### 10.1. Modificacion de los elementos

```javascript
const ul = document.querySelector('.items');

ul.remove();
ul.lastElementChild.remove();
ul.firstElementChild.textContent = 'Hello';
ul.children[1].innerText= 'Gonzalo';
ul.lastElementChild.innerHTML = '<h1>hola</h1>';

const btn = document.querySelector('.btn');
btn.style.background = 'red';
```

### 10.2. Eventos

```javascript
const btn = document.querySelector('.btn');

btn.addEventListener('click', (e) => {
	e.preventDefault();
	console.log('click');
	console.log(e);
	console.log(e.target);
	console.log(e.target.className);
	console.log(e.target.id);
});
```
Modificacion del raton mediante los evento click o el mouseout y este consiste cuando se posiciona sobre el elemento en este caso el boton al posicionarte y salir de este objeto se ejecutara las acciones  dentro del botón

```javascript
const btn = document.querySelector('.btn');

// btn.addEventListener('click', (e) => {
btn.addEventListener('mouseout', (e) => {
	e.preventDefault();
	document.querySelector('#my-form').style.background = '#ccc'
	document.querySelector('body').classList.add('bg-dark');
	document.querySelector('.items').lastElementChild.innerHTML = '<h1>Prueba</h1>';
});
```




* * *

## 11. Tips

### 11.1. Cuidado con el punto y coma

```javascript
const compute = (number) => {
	if (number > 5) {
		return number
		+2;
	}
	if (number > 2) {
	// **error aquí** return;
		return
		number * 2;
	}
};

console.log(compute(6));
console.log(compute(3));
```

En este codigo existe un error ya que al no ingresar un punto y coma **javascript** lo ingresara solo al ver un salto de línea.

* * *

## 12. Spread Operators

Los **spread operator** permiten ingresar una cantidad indeterminadas de parametros a una función sin necesidad de estar asignando variables, el funcionalidad ECMASCRIPT 6 al 8(ES2018)

```js
function multi(a,b,c) {
	return a * b * c;
}

const numeros = [5,2,7,4];

console.log(multi(...numeros));
```
Este código permite ingresar como argumentos una variable con multiples elementos sin necesidad de registrar los elementos individualmente, ya que el spread operator divide los elementos y en este caso solo seleccionara los 3 elementos que necesita la función para poder operar.

```js
let numeros = [1,2,3];
let numeros2 = [...numeros];

console.log(numeros2);

numeros2.push(4);

console.log(numeros);
console.log(numeros2);
```
En este código permite observar que se puede clonar los elementos usando el spread operators en la línea 2, pero al clonarlo significa que se esta haciendo una copia independiente de la original en la cual se puede agregar o modificar sin afectar a la otra.

```js
let numeros = [1,2,3];
let array = ["a", "b", "c",...numeros];
// let array = [...numeros,"a", "b", "c"];

console.log(array);
```
Se puede asignar a una lista como parte de la misma y agregara los elementos del array *numeros*

```js
let numeros = [1,2,3];
let numeros2 = [4,5,6];
let resultado = [...numeros, ...numeros2];

console.log(resultado);
```
Este código permite agregar el listado de las variables numeros, numeros2 y con ello agruparlos a la variable resultado que tendria los datos de los dos array(listas)

Ahora con ECMASCRIPT9(ES2018) se puede clonar objetos

```js
let persona = { nombre: "Gonzalo", edad: 34 };
let persona2 = { ...persona };

console.log(persona2);

persona2.frontend = false;

console.log(persona);
console.log(persona2);
```

Con ello al igual que al modificar array se puede clonar sin modificar el objeto original

ver [video](https://youtu.be/uRI5yV9tG60?t=180)

## 13. Snippets

Snippet para convertir un frase en una URL, transformar texto a slug.
```js
const slugify = str =>
  str
    .toLowerCase()
    .trim()
    .replace(/[^\w\s-]/g, '')
    .replace(/[\s_-]+/g, '-')
    .replace(/^-+|-+$/g, '');

Ejemplo:
slugify('Hello World!'); // 'hello-world'
```

* * *
este cod

```javascript
// var is obsolet, let, const

/* const age = 30;
 * age = 31; */

// console.log(age);

/* let score;
 * score = 10; */
/* const score = 10;
 * console.log(score); */

// Datatypes String, Number, null, undefined, Symbol

/* const name = 'Pedro';
 * const age = 31;
 * const rating = 4.5;
 * const isCool = true;
 * const x = null;
 * const y = undefined;
 * let z; // is the same undefined
 * console.log(typeof y); */

/* const name = 'Pedro';
 * const age = 31; */

// concatenacion
// console.log('Mi nombre es '+ name +' y tengo '+ age + ' años');

// Template String
/* const hello = `Mi nombre es ${name} y tengo ${age} años`;
 * console.log(hello); */

/* const s = 'Hola Mundo';
 * console.log(s.toUpperCase());
 * console.log(s.substring(0,5).toLocaleUpperCase()); */

/* const s = 'techology, computers, it, code';
 * console.log(s.split(',')); */

/* Arrays - variables con multiples valores */

/* const numbers = new Array(1, 2,3,4,5);
 * console.log(numbers); */

/* const fruits = ['apples', 'oranges', 'pears'];
 * // fruits = 'grapes'; this a error
 * fruits.push('mangos');
 * console.log(fruits);
 *
 * fruits.unshift('strawberries');
 *
 * fruits.pop();
 *
 * console.log(Array.isArray(fruits));
 * console.log(Array.isArray("hello"));
 *
 *
 * console.log(fruits.indexOf('oranges')); */

/* console.log(fruits[0]); */

/* const person = {
 *   firstName: 'Pedro',
 *   lastName: 'Lara',
 *   age: 30,
 *   hobbies: ['musica', 'peliculas', 'deportes'],
 *   address: {
 *     street: 'los sauces st',
 *     city: 'Los muermos',
 *     state: 'Los lagos'
 *   }
 * }
 *
 * // console.log(person);
 * // console.log(person.firstName, person.lastName);
 * // console.log(person.hobbies[1]);
 * // console.log(person.address.city);
 *
 * // Descontructor
 * const { firstName, lastName, address: {city} } = person;
 *
 * console.log(firstName, lastName);
 * console.log(city);
 *
 * person.email = 'plara@gmail.com';
 *
 * console.log(person.email); */

/* const todos = [
 *   {
 *     id: 1,
 *     text: 'Bota la basura',
 *     isCompleted: true
 *   },
 *   {
 *     id: 2,
 *     text: 'Reunion con la jefatura',
 *     isCompleted: true
 *   },
 *   {
 *     id: 3,
 *     text: 'Cita con el dentista',
 *     isCompleted: false
 *   }
 * ]; */

// console.log(todos);
// console.log(todos[1].text);

// const todoJSON = JSON.stringify(todos);
// console.log(todoJSON);

// Bucle For
/* for (let i = 0; i < 10; i++) {
 *   // console.log(i);
 *   console.log(`Número del loop: ${i}`);
 * } */

// Bucle while
/* let i = 0;
 * while(i < 10) {
 *   console.log(`Bucle while Número: ${i}`);
 *   i++;
 * }; */

/* for (let i = 0; i < todos.length; i++) {
 *   console.log(todos[i].text);
 * } */

/* for (let todo of todos) {
 *   console.log(todo.id);
 * } */

// forEach, map, filter
/* todos.forEach(function(todo) {
 *   console.log(todo.text);
 * }); */
/* const todoText = todos.map(function(todo) {
 *   return todo.text;
 * });
 * console.log(todoText); */

/* const todoCompleted = todos.filter(function(todo) {
 *   return todo.isCompleted === true;
 * }); */

/* const todoCompleted = todos.filter(function(todo) {
 *   return todo.isCompleted === true;
 * }).map(function(todo) {
 *   return todo.text
 * }); */

/* console.log(todoCompleted); */
```

