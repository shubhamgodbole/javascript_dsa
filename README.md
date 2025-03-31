# Adding Elements to an Array in JavaScript

## 1. Using Default Methods

### a) `push()` - Add to the End
```javascript
let arr = [1, 2, 3];
arr.push(4);  // [1, 2, 3, 4]
console.log(arr);
```

### b) `unshift()` - Add to the Beginning
```javascript
arr.unshift(0); // [0, 1, 2, 3, 4]
console.log(arr);
```

### c) `splice()` - Insert at a Specific Index
```javascript
arr.splice(2, 0, 99); // Inserts 99 at index 2: [0, 1, 99, 2, 3, 4]
console.log(arr);
```

### d) `concat()` - Merge Arrays
```javascript
let newArr = arr.concat([5, 6]); // [0, 1, 99, 2, 3, 4, 5, 6]
console.log(newArr);
```

### e) Spread Operator (`...`) - Create a New Array
```javascript
let arr2 = [...arr, 7]; // Adds 7 at the end
console.log(arr2);
```

---

## 2. Programmatic Approaches

### a) Using a Loop
```javascript
let arr3 = [1, 2, 3];
for (let i = 0; i < 2; i++) {
    arr3.push(i + 4); // Adds 4, 5
}
console.log(arr3); // [1, 2, 3, 4, 5]
```

### b) Using Recursion
```javascript
function addElement(arr, value, index) {
    if (index >= arr.length) {
        arr.push(value);
        return arr;
    }
    arr.splice(index, 0, value);
    return arr;
}
let arr4 = [1, 2, 3];
console.log(addElement(arr4, 99, 1)); // [1, 99, 2, 3]
```

### c) Using `reduce()`
```javascript
let arr5 = [1, 2, 3];
let updatedArr = arr5.reduce((acc, val, idx) => {
    if (idx === 1) acc.push(99); // Insert at index 1
    acc.push(val);
    return acc;
}, []);
console.log(updatedArr); // [1, 99, 2, 3]
```

### d) Using `map()`
```javascript
let arr6 = [1, 2, 3];
let mappedArr = arr6.flatMap((val, idx) => (idx === 1 ? [99, val] : [val]));
console.log(mappedArr); // [1, 99, 2, 3]
