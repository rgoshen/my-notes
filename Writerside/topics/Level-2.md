# Level 2 React

**In-Complete**

![react](reactjs.png)

## Basic Toggle Component {collapsible="true" default-state="expanded"}

_src/components/toggle/BasicToggleButton.jsx_

```javascript
import React, { useState } from 'react';

export default function BasicToggleButton(props) {
  const [isToggled, setToggled] = useState(false);
  const onToggle = () => setToggled(!isToggled);
  return (
    <div>
      {isToggled && props.children}
      <button onClick={onToggle}>Show/Hide</button>
    </div>
  );
}
```

- not very flexible

## Understanding Render Props {collapsible="true" default-state="expanded"}

Render Prop is just passing in a property to the component to render

_src/components/toggle/BasicToggle.jsx_

```javascript
import React, { useState } from 'react';

export default function BasicToggleButton({ render }) {
  const [isToggled, setToggled] = useState(false);
  const onToggle = () => setToggled(!isToggled);
  return (
    <div>
      {render({
        isToggled,
        onToggle,
      })}
    </div>
  );
}
```

The proper named `render` can be named anything you would like

_src/App.js_

```javascript
import './App.css';

// components
import BasicToggle from './components/toggle/BasicToggle';

function App() {
  return (
    <div className='App'>
      <div className='toggle'>
        <BasicToggle
          render={({ isToggled, onToggle }) => (
            <div>
              {isToggled && <p>Show me</p>}

              <button onClick={onToggle}>Show / Hide</button>
            </div>
          )}
        />
      </div>
    </div>
  );
}

export default App;
```

## Children Render Props {collapsible="true" default-state="expanded"}

_src/components/toggle/BasicToggle.jsx_

```javascript
import { useState } from 'react';

export default function BasicToggle({ children }) {
  const [isToggled, setToggled] = useState(false);
  const onToggle = () => setToggled(!isToggled);
  return children({
    isToggled,
    onToggle,
  });
}
```

_src/App.js_

```javascript
import './App.css';

// components
import BasicToggle from './components/toggle/BasicToggle';

function App() {
  return (
    <div className='App'>
      <div className='toggle'>
        <BasicToggle>
          {({ isToggled, onToggle }) => (
            <div>
              {isToggled && <p>Show me</p>}
              <button onClick={onToggle}>Show / Hide</button>
            </div>
          )}
        </BasicToggle>
      </div>
    </div>
  );
}

export default App;
```

## Fragments in React {collapsible="true" default-state="expanded"}

_src/App.js_

```javascript
import './App.css';

// components
import BasicToggle from './components/toggle/BasicToggle';

function App() {
  return (
    <div className='App'>
      <div className='toggle'>
        <BasicToggle>
          {({ isToggled, onToggle }) => (
            <>
              {isToggled && <p>Show me</p>}
              <button onClick={onToggle}>Show / Hide</button>
            </>
          )}
        </BasicToggle>
      </div>
    </div>
  );
}

export default App;
```

## Creating A Reusable Portal {collapsible="true" default-state="expanded"}

What is a portal?

Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent
component.

`ReactDOM.createPortal(child, container)`

The first argument (child) is any renderable React child, such as an element, string, or fragment. The second argument (
container) is a DOM element.

- have any code wrapped so it can be inserted into the DOM anywhere you choose

> NOTE:
> My portal is different from the one below. I am using functional components while this tutorial is using class
> components.
>
> I used this [LogRocket article](https://blog.logrocket.com/build-modal-with-react-portals/) to write my ReactPortal.

_src/Portal.js_

```javascript
import { Component } from 'react';
import ReactDOM from 'react-dom';

const portalRoot = document.getElementById('portal');

export default class Portal extends Component {
  constructor() {
    super();
    this.el = document.createElement('div');
  }

  componentDidMount = () => {
    portalRoot.appendChild(this.el);
  };

  componentWillUnmount = () => {
    portalRoot.removeChild(this.el);
  };

  render() {
    const { children } = this.props;
    return ReactDOM.createPortal(children, this.el);
  }
}
```

_src/App.js_

```javascript
import React, { Component, Fragment } from 'react';
import logo from './logo.svg';
import './App.css';
import Toggle from './ToggleRPC';
import Portal from './Portal';

class App extends Component {
  render() {
    return (
      <div className='App'>
        <header className='App-header'>
          <img src={logo} className='App-logo' alt='logo' />
          <h1 className='App-title'>Welcome to React</h1>
        </header>
        <Toggle>
          {({ on, toggle }) => (
            <Fragment>
              <button onClick={toggle}>Login</button>
              <Portal>{on && <h1>Hi, I;m in a portal</h1>}</Portal>
            </Fragment>
          )}
        </Toggle>
      </div>
    );
  }
}

export default App;
```

## Creating A Reuseable Modal {collapsible="true" default-state="expanded"}

## Improving Our Modal {collapsible="true" default-state="expanded"}

## Creating A Reuseable Icon Component {collapsible="true" default-state="expanded"}

## Index Files for Organization {collapsible="true" default-state="expanded"}

## Elements Module & Absolute Imports {collapsible="true" default-state="expanded"}

## Building Design Utilities {collapsible="true" default-state="expanded"}

## React Context API {collapsible="true" default-state="expanded"}

## Updating Context {collapsible="true" default-state="expanded"}

## Basic Transitions With React Spring {collapsible="true" default-state="expanded"}

## React Spring Basics Part 2 {collapsible="true" default-state="expanded"}

## Animating Modal {collapsible="true" default-state="expanded"}

## Native Mode for Perfomant Animations {collapsible="true" default-state="expanded"}

## Animated Draggable Components {collapsible="true" default-state="expanded"}

## Native Dragging Animation {collapsible="true" default-state="expanded"}

## Interpolation In-depth {collapsible="true" default-state="expanded"}

## Using Position To Interpolate Color {collapsible="true" default-state="expanded"}

## Event With Gestures Based Interface {collapsible="true" default-state="expanded"}

<seealso>
[React Docs](https://reactjs.org/docs/getting-started.html) |
[React Spring](https://react-spring.dev/)
</seealso>
