# Functional Programming: Array Methods

> *Click &#9733; if you like the project. Your contributions are heartily ♡ welcome.*

<br/>

## Table of Contents

* [Map](#-1-map()-method)

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

## # 2. `filter()` method

The Array.filter() method is a built-in function in javascript that takes a callbackback function and invoke it on each element of given array and if element passes the callback function it is added in new Array and then it is returned.

The callback function must return boolean value (true or false), and only if it returns true, the element is added otherwise it is omitted and nothing happens.
The callbackFunc function should return true if the current element should be included in the filtered array, and false if it should be excluded.

**Syntax:**

```js
let newArr = existingArr.filter(callbackFunction)
 //*the callback function that determines which elements to include in the filtered array. *
```

**Example:**

```js
const numbers = [1, 2, 3, 4, 5, 6];
const evenNumbers = numbers.filter(function(num) {
  return num % 2 === 0;
});

console.log(evenNumbers); 
// Output: [2, 4, 6]
```

**Custom version:**

```js
const behindTheFilter = (callbackFunc,arr) => {
    let newArr = []
    for(let i=0; i<arr.length; i++){
        callbackFunc(arr[i]) ? newArr.push(arr[i]) : null
    }
    return newArr
}
```

**Example:**

```js
const ages = [32, 33, 16, 40]; //array
function checkAdult(age) { //callback function
  return age >= 18;
}

behindTheFilter(checkAdult, ages) //custom function
// Output: [32, 33, 40]
```

## # 3. `Slice()` method

The Slice method is a built -in method in javascript, that accepts two index as parameter, 'starting index' and 'ending index'. It is a pure function i.e it does not mutate original arguements instead it creates new array.
The new array it returns contains elements from 'starting index' that is passed till the 'ending index' and just to inform it includes the 'starting index' but excludes 'ending index'

If no values are passed, the default values for 'starting index' is 0, while for 'ending index' is array.length, so if it is passed without any arguements it returns new Array with all elements of original array.
If negatives values are passed, they are treated as offsets from the end of the array.

**Syntax:**

```js
let newArr = arr.slice(startingIndex, endingIndex)
 
```

**Example:**

```js
const fruits = ['apple', 'banana', 'orange', 'kiwi', 'mango'];
const citrus = fruits.slice(2, 4);

console.log(citrus) 
//output: ['orange', 'kiwi']
```

**Custom version:**

```js
const behindTheSlice = (arr, starting =0, ending=arr.length) => {
    if(starting<0) arr.length+starting
    if(ending<0) arr.length +ending
    let newArr = [];
    for(let i=starting; i<ending; i++){
        newArr.push(arr[i])
    }
    return newArr;
}
```

**Example:**

```js
const arr = [0, 1, 2, 3, 4, 5];
const newArr = behindTheSlice(arr, -3, -1); 

console.log(newArr)
// output [3, 4]
```
