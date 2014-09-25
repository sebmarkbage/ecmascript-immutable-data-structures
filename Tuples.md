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

== and === test value equality.

<, >= etc. test value order/equality in enumeration order.

### Notes

Enumeration always proceeds in numeric index order.

`.length` cannot be greater than 2^32 - 1

Tuples are never sparse. They cannot have holes.
