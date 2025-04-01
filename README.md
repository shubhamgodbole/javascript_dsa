# Traversing an Array in JavaScript

In Data Structures and Algorithms (DSA), **traversing** an array refers to accessing each element of the array one by one. In JavaScript, there are several ways to traverse through an array.

---

## 1. Using a `for` Loop (Traditional Loop)

The most basic method of traversing an array is using a simple `for` loop.

```javascript
let arr = [1, 2, 3, 4, 5];
for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]); // Prints each element one by one
}
```

## 2. Using for...of Loop

The for...of loop provides a cleaner and more modern way to loop through the array's values. This is ideal if you don’t need the index.

```
let arr = [1, 2, 3];
for (let value of arr) {
    console.log(value); // Prints each element one by one
}
```

## 3. Using forEach() Method

The forEach() method allows you to execute a provided function once for each element in the array. It's a more declarative approach compared to a traditional loop.

```
let arr = [1, 2, 3, 4, 5];
arr.forEach(value => {
    console.log(value); // Prints each element one by one
});

```

## 4. Using map() Method

The map() method creates a new array by transforming each element. Although it’s typically used for creating new arrays, it can also be used for traversing.

```
let arr = [1, 2, 3, 4, 5];
arr.map(value => {
    console.log(value); // Prints each element one by one
});

```
## Key Differences

-   **`for` Loop**: Gives you complete control over the index and is very flexible.
    
-   **`for...of`**: Cleaner and simpler, especially when you don't need the index.
    
-   **`forEach()`**: Clean, declarative, but does not support breaking or returning values.
    
-   **`map()`**: Typically used for transforming arrays, but can also be used for traversal.
    
-   **`while` Loop**: Provides flexibility but requires careful setup of the loop condition.
    
-   **`reduce()`**: Primarily for accumulating results but can also be used for traversal.
    
-   **`for...in`**: Iterates over array indices; not recommended for arrays due to potential for unexpected behavior.
    
-   **`Object.keys()` + `forEach()`**: Uses object properties to access array indices.
    
-   **`for...of` + `entries()`**: Allows for both index and value in a more readable format.  



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
```

# Merging Two Arrays in JavaScript

## 1. Using Default Methods

### **Method 1: Using `concat()`**
```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const mergedArray = array1.concat(array2);
console.log(mergedArray);  // Output: [1, 2, 3, 4, 5, 6]
```

### **Method 2: Using Spread Operator (`...`)**
```javascript
const mergedArray = [...array1, ...array2];
console.log(mergedArray);  // Output: [1, 2, 3, 4, 5, 6]
```

### **Method 3: Using `push()` with Spread Operator**
```javascript
array1.push(...array2);
console.log(array1);  // Output: [1, 2, 3, 4, 5, 6]
```



# Programmatically Merging Arrays

### **Method 1: Using `for` Loop**
```javascript
let mergedArray = [];
for (let i = 0; i < array1.length; i++) {
  mergedArray.push(array1[i]);
}
for (let i = 0; i < array2.length; i++) {
  mergedArray.push(array2[i]);
}
console.log(mergedArray);  // Output: [1, 2, 3, 4, 5, 6]
```

### **Method 2: Using `forEach()` Loop**
```javascript
let mergedArray = [];
array1.forEach(item => mergedArray.push(item));
array2.forEach(item => mergedArray.push(item));
console.log(mergedArray);
```

### **Method 3: Using `while` Loop**
```javascript
let mergedArray = [];
let i = 0;
while (i < array1.length) {
  mergedArray.push(array1[i]);
  i++;
}
i = 0;
while (i < array2.length) {
  mergedArray.push(array2[i]);
  i++;
}
console.log(mergedArray);
```

---

## 3. Merging Arrays of Different Sizes
```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5];
const mergedArray = [...array1, ...array2];
console.log(mergedArray);  // Output: [1, 2, 3, 4, 5]
```

---

## Summary
- Use `concat()`, spread operator (`...`), or `push()` for quick merging.
- Use loops (`for`, `forEach`, `while`) for manual merging.
- Handle different-sized arrays carefully.

