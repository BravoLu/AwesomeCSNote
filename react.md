# React

## useState

* It takes an initial value as an argument and returns an array with two elements: the current state value and a function to update that value.

* Example

```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default Counter;

```



## useEffect

* It takes two arguments: a function to run after rendering, and an optional array of dependencies.
* example

```javascript
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    // Fetch data when the component is mounted
    fetchData()
      .then((result) => {
        setData(result);
      });
  }, []); // Empty array means this effect runs only once

  return (
    <div>
      <p>Data: {data}</p>
    </div>
  );
}

export default DataFetcher;
```

## useRef

```react
useRef<type>(null)
```





 ## Typewriter

* 
  Creating a typewriter effect in a React application involves animating the rendering of text to simulate the appearance of characters being typed out one by one

## Container

*  It is used to create a responsive container for your application's content, which helps control the width of your content and adapt it to different screen sizes. 

  md = medium

  sm = small

  xl = extra large

  lg = large

* Create a fluid `Container` by adding the `fluid` property to it. This will make the container extend to the full width of its parent container.

```javascript
<Col md={4} className="home-header">  // means 12/4 columns.
```

## NavBar

```javascript
function App() {
  return (
    <Navbar bg="dark" expand="lg" variant="dark">
      <Navbar.Brand href="/">My App</Navbar.Brand>
      <NavbarToggle aria-controls="basic-navbar-nav" />
      <NavbarCollapse id="basic-navbar-nav">
        <Nav className="ml-auto">
          <Nav.Link href="/">Home</Nav.Link>
          <Nav.Link href="/about">About</Nav.Link>
          <Nav.Link href="/contact">Contact</Nav.Link>
        </Nav>
      </NavbarCollapse>
    </Navbar>
  );
}

export default App;
```

- The `Navbar` component sets up the basic structure of the navigation bar.
- `Navbar.Brand` is used to display the brand name or logo.
- `NavbarToggle` is the component that renders the toggle button (often the hamburger icon) for small screens.
- `NavbarCollapse` is the component that contains the navigation links and menu items that will be hidden/shown when the toggle button is clicked.
- `Nav` is used to define the list of navigation links within the `NavbarCollapse`.

The `aria-controls` attribute of the `NavbarToggle` component is set to match the `id` of the `NavbarCollapse`, so they are associated with each other. This is essential for accessibility and ensuring screen readers can understand the collapsible navigation.

This setup creates a responsive navigation bar with a toggle button for small screens. When the screen size is reduced, the navigation links are hidden, and clicking the toggle button reveals them.

## Filter

```react
tags.filter(tag => { tag != 'happy'})
```

## map

```react
tags.map(tag => { tag == 'happy' ? r1 : r2})
```

## reduce

```react
expenses.reduce((acc, expense) => { expense.amount + acc})
```



## produce

```react
setBugs(produce(draft => {
	const bug = draft.find(bug => bug.id === 1);
  if (bug) bug.fixed = true;
}))
```

## Sharing State between Components.

```react
# change the state on the parent of two components if you need to share the state between them.
```

## Zod Library for validation



## onChange

```
onChange = {(event) => setPerson({..person, name: event.target.value})}
```



## react-hook-form

```react
import {useForm} from "react-hook-form"

const {register} = useForm();
```



```react
{ errors.name?.type === 'required' && xxx } 
```



# Build an App from scratch.

## using Vite to generate the infrastructure code.

```shell
npm create vite@latest
```



```
// make the button to right-most
<ModalCloseButton ml="auto"/>   

```



//

The function of justifyContent  ?

<Center> </Center

center layout?

<CardBody p={0}> set no padding



To handle the problem 

```react
function GifAnimation({ name }: { name?: string }) { }
```





as 的作用
