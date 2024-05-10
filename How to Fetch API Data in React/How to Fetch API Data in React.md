# How to Fetch API Data in React

![image](./assets/fetchData.png)

## Introduction

As web developers, we often need to interact with APIs to retrieve data from servers and integrate it into our React applications. Understanding how to fetch data into React applications is essential for every React developer aiming to build modern, real-world web applications. In this article, we will explore how to fetch API data in React, step by step, using both the Fetch API and Axios library.

## Prerequisites

Before we dive into API fetching, make sure you have a basic understanding of React and have set up a React project using Node.js and npm. If you’re new to React, check out the official React documentation for a quick introduction.

## About API

Regarding APIs, they stand for “Application Programming Interface.” It is a set of rules and protocols that allows different software applications to communicate and interact with each other.

An API defines the methods and data formats that developers can use to request and exchange information between applications, services, or systems. It acts as an intermediary that enables the seamless integration of different software components, allowing them to work together and share data.

## Getting Started

Let’s start by creating a new React application using Create React App, a popular tool for setting up a React environment quickly. Open your terminal and run the following commands:

```

npx create-react-app fetch-api-demo
cd fetch-api-demo
npm start

```

## Considerations before Fetching Data

When we request data, we must prepare a state to store the data upon return. For that purpose, we will store the returned data in the React local state.

When we request to fetch data from the backend, we perform a side effect, which is an operation that can generate different outputs for the same data fetching. For instance, the same request returns a success or error.

```
const [data, setData] = useState(null);
const [error, setError] = useState(null);

```

The useEffect hook is used to trigger the API request when the component mounts.

```

useEffect(() => {
  // data fetching here
}, []);

```

## Fetch API

The Fetch API, through the fetch() method, allows us to make an HTTP request to the backend. With this method, we can perform different types of operations using HTTP methods like the GET method to request data from an endpoint, POST to send data to an endpoint, and so on. Since we are fetching data, our focus is the GET method.

Let’s recap what we have so far.

```

import { useState, useEffect } from "react";

```

```

export default function App() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/posts`)
      .then((response) => console.log(response));
  }, []);
  return <div className="App">App</div>;
}

```

In the code, we are using the fetch() method to request post data from the resource endpoint, as seen in the useEffect Hook.

Next, we must resolve the Response object to JSON format using the json() method. This also returns a promise, and from there, we can resolve to get the actual data that we need.

```

useEffect(() => {
  fetch(`https://jsonplaceholder.typicode.com/posts`)
    .then((response) => response.json())
    .then((actualData) => console.log(actualData));
}, []);

```

In the case of a rejection, we need to handle the error like this.

```

useEffect(() => {
  fetch(`https://jsonplaceholder.typicode.com/posts`)
    .then((response) => response.json())
    .then((actualData) => console.log(actualData))
    .catch((err) => {
      console.log(err.message);
    });
}, []);

```

Earlier, we saw how the Response object returns the HTTP status. The OK status is true if we hit the correct endpoint; otherwise, it returns false. By checking for that status, we can write a custom error message for a “404 Not Found” scenario, like so:

And now, the useEffect Hook looks like this:

```

useEffect(() => {
  fetch(`https://jsonplaceholder.typicode.com/posts`)
    .then((response) => {
      if (!response.ok) {
        throw new Error(
          `This is an HTTP error: The status is ${response.status}`
        );
      }
      return response.json();
    })
    .then((actualData) => console.log(actualData))
    .catch((err) => {
      console.log(err.message);
    });
}, []);

```

## Using the async/await Syntax

The previous method explained data fetching using the pure promise syntax. Here we will learn a more elegant method to get data using the async/await.

When we make a request and expect a response, we can add the await syntax in front of the function to wait until the promise settles with the result. But, to use this syntax, we must call it inside the async function in typical JavaScript code.

In the case of fetch(), the syntax looks like so:

```

useEffect(() => {
  async function getData() {
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/posts?_limit=10`
    );
    console.log(response);
  }
  getData();
}, []);

```

In the code, we use the await to wait for the promise from fetch(). Remember, we need the data in json() format, so let’s wait for that as well:

```

useEffect(() => {
  async function getData() {
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/posts?_limit=10`
    );
    let actualData = await response.json();
    console.log(actualData);
  }
  getData();
}, []);

```

Notice we don’t chain .then as we’ve done in the previous method. However, it’s fine to use .then() with async/await:

```

useEffect(() => {
  async function getData() {
    const actualData = await fetch(
    `https://jsonplaceholder.typicode.com/posts?_limit=10`
    ).then(response => response.json());
    console.log(actualData);
  }
  getData();
}, []);

```

In practice, we often use async/await with a try/catch/finally statement to catch errors and manage the loading state. This is similar to using .then, .catch, and .finally in the previous method:

```

useEffect(() => {
  const getData = async () => {
    try {
      const response = await fetch(
        `https://jsonplaceholder.typicode.com/posts?_limit=10`
      );
      if (!response.ok) {
        throw new Error(
          `This is an HTTP error: The status is ${response.status}`
        );
      }
      let actualData = await response.json();
      setData(actualData);
      setError(null);
    } catch(err) {
      setError(err.message);
      setData(null);
    } finally {
      setLoading(false);
    }
  }
  getData();
}, []);

```

The code above is similar to the previous method. Here, when an error occurs in the try block, the catch statement catches and controls the error.

## Using the Axios Library

Axios is a promise-based HTTP client that connects to an endpoint. In this section, we will use it to fetch post data from an endpoint. Unlike the fetch() method, the response returned from this library contains the JSON format we need.

It also has the advantage of robust error handling, so we don’t need to check and throw an error like we did earlier with the fetch() method.

To use Axios, we must install it:

```

npm install axios

```

Once we import it in our app, like so:

```

import axios from "axios"

```

We can then use it to perform a GET request

```

const response = await axios.get(
  `https://jsonplaceholder.typicode.com/posts?_limit=10`
);

```

```

console.log(response);

```

The library returns an object containing the data we need.

We can access the data from the data property with response.data. In the end, our code looks like this:

```

useEffect(() => {
  const getData = async () => {
    try {
      const response = await axios.get(
        `https://jsonplaceholder.typicode.com/posts?_limit=10`
      );
      setData(response.data);
      setError(null);
    } catch (err) {
      setError(err.message);
      setData(null);
    } finally {
      setLoading(false);
    }
  };
  getData();
}, []);

```

See how straightforward it is? With Axios, handling errors is a breeze, leaving us more time to focus on creating amazing apps!

## Conclusion

In this step-by-step guide, we’ve learned how to fetch API data in React using both the Fetch API and Axios library. The Fetch API is built into modern browsers and offers a native way to perform API requests. On the other hand, Axios provides additional features and flexibility, making it a popular choice for many developers.

Remember to handle loading states and errors gracefully in real-world applications. By mastering API fetching in React, you’ll be able to build powerful and interactive web applications that can fetch and display data from various APIs.

I hope you found this guide helpful in understanding how to fetch API data in React. Happy coding!
