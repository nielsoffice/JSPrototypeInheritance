# JS Prototype Inheritance Object
JavaScript Prototype Inheritance using apply function and Object.create method in JS.
This can be your alternative to achieve the associated of arrays data, But in here instead of associated
of array this where you can collect and set all static data Object as similar to or like associated of array
but not array it is Object and you can loop and work through it.


```JS
 // Prototype Object 
 function Artist(talent, name) {

  this.talent = talent;
  this.name = name;

 }

 Artist.prototype.login = function() {
   return ( this.name + ' You can now login!');
 }

 Artist.prototype.logout = function() {
  return ( this.name + ' You are now logout!');
 }
 
 Artist.prototype.getName = function() {
   return  this.name;
 }
 
 // Inheritance Object "Artist"
 function Beterance( ... args ) {
  
  // Handling arguments inside the function scope to iterate instead getting one by one!
  // Arguments as Object: console.log(args) inCaseOf: Beterance( args ) { ... }
  // Object Result: { 0: 'arg_val1' , 1: 'arg_val2' }
  // Arguments as Array : console.log(Array.from(args)) inCaseOf: Beterance( args ) { ... }
  // Array Result: [ 'arg_val1' , 'arg_val2' ]
  // OR inCaseOf: Beterance( ...args ) { ... }
  // Array Result: [ 'args[0]' , 'args[1]' ]  | [ 'args[0]' , 'args[1]', 'args[2]', 'args[3]' ...so on and so forth... ] 
  // Usage: Beterance('arg_val1','arg_val2');
  Artist.apply(this, args);  

 }
 
 // Also Inherit the method or functions!
 // so now beterance has function asl well the as Artist!
 Beterance.prototype = Object.create(Artist.prototype);
 
 // This method only visible to access by Beterance object.
 // While you have a complete copy of methods from Artist!
 Beterance.prototype.functionName = function() {
   // do something! ...
 }
 
 // Extend prototype from primary object 
 Object.setPrototypeOf(Beterance, Artist.prototype);
 Beterance.prototype.getName = function() {
   // In this approach you can now play along with the data !
   return  this.name;
 }
```

```JS 
// Create new Object
const art1 = new Artist('Paint', 'Tame');
const art2 = new Artist('Digital Paint', 'Niel');
const bet1 = new Beterance('All around design', 'Mcgin' );
```

```JS
  // Console.log() | Result
  console.log(bet1);
  console.log(bet1.name);
  console.log(bet1.talent);
  console.log(bet1.login());
  console.log(bet1.logout());
  console.log('-------------------');
  console.log(art1);
  console.log(art1.name);
  console.log(art1.talent);
  console.log(art1.login());
  console.log(art1.logout());
```

```JS
Beterance {talent: 'All around design', name: 'Mcgin'}
    name: "Mcgin"
    talent: "All around design"
  [[Prototype]]: Artist
  [[Prototype]]: Object 
    login : ƒ ()
    logout: ƒ ()
    constructor: ƒ Artist(talent, name)
  [[Prototype]]: Object
   Mcgin
   All around design
   Mcgin You can now login!
   Mcgin You are now logout!
--------------------------------------
Artist {talent: 'Paint', name: 'Tame'} 
   name: "Tame"
   talent: "Paint"
 [[Prototype]] : Object
   login: ƒ ()
   logout: ƒ ()
   constructor: ƒ Artist(talent, name)
 [[Prototype]]: Object
   Tame
   Paint
   Tame You can now login!
   Tame You are now logout!
```

Object.create | Create Object properties to Object

```JS
  const PersonDev = {

    yearsOfExperience() {
       console.log( 'You are qualify '+ this.name + ' as you have '+ this.yExperience ); // suppose that I have property name yExperience
     }
 
  }

  const nielWPDev = Object.create(PersonDev);

  console.log(nielWPDev);

  // The properties that suppose in object 
  nielWPDev.name = 'NielOffice'; 
  nielWPDev.yExperience = 6; // the value is 6
  nielWPDev.yearsOfExperience();
  
  // Console.log() | Result 
 {}
 name: "NielOffice"
 yExperience: 6
 [[Prototype]]: Object
  yearsOfExperience: ƒ yearsOfExperience()
  [[Prototype]]: Object
 ------------------------------------------- 
  You are qualify NielOffice as you have 6

 NOTE: When you use the object inside the function you, you should use the "ObjectName.call();" instead of "new ObjectName()";
 const Dev = function() { ObjectName.call(); }
```

```JS
  // Function as Object Method
  function forVIP() { return this.name + ' is a Happy Client!' }

  const obj1 = {
     name: 'Jhon',
     forVIP: forVIP
  }

console.log(obj1.forVIP()); // Result : Jhon is a Happy Client!
```

