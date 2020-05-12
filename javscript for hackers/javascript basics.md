### prerequistics
- you must be familiar with how html and css works and also with basics of programming 
### what is javascript ?
- it is scripting language used at client side to make webpage responsive , it it not same as java ,at the time when developers were deciding it's name java was trending thus they thought to use javascript as name of this language.

- we can use js in html file under "\<script> js code  \</script>"  tag or we can write js in another file and can call js file using this tag and telling the source destination of the file 

- JavaScript can "display" data in different ways:

    -   Writing into an HTML element, using innerHTML.
    -   Writing into the HTML output using document.write().
    -   Writing into an alert box, using window.alert().
    -   Writing into the browser console, using console.log()

### some basics 
- it has .js file extension
- every line is terminated by " ; " .
- we use // and /*   */ for comments
- some console functions
``` javascript
console.log("hello");
console.table({nitish: 'this', marks:34});
console.warn('This is a warning');
// console.clear();
console.timeEnd('Your code Took');
// console.assert(566<189, 'Age >189 is not possible')
// console.error('This is an error')

```

### data types
- js has 5 data types 

    - integer
    - string (+ use to concatenate , \ escape character)
    - booleans
    - null
    - undefined 
    - arrays
    - objects

### variables 
- we use camal case(first character small second capital eg firstVariable) in javascript.
- typeof function is used to check the type of variable
    - typeof vairable

- we declare variables with keyword "var",we can change the variable again using var, we can also use let which is same as var amd const (cannot change variable)
- let is used for local scope variable for a block , var is used for global 
- must use let 
- var age; declared but undefined 
- null ; means nothing
- = operator is use to assign values to variables
- var age= 15;
- var name="nitish saini";

### operators 
- arithmetic operators
    - \+	Addition
    -  	\- Subtraction
    -   \*	Multiplication
    -   **	Exponentiation (ES2016)
    -   /	Division
    -   %	Modulus (Division Remainder)
    -   ++	Increment
    -   --	Decrement

- comparison operators 
    - ==	equal to
    -   ===	equal value and equal type
    -   !=	not equal
    -   !==	not equal value or not equal type
    -   \>	greater than
    -   <	less than
    -   \>=	greater than or equal to
    -   <=	less than or equal to
    -   ?	ternary operator
- boolean logic
    - && and
    - || or
    - ! not
- falsy values
-   - 0 , "" , null , undefined , Nan (not a number) are alwasys false 

### strings
- it is 0 or more characters written inside quotes (any ' ' or " " )
- number in string is considered as number
- in new version of js we can use template literals , with backtik ` 
``` javascript
let name = "nitish";
let fruit1 = "mango";
let fruit2 = "orange";
let myHtml = `Hello ${name}
            <h1> This is "my" heading </h1>
            <p> You like ${fruit1} and ${fruit2}`;
```
- from this examle we can see we dont need to concatenate strings its like fstrings in python

- to get length of string we use .length 
    - eg var n='nitish;
    - var m=n.length ; or alert(n.length)
- string methods 
    - length to find length of the string
    - indexof('word') - find first occurence
    -  indexof('word',5) - starts searching from 5 position.

    - search ('word') - it same as indexof but more powerful , it does not take 2 arguments but can use regex in it 
    - slice(start, end) , it take negative values
    - substring(start, end) - it does not take negative values
    - substr(start, length) - it takes length as second value
    - toLowerCase()	Converts a string to lowercase letters
    - toString()	Returns the value of a String object
    - toUpperCase()	Converts a string to uppercase letters
    - trim()	Removes whitespace from both ends of a string
    - split()	Splits a string into an array of substrings
    - startsWith()	Checks whether a string begins    with specified characters

    - replace('word to replace ' , 'replace with')
    - charAt(3)
``` javascript 

var string = "hello my name is Nitish";
print(string.length);  // output is 23


var txt = "a,b,c,d,e";   // String
var txt1 = txt.split(","); //[a,b,c,d,e]  as array and not string 
txt[0] = a,b,c,d,e
txt1[0]=a

var x = 100 / "10";     // x will be 10

```

### conditions and loops
- if , else if ,else , switch (but we dont use it more often)
- for , while , 
```javascript
if (condition)
{
    code;
}
else if (condition)
{
    code;
}
else
{
    code;
}

while (condition)
{
     code;
}

for (initiator; condition ; step)
{ 
    code ;
}

 for ( var i=0 ; i<6 ; i++)
{
    code;
}

let obj = {
    name: "nitish",
    age: 20,
    type: "Dangerous Programmer",
    os: "Ubuntu"
    }
