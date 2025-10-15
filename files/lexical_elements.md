# Comments
// - single line comment <br>
/* ... */ - multiline comment <br>

# Tokens
Tokens form the vocabulary of the Go language. <br>
There are four classes:
- identifiers
- keywords
- operators
- punctuation
- literals

# Semicolons
Semicolons should be used only when putting multiple statements on one line, in other cases you may not use them, and it is advised not to.
```go
// Example - no semicolons needed
if x > 10 { return true }
if x > 10 {
    return true
}
result := calculate(a, b, c)
// Example - semicolons needed
x := 5; y := 10
if x > 0 { return x }; return y
```

# Identifiers
Identifier is a saquence of one or more letters/digits *(first char is a letter)* for naming program entities such as variables, types etc.

Some identifiers are predeclared.

# Keywords
The following keywords are reserved and may not be used as identifiers.
```go
break        default      func         interface    select
case         defer        go           map          struct
chan         else         goto         package      switch
const        fallthrough  if           range        type
continue     for          import       return       var
```

# Operators and punctuation
```go
+    &     +=    &=     &&    ==    !=    (    )
-    |     -=    |=     ||    <     <=    [    ]
*    ^     *=    ^=     <-    >     >=    {    }
/    <<    /=    <<=    ++    =     :=    ,    ;
%    >>    %=    >>=    --    !     ...   .    :
     &^          &^=          ~
```
These charachter sequences represent operators and punctuation (added in Go 1.18).

# Integer literals
```go
// Decimal literals
42          // Simple decimal
4_2         // Same as 42 (underscore for readability)
1_000_000   // One million (easier to read than 1000000)
0           // Decimal zero (not octal!)
100         // One hundred

// Binary literals (from Go 1.13)
0b1010      // 10 in decimal
0B1100      // 12 in decimal (capital B)
0b1000_0001 // 129 in decimal
0b_1001     // 9 in decimal (underscore after prefix)

// Octal literals
0600        // 384 in decimal (old-style octal)
0o600       // 384 in decimal (new-style with 'o')
0O600       // 384 in decimal (capital O)
0o_755      // 493 in decimal (file permission style)
0_600       // 384 in decimal (old-style with underscore)

// Hexacademical literals
0xBadFace           // 195951310 in decimal
0xBad_Face          // Same value, more readable
0x_67_7a_2f_cc_40_c6 // With multiple underscores for grouping
0xFF                // 255 in decimal
0xCAFE_BABE         // Common pattern in programming

// Wrong examples
/* These would cause compilation errors:
    _42        // ERROR: underscore at start makes it an identifier
    42_        // ERROR: underscore at end
    4__2       // ERROR: consecutive underscores
    0_xBadFace // ERROR: underscore between prefix and digits
    0b         // ERROR: no digits after prefix
    0x_        // ERROR: no digits after underscore
}
*/
```

# Floating-point literals
Floating-point literal is a decimal or hexacademical representation of a *floating-point constant*.

Decimal floatin-point literal consists of:
- 1. Integer part *(decimal digits)*
- 2. Decimal point *(decimal digits)*
- 3. Fractional part *(decimal digits)*
- 4. Exponent part *(t or E followed by an original sign and decimal digits)*

Some parts may be elidied.
```go 
// Basic forms
0.          // == 0.0
72.40       // 72.4
2.71828     // Euler's number
.25         // 0.25 (integer part elided)
1E6         // 1000000 (fractional part elided)

1.e+0       // == 1.0
6.67428e-11 // Gravitational constant
.12345E+5   // 12345.0
1.5e2       // 150.0 (1.5 × 10²)
2e-3        // 0.002 (2 × 10⁻³)
```
There are also rules for hexacademical ones. 

# Imaginary literals
An imaginary literal represents the imaginary part of a complex constant. 
```go
3 + 4i           // Complex number: 3 real, 4i imaginary
2.5i             // Pure imaginary: 2.5i
0i               // Zero imaginary part
1.e+0i           // 1.0i with exponent
0x1p-2i          // Hexadecimal float: 0.25i
0123i            // 123i (decimal, not octal!)
0o123i           // 83i (explicit octal)
1_000i           // 1000i with underscore
complex(2, 3)    // 2 + 3i using function
var z = 5 + 0i   // Real number as complex
```

# Rune iteralcs 
Rune literal is a [rune constant](https://go.dev/ref/spec#Constants), an integer value identifying a Unicode code point.

# String literals
A string literal represents a [string constant](https://go.dev/ref/spec#Constants) obtained from concatenating a sequence of charachters. 
There are two forms:
- 1. Raw (``) - can be multiline, doesn't understand special chars.
- 2. Interpreted ("") - can't be multilne, understands special chars.
