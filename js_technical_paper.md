# JAVASCRIPT TECHNICAL PAPER

## 1. What are the different types of Data types in JavaScript?
- JavaScript has two main categories of data types:
1. Primitive Data Types (7 types)
- These are simple, immutable, and stored by value.
    1. Number
    - Represents all numeric values (integer, float).
    - Example:
    ```js
    let age = 22;
    let price = 99.5;
    ```
    2. String
    - Text enclosed in " " or ' ' or ` `.
    - Example:
    ```js
    let name = "Jahnavi";
    ```
    3. Boolean
    - Only true or false.
    - Example:
    ```js
    let isPassed = true;
    ```
    4. Undefined
    - A variable declared but not assigned.
    - Example:
    ```js
    let x; // undefined
    ```
    5. Null
    - Represents empty or no value.
    - Example:
    ```js
    let data = null;
    ```
    6. BigInt
    - For very large integers beyond the Number limit.
    - Example:
    ```js
    let big = 12345678901234567890n;
    ```
    7. Symbol
    - Used to create unique keys.
    - Example:
    ```js
    let s = Symbol("id");
    ```
2. Non-Primitive (Reference) Data Types
- These are complex, mutable, and stored by reference.
    1. Object
    - Collection of key–value pairs.
    - Example:
    ```js
    let person = { name: "Jahnavi", age: 22 };
    ```
    2. Array
    - Ordered list of values.
    - Example:
    ```js
    let nums = [1, 2, 3];
    ```
    3. Function
    - Functions are also treated as objects in JavaScript.
    - Example:
    ```js
    function greet() {
    console.log("Hello");
    }
    ```
## 2. What are scopes in JavaScript?
- Scope in JavaScript defines where variables and functions are accessible in your code.
- It ensures that each variable is used only within the region where it’s defined, preventing conflicts and errors.
1. Global Scope
- Variables declared outside all functions and blocks.
- It can be used anywhere in the program.
- Example:
```js
let x = 10; // global

function show() {
  console.log(x); // can access
}

show();
console.log(x); // can access
```
2. Function Scope
- Variables declared inside a function.
- It can be used only inside that function.
- Created by function.
- Example:
```js
function test() {
  let y = 20; // function scoped
  console.log(y); // OK
}

test();
console.log(y); // ❌ ERROR: y is not defined
```
3. Block Scope
- Created by { } (if, for, while, etc.).
- Variables declared using let or const are block scoped.
- Example:
```js
if (true) {
  let z = 30; // block scoped
  console.log(z); // OK
}

console.log(z); // ❌ ERROR
```
4. Lexical Scope (Closures)
- Inner functions can access variables from their outer function.
- Example:
```js
function outer() {
  let a = 100;

  function inner() {
    console.log(a); // can access outer variable
  }

  inner();
}
outer();
```
## 3. Explain about let,var,const?
1. Var
- var is function-scoped and allows redeclaration and updating of variables.
- It does not follow block scope, so variables leak outside { }.
- Examples:
```js
if (true) {
  var a = 5;
}
console.log(a); // 5 (still accessible)
```
2. let
- let is block-scoped and cannot be redeclared in the same block.
- It allows updating but keeps variables limited to the block they are defined in.
- Examples:
```js
let y = 10;
y = 15;   // update allowed
console.log(y); // 15
```
3. const
- const is block-scoped and must be assigned a value at the time of declaration.
- It cannot be updated or redeclared, though object contents can still change.
- Examples:
```js
const z = 100;
// z = 200; // ❌ Error: cannot update const
console.log(z);
```
## 4. Why we must not use var?
- var should be avoided because it is not block-scoped, which causes variables to leak outside {} and creates unexpected bugs.
- It also allows redeclaration and hoisting, making the code harder to predict and maintain.

## 5. Why using global variables is bad.
- Global variables can be changed from anywhere, making bugs hard to find. This leads to unpredictable behavior in the program.

- They increase the chances of name conflicts with other variables. Different parts of the code may overwrite them accidentally.

