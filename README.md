## H2 nativeArrayMethods

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

Array.prototype.forEach = Array.prototype.forEach || function(callback, context) {
    let self = this;
    
    for(let i = 0; i < self.length; i++) {
        callback.call(self, self[i]);
    }
}

pets.myForEach(addLegs);

console.log(pets);
```
