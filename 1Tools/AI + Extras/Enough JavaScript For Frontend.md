# `Foundation`

### `1. Variables: let vs. const`

| **Feature**       | **var (Old)**       | **let (Modern)**                          | **const (Modern)**                                                             |
| ----------------- | ------------------- | ----------------------------------------- | ------------------------------------------------------------------------------ |
| **Scope**         | Function-scoped.    | **Block-scoped** (`{ }`).                 | **Block-scoped** (`{ }`).                                                      |
| **Re-assignment** | Re-assigned করা যায় | Re-assigned করা যায়                       | Re-assigned করা যায় না                                                         |
| **Declaration**   | Re-declared করা যায় | Re-declared করা যায় না                    | Re-declared করা যায় না                                                         |
| **Best Practice** | Use করবো না !       | Use করবো যখন Variable এর Value Change হবে | **Default** এটা Use হয় কিন্তু তখন Use করবো যখন Variable এর Value Change হবে না |
```js
// একটা Block Scope Create করা হইসে !

if (true) {
  let blockVariable = 'I can change';
  const blockConstant = 123;
  
  blockVariable = 'I have changed'; // OK
  // blockConstant = 456; // ERROR: Assignment to constant variable.
}

// console.log(blockVariable); 
// ERROR: blockVariable is not defined outside the block.
```

### `2. Truthy / Falsy & Short-Circuiting`

```js
const getName = function(){
    return 'Mahtabul Shourav';
}

let a = false;
let b = true;

// Logical AND

console.log(a && b); // প্রথমে false পেলেই return false!

// Logical OR

console.log(a && b); // প্রথমে true পেলেই return true!


// Guess What Return ?

console.log(a && getName()); // a = false -> false!

console.log(b && getName()); // b = true -> 'Mahtabul Shourav'!

console.log(a || getName()); // a = false -> 'Mahtabul Shourav'!

console.log(b || getName()); // b = true -> true!
```


### `3. Template Literals`

```js
let name = 'Mahtabul Shourav';
let age = 21;

// Template Literals 

let stringLiterals = `Hi, ${name}, I guess you are ${age} years old!`;

console.log(stringLiterals);
```


### `4. Understanding Objects`

**Object** হলো key-value জোড়া ধরে রাখার একটি ডেটা স্ট্রাকচার। 
একটি object-এর property (key) এবং value থাকতে পারে, value আবার function হতে পারে! 
তখন তাকে method বলা হয়। 

```js
// Object Literal

const pythonUser = {
    name: 'Mahtabul Shourav',
    age: 23,
    location: 'Dhaka',
    isMale: true,
    lastLogin: ['Friday', 'Saturday'],
    sayHi: function(){
        console.log('Everything is pythonic!');    
    },
    'Pythonic' : 'Yes'
};

// Dot দিয়ে Access করা 

console.log(pythonUser.name);
console.log(pythonUser.lastLogin);
pythonUser.sayHi();


// Index (Works Always) দিয়ে Access করা 

pythonUser['sayHi']();
console.log(pythonUser['Pythonic']);


// Values Change করা 

pythonUser['Pythonic'] = 'We love python!';
console.log(pythonUser['Pythonic']);


// Key-Value Add করা 

pythonUser.goodbye = function(){
    return 'Goodbye! Lets Dive Into JavaScript!';
}

const goodbye = pythonUser.goodbye();
console.log(goodbye);


// this দিয়ে Object এর Property Access করা হয় 

pythonUser.thisUse = function(){
    console.log(`I Can Access Name Which Is - ${this.name}`);
}

pythonUser.thisUse();
```


### `5. Shorthand Property Names`

| Comparison      | `==` | `===` |
| --------------- | ---- | ----- |
| Type conversion | Yes  | No    |
| Compares value  | Yes  | Yes   |
| Compares type   | No   | Yes   |
| Recommended     | No   | Yes   |

```js
const id = 1;
const title = 'Malware';
const rating = 5;

// Normally 

const product1 = {
    id : id,
    title : title,
    rating : rating,
}


// Shorthand Property 

const product2 = {
    id,
    title,
    rating,
}
 
console.log(product1 == product2); // Why false ? 
console.log(product1 === product2); // Why false ?

// Objects Compare করা হয় Reference দিয়ে, Value দিয়ে না ! 
// কারন তারা আলাদা ভাবে Memory Allocate করতিসে...
```


### `6. Destructuring (Array & Object)`

Destructuring Use করে **Arrays or Objects Properties** Extract করতে পারবো আলাদা  Variables এর মধ্যে !

| **Type**   | **Before Destructuring**                                                          | **With Destructuring**            |
| ---------- | --------------------------------------------------------------------------------- | --------------------------------- |
| **Object** | `const name = user.name;`                             `const age = user.age;`     | `const { name, age } = user;`     |
| **Array**  | `const first = colors[0];`                            `const second = colors[1];` | `const [first, second] = colors;` |

