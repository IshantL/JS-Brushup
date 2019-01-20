# Javascript

## Let VS Var
- var have functional scope and let have block scope.
- if anything declare before let, we will get not defined error not like in var where hoisting is there and we get undefined as output.
- Even if the let variable is defined as same as var variable globally, the let variable will not be added to the global window object.

```
for(let i=0;i<10;i++){
console.log(i); //i is visible thus is logged in the console as 0,1,2,....,9
}
console.log(i); //throws an error as "i is not defined" because i is not visible

for(var i=0; i<10; i++){
console.log(i); //i is visible thus is logged in the console as 0,1,2,....,9
}
console.log(i); //i is visible here too. thus is logged as 10.
```
let variables cannot be re-declared while var variable can be re-declared in the same scope.

Assume we are using strict mode

'use strict';
var temp = "this is a temp variable";
var temp = "this is a second temp variable"; //replaced easily
We cannot do the same thing with let-

'use strict';
let temp = "this is a temp variable";
let temp = "this is a second temp variable" //SyntaxError: temp is already declared
