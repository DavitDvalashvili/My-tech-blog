# JavaScript Array Methods Your Complete Guide

![image](./assets/Arrays.png)

In JavaScript, an array is a special type of object used to store and organize multiple values. Arrays enable you to group values under a single variable name, facilitating the management and manipulation of data collections. Here’s a more detailed explanation:

A pair of square brackets [] represents an array in JavaScript. All elements in the array are separated by commas ,.

In JavaScript, arrays can contain elements of any type. This means you can create arrays with elements of types such as String, Boolean, Number, Objects, and even other Arrays.

Here’s an example of an array with four elements: a Number, Boolean, String, and Object.

```

const mixedTypedArray = [100, true, 'javascript', {}];

```

The position of an element in the array is known as its index. In JavaScript, array indexing starts with 0 and increments by one for each element. For example, in the above array, the element 100 is at index 0, true is at index 1, 'javascript' is at index 2, and so on.

The number of elements in the array determines its length. For example, the length of the above array is four.

Interestingly, JavaScript arrays are not of fixed length. You can change the length anytime by assigning a positive numeric value. We will learn more about that shortly.

## Destructive Array Methods

Destructive array methods alter the original arrays and return a modified array. Let’s explore various methods for manipulating arrays that change the original array.

Methods to Add to or Remove from an Array

It’s common to need to add or remove an element from an array. For example, consider this array of names:

```

let names = ["John Doe", "Jane Doe", "Ann Doe"];

```

You can manipulate this array using one of the following methods to add or remove either the first, last, or a specific element from the array.

### pop()

This method removes the last element of the attached JavaScript array, altering the original array, and returns the removed element.

```

myArray.pop();

```

Note: You don’t pass anything as a parameter to the pop() method.

Here’s an example showing how to use the pop() method:

```

let names = ["John Doe", "Jane Doe", "Ann Doe"];
names.pop(); // "Ann Doe"
console.log(names); // ['John Doe', 'Jane Doe']

```

### push()

This method adds new element(s) to the end of the attached JavaScript array, changing the original array, and returns the new length of the array. This method accepts the elements you wish to add at the end of the array as parameters.

```

myArray.push(element1, element2, ..., elementX);

```

Let’s now create a new array of scores and then add more scores to the array using the push() method:

```

let scores = [12, 55, 78, 95, 33];
scores.push(66, 77); // 7

console.log(scores); // [12, 55, 78, 95, 33, 66, 77]

```

### shift()

The shift() method removes the first element of an array. It works similarly to the pop() method, but instead of removing from the end, it removes from the beginning of the attached array. It returns the removed/shifted element.

```

myArray.shift();

```

Let’s now create a new array of animal names and then learn how to use the shift() method to remove the first name from the array:

```

let animalNames = ["Lion", "Dog", "Snake", "Tiger"];
animalNames.shift(); // "Lion"

console.log(animalNames); // ['Dog', 'Snake', 'Tiger']

```

### unshift()

The unshift() method works similarly to the push() method as it is used to add new elements to an array, but to the beginning of an array. This method takes the element(s) you wish to add at the beginning of the array as parameters. It also returns the new length of the array.

```

myArray.unshift(element1, element2, ..., elementX);

```

Let’s now create a new array of food names and then add more food names to the array using the unshift() method:

```

let foodNames = ["Salad", "Bread", "Fish", "Rice"];
foodNames.unshift("Pizza", "Cake"); // Returns 6 - the length of the newly changed array
console.log(foodNames); // ['Pizza', 'Cake', 'Salad', 'Bread', 'Fish', 'Rice']

```

### splice()

The splice() method adds or removes specific element(s) from an array. When removing elements, it returns the removed element(s) in an array, and when adding elements, it returns an empty array.

```

myArray.splice(index, howMany, element1, element2, ..., elementX);

```

In the above syntax, index is a required parameter representing the position where you want to add or remove elements. howMany is an optional parameter indicating the number of elements to be removed. Any other parameter is optional and represents the new element(s) you want to add to the specified position.

Suppose you have an array of fruits:

```

let fruits = ["Mango", "Strawberries", "Lime", "Oranges", "Pomegranate"];

```

You can use the splice() method to remove specific elements such as the third fruit, the first and second fruits, and more:

