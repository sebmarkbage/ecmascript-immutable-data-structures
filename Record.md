Records
-------

### Examples

__Initialization__
```javascript
const a = Record({ x: 1, y: 2 });
```

__Initialization Sugar__
```javascript
const a = #{ x: 1, y: 2 };
```

__Extension__
```javascript
const b = Record(Object.assign({}, a, { z: 3 }));
```

__Extension Sugar__
```javascript
const b = #{ ...a, z: 3 };
```

__Type__
```javascript
typeof #[]; // 'record'
```

### Syntax

RecordLiteral:
- `#` `{` (`...` AssignmentExpression)? `}`
- `#` `{` PropertyDataAssignment (`,` PropertyDataAssignment)* (`,` `...` AssignmentExpression)? `}`

PropertyDataAssignment:
- PropertyName `:` AssignmentExpression

### Comparison Semantics

`==` and `===` test value equality.

`<`, `>=` etc. test value order/equality in enumeration order.

### Prototype

Value types are not objects and have no prototype. Member expressions normally access a prototype but the prototype of records is null.

This makes it easier to verify that a record has a particular signature without `hasOwnProperty` checks.

### Notes

Enumeration always proceeds in lexicographic order of property names.

### Polyfill in Terms of Typed Objects

```javascript
let Record = (function() {
  let RecordSymbol = new Symbol('record');
  let RecordConstructor = function(object) {
    const keys = Object.keys(object).sort();
    let fields = {};
    for (let i = 0; i < keys.length; i++) {
      fields[keys[i]] = any;
    }
    // Note: Enumeration order of fields is not guaranteed which
    // makes ValueType a problematic API for this use case.
    let type = ValueType(RecordSymbol, fields);
    // Note: We can't replace the ValueType's prototype object
    // so we have to do the next best thing.
    Object.setPrototypeOf(type.prototype, null);
    return new type(object);
  };
  RecordConstructor.prototype = null;
  return RecordConstructor;
})();
```
