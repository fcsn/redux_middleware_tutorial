# tutorial of redux middleware

## Getting Started

- I am going to use [redux-thunk](https://github.com/gaearon/redux-thunk)
- and [redux-saga](https://github.com/redux-saga/redux-saga)

### What I learned after using redux-thunk

redux-thunk : Simply saying, this middleware gonna make action creator functions. Normal action creator makes only action object, but action creator made by redux-thunk could make mutiple actions.

Actually, redux-thunk is very simple to understand. I get it from redux-thunk/src/index.js.
```
function createThunkMiddleware(extraArgument) {
  return ({ dispatch, getState }) => next => action => {
    if (typeof action === 'function') {
      return action(dispatch, getState, extraArgument);
    }

    return next(action);
  };
}

const thunk = createThunkMiddleware();
thunk.withExtraArgument = createThunkMiddleware;

export default thunk;
```
When redux-thunk takes functional action, it would give dispatch and setState to function. 

