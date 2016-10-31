# cheatsheet-js
A super condensed JavaScript reference for Watch and Code students.

## `this`

1. When you're in a regular function, `this` will be window. This is the default case.

2. When you're in a function that's being called as a method, `this` points to the object that contains the method. For example, if you run `myObject.myMethod()`, `this` points to `myObject`. However, other functions called in the body of `myObject.myMethod` will revert back to the default case.

3. When you're in a callback function, assume the default case unless the outer function explicitly defines `this` (see #5).

4. When you're in a function that's being called as a constructor, `this` points to the object that the constructor will create and return.

5. When you explicitly set the value of `this` manually using `bind`, `apply`, or `call`, it's all up to you.
