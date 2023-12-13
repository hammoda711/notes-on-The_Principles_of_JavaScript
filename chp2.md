###### notes from  **" *OBJECT-ORIENTED THE PRINCIPLES OF***

###### *JAVASCRIPT*"   by NICHOLAS C. ZAKAS

### chapter 2: functions

## intro:

-functions are actually **objects** in JavaScript.

-it has a advantage: the presence of an **internal property named [[Call]]**.

> note: Inter­nal properties are **not accessible via code**, but rather **define the behavior of code** as it executes.

-The **[[Call]]** property is **unique** to functions and indicates that the object can be executed.

------------------------------

## Declarations vs. Expressions:

**declaration**:

```js
function add(num1, num2) { 
    return num1 + num2;            //function name, no variable, no semicolon 
}
```



**expression**:

```js
var add = function(num1, num2) {
    return num1 + num2;             //using variable, no function name, using semicolon 
};
```



-there is an important difference other than the syntax, its **hoisting** 

-hoisting happens **only** for function **declarations**, so you can actually **define a function after it is used in code without generating an error**.

> -hoisting is  is JavaScript's default behavior of moving declarations to the **top** (internally).
>
> ```js
> var result = add(5, 5);
> function add(num1, num2) { 
>     return num1 + num2;                 //no error 
> }
> ```
>
> -what the js engine executes:
>
> ```js
> function add(num1, num2) {              //declaration became on the top 
>     return num1 + num2;
> }
> var result = add(5, 5);
> ```
>
> 

---------------------

## functions as values:

-you can use them just as you do any other objects. You can assign them to variables, add them to objects, pass them to other functions as arguments, and return them from functions. 

-

------

## parameters:

-Another **unique** aspect of JavaScript functions is that **you can pass any number of parameters** to any function **without** causing an error, because function parameters are actually **stored as an array-like structure** called **arguments**.

> note: The **arguments** object is **not** an instance of Array, it just looks like it in the structure.

-parameters in a function **don’t** actually **limit** the number of arguments.

```js
reflect = function() {
    return arguments[0];             //the important is the named parameter not the arguments
};
console.log(reflect("Hi!"));           // "Hi!" 
console.log(reflect("Hi!", 25));        // "Hi!"
console.log(reflect.length);             // 0

```

-some times, using arguments is actually more effective than naming parameters.

```js
function sum() {
var result = 0, 
    i = 0, 
    
    len = arguments.length;
while (i < len) {
    result += arguments[i]; i++;
} 
    return result;
} 
console.log(sum(1, 2));        // 3
console.log(sum(3, 4, 5, 6));  // 18
console.log(sum());            // 0
```

---------

## function overloading:

-the types of parameters a function takes aren’t specified at all, That means JavaScript functions **don’t** actually have signatures. 

-A lack of function signatures also means a **lack of function overloading.**

```js
function sayMessage(message) { 
    console.log(message);
}

function sayMessage() {
    console.log("Default message");  
} 

sayMessage("Hello!");             // outputs "Default message"
                                  // ignore the first function, 
                                  //ignore the argument("hello!") that passed to the function
                                  //because the function doesnot take any parameter.
```

The fact that functions don’t have signatures in JavaScript doesn’t mean you can’t **mimic** function overloading

```js
function sayMessage(message) {
    if (arguments.length === 0) { 
        message = "Default message";
    } 
    console.log(message);
} 
sayMessage("Hello!");         // outputs "Hello!"



///////////////////////////يحتاج الي توضيح   
```

--------------

## object method:

-When a property value is actually a function, the property is considered a method

```js
var person = { 
    name: "Nicholas", 
    sayName: function() {
console.log(person.name); 
    } 
};
person.sayName();   // outputs "Nicholas"
```

-the same example using **this** object

-Every scope in JavaScript has a this object that represents **the calling object** for the function

```js
var person = { 
    name: "Nicholas", 
    sayName: function() {
console.log(this.name); 
    } 
};
person.sayName();   // outputs "Nicholas"
```

----------------------

## to manipulate "this" :

-there are three function methods:

> - call(), apply(), the same work 
> - bind()  ------------??????

--------------------------------------

