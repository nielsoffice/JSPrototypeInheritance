# JSPrototypeInheritance
JavaScript Prototype Inheritance using apply function and Object.create method JS.

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
JSTraining.html:34 Mcgin
JSTraining.html:35 All around design
JSTraining.html:36 Mcgin You can now login!
JSTraining.html:37 Mcgin You are now logout!
-------------------
Artist {talent: 'Paint', name: 'Tame'} 
   name: "Tame"
   talent: "Paint"
 [[Prototype]] : Object
   login: ƒ ()
   logout: ƒ ()
   constructor: ƒ Artist(talent, name)
 [[Prototype]]: Object
JSTraining.html:40 Tame
JSTraining.html:41 Paint
JSTraining.html:42 Tame You can now login!
JSTraining.html:43 Tame You are now logout!
```
