# Simplify Your JavaScript Code with Higher-Order Functions

![image](./assets/higherOrderFunc.png)

When we think of functions in any programming language, we imagine reusable code organized into a separate block that performs specific tasks. Functions can take inputs, process them, and provide output according to the instructions coded within the function.

Functions usually receive values as inputs, such as numbers, strings, and references or copies of objects and lists. They may also optionally return values of those types.

But what if we want to implement a timer function, for example, that executes a given piece of code after a certain number of seconds have passed? Can a timer function take another function as its input?

## What is a Higher-Order Function?

In computer science, higher-order functions, a fundamental concept in functional programming, are functions that can either accept other functions as inputs or return them as outputs. They allow us to create abstractions over existing functionality and combine different functions to build new ones.

## Why Use Higher-Order Functions?

Higher-order functions are valuable for writing code that is more versatile, adaptable, and reusable. They enable us to abstract existing functionality and build new features from them. Moreover, they help us manage scope, simplify callbacks (such as promises), reduce unnecessary code duplication, and write cleaner code by separating the logical flow from the implementation details.

Have you ever worked with filter, map, or forEach methods in JavaScript? These are excellent examples of higher-order JavaScript functions.

## Writing Your First Higher-Order Functions

Let’s start by creating two different higher-order functions. The first one will take a function as input, while the second will return a function. Afterward, we’ll create our definitions for some of the most popular higher-order functions, some of which we’ve already mentioned.

### Taking a Function as an Argument

To begin, let’s build a simple function, doOperation, which takes three arguments:

The operation function
number1
number2

Additionally, we’ll create an operation called sumBothNumbers, which merely returns the sum of two numbers.

```

function doOperation(operation, number1, number2) {
    return operation(number1, number2);
}

function sumBothNumbers(number1, number2) {
    return number1 + number2;
}

doOperation(sumBothNumbers, 2, 7);
//output 9

```

### Returning a Function

Next, we’ll create a higher-order function that returns a function. Our function will be named multiplyBy, and it will take a number as an argument and return a function that multiplies its input by that number.

```

function multiplyBy(multiplier) {
    return function result(num) {
        return num * multiplier;
    }
}

const multiplyByThree = multiplyBy(5);
console.log(multiplyByThree(3));
//output 15;

```

### How to Use Higher-Order Functions

You can use higher-order functions in various ways.

When working with arrays, you can use the map(), reduce(), filter(), and sort() functions to manipulate and transform data in an array.

When working with objects, you can use the Object.entries() function to create a new array from an object.

When working with functions, you can use the compose() function to create complex functions from simpler ones.

There are several built-in higher-order functions, with some of the most common ones being map(), filter(), and reduce. Let's delve into each of these in detail.

## How to Use map() in JavaScript

The map() function takes an array of values and applies a transformation to each value in the array without altering the original array. It is often used to convert an array of data into a new array with a different structure.

Let’s understand it with some examples.

Suppose we want to add 10 to every element in an array. We can use the map() method to iterate over each element in the array and add 10 to it.

```

const arr = [1, 2, 3, 4, 5];
const output = arr.map((num) => num + 10);
console.log(arr); // [1, 2, 3, 4, 5]
console.log(output); // [11, 12, 13, 14, 15]

```

In the above example, arr is an array with five elements: 1, 2, 3, 4, and 5. map is a method that applies a function to each element in an array, returning a new array with the modified elements.

The callback function passed to map uses the arrow function syntax and takes a single argument, num. This function adds 10 to num (every element in the array) and returns the result.

Without using a higher-order function, you’d need to write a loop to achieve the same result:

```

const arr = [1, 2, 3, 4, 5];

for (let i = 0; i < arr.length; i++) {
  arr[i] += 10;
}

console.log(arr); // [11, 12, 13, 14, 15]

```

## How to Use filter() in JavaScript

The filter() function takes an array and returns a new array with only the values that meet specific criteria, without altering the original array. It is often used to select a subset of data from an array based on certain conditions.

You can use filter() to retrieve only the odd numbers from an array of numbers.

```

const arr = [1, 2, 3, 4, 5];
const output = arr.filter((num) => num % 2); // Filter out odd numbers
console.log(arr); // [1, 2, 3, 4, 5]
console.log(output); // [1, 3, 5]

```

In this code, arr is an array with five elements: 1, 2, 3, 4, and 5. The filter method creates a new array with elements that pass a test specified in the provided callback function.

The callback function checks if num is odd by verifying if it's not divisible by 2 (num % 2). If num is not divisible by 2, the function returns true; otherwise, it returns false.

When filter is called on arr, it applies this function to each element in the array, creating a new array with only the elements that returned true or met the specified condition when passed to the function. The original arr remains unchanged.

Without using a higher-order function, achieving the same result would require writing a loop:

```

const arr = [1, 2, 3, 4, 5];
const output = [];

for (let i = 0; i < arr.length; i++) {
  if (arr[i] % 2 === 1) {
    output.push(arr[i]);
  }
}

console.log(arr); // [1, 3, 5]
console.log(output); // [1, 3, 5]

```

## How to Use reduce() in JavaScript

The reduce() method might seem overwhelming at first, but don't worry. We'll learn it through several examples, and I'll do my best to make it easy to understand.

You might wonder why we use the reduce() method when there are already many methods available. The key is to use reduce() when you want to perform operations on the elements of an array and return a single value as a result. This "single value" refers to the accumulated result of repeatedly applying a function to the elements of a sequence.

For example, you can use reduce() to sum all the elements in an array, find the maximum or minimum value, merge multiple objects into a single object, or group different elements in an array.

Now, let’s understand all of this with some examples.

```

const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((total, currentValue) => {
    return total + currentValue;
}, 0);

console.log(sum); // 15

```

In this example, the reduce() method is called on the numbers array and is passed a callback function that takes two arguments: total and currentValue.

The total argument accumulates the values returned from the function in each iteration, and currentValue represents the current element being processed in the array.

The reduce() method also takes an initial value as the second argument, which, in this case, is 0. This initial value is used for the first iteration to set the initial value of total.

In each iteration, the function adds the currentValue to total and returns the new value of total. The reduce() method then uses this returned value as the total for the next iteration, continuing until all elements in the array are processed.

Finally, it returns the final value of total, which is the sum of all the elements in the array.

Without using a higher-order function, you’d need to write a loop to achieve the same result:

```

const numbers = [1, 2, 3, 4, 5];
let sum = 0;

for (let i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}

console.log(sum); // 15

```

## Benefits of Higher-Order Functions

Using higher-order functions offers several important benefits for web developers.

First, higher-order functions improve code readability, making it more concise and easier to understand. This can speed up the development process and simplify code debugging.

Second, higher-order functions help organize code into smaller, more maintainable chunks.

## Conclusion

This article has explored what a higher-order function is, the benefits of using them, and how to use them in practical applications.

By using higher-order functions, web developers can work more efficiently by organizing their code into smaller, more readable chunks, making it easier to debug.

Now, when you encounter methods like map(), filter(), and reduce() and find them confusing, just remember the following:

Use map when you want to transform an array.
Use filter to select a subset of data from an array.
Use reduce when you want to return a single value as a result.
