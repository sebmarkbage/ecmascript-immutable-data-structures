Records
-------

### Examples

__Initialization__
```javascript
const a = new Record({ x: 1, y: 2 });
```

__Initialization Sugar__
```javascript
const a = #{ x: 1, y: 2 };
```

__Extension__
```javascript
const b = new Record(Object.assign({}, a, { z: 3 }));
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

### Notes

Enumeration always proceeds in lexicographic order of property names.

### Polyfill in Terms of Typed Objects

```javascript
let Record = (function() {
  let typeMap = new Map();
  return function(descriptor) {
    const keys = new Tuple(Object.keys(descriptor).sort());
    let type;
    if (typeMap.has(keys)) {
      type = typeMap.get(keys);
    } else {
      const fields = keys.map(key => ({
        name: key,
        value: any
      }));
      type = ValueType(new Symbol('record'), fields);
      typeMap.set(keys, type);
    }
    return new type(descriptor);
  };
})();
```
