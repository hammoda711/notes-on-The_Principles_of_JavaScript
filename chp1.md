###### notes from  **" *OBJECT-ORIENTED THE PRINCIPLES OF***

###### *JAVASCRIPT*"   by NICHOLAS C. ZAKAS

### chapter 1 : Primitive and Reference   Types

## **OOP concepts in JS:**

- ***Encapsulation***: Data can be grouped together with functionality that operates on that data. This, quite simply, is the **definition of an object.**
- ***Aggregation***: One object can reference another object. 
- ***Inheritance***: A newly created object has the same characteristics as another object without explicitly duplicating its functionality. 
- ***Polymorphism***: One interface may be implemented by multiple objects.

-JavaScript has all these characteristics, though because the language
has **no concept of classes**,

-**Leave behind** the notions of classes and class-based inheritance and learn about prototype-based inheritance and constructor functions that behave similarly.

-Java­Script makes **objects** **the central part** of the ­language.

-----------

## primitive and reference:

- **Primitive types** are stored as simple data types,**Primitive values** are stored **directly** on the variable object
- **Reference types** are stored as objects, which are really just references to locations in memory, **Reference values** are placed **as a pointer** in the variable object, which serves as a reference to a location in memory where the object is stored.

------------

## primitive datatypes:

```javascript
var color1 = "red"; 
var color2 = color1;
console.log(color1);         // "red"
console.log(color2);         // "red"

color1 = "blue"; 
console.log(color1);         // "blue" 
console.log(color2);         // "red"
```

-In this code, color1 is changed to "blue" and color2 retains its original value of "red".
-That’s because there are two different storage locations, one for each variable.
-Because each variable containing a primitive value uses its own storage space, **changes to one variable are not       reflected on the other.**

ex:

```js
console.log("5" == 5);              // true
console.log("5" === 5);             // false

console.log(undefined == null);     // true 
console.log(undefined === null);    // false

=>equal in values 
=>not equal(different) in data type
=>except in object both == and === return false 
   because it compares the two refrences not the value or the datatype 
```

-When you use the double equals, the string "5" and the number 5
are considered equal because the double equals converts the string into a number before it makes the comparison.

-The triple equals operator doesn’t consider these values equal because they are two different types.

## primitive methods:

-primitive data types(except =>null, undefined) have **numerous methods** to help you work with them

-Despite the fact that they have methods, **primitive values themselves are not objects**. 

-JavaScript makes them look like objects **to provide a consistent experience** in the language, as you’ll see later in this chapter.

```js
var name = "Nicholas"; 
var lowercaseName = name.toLowerCase();     //convert into lowercase 
//إضافه بعد قراءة الشابتر
//primitive wrapper types
```

--------

## reference types:

- **An object:**

> -is an unordered list of properties consisting of a name (always a string) and a value.
> 
> -you **must** create objects **before** you can begin work­ing with them.

- **Creating Objects:** 

> -There are a couple of ways to ­create, or instantiate, objects. 
> 
> -The first is to use the "new" operator with a **constructor**. 
> 
> ```js
> var object = new Object();     //the name of constructor is begin by capital letter
>                                //the constructor "Object" begins by a capital letter by                                        convintional 
> ```
> 
> -When you assign an object to a variable, you’re actually assigning a
> pointer. That means if you assign one variable to another, each variable **gets a copy of the pointer**, and both still reference the same object in memory.
> 
> ```js
> var object1 = new Object(); 
> var object2 = object1;        // two variables of the same object 
> ```

- **Dereferencing Objects**: 

> -JavaScript is a **garbage-collected language**
> 
> -it’s best to **dereference** objects that you no longer need so that the garbage collector can free up that memory.
> 
> -The best way to do this is **to set the object variable to null.**
> 
> ```js
> var object1 = new Object(); 
> // do something
> object1 = null;          // dereference
> ```

- **Adding or Removing Properties:**

> -there is a unique aspect of JavaScript: You can modify(adding or remove property) objects whenever you want, even if you didn’t define them in the first place.
> 
> ```js
> var object1 = new Object(); 
> var object2 = object1;
> object1.myCustomProperty = "Awesome!";
> console.log(object2.myCustomProperty);       // "Awesome!" 
> //because both object1 and object2 point to the same object.
> ```

- **Instantiating Built-in Types:**

> -**built-in types** are more specialized in their intended usage and can be instantiated at any time.
> 
> ```js
> var items = new Array();
> var now = new Date();
> var error = new Error("Something bad happened.");
> var func = new Function("console.log('Hi');");
> var object = new Object();
> var re = new RegExp("\\d+");
> ```

---------------------

## **Literal Forms:**

-A **literal** is syntax that allows you to define a reference value **without** explicitly creating an object, using the new operator and the object’s constructor.

