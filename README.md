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

- [Dev Tools:](#dev-tools)
  - [Git Bash on Windows](#git-bash-on-windows)
    - [How to Run Git Bash on Windows](#how-to-run-git-bash-on-windows)
    - [Git Installation Help](#git-installation-help)
  - [VS Code Extensions](#vs-code-extensions)
  - [Create React App](#create-react-app)
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

## Dev Tools:
### Git Bash on Windows
"Git Bash is an application for Microsoft Windows environments which provides an emulation layer for a Git command line experience." - Atlassian.com

In laymen terms `Git Bash` is a terminal application that Windows users can utilize in place of the `Command Prompt` terminal that comes as default with all Windows OS. `Git Bash` in turn allows you to use `Git` command in the terminal.

Utilizing `Git Bash` is very helpful when you are working with `React` and other frameworks that run hefty size servers in local development.

Moral of the story: Utilize `Git Bash` to run your `React` server instead of the build in terminal in your text editor.

#### How to Run Git Bash on Windows
1. Press the Windows button on your keyboard
2. Type `Git Bash`
3. Select the program

#### Git Installation Help
In order to use `Git Bash` you must have `Git` installed on your machine. If for some reason you do not have `Git` and or `Git Bash` installed please follow the tutorial below for your OS.

- **Windows** [tutorial](https://www.atlassian.com/git/tutorials/install-git#windows)
  - If you are having trouble with the Windows `Git Bash` installation here is a [tutorial](https://www.stanleyulili.com/git/how-to-install-git-bash-on-windows/#launching-git-bash) with screenshots. Start with the link above though.
- **Mac** [tutorial](https://www.atlassian.com/git/tutorials/install-git#mac-os-x)
- **Linux** [tutorial](https://www.atlassian.com/git/tutorials/install-git#linux)

### VS Code Extensions
Now that we are all set with `Git` lets be sure we all have some helpful `VS Code` extensions installed.

- [Reactjs Code Snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.ReactSnippets): contains helpful code snippets for React.
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode): is a code formatter which helps to keep your code clean and easy to read.
- [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync): this is an awesome extension that allows you to sync your `VS Code` setting to a GitHub Gist. This is super helpful for users who have multiple computers or anyone who would like to back up their `VS Code` settings.
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker): Does exactly what the name says. It is a spell checker for your text editor. Just download it.. Its a life saver.
- [VS Code Tips and Tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks): Where as this is not a `VS Code` extension this is a very helpful guide on tips and tricks that Visual Studio Code has put out for `VS Code`. I would highly recommend give it a read, as a Engineer shortcuts and hotkeys are your best friend.

### Create React App
`Create React App` is a standalone tool that generates and runs a new `React` project utilizing `npm` or `yarn` with just a couple of commands.

Having trouble remembering how to use `create-react-app`? 
Also a quick overview can be found below:
1. Open your terminal
2. Transverse to the directory you would like to create your `React` project inside of.
   - ie: `cd ~/code-differently/projects/`
3. Type `npx create-react-app <provide-a-name-for-your-project>
4. Hit enter

Once `create-react-app` finishes its work you will need to `cd` into the project you created; ie `cd ./<provide-a-name-for-your-project>.

Still a little hazy on what exactly `Create React App` is doing? Check out this awesome [article](https://www.sitepoint.com/create-react-app/) which breaks it all down step by step and gives you a peak under the hood.

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