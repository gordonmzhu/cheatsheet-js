# cheatsheet-js
A super condensed JavaScript reference for [Watch and Code](https://watchandcode.com/) students.

# Required resources

- [Watch and Code](http://watchandcode.com/p/premium)
- [How to be great at asking coding questions](https://medium.com/@gordon_zhu/how-to-be-great-at-asking-questions-e37be04d0603#.y2roq84t7)

# How to read source code

### Why it’s important

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

### Case 1: In a regular function (or if you're not in a function at all), `this` points to `window`. This is the default case.

```javascript
function logThis() {
  console.log(this);
}

logThis(); // window

// In strict mode, `this` will be `undefined` instead of `window`. 
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode
```

### Case 2: When a function is called as a method, `this` points to the object that's on the left side of the dot (aka "left of the dot rule").

```javascript

/*
 * You can also think of this as the "left of the dot" rule. 
 * For example, in myObject.myMethod(), `this` will be myObject
 * because, myObject is to the left of the dot.
 *
 * Of course, if you're using this syntax object[myMethod](),
 * technically it would be the "left of the dot or bracket" rule,
 * but that sounds clumsy and generally terrible.
 */

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

### Case 3: In a function that's being called as a constructor, `this` points to the object that the constructor is creating.

```javascript
function Person(name) {
  this.name = name;
}

var gordon = new Person('gordon');
console.log(gordon); // {name: 'gordon'}
```

### Case 4: When you explicitly set the value of `this` manually using `bind`, `apply`, or `call`, it's all up to you.

```javascript
function logThis() {
  console.log(this);
}

var explicitlySetLogThis = logThis.bind({name: 'Gordon'});

explicitlySetLogThis(); // {name: 'Gordon'}

// Note that a function returned from .bind (like `boundOnce` below),
// cannot be bound to a different `this` value ever again.
// In other words, functions can only be bound once.
var boundOnce = logThis.bind({name: 'The first time is forever'});

// These attempts to change `this` are futile.
boundOnce.bind({name: 'why even try?'})();
boundOnce.apply({name: 'why even try?'});
boundOnce.call({name: 'why even try?'});
```

### Case 5: In a callback function, apply the above rules methodically.

```javascript

function outerFunction(callback) {
  callback();
}

function logThis() {
  console.log(this);
}

/*
 * Case 1: The regular old default case.
 */
 
outerFunction(logThis); // window

/*
 * Case 2: Call the callback as a method
 * (This is unusual (you'll probably NEVER see this) but possible.)
 */
 
function callAsMethod(callback) {
  var weirdObject = {
    name: "Don't do this in real life"
  };
  
  weirdObject.callback = callback;
  weirdObject.callback();
}

callAsMethod(logThis); // `weirdObject` will get logged to the console

/*
 * Case 3: Calling the callback as a constructor. 
 * (You'll also probably never see this. But in case you do...)
 */
 
function callAsConstructor(callback) {
  new callback();
}

callAsConstructor(logThis); // the new object created by logThis will be logged to the console

/*
 * Case 4: Explicitly setting `this`.
 */
 
function callAndBindToGordon(callback) {
  var gordon = {name: 'Gordon'};
  var boundCallback = callback.bind({name: 'Gordon'});
  boundCallback();
}

callAndBindToGordon(logThis); // {name: 'Gordon'}

// In a twist, we give `callAndBindToGordon` a function that's already been bound.
var boundOnce = logThis.bind({name: 'The first time is forever'});
callAndBindToGordon(boundOnce); // {name: 'The first time is forever'}
```
