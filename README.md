## native array methods

```javascript
/*************************************** forEach ***************************************/
let pets = [
    {'type': 'dog', 'sound': 'woof'},
    {'type': 'cat', 'sound': 'meow'},
    {'type': 'mouse', 'sound': 'squeak'},
    {'type': 'dog', 'sound': 'bow-wow'},
    {'type': 'dog', 'sound': 'ruff-ruff'},
    {'type': 'mouse', 'sound': 'squeak squeak'},
    {'type': 'cat', 'sound': 'purr'}
];


let addLegs = el => el.legs = 4;

Array.prototype.myForEach = function(callback, context) {
    let self = this;
    
    for(let i = 0; i < self.length; i++) {
        callback.call(self, self[i]);
    }
}

pets.myForEach(addLegs);

console.log(pets);

/*************************************** map ***************************************/
let numbers = [1, 4, 9, 16];
let timesTwo = el => el * 2;

Array.prototype.myMap = Array.prototype.myMap || function(callback, context) {
    let newArray = [];
    let self = this;

    for(let i = 0; i < self.length; i++) {
        newArray.push(callback.call(self, self[i]));
    }

    return newArray;
}

let outputMap = numbers.map(timesTwo);
let outputMyMap = numbers.myMap(timesTwo);

console.log(outputMap);
console.log(outputMyMap);

/*************************************** filter ***************************************/
let pets = [
    {'type': 'dog', 'sound': 'woof'},
    {'type': 'cat', 'sound': 'meow'},
    {'type': 'mouse', 'sound': 'squeak'},
    {'type': 'dog', 'sound': 'bow-wow'},
    {'type': 'dog', 'sound': 'ruff-ruff'},
    {'type': 'mouse', 'sound': 'squeak squeak'},
    {'type': 'cat', 'sound': 'purr'}
];


let isDog = el => el.type == 'dog';


Array.prototype.myFilter = Array.prototype.myFilter || function(callback, context) {
    let newArray = [];
    let self = this;
    
    for(let i = 0; i < self.length; i++) {
        if(callback.call(self, self[i])) {
            newArray.push(self[i]);
        }
    }

    return newArray; 
}

let outputFilter = pets.filter(isDog);
let outputMyFilter = pets.myFilter(isDog);

console.log(outputFilter);
console.log(outputMyFilter);

/*************************************** every ***************************************/
let numbers = [1, 4, 9, 16];
let greaterThan10 = el => el > 10;

Array.prototype.myEvery = Array.prototype.myEvery || function(callback, context) {
    let self = this;

    for(let i = 0; i < self.length; i++) {
        if(!callback.call(self, self[i])){
            return false;
        }
    }

    return true;
}

let outputEvery = numbers.every(greaterThan10);
let outputMyEvery = numbers.myEvery(greaterThan10);

console.log(outputEvery);
console.log(outputMyEvery);

/*************************************** some ***************************************/
let numbers = [1, 4, 9, 16];

let greaterThan10 = el => el > 10;

Array.prototype.mySome = Array.prototype.mySome || function(callback, context) {
    let self = this;

    for(let i = 0; i < self.length; i++) {
        if(callback.call(self, self[i])){
            return true;
        }
    }

    return false;
}

let outputSome = numbers.some(greaterThan10);
let outputMySome = numbers.mySome(greaterThan10);

console.log(outputSome);
console.log(outputMySome);

```
