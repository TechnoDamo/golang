Type determines a set of values together with operations and methods specific to those values. 

# Boolean 
A *boolean type* represents the set of Boolean truth values denoted by the predeclared constants *true* and *false*. <br>
The predeclared boolean type is **bool**, a defined type.

# Numeric
*Integer*, *floating-point* and *complex* types are collectively called *numeric* types.

The predeclared architechture-independent numeric types:
```go
uint8       // the set of all unsigned  8-bit integers (0 to 255)
uint16      // the set of all unsigned 16-bit integers (0 to 65535)
uint32      // the set of all unsigned 32-bit integers (0 to 4294967295)
uint64      // the set of all unsigned 64-bit integers (0 to 18446744073709551615)

int8        // the set of all signed  8-bit integers (-128 to 127)
int16       // the set of all signed 16-bit integers (-32768 to 32767)
int32       // the set of all signed 32-bit integers (-2147483648 to 2147483647)
int64       // the set of all signed 64-bit integers (-9223372036854775808 to 9223372036854775807)

float32     // the set of all IEEE 754 32-bit floating-point numbers
float64     // the set of all IEEE 754 64-bit floating-point numbers

complex64   // the set of all complex numbers with float32 real and imaginary parts
complex128  // the set of all complex numbers with float64 real and imaginary parts

byte       // alias for uint8
rune       // alias for int32
```

The pedeclared architechture-dependent numeric types:
```go
uint     // either 32 or 64 bits
int      // same size as uint
uintptr  // an unsigned integer large enough to store the uninterpreted bits of a pointer value
```

# String 
A *string* type represents the set of string values. <br/>
A *string value* is a (possibly empty) sequence of bytes. <br/> 
*Length of a string* equal to the amount of bytes. <br/>
Strings in Go are *immutable*. Hence &s[i] is invalid.


# Array
An *array* is a numbered sequence of elements of a single type, called the element type. 
Array types are always one-dimentional but may be composed to form multi-dimensional types.
```go
[32]byte
[2*N] struct { x, y int32 }
[1000]*float64
[3][5]int
[2][2][2]float64  // same as [2]([2]([2]float64))
```
# Slice 
A *slice* is a descriptor for a contiguous segment of n *underlying array* and provides access to a numbered sequence of elements from that array. <br/>

A slice, once initialized, is always assosiated with an underlying array that holds its elements and therefore shares its storage. <br/>

Length and capacity of a slice: <br/>
```go
arr := [6]int{1, 2, 3, 4, 5, 6}
slice := arr[1:4]  // [2, 3, 4]

fmt.Println(len(slice)) // 3 - elements currently in slice
fmt.Println(cap(slice)) // 5 - from position 1 to end of array
```

We can also create slice with the following syntax: <br/>
```go
make([]T, length, capacity)
```
which is equivalent to: <br/>
```go
make([]int, 50, 100)
new([100]int)[0:50]
```
# Struct 
A struct is a sequence of named elements, called **fields**, each of which has a *name* and a *type*. <br/>
Field names may be specified **explicitly** (*IdentifierList*) or **impicitly** (*EmbeddedField*). <br/>
When we embed one struct into another, fields of the embedded struct become **promoted**, meaning we can access them directly from the outer struct. 
```go
// explicit spec
type Person struct {
    Name    string  // Explicit field name "Name"
    Age     int     // Explicit field name "Age"  
    Address string  // Explicit field name "Address"
    _ string - used for padding
}
// implicit spec
type Address struct {
    Street  string
    City    string
}

type Person struct {
    string  // Implicit field name: "string"
    int     // Implicit field name: "int" 
    Address // Implicit field name: "Address" (embedded struct)
}

p := Person{
    string: "John",  // Using implicit field name
    int:    30,
    Address: Address{...},
}
fmt.Println(p.string)  // Access via implicit name
fmt.Println(p.City)    // Promoted field from embedded Address
```

# Pointer 
A *pointer type* denotes the set of all pointers to variables of a given type (*base type*).<br/>
The value of an unitialized pointer is **nil**. <br/>

The type ***\*int*** represents all possible memory addresses that could point to integer variables. <br/>
For **\*int** the *base type* is **int**, the type pointed to.

# Function 
A *function type* denotes the set of all functions with the same parameter and result types. <br/>
The value of an uniniiaized variable of function type is nil. <br/>

Within a list of parameters or results, the names (IdentifierList) must either all be present or all be absent. <br/>
If *present*, all non-blank values in the signature must be unique. If absent - each type stands for one item of that type.<br/> 

The final incoming parameter in a function signature may have a type prefixed with .... A function with such a parameter is called **variadic** and may be invoked with zero or more arguments for that parameter. 
```go
func()
func(x int) int
func(a, _ int, z float32) bool
func(a, b int, z float32) (bool)
func(prefix string, values ...int)
func(a, b int, z float64, opt ...interface{}) (success bool) // vardiac
func(int, int, float64) (float64, *[]int)
func(n int) func(p *T)
```

# Interface
An interface type defines a *type set*. <br/>
A variable of interface type can store a value of any type from that *type set*. <br/> 
Types from the *type set* are said to **implement the interface**.
The value of an unitialized interface is *nil*.


## Basic interfaces
## Embedded interfaces
## General interfaces

# Map
A map is an unordered key-value group of elements.
The value of an uninitialized map is *nil*.
```ebnf
MapType = "map" "[" KeyType "]" ElementType .
```

The *comparison operators* == and != must be fully defined for operands of the key type (so not a function, map or slice), otherwise a runtime panic will be caused.

The number of map elements is called its **length**, and can be discovered with the len() function. 
```go
fmt.Println(len(scores)) // Output: 3
```
Elements can be added using assignments and retrieved with index expressions.
```go
// assignment
scores["Charlie"] = 92
// retrieving
fmt.Println(scores["Alice"]) // Output: 92
// checking key existense, ok is boolean
value, ok := scores["Eve"]
```
Elements may be removed with **delete** and **clear** functions.
```go
// removing a specific key with delete
delete(scores, "Bob")
// remove all keys (from Go 1.21)
clear(scores) 
```

New map is created with the **make** function.
```go
m := make(map[string]int)
m := make(map[string]int, 100) // just an optimization hint
// we can also initialise it with values
scores := map[string]int{
    "Alice": 95,
    "Bob":   89,
    "Eve":   76,
}
```

# Channel