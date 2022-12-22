# JavaScript Array metoder

#### Vad är array methoder.

I JavaScript finns det något som heter **_Built in methods_**. Vi finner att **_build in methods_**
finns tillgängligt för strings, objekt, arrays osv. Dessa metoder är funktioner som hjälper oss att kunna
manipulera data och förstå data.

#### Varför finns array methoder.

Att kunna manipulera data såväl som att flytta data från a till b är en elementär del av JavaScript.
Arrays är en datastruktur som finns för att kunna organisera vår data i form av listor. Det kan vara en
lista av användare, produkter eller star wars characters.

#### Vad finns i det här repository.

Vi kommer utforska en del array metoder i olika scenarion. Notera att array metoder fungera olika
och att en del av dem retunerar en array och vissa inte.
För mer information se: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

Vi kommer gå igenom följande

- MAP
- FILTER
- SOME
- EVERY
- REDUCE
- FIND

## Exemple Data 1 **Characters**

Här är ett API som ni kan använda istället för datan nedanför [Star Wars API](https://swapi.dev/).

```javascript
const characters = [
  {
    name: "Luke Skywalker",
    height: "172",
    mass: "77",
    eye_color: "blue",
    gender: "male",
  },
  {
    name: "Darth Vader",
    height: "202",
    mass: "136",
    eye_color: "yellow",
    gender: "male",
  },
  {
    name: "Leia Organa",
    height: "150",
    mass: "49",
    eye_color: "brown",
    gender: "female",
  },
  {
    name: "Anakin Skywalker",
    height: "188",
    mass: "84",
    eye_color: "blue",
    gender: "male",
  },
];
```

## MAP

1. Get an array of all names
2. Get an array of all heights
3. Get an array of objects with just name and height properties
4. Get an array of all first names

## REDUCE

1. Get the total mass of all characters
2. Get the total height of all characters
3. Get the total number of characters in all the character names
4. Get the total number of characters by eye color (hint. a map of eye color to count)

## FILTER

1. Get characters with mass greater than 100
2. Get characters with height less than 200
3. Get all male characters
4. Get all female characters

## SORT

1. Sort by name
2. Sort by mass
3. Sort by height
4. Sort by gender

## EVERY

1. Does every character have blue eyes?
2. Does every character have mass more than 40?
3. Is every character shorter than 200?
4. Is every character male?

## SOME

1. Is there at least one male character?
2. Is there at least one character with blue eyes?
3. Is there at least one character taller than 200?
4. Is there at least one character that has mass less than 50?

## Exemple Data 2 **Users**

```javascript
const users = [
  {
    id: 1,
    name: "Leia",
    email: "Leia@gmail.com"
    isOnline: false,
    age: 25,
  },
  {
    id: 2,
    name: "Look",
    email: "Look@gmail.com"
    isOnline: true,
    age: 36,
  },
  {
    id: 3,
    name: "James",
    email: "James@gmail.com"
    isOnline: true,
    age: 35,
  },
  {
    id: 4,
    name: "Brook",
    email: "Brook@gmail.com"
    isOnline: false,
    age: 32,
  },
  {
    id: 5,
    name: "Havana",
    email: "Havana@gmail.com"
    isOnline: false,
    age: 29,
  },
];
```

## MAP

**Retunerar en array (manipulerad eller inte), används för att manipulera data eller bara lista befintlig data**

1. Lista allas namn
2. Lista allas age
3. Lista en array med objekt med properties name och age.
4. Ändra namn på obj id 2 till Abraham.
5. Lista allas email i en array.

## FILTER

**Retunerar en array (filtrerad), används för att ta bort element man inte vill ha**

1. Lista alla som är isOnline === true
2. Lista alla som är under 30 år
3. Lista alla som har ett name under 5 bokstäver långt.

## SOME

**Retunerar boolean används för att validera / kolla om det finns något i arrayen**

1. Kolla om någon är online
2. Kolla om det finns någon över åldern 30.
3. Kolla om det finns någon med fler än 5 bokstäver långt namn.

## FOREACH

**Retunerar ingenting, används för att loopa över en array och göra någon form av funktion för varje element**

1. Räkna ut medel åldern för alla users.
2. Räkna ut hur många bokstäver allas namn innehåller.
3. Räkna ut totala åldern för alla users.

## Exemple Data 3 **Products**

```javascript
const products = [
  {
    id: 1,
    title: "Iphone 9",
    price: 8998,
    inStock: true,
    totalAmount: 99,
    discount: true,
  },
  {
    id: 2,
    title: "Iphone 10",
    price: 9998,
    inStock: true,
    totalAmount: 5,
    discount: true,
  },
  {
    id: 3,
    title: "Iphone 11",
    price: 10800,
    inStock: false,
    totalAmount: 0,
    discount: false,
  },
  {
    id: 4,
    title: "Iphone 12",
    price: 11500,
    inStock: true,
    totalAmount: 58,
    discount: true,
  },
  {
    id: 5,
    title: "Iphone 13",
    price: 12998,
    inStock: true,
    totalAmount: 99,
    discount: false,
  },
];
```

## MAP

1. Ändra alla produkters property discount till false.
2. Lista alla produkters namn i en ny array.
3. Ändra discount på produkten med id 5 till true.
4. Ändra price på alla produkter med discount === true, till priset reducerat med 12%.

<details><summary>Facit</summary>

```javascript
/* 1 */
const changedProducts = products.map((product) => {
  if (product.discount === true) {
    return { ...product, discount: false };
  } else {
    return product;
  }
});
/* 2 */
const changedProducts = products.map((product) => {
  return product.name;
});
/* 3 */
const changedProducts = products.map((product) => {
  if (product.id === 5) {
    return { ...product, discount: true };
  } else {
    return product;
  }
});
/* 4 */
const changedProducts = products.map((product) => {
  if (product.discount === true) {
    let newPrice = product.price * 0.88;
    return { ...product, price: newPrice };
  } else {
    return product;
  }
});
```

</details>

## FILTER

1. Filtrera bort alla produkter som inte har discount === true.
2. Filtrera bort alla produkter som har ett pris över 10000kr.
3. Filtrera bort alla produkter som inte är inStock === true.
<details><summary>Facit</summary>

```javascript
/* 1 */
const withDiscount = products.filter((product) => {
  return product.discount === true;
});
/* 2 */
const withPriceFilter = products.filter((product) => {
  return product.price < 10000;
});
/* 3 */
const inStock = products.filter((product) => {
  return product.inStock === true;
});
```

</details>

## FOREACH

1. Räkna ut total priset för alla produkter.
2. Räkna ut totala discount beloppet på alla produkter, med discount på 12%.
3. Räkna ut det totala antalet produkter in stock.

<details><summary>Facit</summary>

```javascript
/* 1 */
let sum = 0;
products.forEach((product) => {
  sum += product.price;
});
/* 2 */
let sum = 0;
products.forEach((product) => {
  sum += product.price;
});
const discount = sum * 0.88;
/* 3 */
let sum = 0;
products.forEach((product) => {
  sum += product.inStock;
});
```

</details>

## EVERY

1. Kolla om alla produkter har ett pris över 7000kr.
2. Kolla om alla produkter är inStock === true.

<details><summary>Facit</summary>

```javascript
/* 1 */
const isOver = products.every((product) => {
  return product.price < 7000;
});
/* 2 */
const isInStock = products.every((product) => {
  return product.inStock === true;
});
```

</details>

## SOME

1. Kolla om det är någon produkt som har ett pris över 15000kr.
2. Kolla om det är någon produkt som inte är inStock === true.
3. Kolla om det är någon produkt som har samma id.

<details><summary>Facit</summary>

```javascript
/* 1 */
const isOver = products.some((product) => {
  return product.price < 15000;
});
/* 2 */
const isInStock = products.some((product) => {
  return product.inStock === true;
});
/* 3 */
const sameId = products.some((product, index, arr) => {
  let target = arr.some((p) => p.id === product.id);
  if (target) return true;
});
```

</details>
