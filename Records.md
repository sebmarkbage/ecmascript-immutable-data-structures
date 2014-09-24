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

== and === test value equality.

<, >= etc. test value order/equality in enumeration order.

### Notes

Enumeration always proceeds in lexicographic order of property names.

== and === test value equality
< etc. test value order/equality