-Using an object literal **doesn’t actually call new Object().** Instead, the JavaScript engine follows the same steps it does when using new Object() without actually calling the constructor. This is true for all reference literals.

1. **Object and Array Literals**
   
   > -object literals:
   > 
   > ```js
   > var book = {
   >     name: "The Principles of Object-Oriented JavaScript",    
   >     year: 2014
   > };
   >                //property: value
   > ```
   > 
   > -You can also use string literals as property names, which is useful when you want a property name to have spaces or other special characters:
   > 
   > ```js
   > var book = { 
   > "name": "The Principles of Object-Oriented JavaScript", 
   > "year": 2014          
   > };
   >                 //property between double quote " "
   > ```
   > 
   > -the equivalent to the previous one:
   > 
   > ```js
   > var book = new Object(); 
   > book.name = "The Principles of Object-Oriented JavaScript"; 
   > book.year = 2014;
   > ```
   > 
   > for array:
   > 
   > ```js
   > var colors = [ "red", "blue", "green" ]; 
   > console.log(colors[0]);     // "red" 
   > ```
   > 
   > This code is equivalent to the following:
   > 
   > ```js
   > var colors = new Array("red", "blue", "green");
   >  console.log(colors[0]);       // "red"
   > ```

2. function literals
   
   > -Creating functions is much **easier and less error** prone when you use the literal form.
   > 
   > ```js
   > function reflect(value) { return value;
   > }
   > ```
   > 
   > This code is equivalent to the following:
   > 
   > ```js
   > var reflect = new Function("value", "return value;");
   > ```

3. regular expression literals
   
   > ```js
   > var numbers = /\d+/g;          // we use /.../
   > ```
   > 
   > This code is equivalent to the following:
   > 
   > ```js
   > var numbers = new RegExp("\\d+", "g");
   > ```

----------------------

## Property Access:

-**Dot notation** is the most common way to access properties in JavaScript.

```js
var array = [];
array.push(12345);
```

-you can also access properties on JavaScript objects by using **bracket ­notation** with a string

```js
var array = []; 
array["push"](12345);  
```

-**bracket notation** allows you to use **special characters in property names**. 

-Developers tend to find dot notation easier to read, so you’ll see it used more frequently than bracket notation.

------------------

## identifying reference type:

-function is easiest reference type to identify, when you use the "**typeof**" operator on a function, the operator should return "**function**"  

```js
function reflect(value) { return value;
} 
console.log(typeof reflect);        // "function"
```

-other reference types are tricky when using "**typeof**" operator, so we use "**instanceof**" operator.

-The instanceof operator takes an **object** and a **constructor** as parameters, output is true or false.

```js
var items = []; 
var object = {};
function reflect(value) { return value;
}
console.log(items instanceof Array);      // true 
                                          //note: "items" is a variable , "Array" is the constructor  
console.log(object instanceof Object);    // true
console.log(reflect instanceof Function); // true
```

> **Identifying Arrays**: when you pass an array from one frame to another, "**instanceof**" operator doesn’t work (in web frames) because the array is actually an instance of Array from a different frame.
> 
> -To solve this problem, ECMAScript 5 introduced **Array.isArray()**,
> 
> ```js
> var items = [];
> console.log(Array.isArray(items));      // true
> ```

----

## Primitive Wrapper Types:

-The primitive wrapper types are **special reference types** that are **automatically** created behind the scenes.

-These special reference types exist to make working with primitive **values** as easy as working with objects. 

-There are three primitive wrapper types (String, Number, and Boolean)

> For example, 
> 
> -in the first line of this listing, a primitive string value is assigned to name. 
> 
> -The second line **treats name like an object** and calls charAt(0) using dot notation (as it happened when using an object)
> 
> ```js
> var name = "Nicholas";
> var firstChar = name.charAt(0); 
> console.log(firstChar);            // "N"
> ```
> 
> -This is what happens behind the scenes = what the JavaScript engine does
> 
> ```js
> var name = "Nicholas";    
> var temp = new String(name);                  //object is created 
> var firstChar = temp.charAt(0);
> temp = null;                                 //object is detroyed (garbage collector)
> console.log(firstChar);          // "N"
> ```
> 
> -Because the second line uses a string (a **primitive**) like an **object**, **the JavaScript engine creates an instance of String** so that charAt(0) will work.
> 
> -The String object exists **only for one statement** before it’s destroyed (a process called **autoboxing**).
> 
> #### **-important notes!!!!!!!!:**
> 
> -You can create primitive wrapper types manually, but there are certain side effects of confusing and inability to identifying the "typeof" of data.
> 
> -Most of the time, using primitive wrapper objects instead of primitives **only leads to errors**.

---------

## notes:

-Reference types are the closest thing to classes in JavaScript,

-and objects are instances of reference types.

-functions are objects in JS.
