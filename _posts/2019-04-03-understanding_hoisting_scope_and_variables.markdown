---
layout: post
title:      "Understanding Hoisting, Scope, and Variables"
date:       2019-04-04 00:33:28 +0000
permalink:  understanding_hoisting_scope_and_variables
---


#**What is hoisting & scope?**

**scope**

First, let’s talk about scope.  Put simply, scope is the limits in which a variable exists within a function.  It’s that simple.  There are different kinds of scope.  Let's take a look:

global scope: Any variable declared in the global scope is accessible anywhere in your JavaScript code.  

```
var kitty = “Fuzz Aldrin”  // I’m in the global scope!

function catNames() {
   // some code
}

	console.log(kitty); // Fuzz Aldrin   
```

local scope: variables that are only accessible within their local scope where they are defined. 

```
function cat() {
	var kitty = “Jerry”;  // I’m in the local scope!
	
	console.log(cat); // Jerry
}

```

lexical Scope: think of lexical scope as the surrounding environment (scope) in which a variable can be accessed. 

```
var cat = 'Jerry';  

function func1(){ 
  
  var dog = 'Chewbarka;  
  
  var func2 = function(){  
    
      console.log(cat); // Jerry  
      console.log(dog); // Chewbarka  
  }
}

```

Because of lexical scoping, nested functions have access to variables declared in their outer scope.  

Here are links to some useful reads on scope:  

[Mozilla - Scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

[w3Schools - Scope](https://www.w3schools.com/js/js_scope.asp)


Now that we understand scope a little better, let’s examine hoisting.  

**hoisting**

Here’s my over simplified interpretation of the MDN definition of Hoisting:

Variable and function declarations are put into memory during the compile phase before it executes any code (thus, hoisted).  It allows you to use a variable or function *before* you declare it in your code.

All variable declarations (`var`, `let`, `const` ) are "hoisted" within its scope.  

**var**

Consider the following code: 

```
kitty = 'Fuzzinator'; // this is the initialization
console.log(kitty); // console.log will return ‘Fuzzinator’
var kitty;  // this is the declaration

```

Console.log will return “Fuzzinator” even though the variable kitty was declared *after* it was used.  How is this possible? 

Before your code is executed, it is first processed.  All variable declarations are identified and put it into memory.  This means your code behaves as if the declaration of 
`var kitty;` came FIRST. In other words, it's been hoisted. Tada!

Note that **only declarations are hoisted**, not initializations. If you declare and initialized your variable *after* using it, the value will then be `undefined`.

```
console.log(kitty) // returns undefined
var kitty;  // this is the declaration
kitty = 'Fuzzinator'; // this is the initialization
```

**let**

let is hoisted within its code block (scope).  Because of this, you will want your` let` declarations to be placed at the top of a code block so they can be made available for that entire block.

```
function getKitty (name) {
    // name does not exist here
    // console.log(name); => ReferenceError: name is not defined

if (name) {
        let kitty = "Sir Fluffington";
        
        return kitty;
    } else {
        // name does exist here either
        return false;
    }
}
```

Note that `name` exists only inside the scope of its block, and will give us an error when accessed outside of it.  

**const**

Const values cannot be re-assigned once they are defined.  Because of this, every const declaration must be initialized at the time of declaration.

```
const kitty = "Luke Skywhisker";  // valid
const kitty;  // syntax error: missing initialization
kitty = "Luke Skywhisker"  // TypeError: Assignment to constant variable
```

A word on variable usage:

* In the world of post ES6, never use `var`.  If you mistakenly redeclare the same variable twice somewhere in your code, you will not throw an error.  Now, you will have to retrace your steps and hunt down the `var` you just changed.  Yikes.
* Use `let ` only for loops and counts, since they can be reassigned only within its block scope
* Use `const`  for everything else.  `const` cannot be reassigned to another value.  Since it cannot be reassigned, you’ll experience less bugs and unwanted side effects.  Stick with `const`!

Some additional reading on variables:

[var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)

[let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)

[const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)


I hope this short introduction provided you with a better understanding of scope & hoisting!

Happy coding!

