# ES6 Classes

### References

- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

### Definition and Examples

- Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 classalike semantics.

- Class syntax has two components:
  1. Class expressions and
  2. Class declarations.

#### Class Declaration

- One way to define a class is using a class declaration. To declare a class, you use the class keyword with the name of the class ("Rectangle" here).

```
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

#### Class Expressions

- A class expression is another way to define a class. Class expressions can be named or unnamed. The name given to a named class expression is local to the class's body.

```
// unnamed
let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// output: "Rectangle"

// named
let Rectangle = class Rectangle2 {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// output: "Rectangle2"
```

#### Class body and method definitions

- The body of a class is executed in strict mode.
- **Constructor** : The constructor method is a special method for creating and initializing an object created with a class. There can only be one special method with the name "constructor" in a class. A constructor can use the super keyword to call the constructor of the super class.
- Prototype methods:

```
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  // Getter
  get area() {
    return this.calcArea();
  }
  // Method
  calcArea() {
    return this.height * this.width;
  }
}

const square = new Rectangle(10, 10);

console.log(square.area)
```

- Generator methods:

```
class Polygon {
  constructor(...sides) {
    this.sides = sides;
  }
  // Method
  *getSides() {
    for(const side of this.sides){
      yield side;
    }
  }
}

const pentagon = new Polygon(1,2,3,4,5);

console.log([...pentagon.getSides()]);
```

- Static methods and properties : The static keyword defines a static method or property for a class. Static members (properties and methods) are called without instantiating their class and cannot be called through a class instance.

```
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  static displayName = "Point";
  static distance(a, b) {
    const dx = a.x - b.x;
    const dy = a.y - b.y;

    return Math.hypot(dx, dy);
  }
}

const p1 = new Point(5, 5);
const p2 = new Point(10, 10);
p1.displayName; // undefined
p1.distance;    // undefined
p2.displayName; // undefined
p2.distance;    // undefined

console.log(Point.displayName);      // "Point"
console.log(Point.distance(p1, p2)); // 7.0710678118654755
```

- Instance properties: Instance properties must be defined inside of class methods:

```
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

Static (class-side) data properties and prototype data properties must be defined outside of the ClassBody declaration:

```
Rectangle.staticWidth = 20;
Rectangle.prototype.prototypeWidth = 25;
```
