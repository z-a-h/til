# Infix Functions

Infix functions are functions where the function name is between the parameters as opposed to prefix functions where the function is named before the parameters.


Prefix function
```
var result = add(1,2)
```

Infix function
```
var result = 1 + 2
```

Elm automatically considers functions named with non alpha-numeric characters as infix functions.

```
(~+) a b =
  a + b + 0.1
```

To create an alpha-numeric infix function you wrap the function name by wrapping the call in back ticks
```
result =
  1 `add` 2
```

Non alpha-numeric named infix functions can also be called as prefix functions by wrapping the function name in parenthesis
```
result =
  (~+) 1 2
```
