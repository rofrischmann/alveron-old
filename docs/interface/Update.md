# Update

(*Object|Function*)

> This is basically your Redux reducer.

Update describes how the model (state) can be changed with different actions.<br>
It has a basic reducer signature which is *(previousState, action) => state*.<br>

The reducer function should always be **pure** and use immutable data structures.<br>
Therefore, it should always return a new *state* and **not** mutate the *previousState.*

## Action
The action is an object created with [redux-actions](https://github.com/acdlite/redux-actions) and follows the [FSA shape](https://github.com/acdlite/flux-standard-action).<br>
It has the following components:

* **type** (*string*): automatically generated by alveron
* **payload?** (*any*): any payload passed to the [action dispatcher](View.md#action-dispatcher)
* **error?** (*boolean*): identifies if an error happened


## Update Shape
There are two ways to define update.<br>
We can either pass a single reducer function or an object with named reducer functions.

### Single reducer function
```javascript
const update = (state, action) => ({
  ...state,
  [action.payload.id]: action.payload.data
})
```

### Object with named reducer functions
```javascript
const update = {
  increment: state => state + 1
  decrement: state => state - 1
  incrementBy: (state, { payload }) => state + payload,
  decrementBy: (state, { payload }) => state - payload
}
```