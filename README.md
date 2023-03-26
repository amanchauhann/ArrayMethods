# Functional Programming: Array Methods

> *Click &#9733; if you like the project. Your contributions are heartily ♡ welcome.*

<br/>

## Table of Contents

* [Map](#-1-map()-method)
* [Filter](#-2-filter()-method)
* [Slice](#-3-slice()-method)
* [Push](#-4-push()-method)
* [Pop](#-5-pop()-method)
* [Shift](#-6-shift()-method)
* [findIndex](#-7-findIndex()-method)
* [Includes](#-8-includes()-method)
* [Every](#-9-every()-method)
* [Some](#-10-some()-method)
* [Reduce](#-11-reduce()-method)

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

## # 4. `push()` method

The Array.push() method is a built in function that adds one or more than one elements at the end of the array, it modifies the original array. It take the original array, and elements to be added.

On called upon it returns the new length of the modified array. While modifying the original array.

**Syntax:**

```js
existingArr.push(elelmentsToBeAdded)
```

**Example:**

```js
const numbers = [1, 2, 3, 4, 5, 6];
numbers.push(7,8,9);

console.log(numbers); 
// Output: [1,2,3,4,5,6,7,8,9]
```

**Custom version:**

```js
function behindThePush(arr, ...elem){
    const elements = [...elem];
    for(let i = 0; i < elements.length; i++){
        arr[arr.length] = elements[i];
    }
    return arr.length; // return the new length of the modified array
}
```

**Example:**

```js
const arr = [1, 3, 5, 7, 9];
const newLength = behindThePush(arr, 2, 4, 6, 8);

console.log(newLength); 
// 9
console.log(arr); 
// [1, 3, 5, 7, 9, 2, 4, 6, 8]
```

## # 5. `pop()` method

The Array.pop() method is a built in function that removes the last element of array. It modifies the original array.

On called upon it returns the last element of the original array.

**Syntax:**

```js
existingArr.pop()
```

**Example:**

```js
const numbers = [1, 2, 3, 4, 5, 6];
numbers.pop();
//ouput: 6

console.log(numbers); 
// Output: [1,2,3,4,5]
```

**Custom version:**

```js
function behindThePop(arr) {
    const lastElement = arr[arr.length-1]
    arr.length = arr.length-1
    return lastElement //returns the last element of the array
}
```

**Example:**

```js
const arr = [1, 2, 3, 4, 5];
behindThePop(arr);
//output: 5

console.log(arr); // [1, 2, 3, 4]
```

## # 6. `shift()` method

The Array.shift() method is a built in function that removes the first element of array. It modifies the original array.

On called upon it returns the first element of the original array.

**Syntax:**

```js
existingArr.shift()
```

**Example:**

```js
const numbers = [1, 2, 3, 4, 5, 6];
numbers.shift();
//ouput: 1

console.log(numbers); 
// Output: [2,3,4,5,6]
```

**Custom version:**

```js
const behindTheShift = arr => {
        const firstElement = arr[0]
        for(let i=0; i<arr.length-1; i++){
            arr[i] = arr[i+1]
        }
        arr.length = arr.length-1
        return firstElement //returns first element of array.
}
```

**Example:**

```js
const arr = [1, 2, 3, 4, 5];
behindTheShift(arr);
//output: 1

console.log(arr); // [2, 3, 4, 5]
```

## # 7. `findIndex()` method

The Array.() method is a built in function that is called upon array and given a function. It returns the index of first element of array for which callback function returns true.

 It should be noted that it doesn't work on empty arrays and if the any given array of elements doesn't pass through the function, it returns -1.
It does not changes the original array in any manner.

**Syntax:**

```js
existingArr.findIndex(callBackFunction)
```

**Example:**

```js
const numbers = [1, 2, 3, 4, 5, 6];
numbers.findIndex( (num)=> num>4 );
//ouput: 3

console.log(numbers); 
// Output: [1, 2, 3, 4, 5, 6] //array remains same
```

**Custom version:**

```js
const behindFindIndex =  (arr, callBack) => {
    for(let i=0; i<arr.length; i++){
         if(callBack(arr[i])){
             return i;
             break
         }
    }
    return -1
}
```

**Example:**

```js
const arr = [1, 2, 3, 4, 5];
behindFindIndex(arr, (num)=>num>=3)

//output:2

console.log(arr); 
// [1, 2, 3, 4, 5];
```

## # 8. `includes()` method

The Array.() method is a built in function that is called upon array or a string. It checks if a given value is included in the given array or string.

It returns true if it contains the specified value and false if it doesn't. If a second aguement is passed i.e. index, it starts searching from that specifc index.
It should be noted that includes is case sensitive.

**Syntax:**

```js
existingArr.includes(value)
```

**Example:**

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.includes("Mango");
//ouput: true

console.log(fruits); 
// Output: ["Banana", "Orange", "Apple", "Mango"]; //array remains same
```

**Custom version:**

```js
const behindInclude = (arr, val, index) => {
    for(let i=(index ? index : 0); i<arr.length; i++){
         if(val === arr[i]){
             return true
         }
}
    return false
}
```

**Example:**

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
behindInclude(fruits, "Pineapple")

//output: false
```

## # 9. `every()` method

The Array.() method is a built in function that is called upon a array, it gets implemented on each element of array, and if all the elements passes the test, it returns true else if not even one passes the test, returns false.

This method does not execute on empty elements of array. It does not change original array.

**Syntax:**

```js
existingArr.every(callBack)
```

**Example:**

```js
const numbers = [2,4,6,8];
numbers.every((num)=>num%2===0) ;
//ouput: true

console.log(numbers); 
// Output: [2,4,6,8]; //array remains same
```

**Custom version:**

```js
const behindTheEvery = (arr, callBack) => {
    for(let i=0; i<arr.length; i++){
        if(!callBack(arr[i]))
            return false
    }
    return true
}
```

**Example:**

```js
const numbers = [2,4,6,8,9];
behindTheEvery(numbers, (num)=> num%2===0)

//output: false
```
## # 10. `some()` method

The Array.some() method is a built in function that is called upon a array, it gets implemented on each element of array, and if even one of the elements passes the test, it returns true else if not any of them passes test it returns false.

This method does not execute on empty elements of array. It does not change original array.

**Syntax:**

```js
existingArr.some(callBack)
```

**Example:**

```js
const numbers = [3, 1, 18, 21];
numbers.some((num)=>num%2===0) ;
//ouput: true

console.log(numbers); 
// Output: [3, 1, 18, 21]; //array remains same
```

**Custom version:**

```js
const behindSome = (arr, callBack) => {
    for(let i=0; i<arr.length; i++){
        if(callBack(arr[i])) return true;
    }
    return false
}
```

**Example:**

```js
const numbers = [3, 1, 19, 21, 33];
behindSome(numbers, (num)=> num%2===0)

//output: false
```

## # 11. `reduce()` method

The Array.reduce() method is a built in function that is called upon a array, it performs the given callback function on the array and returns a single value as result. It executes reducer function and returns single accumulated result.

This method does not changes the original array. It does not exectute on empty array.

**Syntax:**

```js
existingArr.reduce(callback)
```

**Example:**

```js
const numbers = [10, 20, 30, 40, 50];
const callBackFunc = (num) => num / 2;
numbers.reduce(callBackFunc) ;
//ouput: 75

console.log(numbers); 
// Output: [10, 20, 30, 40, 50]; //array remains same
```

**Custom version:**

```js
const behindReduce = (arr, cb, acc) => {
    if(!Array.isArray(arr)) return "please give valid array"        //checks if given "arr" is even array.
    if(arr.length <=0) return "please give valid array length"      //handles "arr" with no elements as it does not exectute on empty array.
    let i =0
    
    if(acc === undefined){
        acc = arr[0]
        i = 1
    }
let curr;
    for(; i<arr.length; i++){
        curr = arr[i]
        acc += cb(curr)
    }
    return acc
}
```

**Example:**

```js
const numbers = [10, 20, 30, 40, 50];
const callBackFunc = (num) => num / 2;
behindReduce(numbers, callBackFunc)

//output: 75
```