```js
const post = {
  id: 1,
  title: 'ES6 Mastery',
  author: 'Gemini',
  tags: ['js', 'ts'],
};

// Extracting 'title' and 'author'

const { title, author } = post;

// console.log(title);   // ES6 Mastery
// console.log(author);  // Gemini

// চাইলে Variables Rename করতে পারবো oldName:newName !! 

const { title: postTitle, id: postId } = post;
// console.log(postTitle); // ES6 Mastery
```

### `7. Spread & Rest Operators`

```js
const arrOne = [1,2,3];

const arrTwo = [4,5,6];


// Spread Operator

console.log(...arrOne); // Value কে Spread করে !

console.log([...arrOne]); // Value কে Spread করে But Array আকারে !


// দুইটা Array কে Spread করে Merge করার জন্য  

console.log([...arrOne, 10, ...arrTwo]); // Extra 10 Add
```

```js
const someThings = function(a,b,c){
    console.log(a,b,c); // 1 2 3
    return 'Without Rest!';
}

console.log(someThings(1,2,3,4,5))


// Spread Operator

const someThing = function(a,b,...c){ // Array Form এ বাকিগুল নিবে !
    console.log(a,b,c); // 1 2 [3,4,5]
    return 'With Rest!';
}

console.log(someThing(1,2,3,4,5))
```


### `8. Arrow Functions (=>)`

Functions লিখার Concise Way.
Key Differences
1. **Shorter Syntax:** `function` keyword এর দরকার নেই .
2. **Implicit Return:** যদি function একটা single expression হয়, তাহলে  `return` keyword আর curly braces (`{}`) বাদ দিতে পারবো.
3. **No `this` Binding (Crucial for React/Node):** Arrow functions do not have their own `this` value, they inherit `this` from the enclosing scope.

| **Function Type**   | **Traditional Syntax**                 | **Arrow Function Syntax**                  |
| ------------------- | -------------------------------------- | ------------------------------------------ |
| **Full Block**      | `function add(a, b) { return a + b; }` | `const add = (a, b) => { return a + b; };` |
| **Implicit Return** | (N/A)                                  | `const multiply = (a, b) => a * b;`        |

```js
const user = {
    username : 'Mahtabul Shourav',
    price: 99,
    welcomeMessage: function(){
	    // Current Context নিয়ে ! 
        console.log(`${this.username}, Welcome to our website!`); 
        

        // Context দেখার জন্য !
        console.log(this)
    }
}



user.welcomeMessage();

// Changing Context!

user.username = 'Ayman Mustakim';
user.welcomeMessage();

// What About Global Context ?

console.log(this); // Empty Object!
```

```js
// Normal Function

const cappuccino = function (){
    let username = 'Mahtabul Shourav';
    console.log(this.username); // Function এর মধ্যে this Use করা যায় না !
}

cappuccino(); // Error Undefined 
```

```js
// Arrow Function

/*
    const functionName = (Parm1, Parm2, ..) => {
        return expresion;    
    }

*/

// Curly Brace দিলে return দিতে হবে !

const addTwo = (num1, num2) =>{
    return num1 + num2;
}

console.log(addTwo(2,3));


// Implicit Return (Parenthesis দিলে return দরকার নেই)
 
const addThree = (num1, num2, num3) =>  (num1 + num2 + num3);

console.log(addThree(2,3,4));


// Returning Objects ({Objects})

const userName = () => ({username: 'Mahtabul Shourav'});

console.log(userName())
```

### `9. Map For Rendering`

```js
// Map 

const personArr = [
    {
        name: 'Person One',
        age: 21,
        city: 'Dhaka'
    },
    {
        name: 'Person Two',
        age: 22,
        city: 'Khulna'
    },
    {
        name: 'Person Three',
        age: 23,
        city: 'Barisal'
    }
]

// Array থেকে সব Name নিয়ে আরেকটা Array বানাবো !

/*
    const newArr = mainArr.map( (value, index) => {
        
        return value.indexName;
    
    });
*/


let nameArr = personArr.map((person,index) => {
    return person.name;
});

console.log(nameArr);


// সব ক্ষেত্রেই Same !

let ageArr = personArr.map((person,index) => {
    return person.age;
});

console.log(ageArr);


// যেকোনো দুইটা একসাথে !

let getArr = personArr.map((person,index) => {
    return `Name: ${person.name}, City: ${person.city}`; 
    // Using Template Literals
});

console.log(getArr);
```


Reference vs Value
Optional Chaining & Nullish Coalescing
Array immutability
Closures (basic understanding)
Promises deeper understanding


