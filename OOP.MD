# Object Oriented Programming :bento:

## Table of contents

1. [Objects](#objects)
2. [prototype](#prototype)
3. [Inheritance](#inheritance)

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