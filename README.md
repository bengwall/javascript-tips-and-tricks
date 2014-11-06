Javascript Tips
===============


Equality
--------

Use `===` instead of `==`.  `===` or 'strict comparison' means is the same type and equal.  `==` simply means equal.  Only use `==` when checking for *null* and *undefined*.

```
1 == "1"     		// true, auto type coercion
1 === "1"    		// false, because they are of a different type
1 !== "1"    		// true, inequality check also available
null == undefined 	// true
null === undefined 	// false
'0' == false 		// true
'0' === false 		// false
```

var
---

Always declar variables with `var`.  When you fail to specify var, the variable gets placed in the global context, potentially clobbering existing values.


True and False Boolean Expressions
----------------------------------

The following are all false in boolean expressions:

* null
* undefined
* '' the empty string
* 0 the number

But be careful, because these are all true:

* '0' the string
* [] the empty array
* {} the empty object

This means that instead of this:

```
while (x != null) {
```

you can write this shorter code (as long as you don't expect x to be 0, or the empty string, or false):

```
while (x) {
```

And if you want to check a string to see if it is null or empty, you could do this:

```
if (y != null && y != '') {
```

But this is shorter and nicer:

```
if (y) {
```

Caution: There are many unintuitive things about boolean expressions. Here are some of them:

* Boolean('0') == true
* '0' != true
* 0 != null
* 0 == []
* 0 == false
* Boolean(null) == false
* null != true
* null != false
* Boolean(undefined) == false
* undefined != true
* undefined != false
* Boolean([]) == true
* [] != true
* [] == false
* Boolean({}) == true
* {} != true
* {} != false

Conditional (Ternary) Operator (?:) for if-then-else
----------------------------------------------------

```
return (b === c) ? d : e                 
// if b equals c, then return d else return e

var a  = (b === c) ? d : e                 
// if b equals c, then make a = d else make a = e

var aa = ((_ref = bb) === cc) ? _ref : ee  
// if bb equals cc, then make aa = bb else make aa = ee
```

&& and ||
---------

These binary boolean operators are short-circuited, and evaluate to the last evaluated term.

"||" has been called the 'default' operator, because instead of writing this:

```
/** @param {*=} opt_win */
function foo(opt_win) {
  var win;
  if (opt_win) {
    win = opt_win;
  } else {
    win = window;
  }
  // ...
}
```

you can write this:

```
/** @param {*=} opt_win */
function foo(opt_win) {
  var win = opt_win || window;
  // ...
}
```

"&&" is also useful for shortening code. For instance, instead of this:

```
if (node) {
  if (node.kids) {
    if (node.kids[index]) {
      foo(node.kids[index]);
    }
  }
}
```

you could do this:

```
if (node && node.kids && node.kids[index]) {
  foo(node.kids[index]);
}
```

or this:

```
var kid = node && node.kids && node.kids[index];
if (kid) {
  foo(kid);
}
```

Object References
-----------------

* In JavaScript, “var object1 = object2” actually just creates a reference.   When you change object1, the object2 will also change.  What you want to do is clone the object using [angular.copy](  http://docs.angularjs.org/api/ng/function/angular.copy).

Arrays
------

* `push` appends a new item on the back of array
* `unshift` prepends a new item on the front of the arry



Other Useful JavaScript Guides 
------------------------------

* [Google's JavaScript style guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
* [Douglas Crockford's JavaScript style guide](http://javascript.crockford.com/code.html)
* [Airbnb JavaScript style guide](https://github.com/airbnb/javascript)
* [JavaScript Garden](http://bonsaiden.github.io/JavaScript-Garden/#equality)


Other Useful Links and Blogs
----------------------------

* [Random Tips](http://blog.tomaka17.com/2012/12/random-tricks-when-using-angularjs/)
* [Bruno Scopelliti's blog](http://blog.brunoscopelliti.com/)
* [AngularJS Blog](http://blog.angularjs.org/)
* [AngularJS Faq](http://docs.angularjs.org/misc/faq)
* [Dean Sofer's tips](http://deansofer.com/posts/view/14/AngularJs-Tips-and-Tricks-UPDATED)