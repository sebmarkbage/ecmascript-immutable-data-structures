Immutable Map
-------------

### Examples

__Initialization__
```javascript
const a = new ImmutableMap([['x', 1], ['y', 2]]);
```

__Extension__
```javascript
const b = a.set('z', 3);
```

__Type__
```javascript
typeof new ImmutableMap(); // 'map'
```

### Prototype

Value types are not objects and have no prototype. Member expressions are exposed on the [Immutable Map's prototype](ImmutableMap.prototype.md) which is unique for each realm, just like other value types. This prototype is exposed on the realm's global [ImmutableMap.prototype](ImmutableMap.prototype.md).