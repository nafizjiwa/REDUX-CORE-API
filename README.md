# Redux-API

- Is an application that follows the core principles of Redux built without a Redux Library
- Libraries provide tools for building a Redux apps while following Redux core principles

### STORE
- One tool from the Redux API is the createStore() method and its methods
    - store.getState( )              --> returns current value of the state
    - stote.dispatch(action)         --> dispatches action to the store
    - store.subsribe(listener)

- Reducer functions decide which action updates the state.
- The action (action object) describes how to change the state with its type property
- `createStore(reducerFunction)` a redux helper function creates a store object = 'store'
- The store enforces one-way data flow and provides methods
### DISPATCH ACTIONS
- store.dispatch( ) --> dispatches an action to the store to change the state
-    `store.dispatch(actionObject) --> with an AO the reducer function executed`
    ##### EXECUTE
      -->1st store.dispatch({ type: 'toggle'}) --> dispatches the action
      -->2nd Then store calls the reducer like so:
            `reducer(store.getState( ),{ type:'toggle'})`
            --> reducer receives current state and action type to change state
### ACTION CREATORS
- THEY RETURN AN ACTION OBJECT:
- 
            store.dispatch(action);
            store.dispatch(action);
            store.dispatch(action);
- Avoid writing identical multiple action objects as above --> USE AN ACTION CREATOR

    store.dispatch(actionCreator(returns actionObject{type: 'actionObject' }))
  
      export const actionCreator = ( ) => {       --> [ ACTION CREATOR ]
        return { type: "actionType" };        --> functions that return action 
       }                                   --> objects with a type property

#### Replace for the above three action Objects dispatched
            store.dispatch(actionCreator());
            store.dispatch(actionCreator());
            store.dispatch(actionCreator());

### RESPOND TO STATE CHANGES

- `store.subscribe( )` - Method used by the store to Listen and Respond to dispatched Actions
  
    `store.subscribe(changeListenerFunction)` --> Subscribes the Listener to the store
- State Change Listener is then executed whenever state changes in the store
  
- Then when Action creator is passed directly to the store.dispatch() the creator executes
  
              store.dispatch(actionCreator());
  
- 'store.subscribe( )' also returns an unsubscribe function which allow the listener to stop listening to store changes or dispatches made to the store

