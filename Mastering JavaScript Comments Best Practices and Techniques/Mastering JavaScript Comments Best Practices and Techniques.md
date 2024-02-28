# Mastering JavaScript Comments: Best Practices and Techniques

![image](./assets/comments.png)

As you embark on your programming journey, you’ll soon realize that writing code isn’t just about giving instructions for your computer to follow. It’s also about ensuring that your code is comprehensible to both yourself and others who may collaborate on it. One crucial method for achieving this is by incorporating comments into your code. Comments are textual annotations that are not executed by the computer but serve to explain what the code accomplishes and why it’s structured the way it is.

In this blog post, we’ll delve into the various methods for adding comments to your JavaScript code, focusing particularly on commenting multiple lines. This skill is especially valuable for programming novices as it instills the habit of documenting code, thereby enhancing its readability for all stakeholders.

## Why Comments are Important in JavaScript

### Enhanced Code Readability:

Comments improve code clarity by providing insights into its purpose and functionality. They serve as guides, especially when revisiting older code after a significant period.

Consider the uncommented code snippet:

```
function calculateTotal(price, quantity) {
    return price * quantity;
}

let totalPrice = calculateTotal(25, 5);
console.log(totalPrice); // Output: 125

```

Understanding the code’s functionality here might prove challenging. Now, let’s add comments for clarity:

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

### Facilitating Collaboration

In a team environment, comments foster collaboration by aiding developers in comprehending each other’s code, thereby facilitating smoother project development.

Imagine a scenario where different developers handle various sections of a project. Clear comments help in understanding each other’s code, as demonstrated below:

```
// Function to validate email format
function validateEmail(email) {
    // Regular expression to check email format
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailRegex.test(email);
}

```

In a collaborative setting, another developer can quickly grasp the purpose of the validateEmail function due to the comment, fostering seamless teamwork that would otherwise be challenging without such annotations.

### Maintenance and Debugging

Well-commented code simplifies maintenance and debugging tasks. Comments can highlight potential issues, explain specific solutions, and assist in locating bugs.

Consider the following commented code snippet:

```
// Function to find the maximum number
function findMax(num1, num2) {
    /* Using the ternary operator to compare num1 and num2
       and return the larger number */
    return (num1 > num2) ? num1 : num2;
}

```

If a bug arises or modifications are needed, the comment clarifies the logic used, aiding in swift debugging or updates.

### Tagging

Using JSDoc tags is another good practice for development teams to express their ideas on code to team members. Tags add a semantic structure to comments, allowing development tools to utilize this data for smart analysis.

```
/**
 * @example
 * // returns 6
 * multiplication(2, 3);
 * @example
 * // returns -6
 * @param {number} a - a number to multiply
 * @param {number} b - a number to multiply
 * multiplication(-2, 3);
 */
function multiplication(a, b) {
  return a * b;
};

```

Likewise, you can use many tagging options, and these tags provide a clear indication for other developers who visit your work.

### Store Metadata

Storing metadata of a file is another common use of comments. For example, we can include information like author, version, and repo links within metadata, which becomes handy in open-source applications.

```
/**
 * @author Nipuni Arunodi
 * @version 0.0.1
 * ...
 */

```

_Note: These usages are not defined or fixed. Developers can have their own practices, and I have presented some of the most used scenarios._

### Commenting Out Code for Testing

Comments can also be used to quickly and easily prevent code execution for testing and debugging purposes, a technique known as “commenting out code.”

If there’s an error in some code you’ve written, commenting out sections will prevent them from running, aiding in pinpointing the issue’s source. You may also use this technique to toggle between code segments to test different results.

```
// Function to add two numbers
function addTwoNumbers(x, y) {
  let sum = x + y;
  return sum;
}

// Function to multiply two numbers
function multiplyTwoNumbers(x, y) {
  let product = x * y;
  return product;
}

/* In this example, we're commenting out the addTwoNumbers
function, therefore preventing it from executing. Only the
multiplyTwoNumbers function will run */

// addTwoNumbers(3, 5);
multiplyTwoNumbers(5, 9);

```

## Best Practices for Commenting in JavaScript

### Use Descriptive Comments

Explain the purpose of functions, variables, or complex logic using descriptive comments. This helps other developers, including your future self, understand the code’s intention.

```
// Function to calculate the area of a circle
function calculateCircleArea(radius) {
    return Math.PI * radius * radius;
}

```

