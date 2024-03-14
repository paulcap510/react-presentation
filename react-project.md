# REACT
## Introduction

### Overview

- Simple React presentation and discussion
- My experience with React 
- For informational purposes only (feel free to correct, ask, etc.)
- My summary: Difficult to learn, easy to get good at, complicated to get great at 

### What is React?

- A JS library (framework?) for creating Single Page Applications (SPAs)
  - SPAs send one request to the server on page load, and the content is rendered client side with each request
  - Browser sends a single request and later interactions involve async API calls using AJAX or Fetch API
  - SPAs allow for a better user experience and faster page loads

### Pros and Cons of React

Pros:
- Growing in popularity
- Easy to to render UI features 
- Fast 
- Easily integrate reusable components to your app (navbar, footer, sidebars, etc.)
- Lots of libraries and third-party tools
  - Redux for managing state 
  - React Router Dom for navigation
  - NextJS for full-stack functionality 

Cons:
- Learning curve
- JSX syntax mixed with HTML
- A lot of boilerplate and clean up required to set up
- Complex state management in larger projects
- Longer inital loads for large projects
- Comprehensive testing can be challenging in larger projects 

### Getting Started

Run following command (using npx):

```
npx create-react-app my-app
cd my-app
npm start
```

![image](https://github.com/paulcap510/react-presentation/assets/118994869/789b1aa3-cd0c-46fe-9f14-6850257a6cc9)

![image](https://github.com/paulcap510/react-presentation/assets/118994869/e878dd3c-dd9d-4629-86fd-ef6dae4f1cfe)

With yarn:
```
yarn create react-app my-app
cd my-app
yarn start
```

Typescript:
```
npx create-react-app my-app --template typescript
```

### File Structure

- When starting a React app, the first thing is to remove unnuecssary files
- React can be unforgiving

`Module not found: Error: Can't resolve './logo.svg' in '/Users/paulprogram/VSProjects/react-tut-0207/my-app/src'
ERROR in ./src/App.js 4:0-30
Module not found: Error: Can't resolve './logo.svg' in '/Users/paulprogram/VSProjects/react-tut-0207/my-app/src'`

#### index.js vs. App.js
- The index.js file is the ENTRY POINT that starts the React application and renders the App.js component to the DOM
- App.js is the root component that usually contains the application's layout, including navigation and routing
- Together, they establish the foundation of a React application's structure, separating the concerns of setting up the application (index.js) from the application's UI structure (App.js).

##### index.js
![image](https://github.com/paulcap510/react-presentation/assets/118994869/907668c4-43a1-45ff-8df1-799f86c1553a)

- index.js contains your <App> component, responsible for the application
- ReactDOM.render() mounts the root React component (<App />) to a specific DOM element (like <div id="root"></div> in the HTML file)
- Using some libraries or frameworks, you may wrap this in certain code, which is why you might come into this file (example: Redux to wrap the <App> with a Provider for state management)

#### public/index.html
- index.html serves as the HTML for the entire app (i.e. where you might import Google fonts, etc.)

### Components

- React is a component-based library.
- You write the component once and can reuse it throughout the application.
- NOTE: Different types of components: Functional, Class, and Pure. Older versions use Class and Pure, but FUNCTIONAL components seem most often used today.
- Mostly in this presentation we will focus on Functional components, but if you work with apps built with older React versions, you may see other ones.

##### Example of the App.js file with the navbar imported

![image](https://github.com/paulcap510/react-presentation/assets/118994869/a8727d0d-2ad7-4039-83b1-54f2e0c3e4d1)

Result:
![image](https://github.com/paulcap510/react-presentation/assets/118994869/98383143-8971-4023-a317-59dfe8aacbe0)

- So you build out the components and pass them to the pages that want to display them
- notice `export default App` here
- `export default Navbar` allows the component to be exported to other pages

### React Hooks and State
- React uses HOOKS to update STATE which in turn manipulate the DOM
- You use STATE to update the DOM contents (using HOOKS)
- Examples: useState; useEffect; useNavigate (with React-Router-Dom)
- STATE is like a variable in other langauges.
- You do not actually MANIPULATE instances of STATE, you instead MANAGE it by recreating new pieces of STATE with each page render

Example from JS (not React): 

`const myList = [1, 2, 3];`

`myList.push(4)`

In React you DO NOT do this.

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
`const [entryDate, setEntryDate] = useState<string>(‘');`

![image](https://github.com/paulcap510/react-presentation/assets/118994869/89d4889e-85fc-47bd-8fa9-efa0fb52c8f4)

![image](https://github.com/paulcap510/react-presentation/assets/118994869/d0495dd2-a059-4747-a6e1-522e9a560de9)

### useEffect

- Allows for functional components to perform side effects (operations that affect others but can't be done during rendering)
- Runs after DOM is rendered and can be used to fetch data and manipulate the DOM

Example to display time on a mounted component:


 `useEffect(() => {
    const now = new Date();
    console.log("The component mounted, current time is:", now);`

  
Example:
- The [] at the end is syntax to explain that this useEffect hook (function) will only be run once the component loads 

![image](https://github.com/paulcap510/react-presentation/assets/118994869/1bac2199-d506-4432-9e55-6cdc2b2a2cd7)






### Navigation

- Navigate is done using 'react-router-dom', a third-party library that allows for easy linking of pages and dynamic navigation
- Example: Every page loads The Navbar, but rest of the content of the page differs depending on the route. Here "/" and "/about" will render the `Home` and `About` components respectively

![image](https://github.com/paulcap510/react-presentation/assets/118994869/499ac828-9f41-4bc0-9d4e-0cc301385d4b)

### Conculsion

- React is a popular JS library for building SPAs
- Growing in popularity due to its performance and efficacy
- Alternatives: Vue, Angular, Svelte 
