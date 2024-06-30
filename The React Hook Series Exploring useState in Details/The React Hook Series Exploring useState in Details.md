# The React Hook Series: Exploring useState in Details

![image](./assets/useState.png)

## What is useState?

This Hook is probably the most commonly used in React. It allows us to declare, read, and update a state variable easily.

It returns an array in the format [value, setValue] where value is the current value of the variable, and the setValue function is the function that updates the value of the variable.

useState only accepts one argument: the initial value of the state variable. Let's take a look at an example.

## Initialization

The very first step is to import the Hook:

```

import React, { useState } from 'react';

```

Then, we can declare and initialize a variable by destructuring the returned array like so:

```

// declares and initializes count as 0
const [count, setCount] = useState(0);

```

In the example above, we are declaring the count variable and its update function setCount. It translates to this.state.count and this.setState in a class-based component. We pass 0 in useState as an argument, which initializes count to 0.

## Getting values

In the traditional class-based component, to get the value of the variable, you can simply use this.state.variable. For example:

```

<p>The value of count is: {this.state.count}</p>

```

It is pretty much similar when using useState except that you can leave out this.state:

```

<p>The value of count is: {count}</p>

```

## Updating values

Instead of using this.setState to update variable values, we can use the update function we declared upon initialization. To increment count, for example:

```

setCount(count+1);

```

You can call this setCount() function like any ordinary function, such as:

```

<button onClick={() => setCount(count + 1)}>
Add count
</button>

const addCount = () =>{
setCount(count + 1);
}

```

## Important Things to Note

We have learned how to use and implement this Hook. It’s really simple and easy to use, and that’s pretty much all you need to know to get started with it. However, there are a couple of details that are useful to know when using this Hook.

1. Update function overrides, not merges: Unlike this.setState in classcomponents, the update function of useState (i.e., setState()) will override instead of merging changes. For example, let's say you have an object variable and initialize it:

```

const [todo, setTodo] = useState({color: 'blue', text: ' '})

```

Then, you want to update the text property and keep color as blue. The code below will override and remove the color property from the object:

```

function addNote(someText){
setTodo(prevState => return {todo.text: someText})
}
// todo = {text: someText}, color property gone

```

Instead, you have to use the spread operator like so:

```

setState(prevState => {
return {...prevState, todo.text: someText};
});
// todo = {color: 'blue', text: someText}

```

2. Update function will enqueue a re-render: Also, note that whenever an update function is called, a re-render is enqueued, which means the component re-renders every time the state is updated. In other words, it can be expensive to use useState for variables that often change and have to be updated. Hence, expensive or frequent state changes can be solved with the useRef or useMemo Hooks which we will see in future articles of this series.

3. useState is called upon every re-renders: Relating to the previous point, an update to the state enqueues a re-render, so what happens after a re-render? As we’ve learned, an argument passed into useState will be used as the initial value of the variable. However, upon subsequent renders, the argument is ignored and instead, the Hook reads the latest value of the variable and returns it. For example, let's say we have a state and initialize it as shown below:

```

const [blog, setBlog] = useState('Victoria Lo'); // initial value

```

On the first render, React will read the argument and set the blog state to its initial value, ‘Victoria Lo’. Then, we perform some kind of update to the state:

```

setBlog('Articles by Victoria');
// now blog should be 'Articles by Victoria'

```

On the next render, React calls the Hook again, but this time, it ignores the argument and returns the latest value of the state (i.e., Articles by Victoria).

4. Remember that variables are immutable: When we initialize our state variables, remember that we use const, meaning that we cannot change their values directly. So if we have an array, for example, we can initialize it as:

```

const [myArray, setMyArray] = useState(['a', 'b']);

```

Usually, we can add elements to an array using .push(), such as:

```

myArray.push('c');

```

This, however, will not work with our update function because we are not allowed to directly modify our array. We can use the spread operator, which will copy and return a new array with updated values. And as mentioned in the first point, the update function overrides, not merges changes.

```

setMyArray(myArray =>([...myArray, 'c']));
// myArray = ['a', 'b', 'c'];

```

## Conclusion

And that’s the gist of this Hook! Thanks for reading this article. I hope it was helpful for React beginners. Please feel free to ask questions in the comments below. Ultimately, practicing and building projects with this Hook will help anyone to pick it up faster.
