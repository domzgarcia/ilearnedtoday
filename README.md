# ilearnedtoday
collate daily learnings

### JS
---
#### Module Pattern

- Object Literals
- Closures, Access Modifiers

>From a historical perspective, the Module pattern was originally developed by a number of people including **Richard Cornford** in 2003. It was later popularized by **Douglas Crockford** in his lectures. Another piece of trivia is that if you've ever played with Yahoo's YUI library, some of its features may appear quite familiar and the reason for this is that the Module pattern was a strong influence for YUI when creating their components.

### Full Example
```javascript
var basketModule = (function () {
  // privates
  var basket = [];
  function doSomethingPrivate() {
    //...
  }
  function doSomethingElsePrivate() {
    //...
  }
  // Return an object exposed to the public
  return {
    // Add items to our basket
    addItem: function( values ) {
      basket.push(values);
    },
    // Get the count of items in the basket
    getItemCount: function () {
      return basket.length;
    },
    // Public alias to a private function
    doSomething: doSomethingPrivate,
    // Get the total value of items in the basket
    getTotal: function () {
      var q = this.getItemCount(),
          p = 0;
      while (q--) {
        p += basket[q].price;
      }
      return p;
    }
  };
})();
```

### Import mixins
>This variation of the pattern demonstrates how globals (e.g jQuery, Underscore) can be passed in as arguments to our module's anonymous function. This effectively allows us to import them and locally alias them as we wish.
```javascript
// Global module
var myModule = (function ( jQ, _ ) {
    function privateMethod1(){
        jQ(".container").html("test");
    }
    function privateMethod2(){
      console.log( _.min([10, 5, 100, 2, 1000]) );
    }
    return{
        publicMethod: function(){
            privateMethod1();
        }
    };
// Pull in jQuery and Underscore
})( jQuery, _ );
myModule.publicMethod();
```
### Exports
>This next variation allows us to declare globals without consuming them and could similarly support the concept of global imports
```
// Global module
var myModule = (function () {
  // Module object
  var module = {},
    privateVariable = "Hello World";
  function privateMethod() {
    // ...
  }
  module.publicProperty = "Foobar";
  module.publicMethod = function () {
    console.log( privateVariable );
  };
  return module;
})();
```

