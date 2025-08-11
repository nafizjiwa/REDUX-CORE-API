# REDUX-CORE-API

- Redux Apps follow the core principles of Redux 
- Redux Library tools help handle an app to follow core principles
- Redux API refers to functions and tools in the redux ecosystem to manage STATE
- Redux has core APIs for creating and managing a store, dispatching actions and reducers.
- Redux Toolkit and React-Redux offer additional APIs 
- Redux apps use one way data flow managed by the store
    - STATE->DISPATCHED ACTIONS->STORE's RREDUCER->NEXT STATE
- CORE REDUX API'S ARE
    - createStore
    - combineReducers
    - applyMiddleware
- REDUX TOOLKIT API'S ARE
    - configureStore
    - createSlice
    - Query API's
- REACT REDUX API'S ARE
    - Provider
    - useSelector
    - useDipatch
    - connect

### CREATE A REDUX STORE
- Create a Redux App with a Redux API tool called createStore() method and its methods
    - store.getState( )              --> returns current value of the state
    - stote.dispatch(action)         --> dispatches action to the store
    - store.subsribe(listener)

- Reducer functions describes how a state is updated with actions and returns the next state of the store.
- The action (action object) describes how to change the state using its type property
- Store's function - execute the reducer with state and action
                  - enfores on way data flow
  
    --Manually do what the store does--
    newState = callReducerFunction(withCurrentState, { type: 'andAction' });

#### Redux helper Function
- `createStore(takesInReducerFunction)` -  to create a 'store'
- Store - is an object
          1. Holds state,
          2. Receives action dispatches and
          3. Executes the reducer.
- 
### DISPATCH ACTIONS TO THE STORE
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

