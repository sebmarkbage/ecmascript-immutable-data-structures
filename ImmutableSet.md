Immutable Set
-------------

### Examples

__Initialization__
```javascript
const a = new ImmutableSet([1, 2]);
```

__Extension__
```javascript
const b = a.add(3);
```

__Type__
```javascript
typeof new ImmutableSet(); // 'set'
```

### Prototype

Value types are not objects and have no prototype. Member expressions are exposed on the [Immutable Set's prototype](ImmutableSet.prototype.md) which is unique for each realm, just like other value types. This prototype is exposed on the realm's global [ImmutableSet.prototype](ImmutableSet.prototype.md).
