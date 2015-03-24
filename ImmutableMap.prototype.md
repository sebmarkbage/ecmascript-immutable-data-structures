ImmutableMap.prototype
----------------------

This prototype object allows easy access to various helpful built-in methods for manipulating [Immutable Maps](ImmutableMap.md).

### ImmutableMap ( [ iterable ] )

Returns an `ImmutableMap` using an optional iterable in a similar way to the `Map` constructor except it cannot be called with `new`. It is not constructable.

## Mutation

All the mutation operations in `Map.prototype` have equivalent immutable operations which return a different `ImmutableMap` as the return value.

### ImmutableMap.prototype.clear ( )

Returns an empty `ImmutableMap`.

### ImmutableMap.prototype.delete ( key )

If `this` does not include an entry with the `key`, return the same `ImmutableMap`. Otherwise,
return an `ImmutableMap` with the same entries, except the one with `key`.

Note: The mutable version returns a boolean if the `key` existed. This use case has to be replaced with a `has(key)` check on the previous version, or the previous and the next map can be compared as a whole.

### ImmutableMap.prototype.set ( key , value )

If `this` does not include an entry with the `key`, return an `ImmutableMap` with all the same entries plus an entry with `[key, value]`. This adds the entry to the end of the enumeration order.

Otherwise, return an `ImmutableMap` with all the same entries as `this`, except the entry with `key` has its `value` replaced with the new `value`. Enumeration order is preserved.

## TLDR

The rest of these are just what you would expect and has similar semantics as the mutable `Map`.

### ImmutableMap.prototype.constructor
### ImmutableMap.prototype.entries ( )
### ImmutableMap.prototype.forEach ( callbackfn [ , thisArg ] )
### ImmutableMap.prototype.get ( key )
### ImmutableMap.prototype.has ( key )
### ImmutableMap.prototype.keys ( )
### get ImmutableMap.prototype.size
### ImmutableMap.prototype.values ( )
### ImmutableMap.prototype [ @@iterator ]( )
### ImmutableMap.prototype [ @@toStringTag ]
