# React Component Lifecycle

## ComponentWillMount

This is called right before the component appears on screen. Because the
component isn't loaded to the DOM, there is not much that can be done. The
component's constructor was already called before this.  

The only thing that usually needs to be done here is connecting to an external API, like firebase.
Typically this is done at the root component though, so it's not often called
inside child components.

## ComponentDidMount

This is where you will load any data via AJAX, draw on a `<canvas>` element or
add event listeners.  `componentDidMount` is where you do all the set up you
couldn't do without the DOM in `componentWillMount`.

## ComponentWillRecieveProps

Called whenever a new stream of props arrives to the component.  This function
has access to both the current props, via `this.props` and the incoming props
via `nextProps`.  Use this to check which props are changed (sometimes none) and
if the props have changed, acted on other changes needed throughout the
component.

One thing to note, `componentWillRecieveProps` is not called on initial render.

## ShouldComponentUpdate

This function recieves both the `nextProps` and the `nextState` and must return
a `boolean`.  If `shouldComponentUpdate` returns `true`, then the component is
updated and re-rendered. If the function returns false then the component is not
changed.  By default `shouldComponentUpdate` returns `true`.  This function is a
great place to improve performance and prevent unecessary re-rendering.

## ComponentWillUpdate

Functions the same as `componentWillReceiveProps`, except `componentWillUpdate`
is not allowed to call `this.setState`.  Typically used in conjunction with
`shouldComponentUpdate` and the component is not using
`componentWillRecieveProps`.

## ComponentDidUpdate

This function can do everything `componentDidMount` does, like redrawing a
canvas or reseting a layout.  However `componentDidUpdate` doesn't know why the
component updated.  As a result this is where you can save have some performance
gains if the component is receiving more props than needed. It's most often used
to update the DOM in response to prop or state changes.

## ComponentWillUnmount

Function called before the is removed from the DOM.  `componentWillUnmount` is
used to cancel any outgoing network requests, remove event listeners. This
function is for cleaning up the component before it disappears.


