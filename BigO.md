## Introduction to Big O

### Time complexity

- It's important to know that we measure the performance of the code, not in terms of time itself, but in the `number of operations`, no matter how fast our computer is, the number of operations will be the same.

### Omega - Lower bound (Best case)

- Describes the `best case scenario` for an algorithm, in other words, the fastest an algorithm can run in the best circumstances. Accessing the first index in an array is the best case which corresponds to omega.

### Theta - Tight bound (Average case)

- Describes the `average case scenario`, it indicates what to generally expect from the time complexity. Accessing the middle index in an array (if we're searching from the begining of the array) is the average case which corresponds to theta

### Omicron (Big O) - Upper bound (Worst case)

- If we have code number 1 and code number 2, Big O is here to help us distinguish which code runs more efficiently both in terms of time and space. Big O describes the `worst case scenario` for an algorithm. Accessing the last index in an array (if we're searching from the begining of the array) is the worst case which corresponds to omicron or big O.



### O(1) | Constant time

- `O(1)` means the time complexity will be `constant`, no matter how many  inputs are in the array, the number of operations will be constant.

#### JavaScript Implementation
```javascript
const boxes = ["iphone cases", "fruits", "macbooks"];
function compressFirstBox(boxes) {
  console.log(boxes[0]);
}
compressFirstBox(boxes);
```

## Time Complexity Analysis

- The `compressFirstBox` function takes an array `boxes` as input and performs the following operations:

- It accesses the first element of the `boxes` array using the index `0`.

- It logs the first element of the `boxes` array to the console using `console.log`.

- In this example although the number of inputs is 3, we're only gonna compress the first item, so no matter how big the number of boxes are inside the array, the number of operations will remain the same.

### O(n) | Linear time

- `O(n)` means the time complexity is `linear,` For each input, we have the same number of operations.

#### JavaScript Implementation
```javascript
const cars = new Array(25).fill("Mercedes"); // Filling an array with 25 Mercedes
findMercedes(cars); // Calling findMercedes function

function findMercedes(arrayOfcars) {
  for (i = 0; i < arrayOfcars.length; i++) {
    // Looping through cars array
    if (arrayOfcars[i] === "Mercedes") {
      console.log(i + 1, "Mercedes are found");
    }
  }
}
```

## Time Complexity Analysis

- The `findMercedes` function takes an array `arrayOfcars` as input and performs the following operations:

- It initializes a loop counter `i` to 0.

- It checks if the loop counter `i` is less than the length of the `arrayOfcars` array.

- If the condition in step 2 is true, it checks if the element at index `i` in the `arrayOfcars` array is equal to the string `'Mercedes'`.

- If the condition in step 3 is true, it logs a message to the console.

- It increments the loop counter `i` by 1.

- It repeats steps 2-5 until the loop counter `i` is no longer less than the length of the `arrayOfcars` array.

- In the given code, the `cars` array is initialized with 25 elements, all set to the string `'Mercedes'`. When the `findMercedes` function is called with the `cars` array as an argument, the loop inside the function will execute 25 times, once for each element in the array.

- The time complexity of an algorithm is a measure of how the running time of the algorithm scales with the size of its input. In this case, the running time of the `findMercedes` function is directly proportional to the length of the `arrayOfcars` array. If the length of the array doubles, the number of iterations in the loop will also double, and the running time will increase proportionally.

- Therefore, the time complexity of the `findMercedes` function is O(n), where n is the length of the `arrayOfcars` array. This means that the running time of the function grows linearly with the size of the input array.

- In the given example, since the `cars` array has 25 elements, the `findMercedes` function will execute 25 iterations of the loop, and the time complexity will be O(25), which is still considered O(n) because the constant factor (25) is ignored in the big O notation.

### Big O rules:

1. `Worst case`

- We consider the `worst case` scenario for the operation. In the example of mercedes, if mercedes is at the end of the array, then we have to loop through each item to find the mercedes, this is the worst case scenario.

2. `Remove constants`

- When an operation has a big O of `O(1 + n/2 + 100)`, we're gonna `remove the constants`, because when the input gets larger and larger, constants typically don't matter that much, so the big O will become `O(n)`.

3.  `Different terms for input`

- If inside a function we have two loops, the first loop iterate through the first item and the second loop iterate through the second item, the big O will be `O(n + m)` and not `O(n + n)` or `O(2n)`.

### O(n^2) | Quadratic time

- When we have a `nested loop`, (one loop inside another loop), the big o will be `O(n * n)` which will be `O(n^2)` for the same input, which is called quadratic time. As the number of inputs increases, the number of operations increases significantly, which is considered a `horrible scenario`.

#### JavaScript Implementation
```javascript
const boxes = [1, 2, 3, 4, 5];
function pairItems(array) {
  for (i = 0; i < array.length; i++) {
    for (j = 0; j < array.length; j++) {
      console.log(array[i] + "," + array[j]);
    }
  }
}
pairItems(boxes);
```

## Time Complexity Analysis

- The `pairItems` function takes an array `array` as input and performs the following operations:
- It initializes a loop counter `i` to 0.
- It checks if the loop counter `i` is less than the length of the `array`.
- If the condition in step 2 is true, it initializes another loop counter `j` to 0.
- It checks if the loop counter `j` is less than the length of the `array`.
- If the condition in step 4 is true, it logs a message to the console that combines the elements at indices `i` and `j` of the `array`.
- It increments the loop counter `j` by 1.
- It repeats steps 4-6 until the loop counter `j` is no longer less than the length of the `array`.
- It increments the loop counter `i` by 1.
- It repeats steps 2-8 until the loop counter `i` is no longer less than the length of the `array`.

- The key observation here is that the function has two nested loops. The outer loop iterates over the `array` once, and for each iteration of the outer loop, the inner loop iterates over the entire `array` again.

- If we assume that the length of the `array` is n. Then, the outer loop will execute n times, and for each iteration of the outer loop, the inner loop will execute n times. This means that the total number of iterations of the inner loop is n * n, which is n^2.

- Therefore, the time complexity of the `pairItems` function is O(n^2), which is quadratic time complexity. This means that the running time of the function grows quadratically with the size of the input array.

- In the given example, where `boxes` is an array of length 5, the `pairItems` function will execute 5 * 5 = 25 iterations of the inner loop, and the time complexity will be O(25), which is still considered O(n^2) because the constant factor (25) is ignored in the big O notation.

### O(m + n)

- Here is an example when there are two different inputs, where the operations are `separated` from each other and `not nested`.

#### JavaScript Implementation
```javascript
const groupOne = ["Alex", "Maria", "Jennifer"];
const groupTwo = ["Suzan", "Sara", "Jamie"];
returnList(groupOne, groupTwo);

function returnList(groupOne, groupTwo) {
  groupOne.forEach(function (groupOne) {
    console.log(groupOne);
  });

  groupTwo.forEach(function (groupTwo) {
    console.log(groupTwo);
  });
}
```

## Time Complexity Analysis

- The `returnList` function takes two arrays, `groupOne` and `groupTwo`, as input and performs the following operations:

- It iterates over the `groupOne` array using the `forEach` method, which executes a callback function for each element in the array.

- Inside the callback function, it logs each element of `groupOne` to the console.

- It iterates over the `groupTwo` array using the `forEach` method, which executes a callback function for each element in the array.

- Inside the callback function, it logs each element of `groupTwo` to the console.

- The time complexity of the `returnList` function depends on the lengths of the input arrays `groupOne` and `groupTwo`.

- Let's assume that the length of `groupOne` is m, and the length of `groupTwo` is n.

- The first `forEach` loop iterates over `groupOne` m times, and the second `forEach` loop iterates over `groupTwo` n times.

- Therefore, the total number of operations performed by the `returnList` function is m + n.

- Since the time complexity is determined by the number of operations performed, the time complexity of the `returnList` function is O(m + n), where m and n are the lengths of the input arrays `groupOne` and `groupTwo`, respectively.

- In the given example, where `groupOne` has a length of 3 and `groupTwo` has a length of 3, the time complexity will be O(3 + 3) = O(6), which is still considered O(m + n) because the constant factor (6) is ignored in the big O notation.

### O(m * n)

- In this piece of code, the for loop is `nested`, and there are two `different inputs`. So, the big O of this will be `O(m * n)`.

#### JavaScript Implementation
```javascript
const box = ["a", "b", "c", "d"];
const box2 = ["e", "f", "g", "h"];

function compressBoxesTwice(box, box2) {
  box.forEach(function (box) {
    box2.forEach(function (box2) {
      console.log(box + "," + box2);
    });
  });
}
compressBoxesTwice(box, box2);
```

## Time Complexity Analysis

- The `compressBoxesTwice` function takes two arrays, `box` and `box2`, as input and performs the following operations:

- It iterates over the `box` array using the `forEach` method, which executes a callback function for each element in the array.

- Inside the callback function of the outer `forEach` loop, it iterates over the `box2` array using another `forEach` method, which executes a nested callback function for each element in `box2`.

- Inside the nested callback function, it logs a message to the console that combines the current elements from `box` and `box2`.

- The time complexity of the `compressBoxesTwice` function depends on the lengths of the input arrays `box` and `box2`.

- We assume that the length of `box` is m, and the length of `box2` is n.

- The outer `forEach` loop iterates over `box` m times, and for each iteration of the outer loop, the inner `forEach` loop iterates over `box2` n times. This means that the total number of iterations of the inner loop is m * n.

- Therefore, the total number of operations performed by the `compressBoxesTwice` function is `m * n`.

- Since the time complexity is determined by the number of operations performed, the time complexity of the `compressBoxesTwice` function is O(m \* n), where m and n are the lengths of the input arrays `box` and `box2`, respectively.

- In the given example, where `box` has a length of 4 and `box2` has a length of 4, the time complexity will be O(4 * 4) = O(16), which is still considered O(m * n) because the constant factor (16) is ignored in the big O notation.

- It's important to note that the time complexity of the `compressBoxesTwice` function is quadratic in the lengths of the input arrays. If the lengths of the input arrays increase, the running time of the function will increase quadratically, which can be inefficient for large input sizes.

- This quadratic time complexity is due to the nested loops, where the inner loop iterates over `box2` for each iteration of the outer loop over `box`. This type of nested loop structure often leads to quadratic time complexity.

4. `Drop non dominants`: The most dominant term will remain, and the other trivial factors will be ignored.

#### JavaScript Implementation
```javascript
const numbers = [11, 21, 42, 84];
logAndSum(numbers);
function logAndSum(numbers) {
  //O(n)
  numbers.forEach(function (numbers) {
    console.log(numbers);
  });
  //O(n^2)
  numbers.forEach(function (number1) {
    numbers.forEach(function (number2) {
      console.log(`${number1} + ${number2} = ${number1 + number2}`);
    });
  });
}
```

- In this example, the big O of the first operation is `O(n)` and the big O of the second operation is `O(n^2)`. So, in total we will have `O(n + n^2)`. In this situation, we can ignore and delete O(n), because when n gets larger and larger, the most impactful factor in this function will be `O(n^2`), and O(n) goes side ways. So, we will always `keep the most dominant` term.

### O(log n) | Logarithmic time 

- We have an array `[1, 2, 3, 4, 5, 6, 7, 8]`. If we want to find the first item, we will use `divide and conquer technique` to get to the first item.

- For this, first we need to divide the array into two halves, and then see whether the first element is in the first half or the second half.

- We do this recursively until we reach the first item. 

- Here is the process [1,2,3,4,5,6,7,8] => [1,2,3,4] => [1,2] =>
  [1]. We accomplished the task of getting the first item in `3 steps`.

- We had `8 items` in the array, and we accomplished the task in `3 steps`.

- The relationship is `2^3 = 8` => `log sub 2 of 8 = 3` => `log 8 = 3`.

#### JavaScript Implementation
```javascript
function binarySearch(arr, target){
  let left = 0; // Index of the first element 
  let right = arr.length - 1; // Index of the last element

  while(left <= right){
    let mid = Math.floor((left + right) / 2);

    if(arr[mid] === target){
      return mid; // Return the index of the target array which is found in mid
    }

    else if(arr[mid] < target){
      left = mid + 1
    }

    else{
      right = mid - 1
    }
  }
  return -1 // If target not found 
}

const sortedArray = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20];
const target = 18;
const result = binarySearch(sortedArray, target)
console.log(`The index of ${target} is ${result}`)
```

## Time Complexity Analysis

- The time complexity of the binary search algorithm is logarithmic, specifically O(log n), where n is the size of the input array.

- The function initializes two variables `left` and `right` to represent the indices of the first and last elements of the array, respectively. This operation takes constant time, O(1).

- The function enters a `while` loop that continues as long as `left` is less than or equal to `right`. In the worst case, this loop will run `log n + 1` times, where n is the length of the input array. Here's why:

   - In each iteration of the loop, the function calculates the middle index `mid` by taking the average of `left` and `right`. This operation takes constant time, O(1).
   - Depending on whether the target value is less than, greater than, or equal to the value at the middle index, the function updates either `left` or `right` to narrow down the search range.
   - In the best case (when the target is found), the loop terminates immediately.
   - In the worst case (when the target is not present in the array), the search range is halved in each iteration. This means that the number of iterations is proportional to the logarithm of the input size, specifically `log n + 1` iterations.

- If the target value is found, the function returns the index `mid`. This operation takes constant time, O(1).

- If the target value is not found, the function returns `-1`. This operation also takes constant time, O(1).

Since the `while` loop dominates the time complexity, and it runs in logarithmic time O(log n), the overall time complexity of the `binarySearch` function is O(log n).

### O(2^n) | Exponential time
- The time complexity `O(2^n)` describes an algorithm whose running time `doubles` with each additional input element. The term "doubles with each additional element" means that if you increase the input size n by 1, the number of operations `approximately doubles`. This does not mean that the number of operations is simply twice the input value; rather, it refers to the exponential nature of the growth. This is one of the most inefficient time complexities and is often seen in problems involving exhaustive search, recursion, and combinations.

### Understanding \( O(2^n) \)

An algorithm with O(2^n) time complexity means that for an input of size \( n \), the algorithm performs on the order of \( 2^n \) operations. This exponential growth quickly becomes impractical for even moderately large \( n \).

### Example: Recursive Calculation of Fibonacci Numbers

A classic example of an algorithm with \( O(2^n) \) time complexity is the naive recursive implementation of the Fibonacci sequence:

#### JavaScript Implementation
```javascript
function fibonacci(n) {
    if (n <= 1) {
        return n;
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Example usage
console.log(fibonacci(5)); // Output: 5
```

### Time Complexity Analysis

The Fibonacci sequence is defined as:
- \( F(0) = 0 \)
- \( F(1) = 1 \)
- \( F(n) = F(n-1) + F(n-2) \) for \( n > 1 \)

In the naive recursive implementation:
- Each call to `fibonacci(n)` makes two additional calls: `fibonacci(n - 1)` and `fibonacci(n - 2)`.
- This branching results in a binary tree of recursive calls, where the number of calls roughly doubles for each increment of \( n \).

### Visualizing the Recursive Calls

For example, to calculate `fibonacci(5)`:
```
fibonacci(5)
├── fibonacci(4)
│   ├── fibonacci(3)
│   │   ├── fibonacci(2)
│   │   │   ├── fibonacci(1)
│   │   │   └── fibonacci(0)
│   │   └── fibonacci(1)
│   └── fibonacci(2)
│       ├── fibonacci(1)
│       └── fibonacci(0)
└── fibonacci(3)
    ├── fibonacci(2)
    │   ├── fibonacci(1)
    │   └── fibonacci(0)
    └── fibonacci(1)
```

Each level of this tree has roughly twice the number of calls as the previous level, leading to an exponential number of calls as \( n \) increases.

### Growth of \( O(2^n) \)

To understand the impact, consider the growth rate:
- For \( n = 5 \), the number of calls is around \( 2^5 = 32 \).
- For \( n = 10 \), the number of calls is around \( 2^{10} = 1024 \).
- For \( n = 20 \), the number of calls is around \( 2^{20} = 1,048,576 \).

### Practical Implications

Because the number of operations grows so rapidly, algorithms with \( O(2^n) \) complexity become infeasible very quickly. For example:
- Calculating `fibonacci(40)` with the naive recursive approach would take an enormous amount of time and resources.
- In practical applications, such algorithms are typically optimized or avoided in favor of more efficient approaches.


### O(n!) | Factorial time
- The time complexity `O(n!)` is known as `factorial time complexity`. This is one of the highest and `least efficient` complexities, growing extremely fast as the input size (n) increases. It typically arises in algorithms that generate all permutations of a set or solve certain combinatorial problems.

#### JavaScript Implementation
```javascript
function permute(arr) {
    const result = [];

    function backtrack(path, options) {
        if (options.length === 0) {
            result.push(path);
            return;
        }
        for (let i = 0; i < options.length; i++) {
            backtrack([...path, options[i]], options.slice(0, i).concat(options.slice(i + 1)));
        }
    }

    backtrack([], arr);
    return result;
}

// Example usage
const input = [1, 2, 3];
const permutations = permute(input);
console.log(permutations);
// Output: [
//   [1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]
// ]
```

### Time Complexity Analysis

- **Recursive Backtracking**: The `backtrack` function is used to generate permutations by recursively building each permutation.
- **Path and Options**: `path` keeps the current permutation being built, and `options` contains the remaining elements to be permuted.
- **Base Case**: When `options` is empty, a complete permutation (`path`) is added to `result`.
- **Looping through Options**: For each element in `options`, the function recursively builds permutations, removing the current element from `options` and adding it to `path`.

### Growth of \( O(n!) \)

Factorial time complexity grows extremely rapidly:
- For \( n = 3 \), \( 3! = 6 \)
- For \( n = 4 \), \( 4! = 24 \)
- For \( n = 5 \), \( 5! = 120 \)
- For \( n = 10 \), \( 10! = 3,628,800 \)

- This rapid growth makes \( O(n!) \) algorithms impractical for even moderately large \( n \).


### Space complexity

- Space complexity is all about the `memory` that the program uses. For example code 1 runs a lot faster but it uses a lot of memory, whereas code 2 runs slower than code 1 but occupies less memory compared to code 1. In this situation if our priority is to use less space in the memory, we would choose code 2.

- What causes space complexity
1.  Variables
2.  Data Structures
3.  Function call
4.  Allocations

#### JavaScript Implementation
```javascript
function hola(n) {
  for (let i = 0; i < n.length; i++) {
    console.log("Hola");
  }
}
hola([1, 2, 3, 4, 5]);
```

### Space Complexity Analysis

- In this example, the time complexity of this function is `O(n)`, but for the space complexity, we consider about the additional space, so we don't include the space taken up by the inputs. So, in general we don't care how big the input is; in other words we don't have a control on how many inputs this function is going to receive. We only have a control on what happens inside the function. Inside the function, the only space we're adding is `i`. So, this function has a `space complexity` of `O(1)`.

- We are interested in the `additional space required by the algorithm`, `not including the space taken up by the input data`. This is because the input data is considered to be part of the problem statement, and the algorithm has no control over its size.

- In the hola function, the only additional space used is the loop counter variable `i`. This variable is a primitive data type (in this case, a number), which takes a constant amount of space, regardless of the size of the input array n.
Yes, there are several spelling and grammatical errors in the text. Here are the corrections:

### JavaScript Implementation

```javascript
function HiNTimes(n) {
  let hiArray = []; // create an array
  for (let i = 0; i < n; i++) {
    hiArray[i] = "hi";
    console.log(hiArray);
  }
  return hiArray;
}

HiNTimes(6);
```

### Space Complexity Analysis

- In this example, the space complexity is `O(n)`. Because we're creating an array and adding `n` items to this array with the help of loops. So, `n` items will reside inside the array and take up some space.

### Big O of arrays

- `Pushing` an item to the `end` of the array => `O(1)`, `popping` an item from the `end` of the array => `O(1)`. This is because we only do one operation, and we do not need to `re-index` the items.

- `Pushing` an item to the `beginning` of the array => `O(n)`, `popping` an item from the `beginning` of the array => `O(n)`. This is because we need to `re-index` the items according to the number of items.

- `Pushing` an item to the `middle` of the array => `O(n)`, `popping` an item from the `middle` of the array => `O(n)`. This is because we need to `re-index` the items according to the number of items. Some would think that the Big O is `O(n/2)`, but this approach is wrong because, first, Big O measures the worst case, and secondly, we always need to `drop constants` when it comes to Big O.

- If we want to find an item at the `end` of the array, and we want to find it by the `value`, we need to iterate through the items and finally find it by the value. The Big O of this would be `O(n)`. If we want to find the item by its `index`, that specific index will help us to access the exact place in the memory. We can directly access the index without the need to iterate through the items. The Big O of this is `O(1)`.

### Wrap up

- The most efficient Big O is `O(1)`, then `O(log n)`, `O(n)`, `O(n log n)`, `O(n^2)`, `O(2^n)`, `O(n!)`.

- `O(1)`: Constant

- `O(log n)`: Divide and conquer

- `O(n)`: Proportional

- `O(n^2)`: Loop within a loop

- For more information, visit: https://www.bigocheatsheet.com/
