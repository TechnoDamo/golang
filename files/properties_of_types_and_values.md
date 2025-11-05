# Representation of values
Values of predeclared types (interfaces any, error, arrays and structs) are **self-contained**, meaning each of such value contains a complete copy of all its data, and vars of such type store the entire value. <br/>
The repective zero values are specific to value's types and are never *nil*.

Non-nil pointer, function, slice, map and channel values contain references to underlying data which my be shared by multiple values:
- A **pointer** value is a reference of a var, holding the pointer base value
- A **function** value contains references to the function (possibly anonymous) and enclosed vars 
- A **slice** value contains the slice length, capacity and a reference to its underlying array
- A **map** or **channel** value is a reference to the implementation-specific data structure.

An *interface* value may or may not be self-contained depending on the interface's *dynamic type*. <br/>
For types that can contain references - *nil* os zero value.
# Underlying types
Every type has an *underlying type* (for predeclared ones it is the type itself).

# Type identity
Two types are either *identical*("the same") or *different*.

A *named type* is always different from any other type.<br/>
Otherwise, two types are identical if their underlying type literals are equivalent. 

# Assignability
Values are assignable to variables only if they meet certain conditions.

# Representability


# Method sets 
The **method set** of a type determines the methods that can be called on an operand of that type. <br/>
Every type has a (possibly empty) method set.


