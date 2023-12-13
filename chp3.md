###### notes from  **" *OBJECT-ORIENTED THE PRINCIPLES OF***

###### *JAVASCRIPT*"   by NICHOLAS C. ZAKAS

### chapter 2: understanding object

## Defining Properties:

-objects in JavaScript are **dynamic**, meaning that they can change **at any point** during code.

-property definition

```js
var person2 = new Object(); 
person2.name = "Nicholas";
person2.age = "Redacted";
```

-When a property is first added to an object, JavaScript uses **an internal method called [[Put]]** on the object. The [[Put]] method **creates a spot** in the object **to store** the property.

-When a new value is assigned to an existing property, a ­separate operation **called [[Set]]** takes place. This operation replaces the current value of the property with the new one.

------------------

## Detecting Properties:

-a wrong way to detect if the property exist is using **if condition**.

> ```js
> // unreliable 
> if (person1.age) {
> // do something with age
> }
> ```
>
> -The if condition evaluates to true if the value is truthy (an object, a nonempty string, a nonzero number, or true) and evaluates to false if the value is falsy (null, undefined, 0, false, NaN, or an empty string)
>
> -Because an object property can contain one of these **falsy values,** the example code can yield false negatives. For instance, if person1.age is 0, then the if condition will not be met even though the property exists

-we can use **in operator** 

```js
var person1 = { 
    name: "Nicholas",
    sayName: function() { 
        console.log(this.name);
  } 
};
console.log("sayName" in person1); // true
```

-to avoid the confusing that results because of prototype property we **use ­hasOwnProperty().**

> ```js
> var person1 = {
>     name: "Nicholas",
>     sayName: function() { 
>         console.log(this.name);
>    } 
> }; console.log("name" in person1);                // true 
> console.log(person1.hasOwnProperty("name"));      // true 
> console.log("toString" in person1);               // true 
> console.log(person1.hasOwnProperty("toString"));  //false
> 
> ```
>
> -The toString() method, however, is a prototype property that is present on all objects. The in operator returns true for toString(), but ­hasOwnProperty() returns false

## Removing Properties:

```js
var person1 = { 
name: "Nicholas"
};
console.log("name" in person1);      // true
delete person1.name;                 
console.log("name" in person1);      //not output 
console.log(person1.name);           // undefined

```

---------------------

## enumerable:

-all properties that you **add to an object** are enumerable, which means that you can **iterate over them** using a **for-in loop**. Enumerable properties have their internal [[Enumerable]] attributes set to **true**.

```js
var property;
for (property in object) { 
    console.log("Name: " + property);              
    console.log("Value: " + object[property]);  
}
```

-using ecmascript5, using **Object.keys()**

```js
var properties = Object.keys(object);
// if you want to mimic for-in behavior
var i, len;
for (i=0, len=properties.length; i < len; i++){
console.log("Name: " + properties[i]); 
console.log("Value: " + object[properties[i]]);
}
```



> note that:
>
> -**not all** properties are enumerable. In fact, **most of the native methods** on objects have their [[Enumerable]] attribute set to **false.**
>
> -you can check if it is a enumerable attribute by using **propertyIsEnumerable()**.
>
> ```js
> var properties = Object.keys(person1);
> console.log("length" in properties);                      //true
> console.log(properties.propertyIsEnumerable("length"));   // false
> ```
>
> 

