# Redux-API

- Is an application that follows the core principles of Redux built without a Redux Library
- Libraries provide tools for building a Redux apps while following Redux core principles

### STORE
- One tool from the Redux API is the createStore() method and its methods
    - store.getState( )              --> returns current value of the state
    - stote.dispatch(action)         --> dispatches action to the store
    - store.subsribe(listener)

- Reducer functions decide which action updates the state.
- The action object describes how to change the state with its type property
- 'createStore(reducerFunction)' a redux helper function creates a store object = 'store'
- The store enforces one-way data flow and provides methods
### DISPATCH ACTIONS
- store.dispatch( ) --> dispatches action to the store for a state change
    - store.dispatch(actionObject) --> this executes the reducer function
##### EXECUTE
      --> store.dispatch({ type: 'toggle'}) --> dispatches an action
      --> then store calls the reducer like so:
            --> reducer(store.getState( ), { type:'toggle'})
            --> reducer gets current state and use it with action type to change state
### ACTION CREATORS
            store.dispatch(actionObject);
            store.dispatch(actionObject);
            store.dispatch(actionObject);
- When dispatching multiple actions --> reduce repitition --> Use an ACTION CREATORS
- ACTION CREATORS also show the actions available to dispatch to the store
  
        export const actionType = ( ) => {       --> ACTION CREATOR
          return { type: "actionType" };        --> functions that return action 
        }                                   --> objects with a property of type

        store.dispatch(actionCreator());
               
        store.dispatch(toggle( )); // Toggles the light to 'off'
        store.dispatch(toggle( )); // Toggles the light back to 'on'
        store.dispatch(toggle( )); // Toggles the light back to 'off'
### RESPOND TO CHANGES

- Actions dispatched to the 'store' are listened for and responded to with 'store.subscribe( )'
- 'store.subscribe(listenerFunction)' --> Subscribes the Listener Function to the store
- 'store.subscribe( )' it also returns an unscribe function to stop listening to store changes
