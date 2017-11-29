# ilearnedtoday
collate daily learnings

### JS
---
#### Module Pattern

- Object Literals
- Closures, Access Modifiers

>From a historical perspective, the Module pattern was originally developed by a number of people including **Richard Cornford** in 2003. It was later popularized by **Douglas Crockford** in his lectures. Another piece of trivia is that if you've ever played with Yahoo's YUI library, some of its features may appear quite familiar and the reason for this is that the Module pattern was a strong influence for YUI when creating their components.

### Full Example
```
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



