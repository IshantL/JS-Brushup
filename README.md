# Javascript/ ES6

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
```
'use strict';
var temp = "this is a temp variable";
var temp = "this is a second temp variable"; //replaced easily
We cannot do the same thing with let-

'use strict';
let temp = "this is a temp variable";
let temp = "this is a second temp variable" //SyntaxError: temp is already declared
```
## Const
- The value cannot change once defined.
- But if we declared object as const we can modify the value of it and also add another property to object.
- but we cannot recreate the object again.
- const nad let both use block scope.


var -global scope
let -block scope
const - block scope

function setup(){
    console.log(x);
    var x= 100;
    console.log(x);
}
undefined
100

function setup(){
    console.log(x);
    let x= 100;
    console.log(x);
}
test.js:16 Uncaught ReferenceError: x is not defined


function setup(){
    let x;
    console.log(x);
    x = 100;
    console.log(x);
}
undefined
100

const y = 50;
y = 90
VM191:1 Uncaught TypeError: Assignment to constant variable.

const particle = {
    x:100,
    y:200
}
    
    particle
    {x: 100, y: 200}
    particle.x = 200;
    200
    particle
    {x: 200, y: 200}
    particle.y = 300;
    300
    particle
    {x: 200, y: 300}
    particle.z = 300;
    300
    particle
    {x: 200, y: 300, z: 300}x: 200y: 300z: 300__proto__: Object
    particle = {x: 20,y:30,z:30}
    VM331:1 Uncaught TypeError: Assignment to constant variable.
        at <anonymous>:1:10


## Higher order functions
HOF we can take arguments as function also we can return function.

## map -filter function returns a new array
## sort and fill on existing array
## reduce special case
map
reduce
sort
filter

map example -->
```
let vals = [1,2,3,4,5];

function doubler(x){
return x*2;
}

vals = vals.map(doubler);
(5) [2, 4, 6, 8, 10]

//es6 ->
vals = vals.map(x => x*2);
(5) [4, 8, 12, 16, 20]

//fill
vals.fill(Math.random(10));
(5) [0.2111157495587459, 0.2111157495587459, 0.2111157495587459, 0.2111157495587459, 0.2111157495587459]

let vals = new Array(100);
undefined
vals
(100) [empty × 100]

vals = vals.map(Math.random(10));
VM577:1 Uncaught TypeError: 0.35617334392871935 is not a function
 


vals = vals.map(x =>Math.random(10));
(100) [empty × 100]length: 100__proto__: Array(0)


vals = vals.fill().map(x =>Math.random(10));
(100) [0.08605421305317718, 0.9321370886339424, 0.5629368316075718, 0.07522099371584678, 0.2904983502873377, 0.7350695008391888, 0.658894344638028, 0.08383739086021857, 0.833597470420333, 0.7747768192918789, 0.38026779257110066, 0.877275023426989, 0.8497664147401451, 0.8769336759032114, 0.8704275969079733, 0.6011383120471856, 0.07440880883259782, 0.6742644489069878, 0.887928529118623, 0.4215158392826297, 0.7841434777271432, 0.7366788535209381, 0.9775310224288176, 0.7139739917754018, 0.307675481880229, 0.08092867429317718, 0.9678127382482111, 0.20435247903002574, 0.9012297564849907, 0.3230934740579958, 0.6538562864948678, 0.781637458968359, 0.9952097617722511, 0.5452491926446146, 0.7447050567564393, 0.6008780807654901, 0.5589131900981386, 0.8901116797234936, 0.09983914590984022, 0.6144993785401089, 0.9767767781423984, 0.6089006646671202, 0.8450306326799266, 0.9093892180801375, 0.9585426775688848, 0.7926260043299294, 0.2392032159095252, 0.9842113312931269, 0.16657065433735307, 0.6566227047171478, 0.17018719444798358, 0.1195863024704189, 0.0016781340267932876, 0.3350100867464272, 0.03690807375123839, 0.236522838584468, 0.47380927796898265, 0.8265375598867275, 0.5202898010275354, 0.5622043429374748, 0.14127578538235475, 0.7631229649312758, 0.9438544618144615, 0.44425343964271113, 0.49866113984147153, 0.18739701896914407, 0.10835245807144611, 0.6526337356020222, 0.8994561857205203, 0.9990690641918609, 0.20958127647314062, 0.9487314487443428, 0.3136935937388088, 0.7553211915997255, 0.6738032388613331, 0.595864291143456, 0.9628773641523642, 0.07338338915151477, 0.9226951638771879, 0.8481964058584728, 0.24141133244051316, 0.5707185822332888, 0.5072862124260056, 0.11507380693079061, 0.4790055630886474, 0.2489905769044367, 0.18320482037122443, 0.6469056255896934, 0.37307069682870164, 0.6728012962973753, 0.7243370166168317, 0.45820300286563387, 0.44078752256968645, 0.18235232457868178, 0.010254664743034603, 0.3508099865867962, 0.49126448048091986, 0.40251901886633035, 0.09326160563624097, 0.32538165319519896]
```
## Reduce

//without reduce
```
var vals = [1,2,3,4,5]
undefined
let sum = 0 ;
undefined
for(let i=0; i <vals.length; i++){
sum += vals[i];
}
15

for(let item of vals){
    sum += item;
    }
30

reduce -accumulator and value
function sums(acc,value){
    return acc+value;
    }
    undefined
    sums(1,10)
    11
acc is like the sum = 0 like in previous program
if we do not give the initial value it will take the array initial value
let sum = vals.reduce(sums);
sum1
15

sum1 = vals.reduce(sums,10);
25

Es6->
let sum = vals.reduce( (acc,value) => acc+value);
15

 min value using reducer
let minval = vals.reduce((acc,val) => {
    if(val <acc){
	acc = val;
    }
    return acc;
})

minval = vals.reduce((acc,val) => val <acc ? val :acc )
1

filter-- even nos

function isEven(num){
    return (num%2 ==0)
   }
   
   undefined
   vals.filter(isEven)
   (3) [6, 2, 4]

```
## es6
```
vals.filter(x => x%2 == 0);

var arr = [1,2,3,undefined,4];
//here the undefined is falsy value and hence filter out

vals.filter(x => x);
[1,2,3,4]

let s = "It was a dark an stormy night.";
s = "It was  a dark an stormy night.";

"It was  a dark an stormy night."
words = s.split(/\W+/);
(8) ["It", "was", "a", "dark", "an", "stormy", "night", ""]
words = s.split(/\W+/).filter(word => word.length);
(7) ["It", "was", "a", "dark", "an", "stormy", "night"]


//sort

vals
(5) [6, 2, 1, 4, 5]
vals.sort();
(5) [1, 2, 4, 5, 6]


let word = ["a", "hello", "B", "bye"]
undefined
word.sort()
(4) ["B", "a", "bye", "hello"]

//for object array it is not sorting the order
var arrs = [{a:2,b:6},{a:3,b:8}]
function compare(a,b){
    return a.y - b.y;
}
arrs.sort(compare)



var arrs = [{a:5,b:6},{a:3,b:8}]

undefined

function compare(x,y){
    return x.b - y.b;
}
arrs.sort(compare)
(2) [{…}, {…}]0: {a: 5, b: 6}1: {a: 3, b: 8}length: 2__proto__: Array(0)

function compare(x,y){
    return x.a - y.a;
}
arrs.sort(compare)
(2) [{…}, {…}]0: {a: 3, b: 8}1: {a: 5, b: 6}length: 2__proto__: Array(0)
```