```
// Remove third fruit
fruits.splice(2,1); // ['Lime']
console.log(fruits); // ["Mango", "Strawberries", "Oranges", "Pomegranate"]

// Remove the first and second fruits
fruits.splice(0,2); // ['Mango', 'Strawberries']
console.log(fruits); // ["Oranges", "Pomegranate"]

```

You can also add specific fruits to specific positions within your array using the splice() method:

```

// Add to the first position without removing any elements
fruits.splice(0, 0, "Grape"); // []
console.log(fruits); // ['Grape', 'Mango', 'Strawberries', 'Lime', 'Oranges', 'Pomegranate']

// Add to the fifth and sixth position by replacing them with new fruits
fruits.splice(4, 2, "Bananas", "Avocado"); // ['Oranges', 'Pomegranate']
console.log(fruits); // ['Grape', 'Mango', 'Strawberries', 'Lime', 'Bananas', 'Avocado']

```

The splice() method is one of the most flexible tools for adding and removing elements from arrays.

## Non-Destructive Array Methods

A non-destructive array method returns a new or non-modified array even after using an array method. If you want to preserve the original array while assigning the new output to a new array, you can use these non-destructive array methods.

### concat()

Suppose you have two or more arrays that you want to join together. You can use the concat() method. This method joins the arrays or adds an element to an array and then returns a new array containing the joined arrays or new element(s).

```

myArray1.concat(myArray2, myArray3, ..., myArrayX)
// or
array1.concat(element1, ..., elementX)

```

Suppose you have two arrays of European and African country names:

```

let EuroCountries = ["Germany", "Poland", "Sweden"];
let AfricanCountries = ["Ghana", "Nigeria"];

```

You can then combine these arrays with the concat() method and assign the new array to a new variable, thereby leaving our original arrays still intact:

```

let countries = EuroCountries.concat(AfricanCountries);

console.log(countries); // ['Germany', 'Poland', 'Sweden', 'Ghana', 'Nigeria']

```

You can also add only elements, or you can add arrays and elements as seen below:

```
let countries = EuroCountries.concat("Togo", "Rwanda");
console.log(countries); // ['Germany', 'Poland', 'Sweden', 'Togo', 'Rwanda']

let countries = EuroCountries.concat(AfricanCountries, "South Africa");
console.log(countries); // ['Germany', 'Poland', 'Sweden', 'Ghana', 'Nigeria', 'South Africa']

```

### slice()

The slice() method takes the specified element(s) from one array into a new one without changing the original. This method takes two optional parameters: the start and end positions. By default, the start is 0, while the end is your array’s last element.

```

// Syntax
myArray.slice(start, end)

```

The start position indicates the index position of the first element, while the end position is the last position that is not included among the copied elements. In this array of countries, we use the slice method to copy elements into new arrays:

```

let countries = ['Germany', 'Poland', 'Sweden', 'Ghana', 'Nigeria', 'South Africa'];

let euroCountries = countries.slice(0, 3);
console.log(euroCountries); // ['Germany', 'Poland', 'Sweden']

let africanCountries = countries.slice(3);
console.log(africanCountries); // ['Ghana', 'Nigeria', 'South Africa']

```

### fill()

Using the fill() operation, we can replace certain elements with static values. This method is an in-place method, meaning that it modifies the original array. It does not return a new array.

```

Syntax:
array.fill(value, start, end)

```

Parameters:

value – The static value which you want to fill in the array
start – The value of the index from where you want to replace the array
end – The last value of the index

```

const nums = [1, 2, 3, 5, 6];
nums.fill(0); // fills the entire array with 0
console.log(nums);

const strings = ["code", "damn", "web2", "web3"];
strings.fill("abc", 2, 4); // fills the elements with abc at index 2 and 3
console.log(strings);

//output
[0, 0, 0, 0, 0]
['code', 'damn', 'abc', 'abc']

```

## Join an Array

Let’s say you need to join all the array elements to become a string. You can do this with the join() method without altering or changing the original array.

### join()

The join() method returns an array as a string. This method takes in your preferred separator as its parameter.

```

// Syntax
myArray.join(separator)

```

The separator parameter is optional – if you don’t put anything in, it will default to using a comma. But, as you can see in our example, it does accept other symbols and spaces to separate each element in your array when converting it to a string:

```

let names = ['John', 'Doe'];
let joinedNames1 = names.join(); // 'John,Doe'
let joinedNames2 = names.join(' '); // 'John Doe'
let joinedNames3 = names.join('-'); // 'John-Doe'

```

