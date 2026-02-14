# Redux-Play

```linux
npm init --yes
// Initializes package.json file with initial settings.
npm install redux
// It will add a dependdency entry for redux in package.json
// crate a file called index.js
To run: node index
```
```text
1. Store holds state of our applic.
2. An action that describes what happened in the applic.
3. A reducer which handles the action and decides how to update the state.
```
# Redux tool kit 3 principles:
```text
1. The global state of your applic is stored as an object inside a single store.
Maintain our applic state in a single object which would be managed by the redux store.
2. The only way to change the state is to dispatch an action, an object that describes what happened.
To update the state of your app, u need to let Redux know about that with an  action.
Not allowed to directly update the state object.
3. To specify how that state  tree is updated based on actions, you write pure reducers.
Reducer- (PreviousState,action)=>new state
```
# Actions
```text
1. The only way your applic can interact with store.
2. Carry some inf from your app to redux store.
3. Plain JS objects.
4. Have a 'type' property that describes something that happened in the applic.
5. The 'type'   property is typically defined as string constants.
```
# index.js: Actions example
```js
// type of action
const Cake_Ordered='Cake_Ordered'
//Action creator(is a func that returns object).
// Action creator-creates an action. In code its simplyits a func that returns an action.
function orderCake(){
return{
  //Define action
  type:Cake_Ordered,
  quantity: 1,
}
}
```
# Reducers
```text
1. Specify how the app's state chnages in response ro actions sent to store.
2. Func that accepts state and action as args, and returns the next state of the applic.
(prevState,action)=>newState
```
# Example that demonstrates actions and reducers:
```js
// type of action
const Cake_Ordered='Cake_Ordered'
//Action creator(is a func that returns object).
// Action creator-creates an action. In code its simplyits a func that returns an action.
function orderCake(){
return{
  //Define action
  type:Cake_Ordered,
  quantity: 1,
}
}
// Reducer takes abojects as arg
const initialState={
    numofCakes:10,
}
const reducer=(state=initialState,action)=>{
    switch(action.type)
    {
        case Cake_Ordered:
            return {
                numofCakes:state.numofCakes-1,
            }
            default:
                return state
    }
}
```
```text 
what if we have multuple objects and we have to change only few:
1st create a copy using spread op and change only what required to change.
```
```js
// type of action
const Cake_Ordered='Cake_Ordered'
//Action creator(is a func that returns object).
// Action creator-creates an action. In code its simplyits a func that returns an action.
function orderCake(){
return{
  //Define action
  type:Cake_Ordered,
  quantity: 1,
}
}
// Reducer takes abojects as arg
const initialState={
    numofCakes:10,
    extraVae:0,
}
const reducer=(state=initialState,action)=>{
    switch(action.type)
    {
        case Cake_Ordered:
            return {
                ...state,
                numofCakes:state.numofCakes-1,
            }
            default:
                return state
    }
}
```
# Redux store
```text
One store for the entire applic.
Responsibilites:
> Holds applic state
>Allows access to state via getState()
> Allows state to be updated via dispatch (action)
> Registers listeners via subscriber (listener)
> Handles unregistering of listeners via the func returned by subscriber(listener).
```

