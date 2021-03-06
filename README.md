# LEARNING - JAVASCRIPT

these are some of the most used methods

## MAP
concept:
![Proceso del Map()](https://miro.medium.com/max/1257/1*4EGwsCicbWJeml2aAm714A.gif)
Syntax:

Example:

Supongamos que ha recibido una matriz que contiene varios objetos, cada uno de los cuales representa a una persona. Sin embargo, lo que realmente necesita al final es una matriz que contenga solo la identificación de cada persona
```js
// What you have
var officers = [
  { id: 20, name: 'Captain Piett' },
  { id: 24, name: 'General Veers' },
  { id: 56, name: 'Admiral Ozzel' },
  { id: 88, name: 'Commander Jerjerrod' }
];
// What you need
[20, 24, 56, 88]
```
Using `.forEach()`:
```js
var officersIds = [];

officers.forEach(function (officer) {
  officersIds.push(officer.id);
});

console.log(officersIds);  // we obtains [20, 24, 56, 88]
```
using `.map()`:
```js
var officersIds = officers.map(function (officer) {
  return officer.id
});

console.log(officersIds);  // we obtains [20, 24, 56, 88]
```
something much better using **ES6 support**:
```js
var officersIds = officers.map(officer => officer.id);

console.log(officersIds);  // we obtains [20, 24, 56, 88]
```
## REDUCE
concept:

The `reduce()` method is used to apply a function to each element in the array to reduce the array to a single value.
![Proceso del Map()](https://miro.medium.com/max/1257/1*dhTC_FFgiH3mKROrnDj12w.gif)

Syntax:
```js
let result = arr.reduce(callback);
// Optionally, you can specify an initial value
let result = arr.reduce(callback, initValue);
```

Example:

Let's say you have pilot data and their respective years of experience

```js
var pilots = [
  {
    id: 10,
    name: "Poe Dameron",
    years: 14,
  },
  {
    id: 2,
    name: "Temmin 'Snap' Wexley",
    years: 30,
  },
  {
    id: 41,
    name: "Tallissan Lintra",
    years: 16,
  },
  {
    id: 99,
    name: "Ello Asty",
    years: 22,
  }
];
```
Necesitamos conocer el total de años de experiencia de todos ellos.
```js
var totalYears = pilots.reduce(function (accumulator, pilot) {
  return accumulator + pilot.years;
}, 0);
```
something much better using **ES6 support**:
```js
const totalYears = pilots.reduce((acc, pilot) => acc + pilot.years, 0);

console.log(totalYears);  // we obtains 82
```
Now let’s say I want to find which pilot is the most experienced one. For that, I can use reduce as well:
```js
var mostExpPilot = pilots.reduce(function (oldest, pilot) {
  return (oldest.years || 0) > pilot.years ? oldest : pilot;
}, {});
```

## FILTER
concept
![Proceso del Map()](https://miro.medium.com/max/1257/1*TOPYVvfMBmjajPh-fqZ9GQ.gif)
Syntax

Example:

What if you have an array, but only want some of the elements in it? That’s where .`filter()` comes in!

```js
var pilots = [
  {
    id: 2,
    name: "Wedge Antilles",
    faction: "Rebels",
  },
  {
    id: 8,
    name: "Ciena Ree",
    faction: "Empire",
  },
  {
    id: 40,
    name: "Iden Versio",
    faction: "Empire",
  },
  {
    id: 66,
    name: "Thane Kyrell",
    faction: "Rebels",
  }
];
```
Say we want two arrays now: one for rebel pilots, the other one for imperials. With .filter() it couldn’t be easier!

```js
var rebels = pilots.filter(function (pilot) {
  return pilot.faction === "Rebels";
});
var empire = pilots.filter(function (pilot) {
  return pilot.faction === "Empire";
});

console.log('These are the rebels',rebels);
console.log('these are the imperial ones',empire);
```
something much better using **ES6 support**:

```js
const rebels = pilots.filter(pilot => pilot.faction === "Rebels");
const empire = pilots.filter(pilot => pilot.faction === "Empire");

console.log('These are the rebels',rebels);
console.log('these are the imperial ones',empire);
```

a much more practical case

```js
data = [
  {
    name: 'Butters',
    age: 3,
    type: 'dog'
  },
  {
    name: 'Lizzy',
    age: 6,
    type: 'dog'
  },
  {
    name: 'Red',
    age: 1,
    type: 'cat'
  },
  {
    name: 'Joey',
    age: 3,
    type: 'dog'
  },
];
```
**The goal is going to be to write some JavaScript that will sum all of the dogs ages in dog years.**

```js
let ages = data
  .filter((animal) => {
    return animal.type === 'dog';
}).map((animal) => {
    return animal.age * 7
}).reduce((sum, animal) => {
    return sum + animal;
},0);
console.log(ages)// ages = 84
```



## ENLACES
* [Simplify your JavaScript – Use .map(), .reduce(), and .filter()](https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d)
* [Learn & Understand JavaScript’s Reduce Function](https://codeburst.io/learn-understand-javascripts-reduce-function-b2b0406efbdc)
* [JavaScript — Learn to Chain Map, Filter, and Reduce](https://codeburst.io/javascript-learn-to-chain-map-filter-and-reduce-acd2d0562cd4)
* [Map, Filter and Reduce – Animated](https://medium.com/@js_tut/map-filter-and-reduce-animated-7fe391a35a47)
* [How JavaScript’s Reduce method works, when to use it, and some of the cool things it can do](https://medium.com/free-code-camp/reduce-f47a7da511a9)
