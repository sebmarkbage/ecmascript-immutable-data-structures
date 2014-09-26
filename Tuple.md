Tuples
------

### Examples

__Initialization__
```javascript
const a = new Tuple([1, 2]);
```

__Initialization Sugar__
```javascript
const a = #[1, 2];
```

__Extension__
```javascript
const b = a.concat(#[3, 4]);
```

__Extension Sugar__
```javascript
const b = #[...a, 3, 4];
```

__Type__
```javascript
typeof #[]; // 'tuple'
```

### Syntax

TupleLiteral:
- `#` `[` (TupleElement (`,` TupleElement)*)? `]`

TupleElement:
- AssignmentExpression
- `...` AssignmentExpression

### Comparison Semantics

`==` and `===` test value equality.

`<`, `>=` etc. test value order/equality in enumeration order.

### Prototype

Value types are not objects and have no prototype. Member expressions are exposed on the [Tuple's prototype](Tuple.prototype.md) which is unique for each realm, just like other value types. This prototype is exposed on the realm's global [Tuple.prototype](Tuple.prototype.md).

### Notes

Enumeration always proceeds in numeric index order.

`.length` cannot be greater than 2^32 - 1

Tuples are never sparse. They cannot have holes.

### Polyfill in Terms of Typed Objects

```javascript
let Tuple = (function() {
  let TupleSymbol = new Symbol('tuple');
  let TupleConstructor = function(iterable) {
    let fields = {};
    let values = {};
    let i = 0;
    for (let value of iterable) {
      i++;
      fields[i] = any;
      values[i] = value;
    }
    // Note: This could probably be replaced with a value array but it's
    // unclear in the current ValueTypes proposal what that means.
    let type = ValueType(TupleSymbol, fields);
    // Note: We can't replace the ValueType's prototype object to
    // the shared object, so we have to do the next best thing.
    Object.setPrototypeOf(type.prototype, TuplePrototype);
    return new type(values);
  };
  let TuplePrototype = TupleConstructor.prototype;
  return TupleConstructor;
})();
```
