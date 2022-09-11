---
title: Javascript inheritance archaeology
last_modified: 2022-09-05
---

This post highlights some professional insights I have gained about software engineering working at
Google.

## 'Doc-driven design'

Or: obscure things about Javascript inheritence that I think I used to know, and wanted to remember, while learning Typescript.

Javascript uses prototypical inheritance, and back in the bad ol' days before `Object.setPrototype` or `extends`, people used to
do the following in order to setup prototypical inheritance in Javascript.

1. Create child and parent constructor functions (`function Child() { ... }`)

    ```
    function Parent() {
      this.parentProp = 'foo';
    }
    // 'create a method on the parent'
    Parent.prototype.parentMethod = function() {
      console.log('parent');
    }
    
    function Child() {
      this.childProp = 'bar';
    }
    // 'create a method on the child'
    Child.prototype.childMethod = function() {
      console.log('child');
    }
    ```

    At this point the prototype of each is a new object having:
   
    * `prototype` equal to `Object.prototype`, and
    * `constructor` equal to the constructor function itself (i.e. `Child.prototype.constructor === Child` is true.)

1. Set the child constructor's `prototype` to `new Parent()`:

    ```
    Child.prototype = new Parent();
    ```

    This was the fundamental step in creating prototypical inheritance.
    
The following additional 'cleanup' steps were followed inconsistently, resulting in inconsistent inheritance patterns and giving Javascript
a bad name (which was not entirely undeserved, since users would have benefited from built-ins for inheritance like we have today.) People tried to circulate libraries for setting up inheritence to standardize the process.
    
1. Set the child constructor's `prototype.constructor` to the child constructor.

    `new Parent()`'s `constructor` is `Parent`, but we want instanes of `Child` to have `Child` as their constructor.
    To correct that: `Child.prototype.constructor = Child`.

1. Copy any properties that were previously on the child constructor's `prototype` to the new prototype.

    Since we overwrote the child constructor's prototype in the last step, some thorough people would create a temporary reference to the old prototype
    and copy over any own-properties after overwriting it with `new Parent()`.

    ```
    var origProto = sub.prototype;
    sub.prototype = Object.create(base.prototype);
    for (var key in origProto)  {
      if origProto.hasOwnProperty(key) {
        sub.prototype[key] = origProto[key];
      }
    }
    ```
1. Setup inheritance between the classes?

    Say that `Parent` had 'static' properties that you wanted to access from `Child`:
    
    ```
    Parent.myStaticField = 'foo';
    
    Child.prototype.doSomethingWild = function() {
      console.log(this.constructor.myStaticField);
    }
    ```
    
    You could set this up to work by creating prototypical inheritance between the constructor's themselves:
    
    ```
    Object.setPrototypeOf(Child, Parent);
    ```
    
    I'm not even sure this is a good idea...class-based inheritance languages like Java wouldn't allow this.
    But it's mentioned towards the end of
    [this MDN article](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor#changing_the_constructor_of_a_constructor_functions_prototype)
    so I'll include it for completeness.
 
    I'm also not sure if this would have been possible prior to `Object.setPrototypeOf`. But since `extends` [does this
    automatically now](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends),
    I guess this is the Javascript way.
    
Did I miss something? Maybe some other common cleanup step that often was included in historical inheritance libraries? Let me know via Twitter!

## References

* http://crockford.com/javascript/prototypal.html
* http://crockford.com/javascript/inheritance.html
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor#changing_the_constructor_of_a_constructor_functions_prototype
* https://stackoverflow.com/a/4389429/39396
