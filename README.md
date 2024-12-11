# REACT-QUICK-REFERENCE

### useState, Objects in State, Setting from a Prevstate

        const [currentState, stateSetter] = useState( initialState );

CurrentState references the states current value 
initialState initializes the value of the state at first render
stateSetter - sets the state

Use State setter callback function when our next value depends on our previous value.


    setProfile((prev)=> (                 ------ these brackets tells JavaScript that our curly brackets 
                                                        ----- refer to a new object to be returned
        {...prev,                         ------ ..., the spread operator copies the previous state  
                                                        ----- into the new state
        `[name]`: value}                  ------  overwrites the appropriate key with its updated value
        ));

This is the Computed Property. Name allows us to use the string value stored by the name variable as a property key.

        [name]: value    


### Function Component Effects
The useEffect() function has no return value as the Effect Hook is used to call another function. We pass the callback function, or effect, to run after a component renders as the argument of the useEffect() function. 

#### Where to Define Event Handlers 

    Simple event handlers ---> inline in our JSX
    Complex event handlers ----> outside of our JSX.


### CleanUp effects

##### If useEffect() `returns` a function, then the Hook always treats that as the cleanup function

    useEffect(() => {
          First Argumet or the EFFECT
      return () => {
            Return statement or CLEAN UP is optional
      };
    }, [ Second Argument or DEPENDENCY - optional ]); 

Second Argument is an array which determines when it runs

    
### Control When Hooks are Called
The dependency array is used to schedule or configure when our effect is called in the following ways:

        Dependency Array	        Effect called after first render & …
        undefined	                every re-render
        Empty array	                no re-renders
        Non-empty array	            when any value in the dependency array changes

### Fetch of the menu data

    useEffect(() => {
      get('/menu').then((response) => setMenuItems(response.data));
    }, []);
