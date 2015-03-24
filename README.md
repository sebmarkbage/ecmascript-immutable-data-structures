Immutable Records, Vectors, Maps and Sets for ECMAScript
--------------------------------------------------------

Immutability and referential transparency has many known benefits and ability for optimization. Several modern JavaScript libraries take advantage of this, and many more functional compile-to-JS languages.

This is based upon the [Value Types](https://github.com/nikomatsakis/typed-objects-explainer/blob/master/valuetypes.md) proposal ([Typed Objects](https://github.com/dslomov-chromium/typed-objects-es7) / [Explainer](https://github.com/nikomatsakis/typed-objects-explainer)).

All these types provide value equality for both `==` and `===`.

### [Record](Record.md)

Records are a new value type that represents the value type analogy of an immutable object.

```javascript
const xy = #{ x: 1, y: 2 }; // frozen value type
const xyz = #{ ...xy, z: 3 }; // functional extension
```

### [Immutable Vector](ImmutableVector.md)

ImmutableVector is a new value type that represents the value type analogy of an immutable array, without holes. It cannot be sparse.

```javascript
const xy = #[ x, y ]; // frozen value type
const xyz = #[ ...xy, z ]; // functional extension
```

### [Immutable Map](ImmutableMap.md)

ImmutableMap is an immutable version of Map. Any mutable operation returns a new ImmutableMap instead of mutating the existing reference.

```javascript
const a = ImmutableMap([['x', 1], ['y', 2]]);
const b = a.set('y', 3);
a.get('y'); // 2
b.get('y'); // 3
```

### [Immutable Set](ImmutableSet.md)

ImmutableSet is an immutable version of Set. Any mutable operation returns a new ImmutableSet instead of mutating the existing reference.

```javascript
const a = ImmutableSet([1, 2]);
const b = a.add(3);
a.size; // 2
b.size; // 3
```

## [Status of this Proposal](https://github.com/tc39/ecma262)

It is my intention to propose this as a Stage 0 proposal to ECMAScript 7.

## [Known Issues](Issues.md)

[See why this matters.](Issues.md)
