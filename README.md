# React Router Dom With Tailwind CSS

## Promo:
[![IPromo Video](https://img.youtube.com/vi/7oWzOGsUDqk/0.jpg)](https://www.youtube.com/watch?v=7oWzOGsUDqk)

# Install Tailwind CSS with Create React App

## 1. Create your project

- Start by creating a new React project with Create React App v5.0+ if you don't have one already set up.

<b>Open Terminal</b>

```jsx
npx create-react-app my-project
cd my-project
```

## 2. Install Tailwind CSS

- Install tailwindcss via npm, and then run the init command to generate your tailwind.config.js file.

```jsx
npm install -D tailwindcss
npx tailwindcss init
```

## 3. Configure your template paths

- Add the paths to all of your template files in your tailwind.config.js file.

```jsx
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

## 4. Add the Tailwind directives to your CSS

- Add the @tailwind directives for each of Tailwind’s layers to your ./src/index.css file.

```jsx
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## 5. Start your build process

- Run your build process with npm run start.

```jsx
npm run start
```

## 6. Start using Tailwind in your project

- Start using Tailwind’s utility classes to style your content.

```jsx
export default function App() {
  return <h1 className="text-3xl font-bold underline">Hello world!</h1>;
}
```

## 7. Add React Router

- To add React Router in your application, run this in the terminal from the root directory of the application:

```jsx
npm i -D react-router-dom@latest
```

## 8. Folder Structure

-To create an application with multiple page routes, let's first start with the file structure.

-Within the src folder, we'll create a folder named pages with several files:

<b>src\pages\:</b>

- NavBAr.jsx
- Home.jsx
- Blogs.jsx
- Contact.jsx
- NoPage.jsx etc [Your components/page name]
  Each file will contain a very basic React component.

## 9. Basic Usage

- Now we will use our <i>BrowserRouter</i> in our index.js file.

```js
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import reportWebVitals from "./reportWebVitals";
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

### We wrap our content first with <BrowserRouter>.
```js
import { BrowserRouter } from "react-router-dom";
<BrowserRouter>
<App />
</BrowserRouter>
```
## 10. Now we will use our Router in our app.js file.

```js
import { Route, Routes } from "react-router-dom";
import GovtJob from "./pages/GovtJob";

import PrivetJob from "./pages/PrivetJob";

import TeacherJob from "./pages/TeacherJob";
import ItJob from "./pages/ItJob";
import Home from "./components/Home";
import NavBar from "./components/NavBar";
import Contact from "./components/Contact";
import Blogs from "./components/Blogs";
import About from "./components/About";

function App() {
  return (
    <div className="max-w-screen-lg mx-auto">
      <NavBar />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/govtJob" element={<GovtJob />} />
        <Route path="/privetJob" element={<PrivetJob />} />
        <Route path="/teacherJob" element={<TeacherJob />} />
        <Route path="/itJob" element={<ItJob />} />
        {/* ============================================= */}
        <Route path="about" element={<About />} />
        <Route path="contact" element={<Contact />} />
        <Route path="blogs" element={<Blogs />} />
      </Routes>
    </div>
  );
}

export default App;
```

## Example Explained

- We define our <Routes>. An application can have multiple <Routes>. Our basic example only uses one.

- <Route>s can be nested. The first <Route> has a path of / and renders the Layout component.

- The nested <Route>s inherit and add to the parent route. So the blogs path is combined with the parent and becomes /blogs.

- The Home component route does not have a path but has an index attribute. That specifies this route as the default route for the parent route, which is /.

- Setting the path to \* will act as a catch-all for any undefined URLs. This is great for a 404 error page.

## Pages / Components

- The NavBar component has <Outlet> and <Link> elements.

- The <Outlet> renders the current route selected.

- <Link> is used to set the URL and keep track of browsing history.

- Anytime we link to an internal path, we will use <Link> instead of <a href="">.

- The "NavBar route" is a shared component that inserts common content on all pages, such as a navigation menu.

```jsx
import React from "react";
import { Outlet, Link } from "react-router-dom";
const NavBar = () => {
  return (
    <div>
      <ul className="flex justify-center items-center gap-10 text-2xl pb-10">
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <Link to="/about">About</Link>
        </li>

        <li>
          <Link to="/contact">Contact</Link>
        </li>
        <li>
          <Link to="/blogs">Blogs</Link>
        </li>
      </ul>
      <Outlet />
    </div>
  );
};

export default NavBar;
```

## Make other page/components

## Nested Routher

- Home Page

```jsx
import React from "react";
import { Link } from "react-router-dom";
const Home = () => {
  return (
    <div>
      <h1 className="text-red-500 underline text-3xl text-center">
        Home Page{" "}
      </h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam et
        voluptate rerum eaque adipisci soluta placeat ad temporibus, laborum
        recusandae quas! Possimus eaque mollitia enim iste neque placeat omnis
        veritatis.
      </p>

      <ul className="flex justify-center items-center gap-10 text-2xl pb-10 text-green-500">
        <li>
          <Link to="/govtJob">Govt Job</Link>
        </li>
        <li>
          <Link to="/privetJob">Privet Job</Link>
        </li>
        <li>
          <Link to="/teacherjob">Teacher Job</Link>
        </li>
        <li>
          <Link to="/itJob">IT Job</Link>
        </li>
      </ul>
    </div>
  );
};

export default Home;
```
