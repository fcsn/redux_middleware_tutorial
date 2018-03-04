# tutorial of redux middleware

## Getting Started

- I am going to use [redux-thunk](https://github.com/gaearon/redux-thunk)
- and [redux-saga](https://github.com/redux-saga/redux-saga)

### What I learned after using redux-thunk

redux-thunk : Simply saying, this middleware gonna make action creator functions. Action creator usually makes only action object, but action creator made by redux-thunk could make mutiple actions.

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

### What I learned after using axios

axios is Promise based HTTP client for the browser and node.js. 
First, I'm going to use GET request. At *post.js* , I made a function named *getPost* that returns Promise named *getPostAPI* . It will dispatch GET_POST_PENDING when it start GET request. And it will dispatch GET_POST_SUCCESS when it succeed in requesting. It also has *.catch* method for error.

And I use getPost function in *componentDidMount* , then it could invoke it's post title and body.
```
componentDidMount() {
        const { number, PostActions } = this.props;
        PostActions.getPost(number);
    }
```





