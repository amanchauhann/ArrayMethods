# Array Methods & their custom behind the hood

> *Click &#9733; if you like the project. Your contributions are heartily ♡ welcome.*

<br/>

## Table of Contents

* [Map](#-1-`map()` method)

<br/>

## # 1. `map()` method

The Array.map() method is a built-in function in JavaScript that allows you to apply a function to each element of an array and then return a new array containing the results of the applied function to each element.

**Syntax:**

```js
let newArr = existingArr.map(elementInArr => {here you wrtite function/logic need to performed on each element of Arr})
```

**Example:**

```js
const arr = [1, 2, 3];
const doubledArr = arr.map((num) => num * 2);

console.log(doubledArr); 
// Output: [2, 4, 6]
```

**Custom version:**

```js
const behindTheMap = (callBackFunc, arr) => {
    let newArr = [];
    for(let i=0; i<arr.length; i++){
        newArr.push(callBackFunc(arr[i]))
    }
    return newArr
}
```

**Example:**

```js
const arr = [1, 2, 3];

behindTheMap((num) => num * 2, originalArray);
// Output: [2, 4, 6]
```
