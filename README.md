# cheatsheet-js
A super condensed JavaScript reference for [Watch and Code](https://watchandcode.com/) students.

# Required resources

- [Watch and Code](http://watchandcode.com/p/premium)
- [How to be great at asking coding questions](https://medium.com/@gordon_zhu/how-to-be-great-at-asking-questions-e37be04d0603#.y2roq84t7)

# How to read source code

### Wny it’s important

1. Most of your time will be spent reading, not writing.
2. Simulates working at a company or open source project.
3. It's the fastest way to learn and improve.
5. Learn how to ignore large parts of a codebase and get a piece-by-piece understanding.

### Before you start

1. Read the docs (if they exist).
2. Run the code.
3. Play with the code to see how it behaves.
4. Think about how the code might be implemented.
5. Get the code into an editor so that you can modify it.

### The process

1. Look at the file structure.
2. Get a sense for the vocabulary.
3. Keep a note of unfamiliar concepts that you'll need to research later.
4. Do a quick read-through without diving into concepts from #3.
5. Test one feature with the debugger.
6. Document and add comments to confusing areas.
7. Research items in #3 only if required.
8. Repeat.

### Next level

1. Replicate parts of the app by hand (in the console).
2. Make small changes and see what happens.
3. Add a new feature.

# Understanding `this`

### Case 1: In a regular function, `this` points to `window`. This is the default case.

```javascript
function logThis() {
  console.log(this);
}

logThis(); // window
```

### Case 2: In a method, `this` points to the object that contains the method. 

```javascript
var myObject = {
  myMethod: function() {
    console.log(this);
  }
};

myObject.myMethod(); // myObject


// However, for functions that are called inside of myObject.myMethod
// (like anotherFunction), `this` will revert to the default case.

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

### Case 3: In a callback function, assume the default case unless the outer function explicitly sets `this` on the callback function.

```javascript
function outerFunction(callback) {
  callback();
}

outerFunction(function() {
  console.log(this); // window
});
```

### Case 4: In a function that's being called as a constructor, `this` points to the object that the constructor is creating.

```javascript
function Person(name) {
  this.name = name;
}

var gordon = new Person('gordon');
console.log(gordon); // {name: 'gordon'}
```

### Case 5: When you explicitly set the value of `this` manually using `bind`, `apply`, or `call`, it's all up to you.

```javascript
function logThis() {
  console.log(this);
}

var explicitlySetLogThis = logThis.bind({name: 'Gordon'});

explicitlySetLogThis(); // {name: 'Gordon'}
```
