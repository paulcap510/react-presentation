# REACT
## Introduction

### Welcome

- Using React 1+ year
- Not an expert! 
- Complicated to learn, easy to get good at, complicated to get great at 
- Informational purposes only

### What is React?

- A JS library for creating Single Page Applications (SPAs)
  - SPAs send one request to the server on page load, and the content is rendered client side with each request
  - Browser sends a single request and later interactions involve async API calls using AJAX or Fetch API
  - SPAs allow for a better user experience and faster page loads

### Pros and Cons

Pros:
- Growing in popularity
- Performant 
- Easily integrate reusable components to your app (navbar, footer, sidebars, etc.)
- Lots of libraries and third-party tools
  - Redux for managing state 
  - React Router for navigation
  - NextJS for full-stack functionality 
- Better SEO

Cons:
- Strictly a frontend framework 
- Learning curve 
- Complex state management in larger projects 
- Some updates can be quite radical (NextJS 13->14)

### Getting Started

Run following command (using npx):
`npx create-react-app my-app`
`cd my-app`
`npm start`

![image](https://github.com/paulcap510/react-presentation/assets/118994869/789b1aa3-cd0c-46fe-9f14-6850257a6cc9)

![image](https://github.com/paulcap510/react-presentation/assets/118994869/e878dd3c-dd9d-4629-86fd-ef6dae4f1cfe)

Also can be run with yarn
`yarn create react-app my-app`
`cd my-app`
`yarn start`

Typescript:
`npx create-react-app my-app --template typescript`

### File Structure

- When starting a React app, the first thing is to remove unnuecssary files
- React can be unforgiving
`Module not found: Error: Can't resolve './logo.svg' in '/Users/paulprogram/VSProjects/react-tut-0207/my-app/src'
ERROR in ./src/App.js 4:0-30
Module not found: Error: Can't resolve './logo.svg' in '/Users/paulprogram/VSProjects/react-tut-0207/my-app/src'`

#### index.html vs. App.js
- The index.js file is the ENTRY POINT that kick-starts the React application and renders the App.js component to the DOM
- App.js is the root component that usually contains the application's layout, including navigation and routing
- Together, they establish the foundation of a React application's structure, separating the concerns of bootstrapping the application (index.js) from the application's UI structure (App.js).
- index.html serves as the HTML for the entire app (i.e. where you might import Google fonts, etc.)

### Components

React uses a components based approach. You write the component once and can reuse it throughout the application.

NOTE: Different types of components: Functional, Class, and Pure. Older versions use Class and Pure, but FUNCTIONAL components seem most often used today.

Mostly in this presentation we will focus on Functional components, but if you work with apps built with older React versions, you may see other ones.

##### Example of the App.js file with the navbar imported

![image](https://github.com/paulcap510/react-presentation/assets/118994869/a8727d0d-2ad7-4039-83b1-54f2e0c3e4d1)

Result:
![image](https://github.com/paulcap510/react-presentation/assets/118994869/98383143-8971-4023-a317-59dfe8aacbe0)

- So you build out the components and pass them to the pages that want to display them
- `export default Navbar` allows the component to be exported to other pages 

### React Hooks
- React uses HOOKS to update STATE which in turn manipulates the DOM
- You use STATE to update the DOM contents visa HOOKS
- Examples: useState; useEffect; useNavigate (with React-Router-Dom)
- STATE is like a variable in other langauges. you do not actually MANIPULATE instances of STATE, you instead MANAGE it by recreating new pieces of STATE with each page render

Example: 
`const myList = [1, 2, 3];`

You don't actually push something to this list as you would in JS:

`myList.push(4)`

In React you use STATE to manage the myList piece of state (i.e. the myList variable)

`const [myList, setMyList] = useState('');`

`myList` is the name of the piece of state you are updating
`setMyList` is the designated function that updates that state 

Sample function of how it gets updated
`
const addItemToList = () => {
  setMyList(prevList => [...prevList, prevList.length + 1]);
};`


Example using TS:
`   const [entryDate, setEntryDate] = useState<string>(‘');`

![image](https://github.com/paulcap510/react-presentation/assets/118994869/89d4889e-85fc-47bd-8fa9-efa0fb52c8f4)

![image](https://github.com/paulcap510/react-presentation/assets/118994869/d0495dd2-a059-4747-a6e1-522e9a560de9)

### useEffect
- allows for functional components to perform side effects (operations that affect others but can't be done during rendering)
- Runs after DOM is rendered and can be used to fetch data and manipulate the DOM

Example to display time on a mounted component:
 `useEffect(() => {
    const now = new Date();
    console.log("The component mounted, current time is:", now);`


  
Example:
- useEffect = being used to set a constant variable ‘now’ to a new Date object as soon as the component mounts (loads)
- The [] at the end is syntax to explain that this useEffect hook (function) will only be run once the component loads 

![image](https://github.com/paulcap510/react-presentation/assets/118994869/1bac2199-d506-4432-9e55-6cdc2b2a2cd7)


### Passing State

- To transfer state from one page to another, you write code to pass it 

`
import { useNavigate } from 'react-router-dom';

function Header({ destination, date, options }) {
  const navigate = useNavigate();

  const handleSearch = () => {
    navigate('/hotels', { state: { destination, date, options } });
  };

  return (
    <div>
      <button onClick={handleSearch}>Search Hotels</button>
    </div>
  );
}

export default Header;
`
This code will navigate to the /hotels page with the state options of destination, date, and options being passed. Destination, date, and options have all been set on the DOM through a `<form>` input.


### Receiving State

`location` below is an object returned by the useLocation hook.


`
import React, { useState, useEffect } from 'react';
import { useLocation } from 'react-router-dom';

function List() {
  const location = useLocation();
  const [destination, setDestination] = useState('');
  const [date, setDate] = useState('');
  const [options, setOptions] = useState({});

  useEffect(() => {
    if (location.state) {
      setDestination(location.state.destination);
      setDate(location.state.date);
      setOptions(location.state.options);
    }
  }, [location]);

  return (
    <div>
      <h2>Hotels in {destination}</h2>
    </div>
  );
}

export default List;
`

### Page Navigation

- Navigate is done using 'react-router-dom', a third-party library that allows for easy linking of pages and dynamic navigation
- Example: Every page loads The Navbar, but rest of the content of the page differs depending on the route. Here "/" and "/about" will render the `Home` and `About` components respectively

![image](https://github.com/paulcap510/react-presentation/assets/118994869/499ac828-9f41-4bc0-9d4e-0cc301385d4b)
