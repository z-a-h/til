#Overview

The Drag n Drop library is built on-top of the HTML5 drag and drop API.
However it doesn't work with touch screens, so it's possible to plug in a custom API for touch events.

## Items
Items are JS objects that describe the component being dragged. This keeps the components decoupled from the dragged data.

## Types
Types are classes or groups of items. In an trello app, you could have classes that are Cards, Lists, Boards.
Types make it easy to specify drag sources and trop targets for each type.

## Monitors
Monitors are used to update the properties of a component when the drag and drop state changes.

## Connectors
Connectors are used to assign a predefined roles (drag source, drag preview, drop target) to a DOM node in the render function


## Drag Sources
Abstraction that is registered for a specific type and implements a method for producing an item from the components props.

## Drop Targets
Abstraction that handles its hover or drop for types
