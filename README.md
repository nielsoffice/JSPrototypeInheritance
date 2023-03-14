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
 
 // Inheritance Object "Artist"
 function Beterance( ... args ) {

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

In addition, keep in mind once you create a "primary object" like Artist where inherit by Beterance, the primary
object all prototype or functions must be visible to all inheritance and a new prototype or functions that only designate 
for the heritance will be exclusive to inheritance through creating it's own prototype. 
Simply, mean once you use object.create() method in JS it will give us a privelage to have a copy of ALL functions or prototypes from it's 
parent to child. While you can add a custom function or prototype to the inherit one that not visible to primary object. 

