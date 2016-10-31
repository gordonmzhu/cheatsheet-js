# cheatsheet-js
A super condensed JavaScript reference for Watch and Code students.

# `this`

#### 1. In a regular function, `this` points to `window`. This is the default case.

```javascript
function logThis() {
  console.log(this);
}

logThis(); // window
```

#### 2. In a method, `this` points to the object that contains the method. 

```javascript
var myObject = {
  myMethod: function() {
    console.log(this);
  }
};

myObject.myMethod(); // myObject

/ *
  * However, for functions that are called inside of myObject.myMethod
  * (like anotherFunction), `this` will revert to the default case.
/ *

function anotherFunction() {
  console.log(this);
}

var anotherObject = {
  anotherMethod: function() {
    anotherFunction();
  }
};

anotherObject.anotherMethod(); // window
```

#### 3. In a callback function, assume the default case unless the outer function explicitly sets `this`.

```javascript
function outerFunction(callback) {
  callback();
}

outerFunction(function() {
  console.log(this); // window
});
```

#### 4. In a function that's being called as a constructor, `this` points to the object that the constructor is creating.

```javascript
function Person(name) {
  this.name = name;
}

var gordon = new Person('gordon');
console.log(gordon); // {name: 'gordon'}
```

#### 5. When you explicitly set the value of `this` manually using `bind`, `apply`, or `call`, it's all up to you.

```javascript
function logThis() {
  console.log(this);
}

var explicitlySetLogThis = logThis.bind({name: 'Gordon'});

explicitlySetLogThis(); // {name: 'Gordon'}
```
