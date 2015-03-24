Immutable Vector
----------------

### Examples

__Initialization__
```javascript
const a = ImmutableVector([1, 2]);
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
typeof #[]; // 'vector'
```

### Syntax

VectorLiteral:
- `#` `[` (VectorElement (`,` VectorElement)*)? `]`

VectorElement:
- AssignmentExpression
- `...` AssignmentExpression

### Comparison Semantics

`==` and `===` test value equality.

`<`, `>=` etc. test value order/equality in enumeration order.

### Prototype

Value types are not objects and have no prototype. Member expressions are exposed on the [Vector's prototype](ImmutableVector.prototype.md) which is unique for each realm, just like other value types. This prototype is exposed on the realm's global [ImmutableVector.prototype](ImmutableVector.prototype.md).

### Notes

Enumeration always proceeds in numeric index order.

`.length` cannot be greater than 2^32 - 1

Vectors are never sparse. They cannot have holes.

### Polyfill in Terms of Typed Objects

```javascript
let ImmutableVector = (function() {
  let VectorSymbol = new Symbol('vector');
  let VectorConstructor = function(iterable) {
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
    let type = ValueType(VectorSymbol, fields);
    // Note: We can't replace the ValueType's prototype object to
    // the shared object, so we have to do the next best thing.
    Object.setPrototypeOf(type.prototype, VectorPrototype);
    return new type(values);
  };
  let VectorPrototype = VectorConstructor.prototype;
  return VectorConstructor;
})();
```
