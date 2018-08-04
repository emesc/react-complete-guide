## React 16 Complete Guide
by Max S

### Setup
`package.json` lists all the dependencies (like Gemfile)
`rc` means release candidate
`react-scripts` package offering all the build workflow, the development server, the next gen js feature for support and all the things we'll be using for the project 

`scripts` are scripts that can be run with `npm run <script_name>`
- `start` starts the server, compiles our code, optimizes the code
- `build` when you're ready for deploying your app which optimises it even more, not launch a development server but instead get your optimised code stored in a folder. because now you won't see your compiled code anywhere, it all happens in memory

`node-modules` dir holds all the dependencies and sub-dependencies of our project

`public` dir is the root folder that gets served by the server in the end
- holds the html file that's the SPA
- you don't need to add more html, all you need is a workflow

script files are in the `source` folder

`manifest.json` because create-react-app gives us a progressive web app out of the box, where we can define some metadata out of our application

### Details
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

Pseudoselector
  - in CSS, means a selector based on another selector as indicated by the :

`npm install --save`
  - also saves an entry in `package.json` so we also fix the version number and easily share our project

CSS Loader
  - transforms CSS code in the css file to an object we can use in the js file

Higher-order Component
  - any component that wraps other component, eg, with the goal of handling any errors

Key
  - always has to be in the outer element in a map method, because that's the element we actually replicate
