# cheatsheet-js
A super condensed JavaScript reference for Watch and Code students.

## `this`

1. When you're in a regular function, `this` will be window. This is the default case.

2. When you're in a function that's being called as a method, `this` will point to the object that contains the method. For example, if you run `myObject.myMethod()`, `this` inside of `myObject.myMethod` will point to `myObject`. However, functions that are called in the body of `myObject.myMethod` will revert back to the default case.

3. When you explicitly set the value of `this` manually using `bind`, `apply`, or `call`, it's all up to you.

4. When you're in a callback function, assume the default case unless the outer function explicitly defines `this`.

5. When you're in a function that's being called as a constructor, `this` points to the newly created object that will be returned.