```JS
const Developer = {
  firstName:"Jhon",
  lastName: "Doe",
  getFullName: function() {
    return this.firstName + " " + this.lastName;
  }
}

const frontEnd = {
  firstName:"Niel",
  lastName: "Zednanref",
}

let getfullName = Developer.getFullName.bind(frontEnd);
console.log(getfullName());

// Demo 1B 
// Inherit the all method and propertiest of Primary method
frontEnd.__proto__ = Developer;
// OR 
// Is Developer Prototype of frontEnd?? 
// Is Developer give something to frontEnd?? // Result YES 
console.log(Developer.isPrototypeOf(frontEnd)); // True < Developer give all methods and properties >
console.log(frontEnd.getFullName()); // Niel Fernandez 
console.log(frontEnd.advancetage); // true

// Get Iterate all Object properties from frontend
for (let prop in frontEnd) {
  if (frontEnd.hasOwnProperty(prop)) {
    const element = prop;
    console.log(element); 
  }
}

// Properties of Object frontend | Result 
firstName
lastName 
```

```JS
// Checking the defualt method for Onbject 
console.log(frontEnd);
// OR 
console.log(frontEnd.__proto__);

// console.log() | result 
{firstName: 'Niel', lastName: 'Zednanref'}
firstName :  "Niel"
lastName  :  "Zednanref"
[[Prototype]] :  Object
 constructor : ƒ Object()
 hasOwnProperty :  ƒ hasOwnProperty()
 isPrototypeOf :  ƒ isPrototypeOf()
 propertyIsEnumerable :  ƒ propertyIsEnumerable()
 toLocaleString : ƒ toLocaleString()
 toString :  ƒ toString()
 valueOf :  ƒ valueOf()
 __defineGetter__ : ƒ __defineGetter__()
 __defineSetter__ : ƒ __defineSetter__()
 __lookupGetter__ : ƒ __lookupGetter__()
 __lookupSetter__ : ƒ __lookupSetter__()
 __proto__ : (...)
 get __proto__ : ƒ __proto__()
 set __proto__ : ƒ __proto__()
```

```JS
// Inherit FrontEnd to Developer 
// Developer give something to FrontEnd < All properties >
const Developer = {
  firstName:"Jhon",
  lastName: "Doe",
  getFullName: function() {
    return this.firstName + " " + this.lastName;
  }
}

// FrontEnd inherited from Developer
// Developer give something to frontEnd < Properties > 
const frontEnd = Object.create(Developer); 
console.log(frontEnd);

// Borrowing Method Object
// Reference: https://github.com/nielsoffice/JSBorrowingMethod_Object
frontEnd.getFullName = Developer.getFullName; 
console.log(frontEnd.getFullName())

// Console.log() | Result 
{}
getFullName: ƒ ()
[[Prototype]]: Object
 firstName: "Jhon"
 getFullName: ƒ ()
 lastName: "Doe"
[[Prototype]] : Object
 Jhon Doe
```

```JS
// EXTEND OR INHERIT DEFAULT OBJECT JS TO CREATE METHOD THAT REQUIRE IN ORDER TO WORKOUT THE DATA.
// Array.map() => to print '🗺'
// Extend Object Date to create another method ! 
Array.prototype.mapV2 = function()  { 
  console.log(this); // this is from array that we need to workout !
  arr = [];
  for (let i = 0; i < this.length; i++) {
    arr.push((this[i]+'🗺'));
  }
  return arr;
}

 // Array we need to workout : [1,2,3]
 // mapV2() we extend the Array Object and create method named mapV2() 
 // to workout our array according to requirements
 // we use the method in array that we need to workout!
 // [1,2,3].mapV2()
 console.log([1,2,3].mapV2()) // Result From: [1, 2, 3] To: ['1🗺', '2🗺', '3🗺']
 console.log(Array.prototype) // < checking all available properties and method from this object >

-------------------------------------------------------------------------------------------------------

 // Extend Object Date to create another method ! 
 Date.prototype.lastYear = function(){
  return this.getFullYear() - 1;  // this.getFullYear() is from Date Object default method.
}
// This a Date Object JS default
// Prototype or I create method from Date object name lastYear
// w/ lastYear method I call the default method getFullYear default from 
// Date Object and substract 1 to get the result which is lastYear
// return this.getFullYear() - 1 Result: 2022
const getLY = new Date('2023-10-10').lastYear(); 

// This is how to create another method within an existing object
// Or this is the way to extend functionality of Object 
console.log(getLY); // Result 2022
console.log(Date.prototype); // < checking all available properties and method from this object >
```

In addition, keep in mind once you create a "primary object" like Artist where inherit by Beterance, the primary
object all prototype or functions will be visible to all inheritance and a new prototype or functions that only designate 
for the heritance will be exclusive to inheritance through creating it's own prototype. 
Simply, mean once you use object.create() method in JS it will give us a privelage to have a copy of ALL functions or prototypes from it's 
parent to child. While you can add a custom function or prototype to the inherit one that not visible to primary object. 

