# Class Constructor Super

`super()` is only needed in an ES6 class when using a constructor function in the react component. `super()` is used to initialize `this` inside constructor.

```
class Component extends React.component {
  constructor() {
    console.log(this) //Error: 'this' is not allowed before super()
  }
}
```

When accessing `this.props` inside a constructor, the `props` must be passed into the constructor method as well as inside `super` itself.

```
class Component extends React.component {
  constructor(props) {
    super()
    console.log(this.props) // this.props is undefined
  }
}
```
[source](http://cheng.logdown.com/posts/2016/03/26/683329)
