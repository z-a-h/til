# Forward Pipe Operator

The forward pipe operator is useful for partial application of functions (currying) as well as chaining functions together.

It allows you to pass the results of the expression on the left side of the operator to the expression on the right side.

Given the below function
```
add a b =
    a + b
```
This is an example without using the pipe operator

```
result =
  add (add 1 2) 3
```

which is equivalent to

```
result =
  add 1 2 |> add 3
```
which evaluates to

```
result =
  add 1 2 |> (b -> 3 + b)
```