## Iterating over Array Elements

Traditionally, you had to use loops to iterate through an array if you wanted to do any kind of data checks or processing on the individual elements.

For example, if you had an array of students where you wanted to display a particular student on a website, you’d have to loop through the entire array and then create your own logic to filter them based on your filter criteria.

Handling all this from scratch can be very complex, but JavaScript already has some built-in methods you can use to perform all these tasks efficiently. Here is an overview of the most common methods for iterating over your arrays.

## includes()

As the term suggests, the includes() method checks through an array to see if the array contains a specified value. If it contains that value, it returns true – if not, it will return false. The method accepts two parameters: the specific value, and the optional start position.

```

// Syntax
myArray.includes(value, start)

```

Suppose you have an array of fruits. Let’s check if the array includes “Apple”:

```

let fruits = ["Apple", "Strawberries", "Mango", "Lime", "Oranges"];

console.log(fruits.includes("Apple")); // true
console.log(fruits.includes("Apple", 3)); // false

```

### every()

The every() method executes a function for each element of an array in the form of an evaluation. It returns true if all the array elements pass the evaluation and returns false (and stops execution) if at least one element fails the evaluation. This method uses a callback function as an argument which is evaluated for each element.

```

// Syntax
myArray.every(callbackFn)

```

Suppose you have an array of users’ ages, and you want to check if all the users are below 50 years old:

```

let usersAge = [22, 56, 75, 33, 22, 80, 12, 43, 23];

console.log(usersAge.every((age) => age < 50)); // false

```

You can also decide to create the function and then pass it in:

```

let usersAge = [22, 56, 75, 33, 22, 80, 12, 43, 23];

function checkAge(age) {
    return age < 50;
}

console.log(usersAge.every(checkAge)); // false

```

Note: This method does not execute the function for empty elements.

### some()

The some() method is very similar to the every() method, but this time returns true and stops execution if it passes the evaluation for one of the array elements. It will return false if all the elements fail the evaluation.

```

// Syntax
myArray.some(callbackFn)

```

In the callback function, you have access to each element, the index, and the original array itself:

```

```

// Normal function
myArray.some(function(element, index, array){ /_ ... _/ })

// Arrow function
myArray.some((element, index, array) => { /_ ... _/ })

```

In our array of users’ ages, suppose you want to check if at least one is above 50 years:

```

let usersAge = [22, 56, 75, 33, 22, 80, 12, 43, 23];

console.log(usersAge.some((age) => age > 50)); // true

```

Note: This method does not execute the function for empty elements.

### find()

The find method is also similar to the some() method but doesn’t return a boolean—it will instead return the first element that passes a test. Like the some() and every() method, it also executes the callback function for every element and will return undefined if no element passes the test. Its syntax is also similar to both methods.

```

// Syntax
myArray.find(callbackFn)

```

Suppose you have an array of students, with each student having an object that contains their name and age. You can find a student with a particular name and output the student’s age:

```

let students = [
{ name: "John Doe", age: 22 },
{ name: "Jane Doe", age: 33 },
{ name: "Karl Don", age: 21 }
];

console.log(students.find((student) => student.name === "John Doe").age); // 22

```

You can decide to extract the function:

```

let students = [
{ name: "John Doe", age: 22 },
{ name: "Jane Doe", age: 33 },
{ name: "Karl Don", age: 21 }
];

const checkStudents = (student) => {
if (student.name === "John Doe") {
return student;
}
};

console.log(students.find(checkStudents).age); // 22

```

Note: This method does not execute the function for empty elements.

```

### findIndex()

This method is very similar to the find() method, but this time, instead of returning the element, it returns the index (position) of the first element in the array that passes the test function. It will return -1 if nothing matches. Its syntax is similar to the find() method.

```

// Syntax
myArray.findIndex(callbackFn)

```

Suppose you have an array of students, each with an object containing their name and age. You can find a student with a particular name and output the index of that student:

```

let students = [
    { name: "John Doe", age: 22 },
    { name: "Jane Doe", age: 33 },
    { name: "Karl Don", age: 21 }
];

const checkStudents = (student) => {
    if (student.name === "Jane Doe") {
        return student
    }
};

console.log(students.findIndex(checkStudents)); // 1

```

