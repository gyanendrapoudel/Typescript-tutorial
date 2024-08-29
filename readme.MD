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