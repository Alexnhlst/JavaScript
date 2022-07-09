# Object Oriented Programming :bento:

## Table of contents

1. [Objects](#objects)
2. [prototype](#prototype)

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