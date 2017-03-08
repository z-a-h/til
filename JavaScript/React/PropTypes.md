# PropTypes

React has built-in typechecking abilites to prevent the spread of bugs.
To run a typechecking on the props of a component, assign the `propTypes` property.

```class HelloWorld extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.world}</h1>
      )
  }
}

HelloWorld.propTypes = {
  world: React.PropTypes.string
}
```

When an invalid datatype is passed into a prop, a warning is logged in the console.
However, `propTypes` is only run in development mode.

[source](https://facebook.github.io/react/docs/typechecking-with-proptypes.html)
