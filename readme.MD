### Useful links
https://www.typescriptlang.org/docs/
To convert from Typescript to JavaScript 
https://www.typescriptlang.org/play/

1. JavaScript is loosely type, variables type are determinant at run time, you do not have to declared type of variable

Typescript Fille> Typescript Compiler(compilation / Transpiling) > Javascript Code

2. It is a superset of JavaScript.
>npm i typescript# Typescript-tutorial

### Type Inference
The typescript compiler can infer the type of the variable based on the literal value that is assigned when it is defined. Just make sure you are working in the typescript file 
```
let awesomeName = 'Mike';
awesomeName = 'Nick';
awesomeName = awesomeName.toUpperCase();
// awesomeName = 20;
``
### Union Type
Union Type allows a variable to hold a value of multiple, distinct types, specified using the | operator. It can also be used to specify that a variable can hold one of several specific values.
example:
```
let tax: number | string = 10;
tax = 100;
tax = '$10';
```

### Any Type
"any" type is a powerful way to work with existing JavaScript, allowing you to opt-out of type-checking and let the values pass through compile-time checks. It means a variable declared with the any type can hold a value of any type. Later will also cover - "unknown" and "never"
```
let notSure: any = 4;
notSure = 'maybe a string instead';
notSure = false; // okay, definitely a boolean
```
Practical example :
```
const books = ['1984', 'Brave New World', 'Fahrenheit 451'];

let foundBook: string | undefined;

for (let book of books) {
  if (book === '1984') {
    foundBook = book;
    foundBook = foundBook.toUpperCase();
    break;
  }
}

console.log(foundBook?.length);
```
### Arrays - Fundamentals
 arrays are used to store multiple values in a single variable. You can define the type of elements that an array can hold using type annotations.
```
let ids: number[] = [100, 75, 42];

let fruits: string[] = ['apple', 'orange'];
// fruits.push(1);
// let people: string[] = ['sam', 'ram', 1];
//
// be careful "[]" means literally empty array
// let randomValues: [] = [1];

// be careful with inferred array types
// let names = ['peter', 'susan'];
// let names = ['peter', 'susan', 1];
let array: (string | boolean)[] = ['apple', true, 'orange', false];
```
### Objects- Fundamentals
In TypeScript, an object is a collection of key-value pairs with specified types for each key, providing static type checking for properties.
```
let car: { brand: string; year: number } = { brand: 'toyota', year: 2020 };
car.brand = 'ford';
// car.color = 'blue';

let car1: { brand: string; year: number } = { brand: 'audi', year: 2021 };
// let car2: { brand: string; year: number } = { brand: 'audi' };

let book = { title: 'book', cost: 20 };
let pen = { title: 'pen', cost: 5 };
let notebook = { title: 'notebook' };

let items: { readonly title: string; cost?: number }[] = [book, pen, notebook];

items[0].title = 'new book'; // Error: Cannot assign to 'title' because it is a read-only property

Also cost?:number is optional property 
```
### Function - fundamentals
In TypeScript, functions can have typed parameters and return values, which provides static type checking and autocompletion support.
```
function sayHi(name: string) {
  console.log(`Hello there ${name.toUpperCase()}!!!`);
}

sayHi('john');
// sayHi(3)
// sayHi('peter', 'random');

function calculateDiscount(price: number): number {
  // price.toUpperCase();
  const hasDiscount = true;
  if (hasDiscount) {
    return price;
    // return 'Discount Applied';
  }
  return price * 0.9;
}

const finalPrice = calculateDiscount(200);
console.log(finalPrice);

// "any" example
function addThree(number: any) {
  let anotherNumber: number = 3;
  return number + anotherNumber;
}
const result = addThree(2);
const someValue = result;

// run time error
someValue.myMethod();
```
### Functions - Optional and Default Parameters
n TypeScript, a default parameter value is an alternative to an optional parameter. When you provide a default value for a parameter, you're essentially making it optional because you're specifying a value that the function will use if no argument is provided for that parameter.

However, there's a key difference between a parameter with a default value and an optional parameter. If a parameter has a default value, and you call the function without providing an argument for that parameter, the function will use the default value. But if a parameter is optional (indicated with a ?), and you call the function without providing an argument for that parameter, the value of the parameter inside the function will be undefined.

a function with optional parameters must work when they are not supplied
```
function calculatePrice(price: number, discount?: number) {
  return price - (discount || 0);
}

let priceAfterDiscount = calculatePrice(100, 20);
console.log(priceAfterDiscount); // Output: 80

let priceWithoutDiscount = calculatePrice(300);
console.log(priceWithoutDiscount); // Output: 300

function calculateScore(initialScore: number, penaltyPoints: number = 0) {
  return initialScore - penaltyPoints;
}

let scoreAfterPenalty = calculateScore(100, 20);
console.log(scoreAfterPenalty); // Output: 80

let scoreWithoutPenalty = calculateScore(300);
console.log(scoreWithoutPenalty); // Output: 300
```

### Function - rest parameter
a rest parameter is denoted by three dots (...) before the parameter's name and allows a function to accept any number of arguments. These arguments are collected into an array, which can be accessed within the function.
```
function sum(message: string, ...numbers: number[]): string {
  const doubled = numbers.map((num) => num * 2);
  console.log(doubled);

  let total = numbers.reduce((previous, current) => {
    return previous + current;
  }, 0);
  return `${message} ${total}`;
}

let result = sum('The total is:', 1, 2, 3, 4, 5); // result will be "The total is: 15"
```
### Functions - "void" return type
void is a special type that represents the absence of a value. When used as a function return type, void indicates that the function does not return a value.
```
function logMessage(message: string): void {
  console.log(message);
}

logMessage('Hello, TypeScript!'); // Output: Hello, TypeScript!
```
It's important to note that in TypeScript, a function that is declared with a void return type can still return a value, but the value will be ignored.For example, the following code is valid TypeScript:
```
function logMessage(message: string): void {
  console.log(message);
  return 'This value is ignored';
}

logMessage('Hello, TypeScript!'); // Output: Hello, TypeScript!
```
### Functions - Using Union Types as Function Parameters

### Challenge
Task is to create a function named processInput that accepts a parameter of a union type string | number. The function should behave as follows:
If the input is of type number, the function should multiply the number by 2 and log the result to the console.
If the input is of type string, the function should convert the string to uppercase and log the result to the console.
```
function processInput(input: string | number) {
  if (typeof input === 'number') {
    console.log(input * 2);
  } else {
    console.log(input.toUpperCase());
  }
}

processInput(10); // Output: 20
processInput('Hello'); // Output: HELLO
```
In this example, the processInput function takes a parameter input that can be either a string or a number. Inside the function, we use a type guard (typeof input === 'number') to check the type of input at runtime. If input is a number, we double it. If input is a string, we convert it to uppercase.

### Functions - Using Objects as Function Parameters

```
function createEmployee({ id }: { id: number }): {
  id: number;
  isActive: boolean;
} {
  return { id, isActive: id % 2 === 0 };
}

const first = createEmployee({ id: 1 });
const second = createEmployee({ id: 2 });
console.log(first, second);

// alternative
function createStudent(student: { id: number; name: string }) {
  console.log(`Welcome to the course ${student.name.toUpperCase()}!!!`);
}

const newStudent = {
  id: 5,
  name: 'anna',
};

createStudent(newStudent);
```
