# React For Everyone

[![reactjs](reactjs.png)](https://reactjs.org/)

Click on [Project](https://github.com/rgoshen/levelup-app) to access the GitHub Project

## Abbreviations {collapsible="true"}

- \*[DOM]: Document Object Model

## Understanding Components {collapsible="true" default-state="expanded"}

- starting in React 18, files do not need `import React from 'react';` at the top of the file anymore.
    - there is a transformer inside of babel that removes the requirement to have import React statement

```javascript
import './App.css';

function App() {
  return (
    <div className='App'>
      <header className='App-header'>
        <HelloWorld/>
        <HelloWorld/>
      </header>
    </div>
  );
}

function HelloWorld() {
  return (
    <h1>
      Hello World!
    </h1>
  );
}

export default App;
```

## What Are Props {collapsible="true" default-state="expanded"}

Props are the way that we pass data between parent and children components.

```javascript
import './App.css';

function App() {
  return (
    <div className='App'>
      <header className='App-header'>
        <HelloWorld name='Rick' greeting='Yo' />
        <HelloWorld name='World' />
      </header>
    </div>
  );
}

function HelloWorld(props) {
  return (
    <h1>
      {props.greeting} {props.name}!
    </h1>
  );
}
export default App;

```

## Default Props {collapsible="true" default-state="expanded"}

Default props are a default value that we can give our props in case a value is not given.

```javascript
import './App.css';

function App() {
  return (
    <div className='App'>
      <header className='App-header'>
        <HelloWorld name='Rick' greeting='Yo' />
        <HelloWorld name='World' />
      </header>
    </div>
  );
}

function HelloWorld({ name, greeting = 'Hello' }) {
  return (
    <h1>
      {greeting} {name}!
    </h1>
  );
}

export default App;

```

- we can also tell out component what type of props to expect

```javascript
import PropTypes  from 'prop-types';
import './App.css';

function App() {
  return (
    <div className='App'>
      <header className='App-header'>
        <HelloWorld name='Rick' greeting='Yo' />
        <HelloWorld name='World' />
      </header>
    </div>
  );
}

function HelloWorld({ name, greeting = 'Hello' }) {
  return (
    <h1>
      {greeting} {name}!
    </h1>
  );
}

HelloWorld.propTypes = {
  name: PropTypes.string.isRequired,
  greeting: PropTypes.string,
};

export default App;
```

## State in Components with useState {collapsible="true" default-state="expanded"}

In order to use state in a component, you need to import `useState` hook then
you `const [state, setState] = useState(defaultState);`

ex.: `const [count, setCount] = useState(0);`

_src/App.js_

```javascript
import PropTypes from 'prop-types';
import { Counter } from './Counter';
import './App.css';

function App() {
  return (
    <div className='App'>
      <Counter />
    </div>
  );
}

function HelloWorld({ name, greeting = 'Hello' }) {
  return (
    <h1>
      {greeting} {name}!
    </h1>
  );
}

HelloWorld.propTypes = {
  name: PropTypes.string.isRequired,
  greeting: PropTypes.string,
};

export default App;
```

_src/Counter.js_

```javascript
import { useState } from 'react';

export function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h3>{count}</h3>
      <button
        onClick={() => {
          setCount(count - 1);
        }}
      >
        -
      </button>
      <button
        onClick={() => {
          setCount(count + 1);
        }}
      >
        +
      </button>
    </div>
  );
}
```

## Conditional Rendering {collapsible="true" default-state="expanded"}

- using state

_src/Accordion.js_

```javascript
import { useState } from 'react';

export function Accordion() {
  const [isToggled, setIsToggled] = useState(false);

  // less common way to do this
  //   const showMe = isToggled ? <h3>Show Me</h3> : null;

  return (
    <div>
      {/* {showMe} */}
      {/* {isToggled ? <h3>Show Me</h3> : null} */}
      {isToggled && <h3>Show Me</h3>}
      <button onClick={() => setIsToggled(!isToggled)}>Toggle</button>
    </div>
  );
}

```

_src/App.js_

```javascript
import { Accordion } from './Accordion';
import './App.css';

function App() {
  return (
    <div className='App'>
      <Accordion />
    </div>
  );
}

export default App;
```

## Controlled Inputs {collapsible="true" default-state="expanded"}

Controlled inputs allow us to take control of our forms and inputs.

- strength of controlled inputs is once you get teh value from an input, you can run conditional or any manipulation you
  really want. See example below.
- basically you have control over its value

_src/Input.js_

```javascript
import { useState } from 'react';

export function Input() {
  const [inputValue, setInputValue] = useState('');

  return (
    <div>
      {inputValue && <p>{inputValue}</p>}
      <input
        value={inputValue}
        // Basic
        // onChange={(e) => setInputValue(e.target.value)}
        onChange={(e) => {
          if (!e.target.value.includes('t')) {
            setInputValue(e.target.value);
          }
        }}
      />
    </div>
  );
}
```

_src/App.js_

```javascript
import { Input } from './Input';
import './App.css';

function App() {
  return (
    <div className='App'>
      <Input />
    </div>
  );
}

export default App;
```

## Looping in React {collapsible="true" default-state="expanded"}

React uses the javascript map method to loop through arrays.

_src/MoviesList.js_

```javascript
const movies = [
  {
    name: '36th Chamber',
  },
  {
    name: 'Man of Iron',
  },
  {
    name: '5 Deadly Venoms',
  },
];

export function MoviesList() {
  return (
    <div>
      <ul>
      // loop
        {movies.map((movie) => {
          return <li key={movie.name}>{movie.name}</li>;
        })}
      </ul>
    </div>
  );
}
```

_src/App.js_

```javascript
import { MoviesList } from './MoviesList';
import './App.css';

function App() {
  return (
    <div className='App'>
      <MoviesList />
    </div>
  );
}

export default App;
```

## Basic Filtering with State {collapsible="true" default-state="expanded"}

_src/MovieList.js_

```javascript
import { useState } from 'react';

const movies = [
  {
    name: '36th Chamber',
  },
  {
    name: 'Man of Iron',
  },
  {
    name: '5 Deadly Venoms',
  },
  {
    name: 'Iron Man',
  },
];

export function MoviesList() {
  const [filter, setFilter] = useState('');
  return (
    <div>
      <label>
        Filter:
        <input value={filter} onChange={(e) => setFilter(e.target.value)} />
      </label>
      <ul>
        {movies
          .filter((movie) =>
            movie.name.toLowerCase().includes(filter.toLowerCase())
          )
          .map((movie) => (
            <li key={movie.name}>{movie.name}</li>
          ))}
      </ul>
    </div>
  );
}
```

_src/App.js_

```javascript
import { MoviesList } from './MoviesList';
import './App.css';

function App() {
  return (
    <div className='App'>
      <MoviesList />
    </div>
  );
}

export default App;
```

## Component Creation Flow {collapsible="true" default-state="expanded"}

- when two components needs access to the same state, you need to "raise up" state into their parent component and then
  pass in as props to those child components
- when a child component needs to "control" the parent component based on state, you need to "raise up" state to the
  parent component
- reason: everything in React flows down and not up, therefore, state needs to be "raised up" in order to obey that rule
  of React

_src/App.js_

```javascript
import { MoviesList } from './movies/MoviesList';
import './App.css';

function App() {
  return (
    <div className='App'>
      <MoviesList />
    </div>
  );
}

export default App;
```

_src/movies/MovieList.js_

```javascript
import { useState } from 'react';
import { Movie } from './Movie';
import { Filter } from '../Filter';

const movies = [
  {
    name: '36th Chamber',
  },
  {
    name: 'Man of Iron',
  },
  {
    name: '5 Deadly Venoms',
  },
  {
    name: 'Iron Man',
  },
];

export function MoviesList() {
  const [filter, setFilter] = useState('');
  return (
    <div>
      <Filter filter={filter} setFilter={setFilter} />
      <ul>
        {movies
          .filter((movie) =>
            movie.name.toLowerCase().includes(filter.toLowerCase())
          )
          .map((movie) => (
            <Movie key={movie.name} movie={movie} />
          ))}
      </ul>
    </div>
  );
}
```

_src/movies/Movie.js_

```javascript
export function Movie({ movie }) {
  return <li>{movie.name}</li>;
}
```

_src/Filter.js_

```javascript
export function Filter({ filter, setFilter }) {
  return (
    <label>
      Filter:
      <input value={filter} onChange={(e) => setFilter(e.target.value)} />
    </label>
  );
}
```

## PropTypes {collapsible="true" default-state="expanded"}

Prop types can help our components know exactly what type of props they should accept and throw errors when the wrong
props are sent to them.

- make components "smart"

References:

- [React Docs propTypes](https://reactjs.org/docs/typechecking-with-proptypes.html)
- [NPM prop-types](https://www.npmjs.com/package/prop-types)

_src/App.js_

```javascript
import { MoviesList } from './movies/MoviesList';
import './App.css';

function App() {
  return (
    <div className='App'>
      <MoviesList />
    </div>
  );
}

export default App;
```

_src/movies/MovieList.js_

```javascript
import { useState } from 'react';
import { Movie } from './Movie';
import { Filter } from '../Filter';

const movies = [
  {
    name: '36th Chamber',
  },
  {
    name: 'Man of Iron',
  },
  {
    name: '5 Deadly Venoms',
  },
  {
    name: 'Iron Man',
  },
];

export function MoviesList() {
  const [filter, setFilter] = useState('');
  return (
    <div>
      <Filter filter={filter} setFilter={setFilter} />
      <ul>
        {movies
          .filter((movie) =>
            movie.name.toLowerCase().includes(filter.toLowerCase())
          )
          .map((movie) => (
            <Movie key={movie.name} movie={movie} />
          ))}
      </ul>
    </div>
  );
}
```

_src/movies/Movie.js_

```javascript
export function Movie({ movie }) {
  return <li>{movie.name}</li>;
}

Movie.propTypes = {
  movie: PropTypes.shape({
    name: PropTypes.string.isRequired,
  }).isRequired,
};
```

_src/Filter.js_

```javascript
export function Filter({ filter, setFilter }) {
  return (
    <label>
      Filter:
      <input value={filter} onChange={(e) => setFilter(e.target.value)} />
    </label>
  );
}

Filter.propTypes = {
  filter: PropTypes.string.isRequired,
  setFilter: PropTypes.func.isRequired,
};
```

## Refs {collapsible="true" default-state="expanded"}

refs have changed a lot throughout the lifespan of React but are currently used with the useRef hook.

- `useRef` returns a mutable ref object whose `.current` property is initialized to the passed
  argument (`initialValue`). The returned object will persist for the full lifetime of the component.

Uses:

- to get access to the actual DOM and elements on in the DOM
    - outside the normal React flow
    - when a ref updates, this does not trigger a rerender of the DOM
    - can use this to store information and change information without rerendering the component
- allows access to actual DOM objects
- "dumb" inputs as to the controlled inputs in a previous notes

`const varName = useRef(initialValue);`

- more simple than the filter example above

Disadvantages:

- can not control rerenders
- no control over the input being used in the text box

_src/movies/MovieList.js_

```javascript
import { useState, useRef } from 'react';
import { Movie } from './Movie';
import { Filter } from '../Filter';

const movies = [
  {
    name: '36th Chamber',
  },
  {
    name: 'Man of Iron',
  },
  {
    name: '5 Deadly Venoms',
  },
  {
    name: 'Iron Man',
  },
];

export function MoviesList() {
  const [filter, setFilter] = useState('');
  const ulRef = useRef(null);
  const ref = useRef(null);

  console.log('ulRef', ulRef);

  return (
    <div ref={ulRef}>
      <form
        onSubmit={(e) => {
          e.preventDefault();
          console.log(ref.current.value);
        }}
      >
        <input ref={ref} />
        <button>Submit</button>
      </form>
      <Filter filter={filter} setFilter={setFilter} />
      <ul>
        {movies
          .filter((movie) =>
            movie.name.toLowerCase().includes(filter.toLowerCase())
          )
          .map((movie) => (
            <Movie key={movie.name} movie={movie} />
          ))}
      </ul>
    </div>
  );
}
```

## useEffect 101 {collapsible="true" default-state="expanded"}

This is a powerful hook and hook helps us to perform actions when a component mount, unmounts, and updates.

- basically the ability to trigger side effects
- you can tell `useEffect` when to run
- `useEffect(() => {}, [])`
    - the empty array after the arrow function tells `useEffect` to run only the first time the component renders (
      on `componentDidMount`)
    - if you put some state in the array such as filter, then it would run the `useEffect` when the filter is updated

_src/movies/MoviesList.js_

```javascript
import { useState, useEffect } from 'react';
import { Movie } from './Movie';
import { Filter } from '../Filter';

const movies = [
  {
    name: '36th Chamber',
  },
  {
    name: 'Man of Iron',
  },
  {
    name: '5 Deadly Venoms',
  },
  {
    name: 'Iron Man',
  },
];

export function MoviesList() {
  const [filter, setFilter] = useState('');

  useEffect(() => {
    console.log('hit effect');
  }, [filter]);

  return (
    <div>
      <Filter filter={filter} setFilter={setFilter} />
      <ul>
        {movies
          .filter((movie) =>
            movie.name.toLowerCase().includes(filter.toLowerCase())
          )
          .map((movie) => (
            <Movie key={movie.name} movie={movie} />
          ))}
      </ul>
    </div>
  );
}
```

## React Router v5 {collapsible="true" default-state="expanded"}

[React Router](https://reactrouter.com/) reference

Routing is necessary for larger applications with multiple pages

_src/App.js_

```javascript
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import { MoviesList } from './movies/MoviesList';
import { MovieDetail } from './movies/MovieDetail';
import './App.css';

function App() {
  return (
    <div className='App'>
      <Router>
        <Routes>
          <Route path='/' element={<MoviesList />} />
        </Routes>
        <Routes>
          <Route path='details' element={<MovieDetail />} />
        </Routes>
      </Router>
    </div>
  );
}

export default App;
```

_src/movies/Movie.jsx_

```javascript
import { Link } from 'react-router-dom';
import PropTypes from 'prop-types';
import './Movie.css';

export function Movie({ movie, config }) {
  return (
    <li>
      <Link to='details'>
        {config.images.base_url && (
          <img
            src={config.images?.base_url + 'w342' + movie.poster_path}
            alt={movie.title + ' Poster'}
            className='movie-poster'
          />
        )}
        <h3 className='movie-title'>{movie.title}</h3>
      </Link>
    </li>
  );
}

Movie.propTypes = {
  movie: PropTypes.shape({
    title: PropTypes.string.isRequired,
    poster_path: PropTypes.string.isRequired,
  }).isRequired,
};
```

_/src/movies/MovieDetail.jsx_

```javascript
export function MovieDetail() {
  return (
    <div>
      <h1>Movie Detail!</h1>
    </div>
  );
}
```

<seealso>
[ReactJS Docs](https://reactjs.org/docs/getting-started.html) |
[Level Up Tutorials](https://leveluptutorials.com/)
</seealso>
