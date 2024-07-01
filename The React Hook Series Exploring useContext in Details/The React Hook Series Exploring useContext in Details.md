# The React Hook Series: Exploring useContext in Details

![image](./assets/useContext.png)

## What is useContext?

The useContext Hook works with React's Context API. Let's take a look how it works.

It accepts a context object created using React.createContext and returns the current context like so:

```

const value = useContext(SomeContext);

```

## Why do I use Context?

For props such as the user's preferred language, theme or authenticated user's properties, it is tedious to have to pass them manually from one component to another. Instead, using React's Context API and the useContext Hook makes it easy to pass props across all components of the app.

## An example

Let’s look at an example on how this Hook works.

### Step 1: Create Context

First, create a context to use our Hook. For example, we make a UserContext to get the value of the current user:

```

// some mock context values
const users = {
  user1: {
    name: "Sherlock Holmes",
    occupation: "Detective"
  },
  user2: {
    name: "James Moriarty",
    occupation: "Professor"
  }
};

// create context
export const UserContext = React.createContext(users.user1);

```

As seen from the code above, we create a context object using React.createContext() and pass in a default value as users.user1.

### Step 2: Context Provider

Every context has a Provider, which allows its children components to subscribe to changes in the context. It passes the value of the context and its consuming (children) components will re-render when value changes.

```

function App() {
  return (
    <UserContext.Provider value={users.user1}>
      <UserProfile/>
    </UserContext.Provider>
  );
}

```

In the example above, the UserProfile is the context consuming component will be subscribed to changes in value.

### Step 3: Get current context

Finally, we get to see the useContext Hook in action. Let's say the UserProfile component displays the name and occupation of the current user in the context.

In the UserProfile component, import the Hook and context:

```

import React, { useContext } from 'react';
import { UserContext } from "./App";

```

Then, get the current user value using the Hook to display the current user’s properties:

```

function UserProfile() {
  const user = useContext(UserContext);
  return (
    <div>
      <p>`I am ${user.name} and my occupation is a ${user.occupation}!`</p>
    </div>
  );
}

```

And that’s a simple way to use this Hook!

## Important Things to Note

There are some details that we should talk about when using the useContext Hook:

### 1. The Single Argument

Note that the Hook only accepts a single argument, and it must be a context object, not the Provider or any other component.

```

useContext(MyContext.Consumer) //wrong

useContext(MyContext.Provider) //wrong

useContext(MyContext) //correct

```

### 2. Getting Current Context

Another important thing to note as mentioned in React Docs:

The current context value is determined by the value prop of the nearest MyContext.Provider above the calling component in the tree.

Hence, this means that the nearest MyContext.Provider determines the value returned by the Hook. If the value prop of the MyContext.Provider is updated, the Hook will be triggered and the component calling the Hook is re-rendered with the new context value.

## Conclusion

And that’s the gist of this Hook! Thanks for reading this article. I hope it was helpful for React beginners. Please feel free to ask questions in the comments below. Ultimately, practicing and building projects with this Hook will help anyone to pick it up faster.