for(let key in obj){
console.log(`The ${key} of object is ${obj[key]}`)

// only used for arrays , it can take as many arguments as we want to pass 
arr.forEach(function(element, index, array){
    console.log(element, index, array);
``` 

### arrays
- declared using [ ] brackets , can be numbers , strings , anything
    - var num=["1","2","3"];
- indexing starts from 0 

- it uses same methods as strings such as length , etc

### array methods
- tostring() - convert array into string 
    - var arr= [array elemets];
    - arr.tostring()

- push() and pop() - use to add and remove element at the end of the array
    - arr.push("7")
    - arr.pop();
- shift and unshift - use to add and remove element a the begining of the array
    - shift - to remove in beg
    - unshift - to add at begi

- index of 
- slice (start , end); -
same as string
- splice () - it is used to add and remove elements in array 
    - splice(2,0,"lemon","kiwi")
    - where to add , delete any , to add elements

    to remove we set splie(2,1)
- sort() and reverse()
### array iteration 
- we can use for loop as we do in other languages like python and c++  
- on more using forEach() function , it calls another fnunction for iteration
     var clr=['red','blue','green'];
     clr.forEach(function(clr){
         console.log(clr);
     });
    

### functions
- these are set of code in a block which are used to prevent code repition 
- function keyword is used to define function
- it has a return statement to return values
- we can pass parameters in the function
``` javascript
var x = myFunction(4, 3);   // Function is called, return value will end up in x

function myFunction(a, b) {
  return a * b ;             // Function returns the product of a and b
}
```

- scopes in js = there are two scopes in js 
    - local
    - global
- arrow functions = it is short form of functions

``` javascript
hello = function() {
  return "Hello World!";
}

hello = () => {
  return "Hello World!";
}

// for single line functions you can remove the brackets and the return keyword

hello = () => "Hello World!";


// with parameters

hello = (val) => "Hello " + val;


```

### objects
- these are like dictionaries in python
- they rae key value pair 
- declared using { } 

```javacript
var person={} // empty object
var person={
    name:"nitish",
    age=20,
    city="pathankot"
};
// to access vlaue we use object.key
person["name"]; or person.name;
// we can update values also 
person.age +=1 ;
```
- arrays and objects 
``` javascript 
var post = [
    {
        title: "js",
        author : ["nitish","saini"]
    },
    {
        title: "js2",
        author: ["internet","https"]
    }
]

post[1].author[1]  // this will give us saini from first object in post 
```

### object methods 
- it is declaring methods or functions inside objects
- these are used to resolve name space collision , means same function but different operation , eg cat m dog uses speak function , thus we create object instead of cat and dog with function speak instead of different function 
```javascript
var hello = {
    name :"nitish",
    add : function (x,y)
    {
        return x+y;
    }
};

hello.add(5,4);
```
### this keyword
- this keyword  = it has different values depending on where it is being used 

- In a method, this refers to the owner object.
- Alone, this refers to the global object.
- In a function, this refers to the global object.
- In a function, in strict mode, this is undefined.
- In an event, this refers to the element that received the event.

``` javascript 
var person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};

// also used in event listners 

<button onclick="this.style.display='none'">
  Click to Remove Me!
</button>
```
- when this is inside object , value will be closest parent object

 ``` javascript 
 var person= {
     firstName:"nitish",
     lastname:"saini",
     sayHi:function(){
         return "hi" +  this.firstName;
     },
     age:{
         sayHello :function(){
             return "Hello" + this.firstName;
         }

     }
 };

 person.sayhi() // we get hi nitish
 person.sayHello() // we get hello undefined ,as this firstname in age is not defined 

```

- to solve this we use call ,apply and bind 
    - person.sayhi.call(object) 
- it also reduces code repition 

- instead of createing object using variable we create object using function constructor
- we should not add property directly we should use prototype for adding properties
- 
``` javascript
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}

var urFather = new Person("nitish", "saini", 20, "blue");
// adding new property, but we should avoid it 

urFather.nationality = "English";

// we should use prototype


Person.prototype.nationality = "English";


// adding method

myFather.name = function () {
  return this.firstName + " " + this.lastName;
};
 
```
### OOPS

- Use the keyword class to create a class, and always add the constructor() method.
- it is used instead of using prototype and inheritance


``` javascript

class Car {
  constructor(brand) 
  {
    this.carname = brand;
  }

  
// methods in class

present()
 {
    return "I have a " + this.carname;
  }

}
 // create new object for this class 
mycar = new Car("Ford");
```
- inheritance ,To create a class inheritance, use the extends keyword.

- By calling the super() method in the constructor method, we call the parent's constructor method and gets access to the parent's properties and methods.
``` javascript
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}

class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}

mycar = new Model("Ford", "Mustang");

```
### debugging
- we can use chrome dev tools and using console.log to get errros 
- using try and catch keyword , it is also used in input validation

```javascript
try
{
    code;
}
catch (err)
{
    code;
}

```

### promises

``` javascript

// Promise: Best video on promises
// -resolve
// -reject
// -pending

function func1() {
    return new Promise(function (resolve, reject) {
        setTimeout(() => {
            const error = true;
            if (!error) {
                console.log('Function: Your promise has been resolved')
                resolve();
            }
            else {
                console.log('Function: Your promise has not been resolved')
                reject('Sorry not fulfilled');
            }
        }, 2000);
    })
}

func1().then(function(){
    console.log("Harry: Thanks for resolving")
}).catch(function(error){
    console.log("Harry: Very bad bro. Reason: " + error)
})


```


``` javascript

// Pretend that this response is coming from the server
const students = [
    { name: "harry", subject: "JavaScript" },
    { name: "Rohan", subject: "Machine Learning" }
]


function enrollStudent(student) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            students.push(student);
            console.log("Student has been enrolled");
            const error = false;
            if (!error) {
                resolve();
            }
            else {
                reject();
            }
        }, 1000);
    })
}

function getStudents() {
    setTimeout(function () {
        let str = "";
        students.forEach(function (student) {
            str += `<li> ${student.name}</li>`
        });
        document.getElementById('students').innerHTML = str;
        console.log("Students have been fetched");
    }, 5000);
}

let newStudent = { name: "Sunny", subject: "Python" }
enrollStudent(newStudent).then(getStudents).catch(function () {
    console.log("Some error occured");
});
// getStudents();

// function inside then is ran as - resolve()
// function inside catch is ran as - reject()
```