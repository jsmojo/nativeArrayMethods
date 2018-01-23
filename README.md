## nativeArrayMethods

```javascript
/******* forEach *********/
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

/******* map *********/
let numbers = [1, 4, 9, 16];

let timesTwo = el => el * 2;


Array.prototype.myMap = function(callback, context) {
    let newArray = [];
    let self = this;

    for(let i = 0; i < self.length; i++) {
        newArray.push(callback(self[i]));
    }

    return newArray;
}

let outputMap = numbers.map(timesTwo);
let outputMyMap = numbers.myMap(timesTwo);

console.log(outputMyMap);
console.log(outputMyMap);
```
