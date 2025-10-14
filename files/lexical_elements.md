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


# Integer literals

# Floating-point literals

# Imaginary literals

# Rune iterals 

# String literals

