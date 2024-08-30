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