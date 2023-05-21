# 📚 React & JS Cheatsheet

This is my cheatsheet for everything ![Untitled-1](https://user-images.githubusercontent.com/58719526/221365354-6d910d17-83a7-464f-836c-c3b5294a664c.png)

## Table of content

[Setting up React](#setting-up-react)<br>
[Creating components](#creating-components)<br>
[Proptypes and Props](#proptypes-and-props)<br>
[Hooks](#hooks)<br>
[Routers](#routers)<br>
[Link component](#link-component)<br>
[Use React Icons](#use-react-icons)<br>
[High Order Array Methods and when to use them](#high-order-array-methods-and-when-to-use-them)<br>
[Ternary operator and && operator](#ternary-operator-and--operator)<br>
[Usefull shorhands or snippets](#usefull-shorhands-or-snippets)<br>


## Setting up React

* Create new project (Add the code below to a command terminal)

```
npx create-rect-app [projects-name] --use-npm
```


* Run project (Add this to Visual Code's terminal)

```
npm run
```

* Remove unnecessary files like:

App.css, App.test.js, logo.svg, reportWebVital.js, setupTest.js

* Also the following code from index.js

```javascript
import reportWebVitals from './reportWebVitals';

reportWebVitals(); //Together with the comments above
```


## Creating components

Components in React are building blocks for creating user interfaces. They are the smallest unit of an application and each component provides a certain functionality. Components have their own state and lifecycle which allows them to be reused and composed into larger UIs.

* Create a folder in source folder called components (Or any other name)
* Create a component for example: Navbar.jsx (.tsx for typescript)
* With the command rfce create the basic structure of the file

```javascript
function Navbar() {
  return (
    <div>
      
    </div>
  )
}

export default Navbar
```

* Then you need to import that to the main js file in this case App.js and place it in the App with:  <Navbar />


```javascript
import Navbar from './components/Navbar';

function App() {
  return (
    <>
      <Navbar />
      <div className="container">
        <h1>My App</h1>
      </div>
    </>
  );
}

export default App;
```


## Proptypes and Props

Proptypes allow you to specify which props a component can expect, as well as their type. For example:

```javascript
// Import proptypes
import PropTypes from 'prop-types'

// Use of proptypes for example in a component called Navbar.jsx
function Navbar({title}) {
  return <nav>
      <Link to='/' className='text-lg font-bold align-middle'>
            {title}
       </Link>
  </nav>
}

Navbar.defaultProps = {
    title: 'Github Finder'
}

Navbar.propTypes = {
    title: PropTypes.string,
}
```

Props (short for properties) are a way to pass data from a parent component to its child components. They are used to customize and configure the child components. Props are essentially read-only, meaning that they cannot be modified by the child components. Props are essential for building reusable and modular components in React. By passing different props to a component, you can create variations of the same component with different behaviors or appearances. This allows for flexible and dynamic UI development.

```javascript
// Parent component
import Header from './components/Header';

function App() {
  return (
    <>
      <Header />
      <div className="container">
        <h1>My App</h1>
      </div>
    </>
  );
}

export default App;
```

```javascript
// Child component
import PropTypes from 'prop-types';

function Header({ text }) {
  return (
    <header>
      <div className="container">
        <h2>{text}</h2>
      </div>
    </header>
  );
}

Header.defaultProps = {
  text: 'Feedback UI',
};

Header.propTypes = {
  text: PropTypes.string,
};

export default Header;
```

## Hooks

* useState Hook
The useState hook provides a convenient and efficient way to manage state in functional components, ensuring that the component's UI reflects the current state and handling the re-rendering process efficiently. The main difference between using the useState hook and storing information in regular variables is how React handles the component's state and triggers re-rendering.

```javascript
const Counter = () => {
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
};

export default Counter;
```

* useParams Hook
The useParams hook returns an object of key/value pairs of the dynamic params from the current URL that were matched by the <Route path>. Child routes inherit all params from their parent routes.
  
 ```javascript
 import { Routes, Route, useParams } from 'react-router-dom';

function ProfilePage() {
  // Get the userId param from the URL.
  let { userId } = useParams();
  // ...
}

function App() {
  return (
    <Routes>
      <Route path="users">
        <Route path=":userId" element={<ProfilePage />} />
        <Route path="me" element={...} />
      </Route>
    </Routes>
  );
}
 ```
  

## Routers

React routers are used to create single page applications with navigation without the page reloading, allowing developers to create more seamless user experiences.

* Install React Router and React Icons

```javascript
npm i react-router-dom react-icons
```

* Add the following code to App.js

```javascript
import { BrowserRouter as Router, Route, Routes} from "react-router-dom";
```

* Example to add different routes to App.js

```javascript
import { BrowserRouter as Router, Route, Routes} from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";
import NotFound from "./pages/NotFound";
import Navbar from "./components/layout/Navbar";
import Footer from "./components/layout/Footer";

function App() {
  return (
        <Router>
          <div className="flex flex-col justify-between h-screen text-white">
            <Navbar />
            <main className="container mx-auto px-3 pb-12">
              <Routes>
                <Route path='/' element={<Home />}/>
                <Route path='about' element={<About />}/>
                <Route path='/notfound' element={<NotFound />}/>
                <Route path='/*' element={<NotFound />}/>
              </Routes>
            </main>
            <Footer />
          </div>
        </Router>
  );
}

export default App;
```

## Link component

The <Link> component in React is used to link between different routes of an application. When clicking on a <Link>, the URL will change, but the page won’t reload.
  
```javascript
// If you want to use links in a component you must import it first and use it like this:
import { Link } from 'react-router-dom'
  
<Link to='/about'>About</Link>
```
  
## Navigate component
 
The <Navigate> component can be used to redirect anywhere

```javascript

import { Navigate } from "react-router-dom";
  
<Navigate to="/notfound>
```
              
## Use React Icons

* Import it first to the component you want to use it then use it like this:

```javascript
import {FaGithub} from 'react-icons/fa'

<FaGithub />
```
  
## High Order Array Methods and when to use them
  * When to use forEach?<br>
  
.forEach() is great you need to execute a function for each individual element in an array. Good practice is that you should use .forEach() when you can’t use other array methods to accomplish your goal. I know this may sound vague, but .forEach() is a generic tool… only use it when you can’t use a more specialized tool.
  
  ```javascript
  const socialObjs = [
    { name: 'Twitter', url: 'https://twitter.com'},
    { name: 'Facebook', url: 'https://Facebook.com'},
    { name: 'LinkedIn', url: 'https://LinkedIn.com'},
    { name: 'Instagram', url: 'https://Instagram.com'},
];

socialObjs.forEach((item) => console.log(item.url));
  
  const socials = ['Twitter', 'LinkedIn', 'Facebook', 'Instagram'];
  
  socials.forEach((social, index, array) => console.log(`${index} - ${social}`, array));
  ```
  
  * When to use map?<br>
  
.map() when you want to transform elements in an array.
  
  ```javascript
  const companies = [
  { name: 'Company One', category: 'Finance', start: 1981, end: 2004 },
  { name: 'Company Two', category: 'Retail', start: 1982, end: 2005 },
  { name: 'Company Three', category: 'Auto', start: 1983, end: 2006 },
  { name: 'Company Four', category: 'Retail', start: 1984, end: 2007 },
  { name: 'Company Five', category: 'Technology', start: 1985, end: 2008 },
  { name: 'Company Six', category: 'Finance', start: 1986, end: 2009 },
  { name: 'Company Seven', category: 'Auto', start: 1987, end: 2010 },
  { name: 'Company Eight', category: 'Technology', start: 1988, end: 2011 },
  { name: 'Company Nine', category: 'Retail', start: 1989, end: 2012 },
];

// Create an array of company names
const companyNames = companies.map((company) => company.name);
console.log(companyNames);

// Create an array with just company and category
const companyInfo = companies.map((company) => {
  return {
    name: company.name,
    category: company.category,
  };
});

console.log(companyInfo);

// Create an array of objects with the name and the length of each company in years
const companyYears = companies.map((company) => {
  return {
    name: company.name,
    length: company.end - company.start + ' years',
  };
});

console.log(companyYears);

// Chain map methods
const squareAndDouble = numbers
  .map((number) => Math.sqrt(number))
  .map((sqrt) => sqrt * 2);

console.log(squareAndDouble);

// Chaining different methods
const evenDouble = numbers
  .filter((number) => number % 2 === 0)
  .map((number) => number * 2);

console.log(evenDouble);
  ```
  
  * When to use filter?<br>
  
 .filter() when you want to select a subset of multiple elements from an array.
  
  ```javascript
  const numbers = [1,2,3,4,5,6,7,8,9,10];

  const evenNumbers = numbers.filter(number => number % 2 === 0);
  
  const companies = [
    {name: 'Company One', category: 'Finance', start: 1981, end: 2004},
    {name: 'Company Two', category: 'Retail', start: 1982, end: 2005},
    {name: 'Company Three', category: 'Auto', start: 1983, end: 2006},
    {name: 'Company Four', category: 'Retail', start: 1984, end: 2007},
    {name: 'Company Five', category: 'Technology', start: 1985, end: 2008},
    {name: 'Company Six', category: 'Finance', start: 1986, end: 2009},
    {name: 'Company Seven', category: 'Auto', start: 1987, end: 2010},
    {name: 'Company Eight', category: 'Technology', start: 1988, end: 2011},
    {name: 'Company Nine', category: 'Retail', start: 1989, end: 2012},
];

// Get only retail companies
const retailCompanies = companies.filter(company => company.category == 'Retail');

// Get companies that started in or after 1980 in or before 2005
const earlyCompanies = companies.filter(company => company.start >= 1980 && company.end <= 2005);

// Get companies that lasted 10 years or more
const longCompanies = companies.filter(company => (company.end - company.start >= 10));

console.log(longCompanies);
  ```
  
   * When to use reduce?<br>
  
 .reduce() when you want derive a single value from multiple elements in an array.
  
  ```javascript
  const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const sum = numbers.reduce(function (accumulator, currentValue) {
  return accumulator + currentValue;
}, 0);

const sum2 = numbers.reduce((acc, cur) => acc + cur, 0);

const cart = [
  { id: 1, name: 'Product 1', price: 130 },
  { id: 2, name: 'Product 2', price: 150 },
  { id: 3, name: 'Product 3', price: 200 },
];

const total = cart.reduce((acc, product) => acc + product.price, 0);

console.log(total);
  ```
  
   * When to use find?<br>
  
.find() When you want to select a single element from an array.
  ```javascript
  const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// Expected output: 12
  ```

  ## Ternary operator and && operator
  
The conditional (ternary) operator is the only JavaScript operator that takes three operands: a condition followed by a question mark (?), then an expression to execute if the condition is truthy followed by a colon (:), and finally the expression to execute if the condition is falsy. This operator is frequently used as an alternative to an if...else statement.
  
  * Ternary operator

  ```javascript
  {showComments 
    ? (
    <ul>
       {comments.map((comment, index) => (
           <li key={index}>{comment.text}</li>
         ))}
     </ul>
     : null
  )}
  ```
  
  In this example we will show the comments in li elements if showComments is true, if false we will return null
  
  * && operator (If there is no need for else)
  
  ```javascript
  {showComments && (
    <ul>
       {comments.map((comment, index) => (
           <li key={index}>{comment.text}</li>
         ))}
     </ul>
  )}
  ```
  
  In this example we will show the comments in li elements if showComments is true
  
  
  ## Usefull shorhands or snippets
  
In order to use these snippets you need to add the Visual Code Extansion called "ES7 React/Redux/GraphQL/React-Native snippets"
  
  ```javascript
// Console log //
  clg 
  
  console.log(object)
  
// Functional React Component with Export //
  rfce

  function $1() {
    return <div>$0</div>
  }

  export default $1
  
// Import PropTypes //
  impt
  
  import PropTypes from 'prop-types';
  ```
 
  
  
