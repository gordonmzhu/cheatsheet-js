# Practical JavaScript notes

## Intro

* Through programming, you can work on three core life skills: logic, communication, and health (especially mental health).
* The Watch and Code approach has three distinct stages: beginning, middle, and late.
* The beginning stage is focused on teaching you the mechanics of programming from the computer's perspective.
* The middle stage helps you understand existing programs through methodically reading code.
* The late stage is where you'll contribute to a large existing software project. The objectives are to learn through independent action in a team environment.
* Try to set up a system where you code as often as possible (ideally every day). Focus your energy on being consistent. Don't worry about how much you get done on any given day. The goal is not to be the hero of a random day, week, or month, but to be a hero over the span of a long career.

## Language considerations

* There are four aspects that make a programming language good for learning. The language is ideally (1 easy to read), has a (2 compact syntax), is (3 easy to set up), and is (4 clearly useful).
* JavaScript does reasonably well in (1 easy to read), very poorly in (2 compact syntax). It does exceptionally well in the last two aspects (3 easy to set up) and (4 clearly useful).
* We can make JavaScript very nearly the perfect language for learning by teaching only the essential features of the language at the beginning. In doing so, we force the language to have a compact syntax. Later on, we can layer on the optional features of the language.

## Support

* Office hours on Mondays.
* If you continue beyond this intro course, you'll have access to a Slack group and daily Zoom meetings where you can get help. 

## Get ready

* Use Google Chrome and VS Code.
* Make sure that you set up VS Code *exactly* the way I do it.
* Don't worry about HTML and DO NOT UNDER ANY CIRCUMSTANCES WASTE TIME MEMORIZING STUFF.
* Make sure your HTML file is structured exactly like mine too. If not, you will fail.
* The computer is a harsh taskmaster. Character level precision matters. If you can't get this right, you will fail.
* This is the easy part. Do not fail at the easy part.

## Todo lists are so f&ast;&ast;king lame. Or are they?

* You can learn more than you think from building a todo list.
* Almost every site is a todo list. There are exceptions, but not many.
* Our todo list is gonna be ugly because we are purposely ignoring visual style.

## V1 - Getting started

* Arrays are lists: `['Item 1', 'Item 2', 'Item 3']`.
* Variables are nicknames for data: `var todos = ['Item 1', 'Item 2', 'Item 3']`.
* Semicolons act sort of like periods do in English. They don't appear at the end of every line though.
* Proper semicolon usage is particularly important when you are saving to a file, so pay close attention to how I use semicolons in `todoList.html`. I'll note exceptions as we get to them.
* You can ignore my semicolon usage in the console since I treat that environment like a temporary scratchpad/whiteboard.
* Use `console.log` to display data in the console. Example: `console.log('hi hi hi!')`.
* Computers start counting from 0, not 1.
* On an array, use `.push` to add data to the end of the array. Example: `myArray.push('new data')`.
* Get an element at a certain position: `array[position]`.
* Change an element at a certain position: `array[position] = 'changed!`.
* Remove an element at a certain position: `array.splice(position, 1)`.

## Functions - Interlude

* Characteristic 1: Functions group multiple lines of code together under a single name.

```javascript
// Declaring a function.
function functionName() {
  // Body of function. You can put 0 or more 
  // lines of code between the curly braces.
}

// To run the function, add a set of parentheses to the function name.
functionName();
```

* Characteristic 2: When you a run a function, you can provide the function with data.

```javascript
// myData is a parameter. Parameters differ from variables in two ways:
// 1. Parameters are declared at the same time a function is created.
// 2. Parameters are assigned a value only when the function is run.
function demoFunction(myData) {
  console.log(myData);
}

demoFunction('gordon'); // myData = 'gordon'
demoFunction('watch and code'); // myData = 'watch and code'

// Notice that we do NOT use semicolons after the opening 
// and closing curly braces in function declarations.
```

## V2 - Using functions

* Functions can have 0, 1, or *more* parameters.

```javascript
function edit(position, newValue) {
  todos[position] = newValue;
  console.log(todos);
}
```

## The computer's perspective - Interlude

* To understand the computer's perspective, you need to understand every little thing that happens in each line of code. To do this, you must learn how to use the debugger effectively.
* When I see the "Step over" button, I think "step over to next line of code that's about to run".
* When you hit "Step over", you will not necessarily go to the next line of code in the file. You have to think about what will happen.
* The "Resume script execution" is sorta of like an unpause button. It'll exit the debugger or go to the next breakpoint (if there is one).
* Delusional thinking is not compatible with success (programming or otherwise).
* Use the expectations/reality framework (along with the debugger) to improve the quality of your thinking.
* Use "Step into" to go into any function call *except* built-in functions.
* Use the `debugger` statement to set breakpoints in the console without writing to a file. 

## Questions and quality - Interlude 

* Ask high quality questions. How you approach this will be a deciding factor in how good you will be.
* Throughout your journey learning to program (or with anything really), you will be faced with choices like this. One path leads to high ability, the other path leads to low ability. Choose wisely.

## Functions and variables - Interlude

* If you're inside of a function, you can look out and see data, but the opposite isn't true. If you're outside, you can't look in.
* Whenever you're in doubt, draw circles and arrows. Arrows can only exit circles; they can never go in.
* "Scope" is a fancy term for describing variable visibility.

