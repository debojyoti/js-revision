
# JavaScript Hoisting Cheat Sheet

## What is Hoisting?
- **Hoisting** is JavaScript's default behavior of moving declarations to the top of the current scope (script or function).

## Key Points
- Only declarations are hoisted, not initializations.
- Both variable and function declarations are hoisted.
- Function expressions are not hoisted.
- `let` and `const` declarations are hoisted but not initialized.

## Variable Hoisting

### `var` Declarations
- `var` variables are hoisted to the top of their function scope.
- They are initialized with `undefined`.

```javascript
console.log(x); // undefined
var x = 5;
```

### `let` and `const` Declarations
- `let` and `const` variables are hoisted to the top of their block scope.
- They are not initialized; accessing them before initialization results in a `ReferenceError`.

```javascript
console.log(y); // ReferenceError
let y = 10;

console.log(z); // ReferenceError
const z = 15;
```

## Function Hoisting

### Function Declarations
- Function declarations are hoisted to the top of their scope.
- They are fully hoisted, including their definition.

```javascript
hoistedFunction(); // "Hello, World!"

function hoistedFunction() {
    console.log("Hello, World!");
}
```

### Function Expressions
- Function expressions are not hoisted.
- They are treated like variable assignments and are initialized only when the execution reaches that line.

```javascript
nonHoistedFunction(); // TypeError: nonHoistedFunction is not a function

var nonHoistedFunction = function() {
    console.log("Hello, World!");
};
```

## Arrow Functions
- Arrow functions behave like function expressions and are not hoisted.

```javascript
arrowFunction(); // TypeError: arrowFunction is not a function

var arrowFunction = () => {
    console.log("Hello, Arrow!");
};
```

## Class Hoisting
- Classes are hoisted but not initialized.
- Accessing a class before its declaration results in a `ReferenceError`.

```javascript
new MyClass(); // ReferenceError: Cannot access 'MyClass' before initialization

class MyClass {
    constructor() {
        console.log("Class created");
    }
}
```

## Temporal Dead Zone (TDZ)
- The TDZ is the time between entering scope and variable declaration where variables are in an uninitialized state.
- Accessing a variable in the TDZ results in a `ReferenceError`.

```javascript
{
    console.log(a); // ReferenceError: Cannot access 'a' before initialization
    let a = 3;
}
```

## Best Practices
- Declare all variables at the top of their scope to avoid confusion.
- Use `let` and `const` instead of `var` to prevent unexpected behavior.
- Be mindful of the TDZ when using `let` and `const`.