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

let awesomeName = 'Mike';
awesomeName = 'Nick';
awesomeName = awesomeName.toUpperCase();
// awesomeName = 20;

### Union Type
Union Type allows a variable to hold a value of multiple, distinct types, specified using the | operator. It can also be used to specify that a variable can hold one of several specific values.
example:
let tax: number | string = 10;
tax = 100;
tax = '$10';

### Any Type
"any" type is a powerful way to work with existing JavaScript, allowing you to opt-out of type-checking and let the values pass through compile-time checks. It means a variable declared with the any type can hold a value of any type. Later will also cover - "unknown" and "never"
let notSure: any = 4;
notSure = 'maybe a string instead';
notSure = false; // okay, definitely a boolean

Practical example :
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

### Arrays - Fundamentals
 arrays are used to store multiple values in a single variable. You can define the type of elements that an array can hold using type annotations.

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

### Objects- Fundamentals
In TypeScript, an object is a collection of key-value pairs with specified types for each key, providing static type checking for properties.

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

### Function - fundamentals
In TypeScript, functions can have typed parameters and return values, which provides static type checking and autocompletion support.

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