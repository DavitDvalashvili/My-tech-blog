# Local Storage in JavaScript

![image](./assets/localStorage.png)

## What is Local Storage

Local storage is a type of web storage that retains data for extended periods — ranging from a day to even a year — depending on the developer’s preference. It’s crucial to note that local storage can only store strings. To store objects, lists, or arrays, you must first convert them into strings using JSON.stringify(). Local storage enables developers to store and retrieve data in the user's browser, and the stored data persists even if the browser window or tab is closed.

## When to Use Local Storage

While you can use localStorage for storing small amounts of data, it’s unsuitable for handling large volumes of information. Keep in mind that localStorage is accessible to anyone using the device, so avoid storing sensitive information with it. Instead, it’s excellent for storing user preferences, such as language or theme choices, and for caching frequently used data. localStorage can also store form data, ensuring it remains available even if the user closes the browser. However, as mentioned earlier, refrain from using localStorage for sensitive data, as other scripts running on the same page can access it.

### Advantages

- It can store up to 5–10MB of data, depending on the browser.
- It’s user-friendly, requiring no web server or backend database.
- It’s ideal for quickly prototyping and testing purposes.

### Limitations

- It’s limited to storing up to 10MB of data (5MB in some browsers).
- It can only store strings, which may limit its use in more complex scenarios. However, HTML can be stored as a string (more on that later).
- It’s local to the browser and specific to the origin (per domain and protocol), with no guarantee that the data will persist even within the same context.
- It’s not secure for storing private or personal information.

## Difference Between Session Storage and Local Storage

localStorage is one of two mechanisms within the Web Storage API, the other being sessionStorage. Both maintain separate storage areas for each available origin during a page session. The primary distinction is that sessionStorage retains data only while the browser is open, including during page reloads or restores. In contrast, localStorage continues to store data even after the browser is closed. Note that localStorage data loaded in an incognito browsing session is cleared when the last private tab is closed.

## How Does Local Storage Works

localStorage offers essential methods for data management:

- setItem(): Adds a key and value to localStorage.
- getItem(): Retrieves items from localStorage.
- removeItem(): Deletes an item from localStorage.
- clear(): Removes all data from localStorage.
- key(): Retrieves the key of a localStorage item based on its index.

## Storing Data in localStorage

You can store data in Local Storage using the setItem() method, which accepts a key and its corresponding value:

```
window.localStorage.setItem('Language', 'JavaScript');

```

To store an array or object, convert it to a string using JSON.stringify():

```
const userObject = {
    firstName: "Davit",
    lastName: "Dvalashvili",
    age: "26"
}

window.localStorage.setItem('user', JSON.stringify(userObject));

```

## Reading Data From Local Storage

Retrieve data from localStorage using the getItem() method by providing the key:

```

let User = window.localStorage.getItem('Language');
let language = window.localStorage.getItem('user');

console.log(User);
console.log(language);

```

If you need to convert the result from a string back to an object, use JSON.parse():

```
let language = JSON.parse(window.localStorage.getItem('Language'));
console.log(language);

```

## Deleting Local Storage Sessions

You can delete localStorage sessions using the removeItem() method. Provide the key as a parameter to delete the corresponding key-value pair:

```

window.localStorage.removeItem('Language');

```

To delete all items in localStorage, use the clear() method, which clears the entire storage for that domain without needing any parameters:

```

localStorage.clear();

```

## Getting the Name of a Key

The key() method is useful when you need to loop through keys while retaining the ability to pass an index to localStorage to retrieve a key's name:

```

localStorage.key(index);

```

## Finding the Length of localStorage

To determine the length of localStorage, use the localStorage.length property:

```

let len = localStorage.length;
console.log(len);

```

### Storage Event

You can listen for storage changes in both localStorage and sessionStorage using the storage event. This event is triggered when an item is created, deleted, or updated. The listener function receives an event object with properties such as newValue, oldValue, key, url, and storageArea. You can set storage event listeners using window.addEventListener("storage", func) or by using the onstorage attribute:

```

window.onstorage = (event) => {
  if (event.key === "title"){
    alert(`Your new title is ${event.newValue} the previous was ${event.oldValue}`);
  }
  alert('SAVED!!');
}

localStorage.setItem("title", "kelly");

```

Note that the function won’t be triggered in the same tab where the change occurred but will be triggered by other tabs or windows of the same domain. This feature facilitates data synchronization across all tabs/windows of the same domain.

## Conclusion

Local storage is a valuable tool for web developers, allowing for data persistence within the user’s browser. However, it should be used judiciously, considering its limitations and security implications. By understanding how Local Storage works and its differences from Session Storage, you can create more efficient and user-friendly web applications.
