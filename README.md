# js-helpers

### All available methods

- [groupBy](#groupBy)

#### ``groupBy(data, key)`` returns grouped result by some key:
```js
var groupBy = function(data, key) { 
  // `data` is an array of objects, `key` is the key (or property accessor) to group by
  // reduce runs this anonymous function on each element of `data` (the `item` parameter,
  // returning the `storage` parameter at the end
  return data.reduce(function(storage, item) {
    // get the first instance of the key by which we're grouping
    var group = item[key];
    
    // set `storage` for this instance of group to the outer scope (if not empty) or initialize it
    storage[group] = storage[group] || [];
    
    // add this item to its group within `storage`
    storage[group].push(item);
    
    // return the updated storage to the reduce function, which will then loop through the next 
    return storage; 
  }, {}); // {} is the initial value of the storage
};
```
or shorter, but not readable version from [https://stackoverflow.com/questions/14446511/most-efficient-method-to-groupby-on-a-array-of-objects/34890276#34890276]
```
var groupBy = function(xs, key) {
  return xs.reduce(function(rv, x) {
    (rv[x[key]] = rv[x[key]] || []).push(x);
    return rv;
  }, {});
};
```