Descriptive comments like this elucidate the purpose of functions or operations, aiding in understanding the code’s intention.

Comments should be insightful for the person who reads them, and we should always avoid writing how the code works in comments. Here, the code should be able to self-explain how it works, keeping comments to address why it’s there in the first place.

```
// Do
let p = 3.14; // Rounded value of Pi
let c = 2 * p * 10; // Calculate the circumference of a circle with radius 10// Don't
let p = 3.14; // Initiate the value of the variable p
let c = 2 * p * 10 // Multiply the value p into 20

```

## Avoid Over-commenting

While comments are beneficial, excessive commenting can clutter the code. Aim for a balance where comments add value without stating the obvious.

```
// Variable to store user data
let userData = fetchUserData(); // Fetch user data from the server

```

In this case, the comment merely reiterates what the code already expresses clearly. Avoiding over-commenting maintains code clarity.

Using comments is good. However, you shouldn’t overdo it by describing the code beyond what’s required. The challenge here is that you also need to maintain comments and modify them. Besides, it could negatively affect the readability of the code.

```
// Do
/**
 * Retrieve a list users from the database
 */
async function getUsers() {
 // ...
}// Don't
/**
 * Retrieve a list of user objects asynchronously by invoking a database query
 */
async function getUsers() {
 // ...
}

```

## Update Comments Regularly:

As code evolves, ensure comments remain accurate and aligned with the code changes. Outdated comments can lead to confusion.

```
// Function to calculate the area of a rectangle
function calculateRectangleArea(length, width) {
    return length * width;
    // Updated comment: Area calculated by multiplying length and width
}

```

Ensuring that comments align with the current functionality or logic of the code is vital for accurate documentation.

## Comment Complex Sections

When dealing with intricate algorithms or unconventional solutions, detailed comments explaining the logic can be immensely helpful.

```
// Function to perform a complex calculation
function performComplexCalculation(data) {
    /*
        Complex logic involving multiple steps:
        - Step 1: Data preprocessing
        - Step 2: Calculation based on preprocessed data
        - Step 3: Final result
    */
    // ... complex calculation logic
}

```

For intricate algorithms or multi-step processes, detailed comments explaining each step can immensely aid in understanding.

### Avoid Abbreviations

Avoid abbreviations like “aka” or “viz” as not everyone may understand them, which defeats the purpose of clear communication.

```
// Do
/**
 * regEx, in other words Regular Expressions
 */// Don't
/**
 * regEx, viz. Regular Expressions

```

## Additional Tips

1. Use Comments Before Code: Place comments above the code you’re explaining to save time for the reader.

```
/**
* Fetches articles of a writer based on writerId
* @param {string} writerId - The Id of the writer.
*/
function getArticles(writerId) {
 // ...
}

```

2. Pay Extra Attention to Numeric Values: Explain units and ranges of numeric values and any input data restrictions using comments.

3. Leverage Editor Support: Modern code editors offer various functionalities for commenting. Utilize shortcuts and extensions to enhance your commenting workflow.

## Types of Comments in JavaScript

### Single-line Comments

In JavaScript, single-line comments start with //. They're suitable for brief explanations or annotating specific lines.

```

// This function calculates the square of a number
function square(number) {
    return number * number;
}

```

### Inline Comments

Single-line comments at the end of a code line are referred to as inline comments.

```

let x = 99;    // assign numerical value to x
let y = x + 2; // assign the sum of x + 2 to y

```

### Multi-line Comments

Multi-line comments begin with /_ and end with _/. They're useful for commenting out blocks of code or providing longer explanations.

```

/*
    This block of code finds the maximum of two numbers
    and returns the larger number.
*/
function findMax(num1, num2) {
    // Logic to find the maximum
    return (num1 > num2) ? num1 : num2;
}

```

### Nested Comments

JavaScript does not support nested multi-line comments. Attempting to nest a comment within another will result in an error. However, you can use single-line comments inside multi-line comments to avoid this issue.

```

/*
This is a multi-line comment
/*
This is an attempt to nest a comment, but it will cause an error!
*/
console.log("Hello, World!");

```

In conclusion, this article discussed various use cases of comments in JavaScript and the best practices to follow. Adhering to these practices increases readability, making it easier for you and your team to understand your code. We hope these suggestions will help you enhance the readability of your code. If you have any suggestions, please share them with others in the comments section.

Thank you for Reading and happy coding!!
