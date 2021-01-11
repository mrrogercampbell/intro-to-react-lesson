# Learning React: Props, State, and Hooks
In this lesson we will walk-through how to instantiate and utilize React `Props`, `State`, and `Hooks`

### Table of Content
- [Learning React: Props, State, and Hooks](#learning-react-props-state-and-hooks)
    - [Table of Content](#table-of-content)
  - [Create React App](#create-react-app)
  - [Props and State](#props-and-state)
    - [Props](#props)
    - [Prompt 1: Create a React Project](#prompt-1-create-a-react-project)
    - [`Class` Component Rendering Props](#class-component-rendering-props)
    - [Deconstructing Props in a Class Component](#deconstructing-props-in-a-class-component)
    - [`Function` Component Rendering Props](#function-component-rendering-props)
    - [Deconstructing Props in a Function Component](#deconstructing-props-in-a-function-component)
    - [Prompt 2: Working with Props](#prompt-2-working-with-props)
  - [State](#state)
    - [Rendering State](#rendering-state)
    - [Deconstructing State](#deconstructing-state)
    - [Passing State and Rendering it as Props](#passing-state-and-rendering-it-as-props)
    - [Passing State: Syntax Sugar](#passing-state-syntax-sugar)
    - [Prompt 3: Working with State](#prompt-3-working-with-state)
  - [React Hooks Basics](#react-hooks-basics)
    - [Prompt 4: React Hook Basics](#prompt-4-react-hook-basics)

## Create React App
`Create React App` is a standalone tool that generates and runs a new `React` project utilizing `npm` or `yarn` with just a couple of commands.

Having trouble remembering how to use `create-react-app`?
Heres a quick guide to creating a new `React` project:
1. Open your terminal
2. Transverse to the directory you would like to create your `React` project inside of.
   - ie: `cd ~/code-differently/projects/`
3. Type `npx create-react-app <provide-a-name-for-your-project>
4. Hit enter

Once `create-react-app` finishes its work you will need to `cd` into the project you created; ie `cd ./<provide-a-name-for-your-project>.

Still a little hazy on what exactly `Create React App` is doing? Check out this awesome [article](https://www.sitepoint.com/create-react-app/) which breaks it all down step by step and gives you a peak under the hood.

## Props and State
`Props` and `State` are what allow you to display and store data within a `React` application. `Props` are a `immutable` data object which can be rendered by components. Whereas `State` stores data about a component that can be changed by things such as user events, data subscriptions, and more.

### Props
**Key Takeaways**:
- `Props` is short for `properties`
- `Props` are variables which store data
- `Props` are `immutable`, meaning their value can not be changed
- `Props` are passed into a component by its `parent` component

### Prompt 1: Create a React Project
[Prompt 1](Prompts/Prompt1.md)


### `Class` Component Rendering Props
```jsx
// App.js
import React, { Component } from 'react';

class Greeting extends Component {
  constructor(props) {
    super(props)
  }
  render() {
    return (
      <div>
        <h1>I am {this.props.name}.... I am {this.props.name}!</h1>
      </div>
    );
  }
}


class App extends Component {
  render() {
    return (
      <div>
        <Greeting name={"Groot"} />
      </div>
    );
  }
}

export default App;
```
### Deconstructing Props in a Class Component
Rather than working with the `props` variable you can deconstruct your `props` right before your class returns its `JSX`.

```jsx
// App.js
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    let { name } = this.props
    return (
      <div>
        <h1>I am {name}.... I am {name}!</h1>
      </div>
    );
  }
}


class App extends Component {
  render() {
    return (
      <div>
        <Greeting name={"Groot"} />
      </div>
    );
  }
}

export default App;
```
You might also notice that in the above example we no longer declare a `constructor`. In reality when your code complies `React` does utilize the `constructor` but it is an explicit action so we do not need to write it. We would need a `constructor` if we were going to store the `props` in state. Which we will look at in a bit.

### `Function` Component Rendering Props
```jsx
// App.js
import React from "react";

const Greeting = props => {
  return (
    <div>
      <h1>
        I am {props.name}.... I am {props.name}!
      </h1>
    </div>
  );
};

const App = props => {
  return (
    <div>
      <Greeting name={"Groot"} />
    </div>
  );
};

export default App;
```
### Deconstructing Props in a Function Component
Rather than working with the `props` variable you can deconstruct all of your `props` right in your functions initial declaration

```jsx
// App.js
import './App.css';

const Greeting = ({ name }) => (
  <div>
    <h1>I am {name}... I am {name}!!!</h1>
  </div>
)

function App() {
  return (
    <div className="App">
      <Greeting name={'Groot'} />
    </div>
  );
}

export default App;
```

### Prompt 2: Working with Props
[Prompt 2](Prompts/Prompt2.md)


## State
Key Takeaways:
- `State` is a JavaScript object which is defined in the constructor of a `Class` component
- `State`is meant to hold data for a component
- You define properties within `state` which in turn can be accessed and rendered within a component
- A parent component can pass it's own `state` to a child component in the form `props`

### Rendering State
Build a `Class` component that renders `state`.

Example:
```jsx
// App.js
import React, { Component } from 'react'

class App extends Component {
  constructor() {
    super();
    this.state = {
      name: "Luke",
      courseName: "How to use a lightsaber while blindfolded"
    }
  }

  render() {
    return (
      <div>
        <h1>Hello {this.state.name}!</h1>
        <h2>Welcome to the course: {this.state.courseName}!</h2>
      </div>
    )
  }
}
export default App
```

### Deconstructing State
Similar to how we were able to deconstruct our `props` we can deconstruct our `state` and make our code more concise.
```jsx
// App.js
import React from "react"

class App extends React.Component {
  constructor() {
    super();
    this.state = {
      name: "Luke",
      courseName: "How to use a lightsaber while blindfolded"
    }
  }

  render() {
    const { name, courseName } = this.state
    return (
      <div>
        <h1>Hello {name}!</h1>
        <h2>Welcome to the course: {courseName}!</h2>
      </div>
    )
  }
}
export default App
```

### Passing State and Rendering it as Props
Same as we were able to pass static data from a parent component to a child we can pass a parent component's state to its child.
```jsx
// App.js
import React from "react";

const CourseDetails = ({ name, courseName }) => (
  <div>
    <h1>Hello {name}!</h1>
    <h2>Welcome to the course: {courseName}!</h2>
  </div>
)

class App extends React.Component {
  constructor() {
    super();
    this.state = {
      name: "Luke",
      courseName: "How to use a lightsaber while blindfolded"
    };
  }

  render() {
    const { name, courseName } = this.state
    return (
      <div>
        <CourseDetails name={name} courseName={courseName} />
      </div>
    );
  }
}
export default App;
```
### Passing State: Syntax Sugar
You can make your code more concise by doing the following:
```jsx
// App.js
import React, { Component } from 'react';

const CourseDetails = ({ name, courseName }) => (
  <div>
    <h1>Hello {name}!</h1>
    <h2>Welcome to the course: {courseName}!</h2>
  </div>
)

class App extends Component {
  constructor() {
    super();
    this.state = {
      name: "Luke",
      courseName: "How to use a lightsaber while blindfolded"
    };
  }

  render() {
    return (
      <div>
        <CourseDetails {...this.statea} />
      </div>
    );
  }
}
export default App;
```
Rather than declaring each property within `state` that we want to pass down, we are able to use the `spread` operator and pass down all of the data within our `state` object at once and our child component is able to still deconstruct the data at put it to use.

### Prompt 3: Working with State
[Prompt 3](Prompts/Prompt3.md)

## React Hooks Basics
React Hooks allow us to instantiate `state` react in `Function` component.

Lets start by creating a `Class` component which displays some data that is stored in its `state`
```jsx
// App.js "Class Component"

import React, { Component } from 'react';

class App extends Component {
  constructor() {
    super();
    this.state = {
      name: "Grogu"
    }
  }
  render() {
    let { name } = this.state
    return (
      <div>
        <h1>Use the force {name}!!</h1>

      </div>
    );
  }
}

export default App;
```

Now lets convert our `Class` component into a `Function` component with state:
```jsx
// App.js "Function Component"
import React, { useState } from "react";

const App = () => {
  const [name, setName] = useState('Grogu')

  return (
    <div>
      <h1>Use the force {name}!!</h1>
    </div>
  )
}
export default App
```
`useState` is a `Hook`. When invoked it allows us to instantiate local `state` inside a `Function` component. `useState` returns two values:
    1. The `Current State`: which is `name` in the example above
    2. A `function` which allows you to update the `Current State`

For now we are only going to focus on utilizing the `Current State`.

### Prompt 4: React Hook Basics
[Prompt 4](Prompts/Prompt4.md)