- Global variables reduce security because they are accessible everywhere. Any function can modify them without restriction.

- They make code less organized and harder to maintain. Relying on globals breaks modular and clean coding practices.

## 6. What are truthy and falsy values?
- **Falsy Values**
- Falsy values are values that become false when JavaScript converts them to a boolean. If a falsy value is used in a condition, it behaves like false.
- Examples:
1. 0
```js
if (0) console.log("runs");  // ❌ won't run
```
2. "" (empty string)
```js
if ("") console.log("hello");  // ❌ won't run
```
3. null
```js
if (null) console.log("yes");  // ❌ won't run
```
- **Truthy Values**
- Truthy values are values that become true when JavaScript converts them to a boolean.
- If a truthy value is used in a condition, it behaves like true.
- Examples:
1. "hello" (non-empty string)
```js
if ("hello") console.log("runs");  // ✅ runs
```
2. 5 (any number except 0)
```js
if (5) console.log("yes");  // ✅ runs
```
3. [] (empty array)
```js
if ([]) console.log("true");  // ✅ runs
```
## 7. What is function hoisting?
- Function hoisting means JavaScript moves function declarations to the top of their scope before the code runs.
- Because of this, you can call a function before it is written in the code. 
- Example:
- You can call the function before it appears.
```js
greet();

function greet() {
    console.log("Hello!");
}
```
## 8. What happens when a function does not have a return statement?
- If a function does not have a return statement, JavaScript automatically returns undefined.
- Example:
```js
function add() {
    console.log("Hello");
}

let result = add();
console.log(result);   // → undefined
```
## 9. What are the different ways of declaring a function.
- In JavaScript, functions can be declared in multiple ways, and each style affects how the function behaves in terms of hoisting, scope, and readability. The main ways to declare a function are:

1. Function Declaration

- A traditional way of defining a named function using the function keyword. It is hoisted, so it can be called before it is defined.
- Example:
```js
function greet() {
    console.log("Hello");
}
```
2. Function Expression
- A function stored inside a variable. It is not hoisted, so it can only be used after the line is executed.
- Example:
```js
const greet = function () {
    console.log("Hello");
};
```
3. Arrow Function
- A shorter, modern syntax introduced in ES6. It does not have its own this and is commonly used for small, simple functions.
- Example:
```js
const greet = () => {
    console.log("Hello");
};
```

## 10. What is pass by value and pass by reference?
- **Pass by Value**
- JavaScript copies the actual value, so changing the parameter does NOT affect the original variable.
- Used for primitive types (number, string, boolean, null, undefined, symbol, bigint).
- Example:
```js
let x = 10;

function changeValue(a) {
    a = 20;          // only local copy changes
}

changeValue(x);
console.log(x);      // 10 → original unchanged
```

- **Pass by reference**
- JavaScript passes the reference (memory address) of objects, so changing the parameter changes the original object.
- Used for objects, arrays, functions.
- Examples:
```js
let obj = { value: 10 };

function update(o) {
    o.value = 20;    // modifies original object
}

update(obj);
console.log(obj.value);   // 20 → original changed
```
## 11. What are the different types of for loops?
1. Regular for Loop (numbers loop)
- Used when you know the exact number of iterations; runs using a counter.
- Example:
```js
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```
2. for…in Loop
- Used to loop over the keys (property names) of an object.
- Example:
```js
const person = { name: "Aarav", age: 20 };

for (let key in person) {
    console.log(key, person[key]);
}
```
3. for…of Loop
- Used to loop over iterables like arrays, strings, maps, sets—returns values.
- Example:
```js
const numbers = [10, 20, 30];

for (let value of numbers) {
    console.log(value);
}
```
4. forEach Loop (array-only)
- A loop method available on arrays; runs a function once for each element.
- Example:
```js
const items = ["apple", "banana", "orange"];

items.forEach(function(item) {
    console.log(item);
});
```
5. While
- Repeats as long as the condition is true; used when the number of iterations is unknown.
- Example:
```js
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```
## 12. What is searching mdn(Mozilla Developer Network)?
- Searching MDN means looking up JavaScript, HTML, or CSS topics on the MDN Web Docs website to get correct, official explanations, examples, and syntax.
- It is the most trusted website for frontend documentation.

