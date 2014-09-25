Known Issues
------------

### Referential/Physical Equality instead of Value Equality

There are performance use cases where a deep equality is too expensive. For example, in a memoization process it can be faster to recompute than it is to do a deep equality on a large data structure.

```javascript
var memoizedInput;
var memoizedResult;

function calculate(input) {
  if (memoizedInput !== input) {
    memoizedResult = calculator(input);
    memoizedInput = input;
  }
  return memoizedResult;
}
```

However, since these values are immutable, it is possible for an implementation to reuse the same allocation. Therefore, these might have internal reference equality which would be a very fast lookup.

It would be valuable to have a way to have both structural equality, which is the default of value types. However, it is also valuable to have physical equality. I propose that this physical equality needs a separate function.

```javascript
var memoizedInput;
var memoizedResult;

function calculate(input) {
  if (Object.referenceEquals(memoizedInput, input)) {
    memoizedResult = calculator(input);
    memoizedInput = input;
  }
  return memoizedResult;
}
```

Potentially memoization could be a built-in concept, however, that doesn't allow side-effects to be fired based on an equality check. That strategy is what powers libraries like React for interop with DOM.

This could be solved in a separate proposal and potentially also includes Typed Objects and strings as well.

### typeof

The type of these objects are all types. This causes an explosion of new types. It doesn't work well with existing code that assume a finite set of types.

Perhaps these types should share a single type such as 'record'?

### Polyfill

It's possible to implement these features in user land on top of Typed Objects. However, to get the proper `===` semantics you're locked to a certain structure layout which puts significants constraints on the performance optimizations that could be made. This is why this needs to be implemented in engines.
