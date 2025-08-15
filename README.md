# REDUX-CORE-API-INTRO

### 1. WHAT is REDUX API
- Redux Apps follow the core principles of Redux 
- Redux Library tools help handle an app to follow core principles
- Redux API refers to functions and tools in the redux ecosystem to manage STATE
- Redux has core APIs for creating and managing a store, dispatching actions and reducers.
- Redux Toolkit and React-Redux offer additional APIs 
- Redux apps use one way data flow managed by the store
    - State → View → Actions → State → View … 
    - STATE->DISPATCHED ACTIONS->STORE's REDUCER->NEXT STATE
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

### 2. CREATE A REDUX STORE --createStore(reducerFunction)--
- createStore() is a Redux API tool from REDUX library
- A Reducer functions updates State. It receives actions --> returns the store's next state.
- The action object { type: , payload:} describes how to change the state
- The Store's function - Holds state
                       - Receives dispatched action
                       - Execute the reducer
                       - Enforces one way data flow
  
        - We can manually do what the store does: Execute a Reducer--
        newState = callReducerFunction(withCurrentState, { type: 'andAction' });

#### The Redux helper Function to Create a Store  
#### -- createStore(inputREDUCERFunction) --> Returns STORE OBJECT
- Store's structure:

        import { createStore } from 'redux';   --> 1st Import REDUX helper function:
          const initialState = 0                 --> 2nd render initialState
          export function ActionCreatorName() {     --> 3rd Create + export Action Creators
              return {type: `actiontype`}
          }
          const reducerName = (state=initialState, action) => {
              switch(action.type){
                  case'1':{                            --> 4th Create reducer with
                      return updatedState;                    types of actions
                  }
                  default: {
                      return state;
                  }
              }
          }
         export const store = createStore(takesInREDUCER_FUNCTION)
          --> 5th Create a 'store' object with a create store call
##### `createStore(inputREDUCER) --> returns STORE OBJECT`


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
- In REDUX a dispatched action of a store is listened to using this method:

    `store.subscribe(accepts_a_listener_argument)`
- When an action is dispatched to the `store` a change in state occurs and the listener is executed
  
      store.subscribe(stateChangeListenerFunction)
- The LISTENER is firee everytime state changes
  
- To execute an Action creator pass it to the store.dispatch():
  
          store.dispatch(actionCreator());
  
- The 'store.subscribe( )' also returns an unsubscribe function
- To stop listening to dispatches to the store to just call unsubscribe:
  
          unsubscribe()
### EXAMPLE
##### - 1st import store and action creators from store.js file to main.js file

    import { store, increment, decrement } from "./store"
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
        
### 6. CONNECT A REDUX STORE TO A UI
-REDUX without REACT lacks a user interface
- TO CONNECT A STORE TO REACT SO THAT REACT CAN MANGE STATE AND THEN SHOW THE USER

-App.js-file

        Store's action creators imported in
            import { actionCreator1, actionCreator2 } from "./store";
        Action creators are dispatched within click handlers if a buttons exist
            const clickHandlerFunction = () => {
                    dispatch(actionCreator1());
              }
        App component expects 2 props: state and dispatch passed from index.js
            function App({ state, dispatch}) {
                    return ( code to render here )
                }
-index.js-file

        Store is imported in --> import { store } from './store.js'
        Pass store and dispatch to App
        <App state={store.getState()} dispatch={store.dispatch} />);
        Subscribe a change listerner to the store 
                - so the UI is updated when state changes
                - subscribe the index.js render()
                - so App is always re-rendered when changes to state which
                - can update the UI for the user to see changes
        store.subscribe(listener); --> listener here is the render function
        store.subscribe(render);

  |REVIEW|NOTES|
  |:---|:---|
  | Redux library's createStore( )| Creates a store object|
  ||Holds the state|
  |Stores Methods:| store.getState() - gets current state|
  ||store.disptach(action) - dispatches action to store|
  ||store.subscribe(listener) - registers a function to respond to store changes |
  |actionCreators|creates multiple action objects|
  
  
  
