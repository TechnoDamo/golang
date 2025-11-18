A declaration binds a *non-blank identifier* to a **constant**, **type**, **type parameter**, **variable function**, **label** or **package**. <br/>

The blank identifier and init function do not introduce new bindings. 

**Scope** of an identifier is the region of the code where that identifier can be used to refer to the same entity (variable, function, struct, etc.) that it was declared to represent.

---add about scoping

# Label scope 
In Go, **labels** are identifiers used to mark specific points in code, primarily for control flow with *break*, *continue*, and *goto* statements. 

# Blank identifier
The *blank identifier* - _, serves as an anonymous placeholder instead of regular non-blank identifier. 

# Predeclared identifiers 
 The following identifiers are implicitly declared in the universe block [Go 1.18] [Go 1.21]:
```go
Types:
	any bool byte comparable
	complex64 complex128 error float32 float64
	int int8 int16 int32 int64 rune string
	uint uint8 uint16 uint32 uint64 uintptr

Constants:
	true false iota

Zero value:
	nil

Functions:
	append cap clear close complex copy delete imag len
	make max min new panic print println real recover
```

# Exported identifiers
An identifier may be exported to permit access to it from another package. <br>
An identifier is exported if both: <br/>
    1. the first charachter is Unicode uppercase <br/>
    2. the identifier is declared in the package block or it is a field name or method name 
```go
package mypackage

// These can be exported
var GlobalVar int = 42          // Unexported
const GlobalConst = "hello"     // Unexported  
type MyStruct struct {          // Exported!
    ExportedField   int         // Exported field
    unexportedField string      // Unexported field
}

func ExportedMethod() {}        // Exported!
func unexportedMethod() {}      // Unexported
package mypackage

func SomeFunction() {
    var localVar int           // Never exported (local scope)
    type localType struct{}    // Never exported (local scope)
}
```

# Uniqness of identifiers
Two identifiersare different if they are spelled differently, or if they appear in different packages and are not exported. Otherwise, they are the same. 

# Constant declarations 
```go
const (
        Sunday = iota  // 0
        Monday         // 1 (repeats previous expression: iota)
        Tuesday        // 2
        Wednesday      // 3
        Thursday       // 4
        Friday         // 5
        Saturday       // 6
        numberOfDays   // 7 (unexported)
    )
```

# Iota
Within a constant declaration, the predeclared identifier *iota* represents successive untyped integer constants. 
```go
const (
	c0 = iota  // c0 == 0
	c1 = iota  // c1 == 1
	c2 = iota  // c2 == 2
)

const (
	a = 1 << iota  // a == 1  (iota == 0)
	b = 1 << iota  // b == 2  (iota == 1)
	c = 3          // c == 3  (iota == 2, unused)
	d = 1 << iota  // d == 8  (iota == 3)
)

const (
	u         = iota * 42  // u == 0     (untyped integer constant)
	v float64 = iota * 42  // v == 42.0  (float64 constant)
	w         = iota * 42  // w == 84    (untyped integer constant)
)

const x = iota  // x == 0
const y = iota  // y == 0
```

# Type declarations 
A type declaration bind an identifier, the type name, to a type. 
## Alias declarations
An alias declaration binds an identifier to the given type [Go 1.9].
```go
package main

import "fmt"

// Basic type aliases
type MyInt = int
type MyString = string
type MyFloat = float64
var x MyInt = 42
var s MyString = "hello"
var f MyFloat = 3.14
```
* generic alias
## Type definitions
A type definition creates a new, distinct type with the same underlying type and operations as the given type and binds an identifier, the *type name*, to it.
```go
// Basic type definitions (create new distinct types)
type Celsius float64
type Fahrenheit float64
type Kelvin float64
```
# Type parameter declarations
```go
// Function with type parameters
func FunctionName[T constraint](param T) T {
    // ...
}

// Type with type parameters
type TypeName[T constraint] struct {
    field T
}
```
## Type constraints
## Satisfying a type constraint

# Variable declarations 
```go
var i int
var U, V, W float64
var k = 0
var x, y float32 = -1, -2
var (
	i       int
	u, v, s = 2.0, 3.0, "bar"
)
var re, im = complexSqrt(-1)
var _, found = entries[name]  // map lookup; only interested in "found"
```

# Short variable declarations 
```go
i, j := 0, 10
f := func() int { return 7 }
ch := make(chan int)
r, w, _ := os.Pipe()  // os.Pipe() returns a connected pair of Files and an error, if any
_, y, _ := coord(p)   // coord() returns three values; only interested in y coordinate
```

# Function declarations 
A function declaration binds an identifier, the *function name*, to a function. <br/>

# Method declarations 
```go
package main

import "fmt"

type Calculator struct {
    result int
}

// Method with value receiver
func (c Calculator) Add(a, b int) int {
    return a + b
}

// Method that modifies receiver (pointer receiver)
func (c *Calculator) AddAndStore(a, b int) {
    c.result = a + b
}

// Method accessing struct fields
func (c *Calculator) GetResult() int {
    return c.result
}
```