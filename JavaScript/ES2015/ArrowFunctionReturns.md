# Arrow Function Returns

If an arrow function only contains a single return statement, you can replace the body of the arrow function with just that value.
If the function returns an object, be sure to wrap the object in parens so the function doesn't confuse it for a statement block
```
const arrowFunc = () => {
  return {
    object: 'property'
  }
}

const arrowFunc = () => ({
  object: 'property'
})
```
