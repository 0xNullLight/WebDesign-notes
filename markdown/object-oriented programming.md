---
aliases: ["OOP", "classical inheritance"]
---
- centered around the concept of [[class|classes]]
	- e.g. **cookies cutter**
	- an [[instance]] is an [[object]] or for analogies sake it is the *cookie*
- template for [[Zettelkasten/Cyber/object|objects]]

## prototypal inheritance
- in #javascript we capitalize the first letter of the name of the function to indicate a [[class]]
- #javascript **approximates** object-oriented programming because under the hood it is [[prototypal]]
	- #javascript does not implement classes in the true sense. It is unable to implement classical inheritance needed for object-oriented programming
- ES6 allows you to be more disguised because it uses `class` keyword

```js
function Dog(name, age, breed) {
  this.name = name;
  this.age = age;
  this.breed = breed;
  // this is called a "method" of the Class
  // e.g. Function.prototype.apply() / Array.prototype.map()
  this.nap = function () {
    console.log('Zzzzzzzzz');
  };
}
```

```js
// this is a class yet...really its a function and also technically an object
function Dog {

}
```

```js
// ES6 looks like a python-like "classical" implementation with "syntactic sugar"
class Cat {
  constructor(name, age, breed) {
    this.name = name;
    this.age = age;
    this.breed = breed;
  }

  nap() {
    console.log('Zzzzzzzzz');
  }
}
```
