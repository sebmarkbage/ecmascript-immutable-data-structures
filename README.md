Immutable Records, Tuples, Maps and Sets for ECMAScript
-------------------------------------------------------

Immutability and referential transparency has many known benefits and ability for optimization. Several modern JavaScript libraries take advantage of this, and many more functional compile-to-JS languages.

All these types provide value equality for both `==` and `===`.

This proposal provides convenient syntax and semantics for immutable data structures and helpers to extend them. The actual implementation details of the extend operations are not covered by this spec but it's expected that engines optimize beyond just copying. E.g. using persistent data structures.

This is based upon the [Typed Object](https://github.com/dslomov-chromium/typed-objects-es7) proposal ([Explainer](https://github.com/nikomatsakis/typed-objects-explainer)).

### [Records](Records.md)

Records are a new value type that represents an immutable object without a prototype.

```javascript
const xy = #{ x: 1, y: 2 }; // frozen value type
const xyz = #{ ...xy, z: 3 }; // functional extension
```

### [Tuples](Tuples.md)

Tuples are a new value type that represents an immutable array without a prototype and no holes. It cannot be sparse.

```javascript
const xy = #[ x, y ]; // frozen value type
const xyz = #[ ...xy, z ]; // functional extension
```

### [Immutable Map](ImmutableMap.md)

ImmutableMap is an immutable version of Map. Any mutable operation returns a new ImmutableMap instead of mutating the existing reference.

```javascript
const a = new ImmutableMap([['x', 1], ['y', 2]]);
const b = a.set('y', 3);
a.get('y'); // 2
b.get('y'); // 3
```

### [Immutable Set](ImmutableSet.md)

ImmutableSet is an immutable version of Set. Any mutable operation returns a new ImmutableSet instead of mutating the existing reference.

```javascript
const a = new ImmutableSet([1, 2]);
const b = a.add(3);
a.size; // 2
b.size; // 3
```

## [Status of this Proposal](https://github.com/tc39/ecma262)

It is my intention to propose this as a Stage 0 proposal to ECMAScript 7.

## [Known Issues](Issues.md)

[See why this matters.](Issues.md)
