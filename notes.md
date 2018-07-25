Component
  - need to still import React because the component has to be transformed to a React.createElement
  - is a function returning some jsx
  - if a function, you don't need to import { Component }, just `import React from 'react'`

Children
  - refers to any elements (including plain text) between opening and closing tags

Property
  - a class has properties (which can be a variable of a class)

State
  - is a property that can be changed which will trigger react to re-render the DOM
  - only works in components which `extends Component`
  - `this` inside a class (eg, `this.state`) refers to the class itself

Event Handling
  - `*handler()` is a function name to indicate it's not a method you're actively calling, but you're assigning as an event handler
  - eg, `switchEventHandler = () => {}` is a property which holds a function which can be executed then in onClick, `this.switchEventHandler` without () because we only want to pass a reference (to the property which holds the function), we don't want to execute it immediately once react renders it to the DOM

Functional (STATELESS) Component
Class (STATEFUL) Component aka Container

Passing method references between components
  - can pass methods also as props so you can call a method which might change the state in another component which doesn't/shouldn't have direct access to the state
  - eg, you can pass down `clickHandler`s which allow you to change data in the parent component

<input>
  - react/js passes the event object, like <button>
  - `event.target.value` where target is the input in which we type, value is the value the user entered

Two-way binding (eg for <input>)
  1. when we change it, we want to propagate that change so that we can update the state
  2. we also want to see the current state right from the start

render()
  - everything inside, not just `return` gets executed during render/re-render

`click = {() => this.deletePersonHandler(index)}` or
`click = {this.deletePersonHandler.bind(this, index)}`

`#splice(index, numberOfElements)`

```
const persons = this.state.persons
persons.splice(personIndex, 1)
this.setState({persons: persons})
```
persons was a constant then spliced but arrays & objects are referenced types so it's only holding a pointer, the element it was pointing to can be changed

Spread operator
- `const persons = this.state.persons.slice()`
  - #slice without args, simply copies the persons array or better yet:
- `const persons = [...this.state.persons]`
  - spread operator simply makes a new array out of the array you're spreading

