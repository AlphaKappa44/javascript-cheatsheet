# Object Oriented Javascript
## Create Object 
There are multiple ways to create an object in Javascript. 

### First Way to Create Object 
```javascript 
// Create Object
var person = {
  name: 'Bob',
  age: 21,
  bio: function() {
    consoloe.log("Hi, I'm Bob");
  };
};
```

### Second Way to Create Object 
```javascript 
function Person(name, age) {
  this.name = name
  this.age = age;
  this.bio: function() {
    consoloe.log("Hi, I'm Bob");
  };
 };
}

// Create Object
var bob = new Person('Bob', 20);
```

### Third Way to Create Object
```javascript 
// Create Object
var person = new Object();

person.name = 'Bob';
person['age'] = 21;
person.greeting = function() {
  consoloe.log("Hi, I'm Bob");
};
```

### Fourth Way to Create Object 
```javascript 
// Create Object
var person = new Object({
  name: 'Bob',
  age: 21,
  greeting: function() {
    consoloe.log("Hi, I'm Bob");
  }
});
```

### Fifth Way to Create Object 
```swift
// Create Object
var newPerson = Object.create(person); // inheritance

newPerson.name
newPerson.greeting() // "Hi, I'm Bob"
```


### Sixth Way to Create Object 
```javascript 
function Person(name, age) {
    this.name = name;
    this.age = age;
    this.greet = function() {
      console.log("Hi, I'm Bob")
    }
};

Person.prototype.introduce = function() {
  console.log("Hi, I'm Bob")
};

// Create Object
let bob = Person("Bob", 21)
bob.greet() // "Hi, I'm Bob"
bob.introduce() // "Hi, I'm Bob"
```


## Inheritance 

### Design Parernt
```javascript 
var Parent = function() {
    this.name = "Paremt";
}

Parent.prototype.print = function() {
    console.log(this.name);
}

var parent = new Parent();

parent.print(); // "Parent"
```

## Design Child
```javascript
var Child = function() {
    this.name = "Child";
    this.initial = "Jr.";
}
```

## Design Function
```javascript
var inheritsFrom = function (child, parent) {
    child.prototype = Object.create(parent.prototype);
};

inheritsFrom(Child, Parent);
```

### Method Available 
```javascript 
var son  = new Child();
son.print(); // "Child"
```

### Override Method
```javascript 
Child.prototype.print = function() {
    Parent.prototype.print.call(this);
    console.log(this.initial);
}

son.print() // "Jr."
```

### Child to Grand Child

```javascript
var GrandChild = function() {
    this.name = "Grand Child";
    this.initial = "JrJr.";
}

inheritsFrom(GrandChild, Child);
```

```javascript 
GrandChild.prototype.dance = function() {
  console.log("Let me dance for you, Bob")
}

GrandChild.prototype.print = function () {
    Child.prototype.print.call(this);
    console.log(this.initial);
}
```

```javascript 
var grandChild = new GrandChild();
grandChild.print(); // "JrJr."
```

## `Call`
Call is like calling `super.init` in Swift 
```javascript
function Product(name, price) {
  this.name = name;
  this.price = price;
}

function Food(name, price) {
  Product.call(this, name, price);
  this.category = 'food';
}

function Toy(name, price) {
  Product.call(this, name, price);
  this.category = 'toy';
}

var cheese = new Food('feta', 5);
var fun = new Toy('robot', 40);
```



#### Need to Study More

> __proto__ is the actual object that is used in the lookup chain to resolve methods, etc. prototype is the object that is used to build __proto__ when you create an object with new:

```javascript 
( new Foo ).__proto__ === Foo.prototype
( new Foo ).prototype === undefined
```

``prototype` is a property of a Function object. It is the prototype of objects constructed by that function.


```javascript
function Point(x, y) {
    this.x = x;
    this.y = y;
}

var myPoint = new Point();

// the following are all true
myPoint.__proto__ == Point.prototype
myPoint.__proto__.__proto__ == Object.prototype
myPoint instanceof Point;
myPoint instanceof Object;
```

Here `Point` is a constructor function, it builds an object (data structure) procedurally. `myPoint` is an object constructed by `Point()` so `Point.prototype` gets saved to `myPoint.__proto__` at that time.







#### Study Materials: 
  - http://javascriptissexy.com/oop-in-javascript-what-you-need-to-know/
  - https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Basics
  - https://www.thecodeship.com/web-development/methods-within-constructor-vs-prototype-in-javascript/
  - https://www.sitepoint.com/simple-inheritance-javascript/
  - http://archive.oreilly.com/oreillyschool/courses/advancedjavascript/Advanced%20JavaScript%20Essentials%20v1.pdf
