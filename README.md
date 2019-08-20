# Curso - JavaScript



## Arrays - Métodos

### Arrays - Métodos II

**.from(iterable)** - Convierte en array el elemento iterable.

```javascript
let word = 'Hola mundo';
console.log(Array.from(word));
console.log(word.split(' ')); 
```



**.sort([callback])** - Ordena los elementos de un array alfabéticamente(valor Unicode), si le pasamos un callback los ordena en función del algoritmo que le pasemos.

```javascript
	/* SORT */

const letter = ['b', 'z', 'a', 'c'];
const number = [3, 1, 7, 100, 300];

console.log(letter.sort());

console.log(number.sort((a,b)=>a-b)); //Orden de menor a mayor
console.log(number.sort((a,b)=>b-a)); //Orden de mayor a menor

function menorMayor(a, b) {
if (a-b < 0) return -1;
if (a-b > 0) return 1;
if(a == b) return 0;
}
function mayorMenor(a, b) {
if (b-a < 0) return -1;
if (b-a > 0) return 1;
if(b == a) return 0;
}
```



**.forEach(callback(currentValue, [index]))** - ejecuta la función indicada una vez por cada elemento del array.

```javascript
const number = [12, 25, 47, 84, 98];

number.forEach((number) => console.log(number));
number.forEach((number, index) => console.log(`${number} está en la posición ${index}`));
```



**.some(callback)** - Comprueba si al menos un elemento del array cumple la condición.
**.every(callback)** - Comprueba si todos los elementos del array cumplen la condición.

```javascript
const words = ['HTML', 'CSS', 'JavaScript', 'PHP'];

console.log(words.some(word => word.length > 3 ));
console.log(words.every(word => word.length > 3 ));
```



**.map(callback)** - Transforma todos los elementos del array y devuelve un nuevo array.

```javascript
/* Map */

const numbers = [12, 25, 47, 84, 98];

//numbers.map(number => console.log(number*2));

const numbers2 = numbers.map(number => number*2);
console.log(numbers2);

for (const number of numbers) {
	console.log(number*2);
}
```



**.filter(callback)** - Filtra todos los elementos del array que cumplan la condición y devuelve un nuevo array.

```javascript
/* Filter */

const numbers = [12, 25, 47, 84, 98];

const numbers2 = numbers.filter(number => number>40);
console.log(numbers2);
```



**.reduce(callback)** - Reduce todos los elementos del array a un único valor.

```javascript
/* Reduce */

const numbers = [1, 2, 3, 4, 5];
console.log(numbers.reduce((a,b) => a+b));
```



## Clases y objetos - Práctica guiada.

```javascript
/* 
Crea una clase Libro

La clase libro tendrá título, autor, año y género.

Crea un método que devuelva toda la información del libro

Pide 3 libros y guárdalos en un array

Los libros se introducirán al arrancar el programa pidiendo los datos con prompt.

Validar que los campos no se introduzcan vacíos

Validar que el año sea un número y que tenga 4 dígitos

Validar que el género sea: aventuras, terror o fantasía

Crea una función que muestre todos los libros

Crea una función que muestre los autores ordenados alfabéticamente

Crea una función que pida un género y muestre la información de los libros que pertenezcan a ese género usando un el método que devuelve la información
*/

class Book {

​    constructor(title, author, year, gender) {
​        this.title = title;
​        this.author = author;
​        this.year = year;
​        this.gender = gender;
​    }

​    getAuthor() {
​        return this.author;
​    }

​    getGender() {
​        return this.gender;
​    } 

​    bookInfo() {
​        return `${this.title} es un libro de ${this.gender} escrito por ${this.author} en el año ${this.year}`
​    }

}

let books = [];

while (books.length<3) {
​    let title = prompt('Introduce el título del libro')
​    let author = prompt('Introduce el autor del libro')
​    let year = prompt('Introduce el año del libro')
​    let gender = prompt('Introduce el género del libro').toLowerCase()

​    if(title != '' && author != '' && !isNaN(year) && year.length==4 &&
​       (gender == 'aventuras' || gender == 'terror' || gender == 'fantasía')){
​           books.push(new Book(title, author, year, gender))
​       }
}

const showAllBooks = () => {
​    console.log(books);
}

const showAllAuthor = () => {
​    let authors = [];
​    for (const book of books) {
​        authors.push(book.getAuthor());
​    }
​    console.log(authors.sort());
}

const showGender = () => {
​    const gender = prompt('Introduce el género a buscar');
​    for (const book of books) {
​        if (book.getGender() == gender) {
​            console.log(book.bookInfo());
​        }
​    }
}

showAllBooks();
showAllAuthor();
showGender();
```

