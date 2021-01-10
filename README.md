Outline:
- Dev Tools:
  - Git Bash
  - npx
  - VS Code Extensions
- npx create-react-app
- Function Components
- Class Components
- Rendering Components
  - The two different ways to return a component and why they work:
    1. `()`
    2. ` { return <div></div> }`
- Props
  - Deconstructing props
- State
- React Hooks - Baseline
- Working with data in a class component

- [Props and State](#props-and-state)
  - [Props](#props)
  - [Rendering Props: I Do](#rendering-props-i-do)
    - [Deconstructing Props](#deconstructing-props)
  - [State](#state)
    - [Rendering State: I Do](#rendering-state-i-do)
    - [Deconstructing State](#deconstructing-state)
  - [Passing State and Rendering State: I Do](#passing-state-and-rendering-state-i-do)
    - [Passing State: Syntax Sugar](#passing-state-syntax-sugar)
  - [React Hooks Basics](#react-hooks-basics)

## Props and State
<Need a section intro!!>

**Key Takeaways**:
- React is a front end library
- It allows developers to rapidly build front end web applications
- React alleviates the heavy lifting a developers has to do when working with Vanilla JavaScript, HTML, and CSS.

### Props
**Key Takeaways**:
- `Props` is short for `properties`
- `Props` are variables which store data
- `Props` are `immutable`, meaning their value can not be changed
- `Props` are passed into a component by its `parent` component

### Rendering Props: I Do
Demonstrate to students how to write a `Functional` and `Class` component which both render `props`.

Example:
```JSX
import React from "react";
import "./styles.css";

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
#### Deconstructing Props
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

### State
Key Takeaways:
- `State` is a JavaScript object which is defined in the constructor of a `Class` component
- `State`is meant to hold data for a component
- You define properties within `state` which in turn can be accessed and rendered within a component
- A parent component can pass it's own `state` to a child component in the form `props`

#### Rendering State: I Do
Build a `Class` component that renders `state`.

Example:
```jsx
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

#### Deconstructing State
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

### Passing State and Rendering State: I Do
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
#### Passing State: Syntax Sugar
You can make your code more concise by doing the following:
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

### React Hooks Basics
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