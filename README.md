# REACT-QUICK-REFERENCE

### Objects in State
Use state setter callback function when our next value depends on our previous value.
copy the previous state into the next state like 

    setProfile((prev)=> (                 ------ these brackets tells JavaScript that our curly brackets 
                                                        ----- refer to a new object to be returned
        {...prev,                         ------ ..., the spread operator fills in the corresponding 
                                                        ----- fields from our previous state
        `[name]`: value}                  ------  overwrites the appropriate key with its updated value
        ));

This is the Computed Property. Name allows us to use the string value stored by the name variable as a property key.

        [name]: value    

const [currentState, stateSetter] = useState( initialState );

The currentState references the current value of the state and initialState initializes the value of the state for the component’s first render.

The useEffect() function has no return value as the Effect Hook is used to call another function. We pass the callback function, or effect, to run after a component renders as the argument of the useEffect() function. 

define simple event handlers inline in our JSX and complex event handlers outside of our JSX.


### Some effects require cleanup

##### `If useEffect() returns a function, then the Hook always treats that as the cleanup function`

useEffect(() => {
      First Argumet or the EFFECT
  return () => {
        Return statement or CLEAN UP is optional
  };
}, [ Second Argument or DEPENDENCY]); 

