# REDUX-CORE-API-INTRO

### 1. WHAT is REDUX API
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

### 2. CREATE A REDUX STORE
- createStore() is a Redux API tool 
- A Reducer functions updates State. It receives actions --> returns the store's next state.
- The action object describes how to change the state
- Store's function - execute the reducer 
                   - enforces one way data flow
  
        --Manually do what the store does execute Reducer--
        newState = callReducerFunction(withCurrentState, { type: 'andAction' });

#### The Redux helper Function to Create a Store
- 1st Import the funciton:

        import { createStore } from 'redux';
- 2nd Call it to create a 'store' object

        export const store = createStore(takesInREDUCER_FUNCTION)
- Store: </br>
          1. Holds state, </br>
          2. Receives action dispatched and </br>
          3. Executes the reducer. </br>
 
### 3. DISPATCH ACTIONS TO THE STORE
- A Redux App created with Redux API tool createStore() method has access to other `STORE` methods of state
    - `store.getState( )`              --> returns current value of the state
    - `store.dispatch({ type:'action' })`       --> dispatches an action to the store's reducer to change the state
    - `store.subsribe(listener/actionObject)`   --> With an AO the reducer function executed`
- Store Calling Reducer

        storeReducer(store.getState(), { type: 'toggle' });

  ##### HOW ITS EXECUTED
      -->1st store.dispatch({ type: 'toggle'}) --> dispatches action of type 'toggle'
      -->2nd Then store calls the reducer like so:
            `reducer(store.getState( ),{ type:'toggle'})`
            --> reducer receives current state and action type 'toggle' to change state
### 4. ACTION CREATORS
- They reduce the repetitive creation of the same action 

          store.dispatch(actionObject1); ---> action object
          store.dispatch(actionObject1); ---> action object
          store.dispatch(actionObject1); ---> action object
- To Avoid writing multiple identical action objects --> USE AN ACTION CREATOR

      store.dispatch(ACTION_CREATOR_FUNC(returns ActionObject-->{type: 'actionType' }))
-
      export const ACTION_CREATOR_FUNCTION = ( ) => {       --> functions that
        return { type: "actionType" };             --> returns an ACTION OBJECT
       }                                           --> with a type property = an action type

##### Replace above three action Object dispatches with 3 function calls to action creators 
            store.dispatch(call_actionCreator()) X 3
        
### 5. RESPOND TO STATE CHANGES
- Applications with user interaction triggering DOM events as a 'click' are listened to by event listeners.
- In REDUX a dispatched action of a store are listened to using this method:

    `store.subscribe(accepts_a_listener_argument)`
- When an action is dispatched to the `store` a change in state occurs and the listener is executed
  
      store.subscribe(stateChangeListenerFunction)
- This connection allows the listener to automatically fire everytime state changees
  
- Then when Action creator is passed directly to the store.dispatch() the creator executes
  
          store.dispatch(actionCreator());
  
- The 'store.subscribe( )' also returns an unsubscribe function
- To stop listening to dispatches to the store to just call unsubscribe:
  
          unsubscribe()
### EXAMPLE
// Define your change listener function.

       const printCountStatus=()=>{
          console.log(`The count is ${store.getState()}`);
        }
// Subscribe the listener function to the store 

        store.subscribe(printCountStatus)
// Below we: Dispatch the actions to the store</br>
// and Check their changes in state</br> 

    store.dispatch(decrement()); 
        // Listener fires so console --> The count is -1
    store.dispatch(increment());
        // Listener fires so console --> The count is 0
    store.dispatch(increment());
        // Listener fires so console --> The count is 1