## 13. What are the popular array utility methods?
**Basics**
1. Array.pop()
- Definition: Removes the last element from an array and returns it.
- Mutable: Yes (changes the original array)
- Example:
```js
let arr = [1, 2, 3];
let last = arr.pop();

console.log(last);   // 3
console.log(arr);    // [1, 2]
```
2. Array.push()
- Definition: Adds one or more elements to the end of the array.
- Mutable: Yes
- Example:
```js
let arr = [1, 2];
arr.push(3, 4);

console.log(arr);   // [1, 2, 3, 4]
```
3. Array.concat()
- Definition: Combines two or more arrays and returns a new array.
- Immutable: No mutation (original array remains unchanged)
- Example:
```js
let a = [1, 2];
let b = [3, 4];

let result = a.concat(b);

console.log(result); // [1, 2, 3, 4]
console.log(a);      // [1, 2]
```
4. Array.slice()
- Definition: Returns a portion of an array as a new array.
- Immutable: No mutation
- Example:
```js
let arr = [10, 20, 30, 40];
let part = arr.slice(1, 3);

console.log(part);  // [20, 30]
console.log(arr);   // [10, 20, 30, 40]
```
5. Array.splice()
- Definition: Adds/removes elements from any position in the array.
- Mutable: Yes (changes original array)
- Example:
```js
let arr = [10, 20, 30, 40];
arr.splice(1, 2, 99);   // remove 20,30 and insert 99

console.log(arr);  // [10, 99, 40]
```
6. Array.join()
- Definition: Converts array elements into a single string, separated by a chosen separator.
- Immutable: No mutation
- Example:
```js
let arr = ["a", "b", "c"];
let str = arr.join("-");

console.log(str);  // "a-b-c"
console.log(arr);  // ["a", "b", "c"]
```
7. Array.flat()
- Definition: Flattens nested arrays one level deep (or more if depth is specified).
- Immutable: No mutation
- Example:
```js
let arr = [1, [2, 3], [4, [5]]];
let flatArr = arr.flat(2);

console.log(flatArr); // [1, 2, 3, 4, 5]
console.log(arr);     // original unchanged
```

**Finding**
1. Array.find()
- Definition: Returns the first element that matches the condition.
- Mutable: No (does not change the array)
- Example:
```js
let arr = [10, 20, 30, 40];

let result = arr.find(num => num > 25);

console.log(result); // 30
console.log(arr);    // [10, 20, 30, 40]
```
2. Array.indexOf()
- Definition: Returns the index of the given value (or -1 if not found).
- Mutable: No
- Example:
```js
let arr = ["apple", "banana", "orange"];

console.log(arr.indexOf("banana")); // 1
console.log(arr.indexOf("grape"));  // -1
```
3. Array.includes()
- Definition: Returns true/false if the value exists in the array.
- Mutable: No
- Examples:
```js
let arr = [1, 2, 3];

console.log(arr.includes(2)); // true
console.log(arr.includes(5)); // false
```
4. Array.findIndex()
- Definition: Returns the index of the first element that matches the condition (or -1 if not found).
- Mutable: No
- Examples:
```js
let arr = [5, 12, 8, 130];
let index = arr.findIndex(num => num > 10);
console.log(index); // 1 (because 12 is the first match)
```
**Higher Order Array Functions**
1. Array.forEach()
- Definition: Runs a function once for each element, mainly for looping/side effects.
- Mutable: No (does not change array unless you modify items manually)
- Examples:
```js
let arr = [1, 2, 3];

arr.forEach(num => {
    console.log(num * 2);
});
// Output: 2, 4, 6
```
2. Array.filter()
Definition: Returns a new array containing elements that satisfy the condition.
Immutable: No mutation (returns new array)