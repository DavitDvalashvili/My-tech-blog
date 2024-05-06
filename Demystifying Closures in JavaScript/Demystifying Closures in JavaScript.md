# Demystifying Closures in JavaScript

![image](./assets/closure.png)

JavaScript is a versatile and dynamic language, but some of its concepts can be quite puzzling, especially for beginners. One such concept is closures. In this article, we’ll break down the concept of closures, explain how they work, and explore some real-world use cases. By the end of this guide, you’ll have a clear understanding of closures, even if you’re new to programming.

## What are Closures?

In JavaScript, a closure is created when a function is defined within another function, and the inner function has access to the outer function’s variables and parameters. In simpler terms, a closure is a combination of a function and the environment in which it was declared.

## How Closures Work

JavaScript uses lexical scoping, which means that the scope of a variable or function is determined by its position in the code. When a function is defined inside another function, the inner function forms a closure over the outer function’s variables and parameters. This enables the inner function to access these variables even after the outer function has completed its execution.

Let’s see a practical example:

```

function outer() {
  const name = 'John';

  function inner() {
    console.log(`Hello ${name}!`);
  }

  return inner;
}

const greet = outer();
greet(); // Output: Hello John!

```

In this example, inner has access to the name variable from the outer function even after outer has finished executing.

```

// Function to calculate the total cost
function calculateTotal(price, quantity) {
    return price * quantity;
}

// Calculate the total price of 5 items at $25 each
let totalPrice = calculateTotal(25, 5);
console.log(totalPrice); // Output: 125

```

With comments, it’s evident what each part of the code does, significantly enhancing its readability.

## Private Variables and Functions

One of the key advantages of closures is their ability to create private variables and functions in JavaScript. Private variables or functions are not accessible outside the scope of the closure.

```

function counter() {
  let count = 0;

  return function() {
    count++;
    console.log(count);
  }
}

const increment = counter();
increment(); // Output: 1
increment(); // Output: 2
increment(); // Output: 3

```

Here, the count variable is private to the counter function, and it cannot be directly accessed or modified from outside the closure.

## Callback Functions

Closures are also commonly used to create callback functions, which are functions passed as arguments to other functions and executed by them. Callback functions can access variables in their outer scope, making them powerful tools in asynchronous programming.

```

function getData(url, callback) {
  const xhr = new XMLHttpRequest();

  xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 and xhr.status === 200) {
      const data = JSON.parse(xhr.responseText);
      callback(data);
    }
  };

  xhr.open('GET', url);
  xhr.send();
}

getData('https://example.com/data', function(data) {
  console.log(data);
});

```

In this example, the callback function has access to the data variable from its outer scope, allowing it to handle the response data effectively.

## Understanding Scope

Before diving deeper into closures, it’s crucial to understand the concept of scope. In JavaScript, a scope is created by a function or a code block. It defines the boundaries within which variables are accessible.

function foo() {
let count = 0;
console.log(count); // logs 0
}

```
foo();
console.log(count); // ReferenceError: count is not defined

```

Variables are accessible only within their respective scopes. You can reuse common variable names in different scopes without conflicts.

```

function foo() {
  let count = 0;
  console.log(count); // logs 0
}

function bar() {
  let count = 1;
  console.log(count); // logs 1
}

foo();
bar();

```

## Scopes Nesting

JavaScript allows you to nest scopes, with inner scopes accessing variables from outer scopes.

```

function outerFunc() {
  let outerVar = 'I am outside!';

  function innerFunc() {
    console.log(outerVar); // logs "I am outside!"
  }

  innerFunc();
}

outerFunc();

```

In this example, innerFunc can access the outerVar variable from its outer scope, showcasing the concept of scopes nesting.

## The Lexical Scope

JavaScript uses lexical (or static) scoping, which means that the accessibility of variables is determined by their position within nested scopes. This allows inner scopes to access variables from outer scopes.

```

const myGlobal = 0;

function func() {
  const myVar = 1;
  console.log(myGlobal); // logs "0"

  function innerOfFunc() {
    const myInnerVar = 2;
    console.log(myVar, myGlobal); // logs "1 0"
  }

  innerOfFunc();
}

func();

```

## The Closure

The closure is the final piece of the puzzle. A closure is a function that remembers the variables from the place where it is defined, regardless of where it is executed later.

```

function outerFunc() {
  let outerVar = 'I am outside!';

  function innerFunc() {
    console.log(outerVar); // logs "I am outside!"
  }

  return innerFunc;
}

function exec() {
  const myInnerFunc = outerFunc();
  myInnerFunc();
}

exec();

```

In this example, innerFunc still has access to outerVar from its lexical scope, even when executed outside of that scope. It "closes over" the variable, hence the term "closure."

## Conclusion

Closures are a fundamental concept in JavaScript, and they empower you to write more robust and maintainable code. By understanding how they work and their practical applications, you can take your JavaScript skills to the next level. Closures allow you to create private variables, implement callback functions, and work with nested scopes, making them a valuable tool in your programming arsenal.

In summary, closures are not as intimidating as they may seem at first. They are a powerful feature that can enhance your JavaScript coding capabilities, even if you’re just starting your programming journey. So, embrace closures, experiment with them, and watch your code become more elegant and efficient. Happy coding! 🚀
