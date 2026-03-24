### What is Local Storage in Your Browsers ? 


![alt](https://www.datocms-assets.com/22695/1751323409-1726578015-local-storage.webp)

Local Storage is a feature of web browsers that allows websites to store data on a user's device. The stored data remains saved even if the page is refreshed or the browser is closed, until it is manually deleted.

### Why it is used ? 

Stores data in the browser so websites can save information on the user’s device.

Data stays after page refresh and even after closing the browser.

Used to save user preferences like theme, language, or settings.

Reduces server requests because data can be read directly from the browser.

Helps websites load faster by using locally stored data. 


### How to use ?

**1. Store data (Save data)**

`localStorage.setItem("key", "value");`

**2. Get data (Read data)**

`let data = localStorage.getItem("key");`

**3. Remove specific data**

`localStorage.removeItem("key");`

**4. Clear all local storage data**

`localStorage.clear();`


**Example:**

```
// Save username
localStorage.setItem("username", "Mohit");

// Get username
let name = localStorage.getItem("username");
console.log(name);

```

### Some important things

Data in Local Storage is stored as a string in key–value format. Therefore, when storing objects or arrays, we convert them into a string using JSON.stringify(). When retrieving the data, we convert it back to its original format using JSON.parse().

**Working :**

```
// Object
const user = { name: "Mohit", age: 20 };

// Store in local storage
localStorage.setItem("user", JSON.stringify(user));

// Get from local storage
const storedUser = JSON.parse(localStorage.getItem("user"));

console.log(storedUser.name);
```