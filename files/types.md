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

# Pointer 

# Function 

# Inerface

# Map

# Channel