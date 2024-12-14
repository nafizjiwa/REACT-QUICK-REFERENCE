# REACT-QUICK-REFERENCE

### useState, Objects in State, Setting state from a Prevstate, Initialize State

        const [currentState, stateSetter] = useState( initialState );
        -------------------------------------------------------------
        InitialState  
                         = (0)
                         = ([array])
                         = ({object})
                         = ([ {obect}, {object}, {object} ])
                         = (Boolean)

CurrentState references the states current value <br />
initialState initializes the value of the state at first render <br />
stateSetter - sets the state <br />

### Function Component Effects
The useEffect() function has no return value as the Effect Hook is used to call another function. We pass the callback function, or effect, to run after a component renders as the argument of the useEffect() function. 

### Where to Define Event Handlers 

    Simple event handlers ---> inline in our JSX
    Complex event handlers ----> outside of our JSX.


### CleanUp effects

##### If useEffect() `returns` a function, then the Hook always treats that as the cleanup function

    useEffect(() => {
          First Argument or the (EFFECT)
      return () => {
            Return statement or (CLEAN UP) is optional
      };
    }, [ Second Argument or DEPENDENCY - optional ]); 

Second Argument is an array which determines when the effect runs

    
### Control When Hooks are Called
Dependency array is used to schedule or configure when our effect is called in the following ways:
useEffect(()=>{callback}, [array]);

        Dependency Array	        Effect called after first render & …
        undefined	                every re-render
        Empty array	                no re-renders
        Non-empty array	            when any value in the dependency array changes

### Fetch of the menu data

    useEffect(() => {
      get('/menu').then((response) => setMenuItems(response.data));
    }, []);

### TO FIND NEXT VALUE FROM PREVIOUS VALUE use a State setter callback function.


    setProfile((prev)=> (                 ------ these brackets tells JavaScript that our curly brackets 
                                                        ----- refer to a new object to be returned
        {...prev,                         ------ ... `the spread operator` copies the previous state  
                                                        ----- into the new state
        `[name]`: value}                  ------  overwrites the appropriate KEY with its updated VALUE
        ));

### [name] This is the Computed Property
Name allows us to use the string value stored by the name variable as a property key. So A String Value = key 

        [name]: value    
    
### Create an input box with an initial value of empty `useSate`

        const [ text, setText ]= useState('') this creates a state with an initial of empty space
        
To reset an input box back to an empty space use the set function.
        
        setText('') to clear a text box


<br />
### A helper function to remove a specific id would look something like the following code:

      const functionToRemoveId = (idToRemove) => {
         setterFunction((passInArrayWithIds) => 
                                         ArrayWithIds.filter((eachArrayValue) => 
                                                                 eachArrayValueSpecific.id !== idToRemove));
      };

removeThought={removeThought}

### Passing Props
`App.js file`

        function ParentComponent(){
                return (
                        <ChildComponent 
                                propertyName=`{ nameOfFunctionPassedDown }`
                                        -passing this function allows us to use it
                                        - in the Child component
                                clickHandler = { clickHandlerFunction }
                                propertyName = `{nameOfPropertyPassedDown}`
                        />
                )
        }

`Child.js file` child uses the function or displays something on screen <br/>

        function Child(props){
                return (
                      <div>
                        <img 
                        src=`{props.src}`
                        />
                        <button onClick={props.clickHandler}>
                                Click Me
                        </button>
                      </div>
                );
        }

### Passing a function as a prop:
clickHandler is a function passed from parent (App)  to child (Banner) </br>
The child destructures the values name and clickHandler from props object </br>

        const Banner = ({ name, clickHandler }) => {
          return (
            <div>
              <p>Hello {name}</p>
              <button onClick={clickHandler}>Click Me</button>
            </div>
          )
        }
Here the parent App sends 2 properties to Banner component </br>
1. The property name as Jason
2. The property clickHandler as the function showAlert

        function App() {
          function showAlert (){
           alert("Welcome!")
          }
          //const showAlert = () => {
          //  alert("Welcome!")
          // }
        
          return (
            <div>
              <Banner name="Jason" clickHandler={showAlert} />
            </div>
          )
        }

#### ACCEPTING A PROP IN A FEW WAYs:

| Methods | An Example in Function |How its used in Function | Description | Example |
|:--------- | ---------- | ---------- | ---------- |---------- |
| Accept props as parmeters  |functionName(props) { } |  props.propertyName | Then use required properties in the function||
| Destructure ojbect with properites as parameters  | functionName({propertyName}) { } | propertyName | Then use just propteryName anywhere in function||
| Destructure properties within the function  | functionName(props) { } | const { propertyName } =props | Then once destructured use propertyName anywhere ||

### STYLING

#### INLINE STYLING:

`<h1 style={{color: "red"}}> Hello, World! </h1>` <br/>

Double curly braces to inject a JavaScript object literal into JSX. 
{first curlies inidcate insertion of JavaScript into JSX}
{{second curlies signal an object literal injected into JSX }}

#### OBJECT VARIABLE

Define object variable styles with name myStyle ->
const myStyle = { <br/>
color: "red" <br/> 
} <br/>
- To apply the styles:
`<h1 style={myStyle}> Hello, World! </h1>` <br/>

#### MULTIPLE STYLE SHEETS

import './App.css' <br/>
import './Style.css' <br/>

When multiple style sheet cause a clash with className we can use a module

#### CSS MODULE FILE

Import it as a module, the stylesare available to the component that imported the style.
Then create unique class names for each module.
Then some class names we’ve used across stylesheets.

-> fileName is the name of the component you’re styling: <br/>
fileName.module.css---so the css for the file `fileName` is found in a file only for itself not in a common style.css file
not
style.css

import styles first like from `"./App.module.css";` --- go to file App.module.css to get the styles for App and store in a styles object

        import styles from "./App.module.css"; ---> styles is object

        function App() {
          return (
                <>
                      <div className={styles.Wrapper}> {objectName.className}
                </>



