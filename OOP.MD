# Object Oriented Programming :bento:

## Table of contents

1. [Objects](#objects)
2. [prototype](#prototype)
3. [Inheritance](#inheritance)
4. [IIFE](#iife)

---

## Objects

Think about things people see every day, like cars, shops, and birds. These are all objects. What are some qualities of these objects? A car has wheel, shops sell items, birds have wings. These qualities, or properties, define what makes up an object. Similar objects share the same properties, but may have different values for those properties.
Objects in JavaScript are used to model real-world objects, giving them properties and behavior just like their real-world counterparts.
Objects can have methods, they are functions that add different behavior to an object.
Constructors are functions that create new objects. They define properties and behaviors that will belong to the new object. Think of them as a blueprint for the creation of new objects.

```JavaScript
function Bird(name, color) {
    this.name;
    this.color;
    this.numLegs = 2;
}

let blueBird = new Bird("Bruce", "blue");
```

Anytime a constructor function creates a new object, that object is said to be an instance of its constructor. JavaScript gives a convenient way to verify this with the `instanceof` operator. It returns `true` or `false` based on whether or not that object was created with the constructor.

```JavaScript
blueBird instanceof Bird //true
```

---

## prototype

Since `numLegs` will probably have the same value for all instances of `Bird`, you essentially have a duplicated variable `numLegs` inside each `Bird` instance. A better way is to use the `prototype` of `Bird`. Properties in the `prototype` are shared among all instances of `Bird`.

```JavaScript
Bird.prototype.numLegs = 2;
```

>Now all instances of `Bird` have the `numLegs` property

Own properties are defined directly on the object instance itself. And prototype properties are defined on the `prototype`.w
A more efficient way is to set the `prototype` to a new object that already contains the properties.
Setting the prototype to a new object erases the `constructor` property. This property can be used to check whick constructor function created the instance. Whenever a prototype is manually set to a new object, remember to define the `constructor` property.

```JavaScript
Bird.prototype = {
    constructor: Bird,
    numLegs: 2,
    eat: function() {
        console.log("nom nom nom");
    },
    describe: function() {
        console.log("My name is " + this.name)
    }
}
```

> the `isPrototypeOf` method can be used to check if a property is a prototype property

A `prototype` is an object, so it can have its own `prototype`.

```JavaScript
Object.prototype.isPrototypeOf(Bird.prototype)
```

---

## Inheritance

There's a principle in programming called *Don't Repeat Yourself (DRY)* The reason repeated code is a problem is because any change requires fixing code in multiple places. If a method, or property, exists in two similar classes, the code can be edited to follow the DRY principle by creating a `supertype` (or parent)

```JavaScript
function Animal() { };

Animal.prototype = {
    constructor: Animal,
    describe: function() {
        console.log("My name is " + this.name);
    }
}

let animal = Object.create(Animal.prototype);
Bird.prototype = Object.create(Animal.prototype);
```

>`Object.create(obj) creates a new object, and sets `obj` as the new object's `prototype` 

A constructor function that inherits its `prototype` object from a supertype constructor function can still have its own methods in addition to inherited methods.

```JavaScript
function Animal() { }
Animal.prototype.eat = function() {
  console.log("nom nom nom");
};
function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.constructor = Bird;

Bird.prototype.fly = function() {
  console.log("I'm flying!");
};
```

It's possible to override an inherited method. It's done by adding a method to `ChildObject.prototype`

```JavaScript
function Animal() { }
Animal.prototype.eat = function() {
  return "nom nom nom";
};
function Bird() { }

Bird.prototype = Object.create(Animal.prototype);

Bird.prototype.eat = function() {
  return "peck peck peck";
};
```

For unrelated objects, it's better to use mixins. A mixin allows other objects to use a collection of functions.

```JavaScript
let flyMixin = function(obj) {
  obj.fly = function() {
    console.log("Flying, wooosh!");
  }
};

let bird = {
  name: "Donald",
  numLegs: 2
};

let plane = {
  model: "777",
  numPassengers: 524
};

flyMixin(bird);
flyMixin(plane);
```

---

## IIFE

A common pattern in JavaScript is to execute a function as soon as it is declared

```JavaScript
(function () {
    console.log("Chirp, chirp!")
})();
```

The two parentheses at the end of the function expression cause it to be immediately executed or invoked. This patter is knows as an *immediately invoked function expression* or *IIFE* 