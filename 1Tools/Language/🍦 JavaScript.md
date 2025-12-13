
- Always AI Use করবো Concept বুঝার জন্য 
- যখন কোনো কিছু দরকার / করার জন্য Documentations দেখবো 
### 📘 Step 1 — Core Fundamentals

#### ` Basic Syntax Of Python `

```js
// যেহেতু JavaScript Interpreted Language তাই এটার
// C++ এর মতো কোনো main() নেই

// Print Pyramid Using console.log() Function
console.log('*')
console.log('*'.repeat(2))
console.log('*'.repeat(3))
console.log('*'.repeat(4))
console.log()
console.log('*' * 5) // String Can't Multiply N Times!
// Output: NaN = Not A Number
```

#### `Variables`

```js
// কোনো কিছু Store করার জন্য Variable Use করা হয় !
// লিখার ৩ টা নিয়ম -
// Camel Case: studentInfo
// Pascal Case: StudentInfo
// Snake Case: student_info

let studentDepartment = 'CSE'; // Redeclare করা যায় না, Block Scope আছে, Hoisted হয় কিন্তু Undefined Set করে নি, Reassign করা যাবে  
var StudentBatch = 67; // Redeclare করা যায়, Block Scope নাই, Hoisted হয় & নিচে Undefined Set করে, Reassign করা যাবে 
var StudentBatch = 'Batch 67' 
const student_id = 202331067042; // Must Initialize করতে হবে, Reassign করা যাবে না, Block Scope আছে, Hoisting let এর মতো 

// JavaScript এ তিনটা Scope আছে 
// 1. Global  = সব জায়গা থেকে Access করা যাবে 
// 2. Function = function { }
// 3. Block  = Only { এই Block এর মধ্যে Access করা যাবে } 

let X = 10 // Global

if(true){
    let X = 'Shourav'; // এটা String X 
    console.log(X)
}

if(true){
    let X = 67;       // এটা Number X
    console.log(X)
}


if(true){
    let X = true;    // এটা Boolean X
    console.log(X)
}

console.log(X)

// Var Hoisting 
// var A;          Step 1
// A = undefined;  Step 2

A = 'Shourav';  // Step 3
let A;
console.log(A);


// Let Hoisting 
// let B;          Step 1

// B = 'Shourav';  // Step 2
// let B;
// console.log(B);  // B = undefined;  Step 2 করে নি তাই Error!!

// Always let, const Use করবো !!!
```

#### `Data Types`

```js
// Data Types হচ্ছে যেগুলো আমরা Variable এ Store করি,
// এবং এটি নির্ধারণ করে যে Variable টি কোন ধরনের ডেটা আছে

// JavaScript এ দুটি ধরনের Data Types আছে:
// 1. Primitive Data Types
// 2. Non-Primitive (Reference) Data Types

// Basic Primitive Data Types:
// 1. Number     -> integer + float সবই Number
// 2. String     -> Text 
// 3. Boolean    -> true / false
// 4. Undefined  -> Value দেওয়া হয়নি
// 5. Null       -> Intentionally empty value
// 6. BigInt     -> বড় integer এর জন্য
// 7. Symbol     -> Unique identifier যা পরে দেখবো !!

// Non-Primitive (Reference) Data Types যা পরে দেখবো !! 
// 1. Object
// 2. Array
// 3. Function


// 1. Primitive Data Types

// 1. Number     -> integer + float সবই Number

let IntNum = -5;
let FloatNum = 2.5;
console.log('Int: ', typeof IntNum, '\nFloat: ', typeof FloatNum);


// 2. String এমন এক ধরনের ডেটা যা যেকোনো কিছু সংরক্ষণ করতে পারে,
// কীবোর্ডে থাকা যেকোনো অক্ষর, সংখ্যা, চিহ্ন ইত্যাদি সব, ' ' অথবা " "

let FullName = 'Mahtabul Shourav';
console.log('Name: ', typeof FullName);


// 3. Boolean (True/1 অথবা False/0)

let ManIsMortal = true;
console.log('Man Is Mortal: ', typeof ManIsMortal);


// 4. Undefined -> Value দেওয়া হয়নি

let GetValue; // value দেওয়া হয়নি → undefined

console.log('Undefined: ', typeof GetValue);

GetValue = 'FirstName';   // এখন value দেওয়া হয়েছে

console.log('Value: ', typeof GetValue);


// 5. Null -> Intentionally empty value

let Data = null;   // ইচ্ছাকৃতভাবে খালি মান সেট করা হয়েছে

console.log('Null: ', typeof Data);

// পরে মান যোগ করলে টাইপ পরিবর্তন হবে
Data = 'LastName';

console.log('Value: ', typeof Data);

// null কে  প্রাথমিক মেমোরি ডিজাইনে ভুলবশত object হিসেবে ট্যাগ করা হয়েছিল,
// যা একটি ঐতিহাসিক bug এবং backward compatibility-এর কারণে এখনও ঠিক করা হয়নি।


// 6. BigInt     -> বড় integer এর জন্য

let BigInt = 123456789123456789123456789n; // n Suffix দিয়ে BigInt
console.log('BigInt: ', typeof BigInt);
```

#### `Strings and String Methods`