You can also use one line with an arrow function:

```

let students = [
    { name: "John Doe", age: 22 },
    { name: "Jane Doe", age: 33 },
    { name: "Karl Don", age: 21 }
];

console.log(students.findIndex((student) => student.name === "Jane Doe")); // 1

```

### indexOf()

The indexOf() method checks each element and returns the index of the first element that matches the specified value. It searches using strict equality (===) and returns -1 if the specified value does not match any element(s) in the array.

The findIndexOf() method and indexOf() are similar, but findIndexOf() takes a callback function, while indexOf() allows you to directly pass the value you’re looking for.

```

// Syntax
myArray.indexOf(item)
myArray.indexOf(item, start)

```

The start parameter is optional, indicating the index position from which the search should begin. When using a negative number, the search begins from the end of the array. By default, its value is 0. Here's an example:

```

let scores = [23, 56, 67, 22, 45, 57, 45, 7, 5, 34, 7];

console.log(scores.indexOf(7));     // Output: 7
console.log(scores.indexOf(7, -1)); // Output: 10

```

### filter()

The filter() method traverses the entire array, selecting elements that meet a specified condition, and returns them in a new array.

```

// Syntax
myArray.filter(callbackFn)

```

In the callback function, you have access to each element, its index, and the original array itself. For example:

```

let students = [
    { name: "John Doe", age: 22 },
    { name: "Jane Doe", age: 33 },
    { name: "Karl Don", age: 21 }
];

console.log(students.filter((student) => student.age < 30));

```

This will output:

```

[
    { "name": "John Doe", "age": 22 },
    { "name": "Karl Don", "age": 21 }
]

```

Note: filter() doesn't execute the function for empty elements.

### forEach()

The forEach() method loops through all array elements and calls a function (callback function) for each element. The callback function has access to the current element, index, and the entire array on every loop.

```

// Syntax
myArray.forEach(callbackFn)

```

For example:

```

let staff = [
    { name: "John Doe", salary: 120 },
    { name: "Jane Doe", salary: 350 },
    { name: "Karl Don", salary: 710 }
];

let totalSalary = 0;

staff.forEach((staffPerson) => {
    totalSalary += staffPerson.salary;
});

console.log(totalSalary); // Output: 1180

```

Note: forEach() doesn't execute the function for empty elements.

### map()

The map() method iterates over an array, applying a callback function to each element and returning a new array of modified elements.

```

// Syntax
myArray.map(callbackFn)

```

For example:

```

let scores = [45, 71, 65, 80, 47];

let newScores = scores.map((score) => score + 5);

console.log(newScores); // Output: [50, 76, 70, 85, 52]

```

### reduce()

The reduce() method applies a reducer function to each element of an array and returns a single output. The reducer function iterates through all elements in the array and returns the result of the previous element’s calculation.

```

/ Syntax
myArray.reduce(callbackFn, initialValue)

```

For example:

```
let staff = [
    { name: "John Doe", salary: 120 },
    { name: "Jane Doe", salary: 350 },
    { name: "Karl Don", salary: 710 }
];

const totalSalary = staff.reduce((total, staffPerson) => {
    total += staffPerson.salary;
    return total;
}, 0);

console.log(totalSalary); // Output: 1180

```

Note: reduce() is a complex array method.

### flat()

The flat() method creates a new array by concatenating all sub-array elements based on a specified depth.

```

// Syntax
myArray.flat()
myArray.flat(depth)

```

For example:

```

let numbers = [23, 56, 67, [22, 45, 57, [45, 7], 5], [34, 7]];

console.log(numbers.flat());  // Output: [23, 56, 67, 22, 45, 57, [45, 7], 5, 34, 7]
console.log(numbers.flat(2)); // Output: [23, 56, 67, 22, 45, 57, 45, 7, 5, 34, 7]

```

### flatmap()

The flatmap() method combines map() and flat(), applying a given callback function to each array element and then flattening the result by one level.

```

// Syntax
myArray.flatMap(callbackFn)

```

For example:

```

let numbers = [23, 56, 67, 22, 45, 57, 45, 7, 5];

let doubleNumbers = numbers.flatMap((number) => number * 2);

console.log(doubleNumbers); // Output: [46, 112, 134, 44, 90, 114, 90, 14, 10]

```

End of the Array,

Happy coding….. ❤
