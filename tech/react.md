# React

## HOC

## Redux

* Redux
* Store
  * Action Creators
  * Dispatch (actions)
  * Middleware
    * Extension point
    * Modifies action/payload, dispatched new actions
  * Reducers (return new (modified) state). Updates state tree.

### Redux Middleware

```
const loggerMiddleware = store => next => action => {
  console.log("dispatching: ", action);
  next(action);
};
```

### Hot Module Replacement in create-react-app

TODO

### Selectors in Redux

https://www.youtube.com/watch?v=frT3to2ACCw

### Immutability in JavaScript

https://www.youtube.com/watch?v=4LzcQyZ9JOU

## react-router

http://stackoverflow.com/questions/41474134/nested-routes-with-react-router-v4

```js
import React, { Component } from "react";
import { Switch, Route, Redirect, Link } from "react-router-dom";

const Home = () => (
  <div>
    <h1>Home</h1>
  </div>
);
const User = () => (
  <div>
    <h1>User</h1>
  </div>
);
const Error = () => (
  <div>
    <h1>Error</h1>
  </div>
);

const Frontend = props => {
  console.log("Frontend");
  return (
    <div>
      <h2>Frontend</h2>
      <p>
        <Link to="/">Root</Link>
      </p>
      <p>
        <Link to="/user">User</Link>
      </p>
      <p>
        <Link to="/admin">Backend</Link>
      </p>
      <p>
        <Link to="/the-route-is-swiggity-swoute">Swiggity swooty</Link>
      </p>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/user" component={User} />
        <Redirect
          to={{
            state: { error: true }
          }}
        />
      </Switch>
      <footer>Bottom</footer>
    </div>
  );
};

const Backend = props => {
  console.log("Backend");
  return (
    <div>
      <h2>Backend</h2>
      <p>
        <Link to="/admin">Root</Link>
      </p>
      <p>
        <Link to="/admin/user">User</Link>
      </p>
      <p>
        <Link to="/">Frontend</Link>
      </p>
      <p>
        <Link to="/admin/the-route-is-swiggity-swoute">Swiggity swooty</Link>
      </p>
      <Switch>
        <Route exact path="/admin" component={Home} />
        <Route path="/admin/user" component={User} />
        <Redirect
          to={{
            state: { error: true }
          }}
        />
      </Switch>
      <footer>Bottom</footer>
    </div>
  );
};

class GlobalErrorSwitch extends Component {
  previousLocation = this.props.location;

  componentWillUpdate(nextProps) {
    const { location } = this.props;

    if (nextProps.history.action !== "POP" && (!location.state || !location.state.error)) {
      this.previousLocation = this.props.location;
    }
  }

  render() {
    const { location } = this.props;
    const isError = !!(
      location.state &&
      location.state.error &&
      this.previousLocation !== location
    ); // not initial render

    return (
      <div>
        {isError ? (
          <Route component={Error} />
        ) : (
          <Switch location={isError ? this.previousLocation : location}>
            <Route path="/admin" component={Backend} />
            <Route path="/" component={Frontend} />
          </Switch>
        )}
      </div>
    );
  }
}

class App extends Component {
  render() {
    return <Route component={GlobalErrorSwitch} />;
  }
}

export default App;
```

## NextJS

[NextJS: From npm init to production](https://medium.com/@sscaff1/nextjs-from-npm-init-to-production-c9f543169bfb) (May 18 2017)

## Authentication

A good and secure way to restful authentication?

<https://www.reddit.com/r/reactjs/comments/7cbe06/a_good_and_secure_way_to_restful_authentication/?st=J9WIXW4X&sh=3a51c0e7>
