

Main topic: What is variable scope and hoisting in JavaScript?

[10:13]
Suggested questions (include example code):




What elements of code are hoisted to the top at runtime?

All variable declarations are hoisted (lifted and declared) to the top of the function, if defined in a function, or the top of the global context, if outside a function.

I just read a great article about JavaScript Scoping and Hoisting by Ben Cherry in which he gives the following example:

var a = 1;

function b() {
    a = 10;
    return;

    function a() {}
}
b();
alert(a);
Using the code above, the browser will alert "1".

I'm still unsure why it returns "1". Some of the things he says come to mind like: All the function declarations are hoisted to the top. You can scope a variable using function. Still doesn't click for me.


 variable assignment is not hoisted, and neither is function assignment



 At the start of runtime in a JavaScript environment there

 * Hoisting is the process of lifting/declaration of functions and variables to the top of either the function they are defined in or the global context if defined outside of a function.
 * Neither variable or function assignment are hoisted on runtime, only the declaration of the var/function
 * It is important to note that function expressions, such as the example below, are not hoisted.
  `var myName = function () {
  console.log ("Rich");
  }`

The following is an example of how variable declaration is hoisted (taken from http://stackoverflow.com/questions/7506844/javascript-function-scoping-and-hoisting)

```
var a = 1;

function b() {
    a = 10;
    return;

    function a() {}
}
b();
alert(a);


Using the code above, the browser will alert "1".

This is due to function hoisting

function b() {
   a = 10;
   return;
   function a() {}
}

The above code will be rewritten by the interpreter to look like this

function b() {
  function a() {}
  a = 10;
  return;
}

in the above example functiona() {} behaves like so
var a = function () {}

This means that the global variable does not get overwritten as a = 10 can find the var a that has been declared within the scope of its function and as such does not look above its function.

 * It is important to know that only variable declarations are hoisted to the top, not variable initialization or assignments (when the variable is assigned a value).
```

What has priority - local variables, or global variables?

```
Variables declared within a JavaScript function, become LOCAL to the function.

Local variables have local scope: They can only be accessed within the function.



So, within the scope of a given function, any variable declared will take priority over any Global variables of the same name, within the scope of said function.
If no 'local' variable is declared, then the function will look in each level of scope above itself until it finds a variable declaration it can use for assignment or other such purposes.

for example:

  //'global variable'

  var carName = 'BMW'

  function myFunction() {

      //'local variable'

      var carName = "Volvo";

      return carName

  }

console.log(carName) ==> 'BMW'

console.log(myFunction) ==> 'Volvo'

So in the context of this example the var carName declared within the scope of myFunction takes priority over the 'global' var carName which is declared outside of the scope of the function.

```


What is executed first, an anonymous function assigned to a variable, or a named function?

```
Anonymous function assigned to a variable:

  var helloWorld = function() {
                      return 'namita'
                   }


Named Function:

  function helloWorld() {
    return 'max'
  }



Function assignment does not get hoisted on runtime and as a result a named function will usually be executed first.


```

What is the difference between function level scope and block level scope?

```
Information available here, need to complete a definition for function and block level scope at a later time scope!...
https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch3.md

```

