# REACT-QUICK-REFERENCE

### useState, Objects in State, Setting state from a Prevstate, Initialize State

        const [currentState, stateSetter] = useState( initialState );
        -------------------------------------------------------------
        Initialize state  
                         = useState(0)
                         = useState([array])
                         = useState({object})
                         = useState([ {obect}, {object}, {object} ])
                         = useState(Boolean)

CurrentState references the states current value <br />
initialState initializes the value of the state at first render <br />
stateSetter - sets the state <br />

Use a State setter callback function when our next value depends on our previous value.


    setProfile((prev)=> (                 ------ these brackets tells JavaScript that our curly brackets 
                                                        ----- refer to a new object to be returned
        {...prev,                         ------ ... `the spread operator` copies the previous state  
                                                        ----- into the new state
        `[name]`: value}                  ------  overwrites the appropriate KEY with its updated VALUE
        ));

This is the Computed Property [name]. <br />
Name allows us to use the string value stored by the name variable as a property key. So value = key 

        [name]: value    


### Function Component Effects
The useEffect() function has no return value as the Effect Hook is used to call another function. We pass the callback function, or effect, to run after a component renders as the argument of the useEffect() function. 

#### Where to Define Event Handlers 

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
    
To set an input box in REACT with an initial value of empty set the variable with useState

        const `[ text, setText ]`= useState('') this creates a state with an initial of empty space
to reset the input box back to an empty space use the set function.
        
        setText('') to clear a text box


A helper function to remove a specific id would look something like the following code:

const removeId = (`idToRemove`) => {
  setThoughts((passInArrayWithIds) => ArrayWithIds.filter((eachArrayValue) => eachArrayValueSpecific.id !== `idToRemove`));
};


