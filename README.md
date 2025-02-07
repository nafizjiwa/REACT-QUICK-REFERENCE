# REACT-QUICK-REFERENCE
### REACT FORMS: Inputs `<input>` and Labels `<label>`

#### TYPES OF INPUTS - TEXT, CHECKBOX, RADIO BUTTON. Change the type by changing the type's value which by default its text.<br/>

        VALUE --> type="checkbox" for a checkbox
              --> type="radio" for a radio button

      <label>
        Text input: <input name="myInput" />
      </label>
      <label>
        Checkbox: <input type="checkbox" name="myCheckbox" />
      </label>
      <p>
        Radio buttons:
        <label>
          <input type="radio" name="myRadio" value="option1" />
          Option 1
        </label>
      </p>
      
#### Inputs typically are NESTED, `<input/>` inside a `<label> <input/> </label>` tag. Notifies to the browser the tags are associated, so when a label is clicked the browser focuses on associated input. <br/>

        *Important for the screen reader so it can focums on the input.<br/>

#### If NOT NESTED we associate <input> and <label> with the same value for `id` and `htmlFor` <br/>

        <input id ={ageInput} > and <label htmlFor={ageInput}>. 

#### To Specify an Initial Value for an input use 
        
        defaultValue="Some initial value"
#### To Read the input values when submitting a form

        Add a <form> around <inputs/> within the form add a submit button
                <button type="submit">Submit form</button>. 
                
The button will call the `<form onSubmit>` event handler (below example it is handleSubmit). 

        --> <form method="post" onSubmit={handleSubmit}>
            </form>
Browser default is to send the form data to the current URL and refresh the page.
To override this behavior call 

                --> e.preventDefault().

              
### useState, Objects in State, Setting state from a Prevstate, Initialize State

        const [currentState, stateSetter] = useState( initialState );
        -------------------------------------------------------------
        InitialState     = (0)
                         = ([array])
                         = ({object})
                         = ([ array: {obect}, {object}, {object} ])
                         = (Boolean)

CurrentState - current state value <br />
initialState - initializes the VALUE of the state at first render <br />
stateSetter - Funciton changes state <br />

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
The child destructures the values name prop and clickHandler function from the props object </br>
Destructuring unpacks values from arrays, or properties from objects, into distinct variables. </br>

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
        const myStyle = { 
                        color: "red" 
                } 
- To apply the styles:
`<h1 style={myStyle}> Hello, World! </h1>` <br/>

#### MULTIPLE STYLE SHEETS

import './App.css' <br/>
import './Style.css' <br/>

Multiple style sheets can cause a clash with className so use a MODULE FILE

#### CSS MODULE FILE

Importing as a module, the styles are available to the component that imported the styles.<br/>
We can create unique class names for each module.<br/>
We can a general class names across stylesheets.<br/>

-> SYNTAX<br/>
fileName.module.css<br/>
---> so the css STYLES are found in a file which is `fileName` not in a common stylesheet style.css file<br/>
-> fileName is usually the name of the component you’re styling: <br/>

import styles first like from `"./App.module.css";` --- go to file App.module.css to get the styles for App and store in a styles object

        import styles from "./App.module.css"; ---> styles is the created object

        function App() {
          return (
                <>
                      <div className={styles.Wrapper}> {objectName.className}
                </>



