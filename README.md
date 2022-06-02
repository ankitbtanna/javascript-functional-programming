# JavaScript Functional Programming
## I encourage you to use functional programming because it saves a lot of hassle and it is quite clean!
opinionated guideline to functional programming

![N|Solid](https://res.cloudinary.com/carloscuesta/image/upload/v1616513220/blog-featured-images/Functional_programming_in_JavaScript.png)

### This is an opinionated guideline. Feel free to add something you feel is important

### Outline
- What is functional programming?
- Why functional programming?
- Functional vs Object Oriented

#### What is functional programming?
- It is a programming paradigm where functions are the most important thing. Its a coding style. Its the way you organize your code. Its a mindset
- Some of the other programming paradigms are like - Imperative programming -- Do this and then do that! Other is Object oriented programming where you see how one object is built by extending from other objects and also understand about the context (the `this` keyword)

#### Why functional programming?
- I found object oriented super confusing
- OO was tricky, tracking the context, the `this` keyword binding
- Functional programming is exact opposite. Its easier to debug, its easier to maintain.
- Large community

## How do we implement functional programming? 
### 1. Do every thing using functions
Inputs ---> Outputs
Understand the flow of the data
Try to express everything into a function

```javscript
// Non functional
var name = "Ankit";
var greeting = "Hello, I'm ";
console.log(greeting + + name);
```

```javscript
// functional
var name = "Ankit";

function greet(name) {
    return "Hello, I'm " + name;
}

greet("Ankit"); // Hello, I'm Ankit
```

### 2. Avoid side effects, Always try to use "pure" functions
Don't try to manipulate the variables which are not in scope of the function.
Don't try to use outside variables which are not in scope of the function for computations inside the function.
A pure function solely relies upon the input it is given and the output is solely dependent on input it recieves. 

Side Effect? - printing to console, reading a global variable, manipulating a variable outside the scope of the function. Don't involve or get involved in anything that is outside the function.

Advantage:
- Result is consistent
- Unit testing is smooth as butter

```javascript
// Not Pure function
var name = "Ankit";
function greet() {
    console.log(name);
}
```

```javascript
// Pure function
function greet(name) {
     return "Hi, I'm " + name; 
}
```

Think about things as purely as possible

### 3. Use higher-order functions
- A function that can take a function as a paramenter (like a callback function)
- A function that can return a function

```javascript
// Higher order function
function adjectifyString(adjective) {
    return function (string) {
        return adjective + " " + string;
    }
}

var coolify = adjectifyString("cool");
coolify("examples!") // cool examples
```
We need this higher order functions inorder to avoid trickeries for object oriented code.

### 4. Avoid Looping. Don't Iterate
- Instead of using for loop, while loop
- Use map, reduce, filter, forEach
- Use these for transforming the data
![N|Solid](https://clojurebridgelondon.github.io/workshop/images/map-reduce-sandwich.png)

### 5. Avoid Mutability
- Avoid mutability
- Avoid changing objects in place
- Always work with immutable objects/arrays

```javascript
// Mutation is bad
var names = ["Ankit", "Amit", "Krunal"];
names[2] = "Anuj";
rooms; // ["Ankit", "Ankit", "Anuj"]
```

```javascript
// Immutability is good
var names = ["Ankit", "Amit", "Krunal"];
var newRooms = names.map((name) => {
    if (name === "Krunal") return "Anuj";
    return name;
}); // creates a brand new array
rooms; // ["Ankit", "Ankit", "krunal"]
newRooms; // ["Ankit", "Ankit", "Anuj"]
```

### 6. Persistent data structures for efficient immutability
- Use libs like Mori, immutable.js
- Problem with immutability is we go ahead and create a lot of copies
- For smaller arrays its fine, for larger arrays its not memory efficient.
