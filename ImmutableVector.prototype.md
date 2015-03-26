ImmutableVector.prototype
-------------------------

This prototype object allows easy access to various helpful built-in methods for manipulating an [ImmutableVector](ImmutableVector.md).

### ImmutableVector ( ...items )

Returns an `ImmutableVector` using an optional iterable in a similar way to the `Array` constructor except it cannot be called with `new`. It is not constructable.

Note: The `Array` constructor has a `Array(length)` but we don't need an equivalent here because an `ImmutableVector` cannot have holes and prespecifying a length has no meaning. Therefore the call `ImmutableVector(123)` returns a single element vector with the first value being `123`.

### Indices and .length

Accessing index properties (e.g. `vector[index]`) and `vector.length` behaves in a similar way as for strings that are also value types with indexable properties. Except the element value is returned for the index, rather than a new string.

### ImmutableVector.prototype.copyWithin (target, start [ , end ] )

Creates a new `ImmutableVector` with the same values except it copies the sequence of elements within the array-like object or vector to the position starting at target. Note: It returns a new `ImmutableVector`, it doesn't mutate the original vector.

### ImmutableVector.prototype.fill (value [ , start [ , end ] ] )

Fills all the elements of an array-like object or vector from a start index to an end index with a value. Note: It returns a new `ImmutableVector`, it doesn't mutate the original vector.

### ImmutableVector.prototype.pop ( )

Returns a new `ImmutableVector` with a excluding the last index in `this`. Note: It does not mutate the original vector. This differs from its `Array` equivalent because it returns the new `ImmutableVector` rather than the removed value. Use `vector[vector.length - 1 ]` to get the last value.

### ImmutableVector.prototype.push ( ...items )

Returns an `ImmutableVector` with all the elements of the original array-like object and with each `item` added to the end of the vector. Note: It does not mutate the original vector. Unlike its `Array` equivalent, it returns a new `ImmutableVector`. It does not return the new `length`. That use case have to be a separate operation to get `vector.length`.

### ImmutableVector.prototype.reverse ( )

Returns a `ImmutableVector` with all the elements of the original array-like object or vector, in the reverse order of the original vector.

### ImmutableVector.prototype.shift ( )

Returns an `ImmutableVector` with a length ones less than `this`, excluding the first index, shifting all other values to a lower index. Note: this differs from its `Array` equivalent because it returns a new `ImmutableVector` rather than the removed value. Use `vector[0]` to get the first value.

### ImmutableVector.prototype.splice (start [, deleteCount [ , ...items ] ] )

Changes the content of an array by removing existing elements and/or adding new elements. Note: It does not mutate the original array-like object. It returns the new `ImmutableVector`. Note: Unlike its `Array` equivalent, it does not return the removed items. That use case can be solved by calling `slice` on the original vector, either before or after.

### ImmutableVector.prototype.sort ([comparefn])

Returns a `ImmutableVector` with all the elements of the original array-like object or vector, sorted according to the `compareFn`. Note: This is .

### ImmutableVector.prototype.unshift ( ...items )

Adds one or more elements to the beginning of an array. Note: It does not mutate the original vector. Unlike its `Array` equivalent, it returns a new `ImmutableVector`. It does not return the new `length`. That use case have to be a separate operation to get `vector.length`.

## TLDR

The rest of these are just what you would expect and has similar semantics as the mutable `Array`, except they return an `ImmutableVector` for operations like `filter`, `map` etc. It is plausible that these methods are not needed and that they could just go on iterables as part of a more generic combinators API.

### ImmutableVector.prototype.concat ( ...arguments )
### ImmutableVector.prototype.constructor
### ImmutableVector.prototype.entries ( )
### ImmutableVector.prototype.every ( callbackfn [ , thisArg] )
### ImmutableVector.prototype.filter ( callbackfn [ , thisArg ] )
### ImmutableVector.prototype.find ( predicate [ , thisArg ] )
### ImmutableVector.prototype.findIndex ( predicate [ , thisArg ] )
### ImmutableVector.prototype.forEach ( callbackfn [ , thisArg ] )
### ImmutableVector.prototype.indexOf ( searchElement [ , fromIndex ] )
### ImmutableVector.prototype.join (separator)
### ImmutableVector.prototype.keys ( )
### ImmutableVector.prototype.lastIndexOf ( searchElement [ , fromIndex ] )
### ImmutableVector.prototype.map ( callbackfn [ , thisArg ] )
### ImmutableVector.prototype.reduce ( callbackfn [ , initialValue ] )
### ImmutableVector.prototype.reduceRight ( callbackfn [ , initialValue ] )
### ImmutableVector.prototype.slice (start, end)
### ImmutableVector.prototype.some ( callbackfn [ , thisArg ] )
### ImmutableVector.prototype.toLocaleString ( [ reserved1 [ , reserved2 ] ] )
### ImmutableVector.prototype.toString ( )
### ImmutableVector.prototype.values ( )
### ImmutableVector.prototype [ @@iterator ] ( )

## Not Needed

There is no need for an equivalence to `Array.of ( ...items )` and `Array.from` because `ImmutableVector` cannot be subclassed and it is unobservable if a copy or the same one is returned.
