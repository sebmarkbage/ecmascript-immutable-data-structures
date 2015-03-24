ImmutableSet.prototype
----------------------

This prototype object allows easy access to various helpful built-in methods for manipulating [Immutable Sets](ImmutableSet.md).

### ImmutableSet ( [ iterable ] )

Returns an `ImmutableSet` using an optional iterable in a similar way to the `Set` constructor except it cannot be called with `new`. It is not constructable.

## Mutation

All the mutation operations in `Set.prototype` have equivalent immutable operations which return a different `ImmutableSet` as the return value.

### ImmutableSet.prototype.clear ( )

Returns an empty `ImmutableSet`.

### ImmutableSet.prototype.delete ( value )

If `this` does not include an entry with the `value`, return the same `ImmutableSet`. Otherwise,
return an `ImmutableSet` with the same entries, except the one with `value`.

Note: The mutable version returns a boolean if the `value` existed. This use case has to be replaced with a `has(value)` check on the previous version, or the previous and the next set can be compared as a whole.

### ImmutableSet.prototype.add ( value )

If `this` does not include an entry with the `value`, return an `ImmutableSet` with all the same entries plus an entry with `value`. This adds the entry to the end of the enumeration order.

Otherwise, return the same `ImmutableSet` as `this`.

## TLDR

The rest of these are just what you would expect and has similar semantics as the mutable `Set`.

### ImmutableSet.prototype.constructor
### ImmutableSet.prototype.entries ( )
### ImmutableSet.prototype.forEach ( callbackfn [ , thisArg ] )
### ImmutableSet.prototype.has ( value )
### ImmutableSet.prototype.keys ( )
### get ImmutableSet.prototype.size
### ImmutableSet.prototype.values ( )
### ImmutableSet.prototype [ @@iterator ]( )
### ImmutableSet.prototype [ @@toStringTag ]
