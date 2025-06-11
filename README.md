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
      `store.dispatch(actionObject) --> this executes the reducer function`
##### EXECUTE
      --> store.dispatch({ type: 'toggle'}) --> dispatches an action
      --> then store calls the reducer like so:
            --> reducer(store.getState( ), { type:'toggle'})
            --> reducer gets current state and use it with action type to change state
### ACTION CREATORS
            store.dispatch(actionObject);
            store.dispatch(actionObject);
            store.dispatch(actionObject);
- Dispatching multiple actions --> reduce repitition --> Instead Use ACTION CREATORS
- ACTION CREATORS show the actions available to dispatch to the store
  
      export const actionTypeName = ( ) => {       --> [ ACTION CREATOR ]
        return { type: "actionTypeName" };        --> functions that return action 
       }                                   --> objects with a property of type

#### Replace for the above three action Objects dispatched
            store.dispatch(actionCreator());
            store.dispatch(actionCreator());
            store.dispatch(actionCreator());

### RESPOND TO CHANGES

- Actions dispatched to the 'store' are listened for and responded to with 'store.subscribe( )'
- 'store.subscribe(listenerFunction)' --> Subscribes the Listener Function to the store
  
        Action creators can be passed directly to the store.dispatch()
              store.dispatch(actionCreator());
- 'store.subscribe( )' also returns an unsubscribe function to stop listening to store changes or dispatches made to the store
