# React.js Interview Questions

This document contains advanced-level questions that cover various aspects of React.js, including hooks, state management, performance optimization, routing, and more. It is designed for experienced developers and aims to evaluate their expertise in building robust applications. Reading through this document will take approximately 30-45 minutes.

## Questions and Answers

<details>
<summary><strong style="font-size: 1.2em;">1. What are Higher-Order Components (HOCs) and how do they benefit React applications?</strong></summary>

Higher-Order Components are functions that take a component as an argument and return a new component with additional functionality. They promote code reuse and help manage cross-cutting concerns like authentication and data fetching.

**Hint:** 💡 HOCs are a pattern for reusing component logic without altering the original component.

**Further Reading:** [Complete Guide to React Refs - LogRocket](https://blog.logrocket.com/complete-guide-react-refs/)

```javascript
const withAuth = (WrappedComponent) => {
  return (props) => (
    <div>
      {isAuthenticated ? <WrappedComponent {...props} /> : <p>Please log in.</p>}
    </div>
  );
};

// Usage
const ProtectedComponent = withAuth(MyComponent);
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">2. Explain the concept of React Hooks and their advantages over class components.</strong></summary>

React Hooks allow functional components to manage state and side effects without converting them into class components. They simplify component logic and promote code reuse through custom hooks.

**Hint:** 💡 Hooks enable you to use state and other React features without writing a class.

**Further Reading:** [React Hooks Documentation](https://react.dev/reference/react)

```javascript
import { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return <button onClick={() => setCount(count + 1)}>Increment</button>;
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">3. What is the purpose of the `useMemo` hook?</strong></summary>

The `useMemo` hook is used to memoize expensive calculations, preventing unnecessary recalculations on every render. It returns a memoized value that only updates when its dependencies change.

**Hint:** 💡 Use `useMemo` to optimize performance for expensive computations.

```javascript
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">4. How does lazy loading work in React?</strong></summary>

Lazy loading in React allows components to be loaded only when they are needed, improving performance by reducing the initial load time. This can be achieved using `React.lazy` and `Suspense`.

**Hint:** 💡 Lazy loading helps in splitting your code into smaller chunks.

```javascript
const LazyComponent = React.lazy(() => import('./LazyComponent'));

<Suspense fallback={<div>Loading...</div>}>
  <LazyComponent />
</Suspense>
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">5. Describe how to implement advanced routing in a React application.</strong></summary>

React Router provides advanced routing capabilities such as nested routes, dynamic routing, and route guards. You can define routes using the `<Route>` component and manage navigation with hooks like `useHistory`. 

You can also use `createBrowserRouter` for more complex routing scenarios, including child routes.

**Hint:** 💡 Use `<Switch>` to render only the first matching route.

**Further Reading:** [React Router Documentation](https://reactrouter.com/)

```javascript
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
    children: [
      {
        path: "about",
        element: <About />,
      },
      {
        path: "user/:id",
        element: <User />,
      },
    ],
  },
]);

function App() {
  return (
    <RouterProvider router={router} />
  );
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">6. What is prop drilling and how can it be avoided?</strong></summary>

Prop drilling occurs when you pass data through multiple layers of components that do not need it. This can be avoided by using context or state management libraries like Redux.

**Hint:** 💡 Context API is a great way to avoid prop drilling for global state.

```javascript
const MyContext = createContext();

function Parent() {
  const value = "Hello from Parent";

  return (
    <MyContext.Provider value={value}>
      <Child />
    </MyContext.Provider>
  );
}

function Child() {
  return (
    <MyContext.Consumer>
      {(value) => <div>{value}</div>} {/* Output: Hello from Parent */}
    </MyContext.Consumer>
  );
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">7. Explain the concept of Context API in React.</strong></summary>

The Context API provides a way to share values between components without having to explicitly pass props through every level of the tree. It is useful for global state management.

**Hint:** 💡 Use context for themes or user authentication states shared across multiple components.

```javascript
const MyContext = createContext();

function App() {
  const value = { user: "John Doe" };

  return (
    <MyContext.Provider value={value}>
      <Child />
    </MyContext.Provider>
  );
}

function Child() {
  const context = useContext(MyContext);
  
  return (
    <div>User: {context.user}</div> {/* Output: User: John Doe */}
  );
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">8. How do you implement two-way data binding in React?</strong></summary>

Two-way data binding can be implemented by managing form input state using hooks like `useState`, allowing both the input field and the state to stay in sync.

**Hint:** 💡 React primarily uses one-way data binding; however, you can achieve two-way binding with controlled components.

```javascript
function TwoWayBinding() {
  const [value, setValue] = useState('');

  return (
    <input
      type="text"
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">9. What are render props and how do they differ from HOCs?</strong></summary>

Render props is a technique for sharing code between components using a prop whose value is a function. Unlike HOCs, render props provide more flexibility by allowing the consumer to control rendering.

**Hint:** 💡 Render props can lead to cleaner code compared to HOCs in certain scenarios.

```javascript
function DataProvider({ render }) {
  const data = fetchData();
  
  return render(data);
}

// Usage
<DataProvider render={(data) => <Display data={data} />} />
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">10. How can you optimize performance in a large React application?</strong></summary>

Performance optimization techniques include code splitting with dynamic imports, memoization with `React.memo` or `useMemo`, avoiding unnecessary re-renders with `shouldComponentUpdate`, and using the Profiler API for performance measurement.

**Hint:** 💡 Always profile your app before optimizing; focus on actual bottlenecks.

```javascript
const MemoizedComponent = React.memo(({ prop }) => {
  // Component logic
});
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">11. What is the difference between controlled and uncontrolled components?</strong></summary>

Controlled components have their form data managed by React state, while uncontrolled components store their own state internally using refs. Controlled components offer better control over form behavior.

**Hint:** 💡 Controlled components are generally recommended for better predictability.

```javascript
// Controlled Component Example
function ControlledInput() {
  const [value, setValue] = useState('');

  return (
    <input value={value} onChange={(e) => setValue(e.target.value)} />
  );
}

// Uncontrolled Component Example
function UncontrolledInput() {
  const inputRef = useRef(null);

  const handleSubmit = () => {
    alert(`Input Value: ${inputRef.current.value}`);
  };

  return (
    <>
      <input ref={inputRef} type="text" />
      <button onClick={handleSubmit}>Submit</button>
    </>
  );
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">12. How do you handle error boundaries in React?</strong></summary>

Error boundaries are React components that catch JavaScript errors in their child component tree during rendering, lifecycle methods, and constructors. They can be implemented using the `componentDidCatch` lifecycle method.

**Hint:** 💡 Error boundaries only catch errors during rendering; they do not catch errors inside event handlers.

```javascript
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error("Error caught:", error);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children; 
  }
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">13. Explain how to implement server-side rendering (SSR) with React.</strong></summary>

Server-side rendering involves rendering React components on the server rather than in the browser. This can be achieved using frameworks like Next.js or by setting up an Express server to serve pre-rendered HTML.

**Hint:** 💡 SSR improves SEO since search engines can crawl rendered HTML more easily.

```javascript
import express from 'express';
import { renderToString } from 'react-dom/server';
import App from './App';

const server = express();

server.get('*', (req, res) => {
   const html = renderToString(<App />);
   res.send(`<!DOCTYPE html><html><body>${html}</body></html>`);
});

server.listen(3000);
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">14. What is reconciliation in React?</strong></summary>

Reconciliation is the process by which React updates the DOM efficiently when changes occur in the component tree. It compares the current tree with the previous one to determine what has changed.

**Hint:** 💡 Key props play a crucial role in reconciliation by helping identify elements uniquely.

```javascript
// Example of reconciliation during state updates
setCount(count + 1);
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">15. How do you manage global state in a React application?</strong></summary>

Global state can be managed using Context API or third-party libraries like Redux or MobX. These tools allow you to store application-wide state and provide mechanisms for updating it.

### Context API Example

**Hint:** 💡 Choose Context API for simpler applications; consider Redux for complex state management needs.

```javascript
import { createContext, useContext } from 'react';

const MyContext = createContext();

function App() {
   const value = { user: "John Doe" };

   return (
       <MyContext.Provider value={value}>
           <Child />
       </MyContext.Provider>
   );
}

function Child() {
   const context = useContext(MyContext);
   return (
       <div>User: {context.user}</div> {/* Output: User: John Doe */}
   );
}
```

### Redux Example

```javascript
import { createStore } from 'redux';
import { Provider } from 'react-redux';

const initialState = { user: null };

function reducer(state = initialState, action) {
   switch (action.type) {
      case 'LOGIN':
         return { ...state, user: action.payload };
      default:
         return state;
   }
}

const store = createStore(reducer);

// Usage in a component:
function App() {
   const user = useSelector((state) => state.user);
   return (
       <Provider store={store}>
           {/* Your app's components */}
       </Provider>
   );
}

// Further Reading:
// [React Context API](https://reactjs.org/docs/context.html)
// [Redux Documentation](https://redux.js.org/introduction/getting-started)
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">16. What is code splitting and how does it benefit a React application?</strong></summary>

Code splitting allows you to split your code into smaller chunks that can be loaded on demand rather than all at once during initial load. This improves performance by reducing load times.

**Hint:** 💡 Use dynamic imports along with `React.lazy` for effective code splitting.

```javascript
const LazyComponent = React.lazy(() => import('./LazyComponent'));

<Suspense fallback={<div>Loading...</div>}>
   <LazyComponent />
</Suspense>
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">17. Describe how minification and compression work in optimizing a React application.</strong></summary>

Minification reduces file size by removing whitespace, comments, and other unnecessary characters from code files without changing functionality. Compression further reduces file size during transmission over networks (e.g., Gzip).

**Hint:** 💡 Use build tools like Webpack or Parcel for automatic minification during production builds.

### Minification Example

```javascript
// Webpack configuration example for minification:
module.exports = {
   mode: 'production',
   optimization: {
      minimize: true,
   },
};
```

### Compression Example

To enable Gzip compression on an Express server:

```javascript
import compression from 'compression';
import express from 'express';

const app = express();
app.use(compression());
app.use(express.static('public'));
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">18. How do you implement caching strategies in a React application?</strong></summary>

Caching strategies can be implemented using browser caching (HTTP headers), service workers (for offline capabilities), or libraries like SWR or React Query for data-fetching caching mechanisms.

**Hint:** 💡 Caching improves performance by reducing redundant network requests.

### Further Reading:
- [SWR Documentation](https://swr.vercel.app/)
- [React Query Documentation]([https://react-query.tanstack.com/](https://tanstack.com/query/latest/docs/framework/react/guides/caching))

```javascript
import useSWR from 'swr';

function DataFetchingComponent() {
   const { data } = useSWR('/api/data', fetcher);
   return <div>{data}</div>;
}
```
</details>

<details>
<summary><strong style="font-size: 1.2em;">19. Explain how to debug performance issues in a React application.</strong></summary>

Performance issues can be debugged using tools like Chrome DevTools' Performance tab or the built-in Profiler API provided by React to measure rendering times and identify bottlenecks.

**Hint:** 💡 Focus on measuring component re-renders and identifying slow-rendering components first.

### Further Reading:
- [YouTube Tutorial on Debugging Performance Issues](https://www.youtube.com/watch?v=Qwb-Za6cBws)

```javascript
import { Profiler } from 'react';

function App() {
   const onRenderCallback = (id, phase, actualDuration) => {
      console.log({ id, phase, actualDuration });
   };

   return (
      <Profiler id="App" onRender={onRenderCallback}>
         {/* Your app's components */}
      </Profiler>
   );
}
```
</details>

---

*Prepared by Husain Amravatiwala*
