# 📚 React & JS Cheatsheet

This is my cheatsheet for everything ![Untitled-1](https://user-images.githubusercontent.com/58719526/221365354-6d910d17-83a7-464f-836c-c3b5294a664c.png)

## Table of content

[Setting up React](#setting-up-react)<br>
[Creating components](#creating-components)<br>
[Proptypes](#proptypes)<br>
[Routers](#routers)<br>
[Link component](#link-component)<br>
[Use React Icons](#use-react-icons)<br>


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

## Proptypes

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

## Routers

React routers are used to create single page applications with navigation without the page reloading, allowing developers to create more seamless user experiences.

* Install React Router and React Icons

```
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
  

## Use React Icons

* Import it first to the component you want to use it then use it like this:

```javascript
import {FaGithub} from 'react-icons/fa'

<FaGithub />
```
  
## High Order Array Methods and when to use them
  * When to use forEach?
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
  
  * When to use map?
  .map() when you want to transform elements in an array.
  
  * When to use filter?
  .filter() when you want to select a subset of multiple elements from an array.
  
   * When to use reduce?
  .reduce() when you want derive a single value from multiple elements in an array.
  
   * When to use find?
  .find() When you want to select a single element from an array.
