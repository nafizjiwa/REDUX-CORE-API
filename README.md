# Redux-API

- Is an application that follows the core principles of Redux built without a Redux Library
- Libraries do provide useful tools for building a Redux application while following Redux core principles.
- One tool from the Redux API is the createStore() method and its methods
    - store.getState()
    - stote.dispatch(action)
    - store.subsribe(listener)

//Redux apps use Reducer functions to decide which action updates the state to the next state.
//The store enforces one-way data flow 
//store=createStore(reducerFunction) 'a redux helper function' creates a store object
//One method dispatches action to the store to update state
//store.dispatch(actionObject)
//The action object describes how to change the state with its type property
// First, Import createStore here