## V3 - Using objects

* `true` and `false` are boolean values.
* Use objects to group related data together

```javascript
var todo = {
  todoText: 'Get groceries',
  completed: false
};

// Access properties with dot notation.
console.log(todo.todoText); // 'Get groceries'
console.log(todo.completed); // false
```

## V4 - Toggling
* Comparisons: Use `===` to see if two things are equal to each other.
* Use if statements to conditionally run chunks of code.
```javascript
if (true) {
  console.log('This line of code will run.');
}

if (false) {
  console.log('This line of code will not run.');
}

// Notice that we do NOT use semicolons after the opening 
// and closing curly braces in if statements.

```
* `if/else` statements offer another way to structure conditional logic.
```javascript
if (condition) {
  // Will run if condition is true.
} else {
  // Will run if condition is false.
} 
```

## Data types and comparisons - Interlude

* JavaScript has two broad types of data, objects and primitives.
* Objects can be as complex as you want. Examples include arrays and functions.
* Primitives are the simple building blocks of the language.
* There are five main primitives: strings, numbers, booleans, undefined, and null.
* Comparisons with primitives work how most people would expect (like math class).
* Comparisons with objects work very differently.
* Make sure you understand why `[1, 2, 3] === [1, 2, 3]` is `false`.

## V5 - Displaying data better

* Use a for-loop to repeat a piece of code any number of times.

```javascript
for (var i = 0; i < 5; i++) {
  console.log(i);
  // 0
  // 1
  // 2
  // 3
  // 4
}

// Notice that we do NOT use semicolons after the opening 
// and closing curly braces in for-loops.
```

## V6 - Toggle all

* Boolean logic can be complicated. Make sure that you carefully think about different situations before you start coding. 

## V7 - Buttons!

* HTML syntax for buttons: `<button>My button</button>`.
* Vocab lesson: A function on an object is called a "method".
```javascript
var gordon = { 
  name: 'Gordon',                  // property
  city: 'San Francisco',           // property
  myMethod: function sayHi() {     // method
    console.log('Hi');
  }
};
```
* Use the `document` object to access the webpage in your JavaScript.
* Use the `document.getElementById` method to grab an element by id.
```javascript
var displayTodosButton = document.getElementById('display-todos-button');
```
* Elements have a `addEventListener` method, which can be used to respond to events.
```javascript
// The first argument is an event type.
// The second argument is a function that'll run 
// whenever the event occurs on the element.
// In this example, whenever the displayTodosButton is clicked,
// the displayTodos function will run.
displayTodosButton.addEventListener('click', displayTodos);
```

## Experimenting with functions - Interlude
* You need to get to the point where the results of these experiments are obvious and familiar to you.
```javascript
function demoFunction() {}

var experiment1 = demoFunction;   // ?
var experiment2 = demoFunction(); // ?

function demoFunctionThatReturnsAString() {
  return 'a string';
}
 
var experiment3 = demoFunctionThatReturnsAString;   // ?
var experiment4 = demoFunctionThatReturnsAString(); // ?

function demoFunctionThatReturnsUndefined() {
  return undefined;
}

var experiment5 = demoFunctionThatReturnsUndefined;   // ?
var experiment6 = demoFunctionThatReturnsUndefined(); // ?

function logThis(thing) {
  console.log(thing);
}

// Experiment 7
logThis(demoFunctionThatReturnsAString);   // ?

// Experiment 8
logThis(demoFunctionThatReturnsAString()); // ?
```

## V8 - Getting data from inputs

* In your HTML, use `<input>` to get user input.
* In your JavaScript, use `input.value` to get/set an input's value.

## V9 - Escape from the console

* In HTML, use `ul`s and `li`s for listing data.
```
<ul>
  <li>First</li>
  <li>Second</li>
  <li>Third</li>
</ul>
```
* Use `document.createElement` to create elements in JavaScript.
```javascript
var todoLi = document.createElement('li');
```
* Use the `appendChild` method to add elements to the page.
```javascript
var todosUl = document.getElementById('todos-ul');
todosUl.appendChild(todoLi);
```
* Use the `innerHTML` property to get/set an element's html.
* Use the `innerText` property to get/set an element's text.
* Use `+` to combine strings. 

## V10 - Click to delete
* Went through the pros/cons of different ways to access the remove button that was clicked. Making informed tradeoffs is one of the most important skills that you will learn.
* Functions passed to `addEventListener` are called with an event object, which describes the event that occurred.
```javascript
function remove(event) {
  // We used event.currentTarget to access the remove button element that was clicked.
  // Elements have an id property we can use to get/set the id.
  var position = event.currentTarget.id;
  todos.splice(position, 1);
  displayTodos();
}
```

## V11 - Click to toggle

* Element ids should be unique.
* Practiced thinking through the pros/cons of different ways to extract position from ids.
```javascript
// We ended up choosing this technique.
var idString = 'todo-0';
var position = idString.split('-')[1];
```

## V12 - Click to edit

* `prompt()` is a simple way to get user input.
* Use `!==` to test for inequality.
* Use `&&` to combine comparisons.
