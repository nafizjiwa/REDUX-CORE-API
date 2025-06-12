# REACT-Redux-API

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
- `store.dispatch(actionObject) --> with an AO the reducer function executed`
  
  ##### EXECUTE
      -->1st store.dispatch({ type: 'toggle'}) --> dispatches the action
      -->2nd Then store calls the reducer like so:
            `reducer(store.getState( ),{ type:'toggle'})`
            --> reducer receives current state and action type to change state
### ACTION CREATORS
- They reduce the repetitive creation of action objects
          store.dispatch(actionObject1);
          store.dispatch(actionObject1);
          store.dispatch(actionObject1);
- Avoid writing multiple identical action objects --> USE AN ACTION CREATOR
- THEY RETURN AN ACTION OBJECT</br>

     store.dispatch(ACTION_CREATOR(returns ActionObject {type: 'actionObject' }))
  
      export const ACTION_CREATOR = ( ) => {       --> functions that
        return { type: "actionType" };             --> return an action object
       }                                           --> with a type property

#### Replace for the above three action Objects dispatched
            store.dispatch(actionCreator());
            store.dispatch(actionCreator());
            store.dispatch(actionCreator());

### RESPOND TO STATE CHANGES

    `store.subscribe(listener)`
- Register a State Change Listener to the store so it can respond to
- Dispatched actions and changes to the store
  
      store.subscribe(stateChangeListenerFunction)
- This connection allows the listener to automatically fire everytime state changees
  
- Then when Action creator is passed directly to the store.dispatch() the creator executes
  
          store.dispatch(actionCreator());
  
- The 'store.subscribe( )' also returns an unsubscribe function which allows the listener to stop listening to dispatches to the store just call it
  
          unsubscribe()
### EXAMPLE
// Define your change listener function.

       const printCountStatus=()=>{
          console.log(`The count is ${store.getState()}`);
        }
// Subscribe change listener function to the store 

        store.subscribe(printCountStatus)
// Dispatch the actions to the store</br>
// Check their changes in state</br> 

    store.dispatch(decrement()); 
        // Listener fires so console --> The count is -1
    store.dispatch(increment());
        // Listener fires so console --> The count is 0
    store.dispatch(increment());
        // Listener fires so console --> The count is 1

