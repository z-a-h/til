# Redux Overview

Redux is a 'predictable state container' for JavaScript apps. In plain english, Redux is a library for managing state.

The three principles of Redux are:
  1. There is a single source of truth for application state
  2. State is read-only
  3. Changes to state can only be made via pure functions


The three principles are implemented via three abstractions.
  1. The Store is the single source of truth.
  2. Actions are objects that describe what you can do in your application. Actions are dispatched to trigger changes.
  3. Reducers are pure functions that take in the current state and an action as inputs and returns the next state.
