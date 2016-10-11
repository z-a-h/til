# Local Variables

Local variables can be defined in a function by using a `let` code block. The variable is then used inside of the `in` block, following the `let` block.

For example, the code below assings a local variable of localCount inside the increment function.

```
increment cnt amt =
  let
    localCount =
      cnt
  in
    localCount + amt
```