# REACT-QUICK-REFERENCE

### Objects in State
Use state setter callback function when our next value depends on our previous value.
copy the previous state into the next state like 

setProfile((prev)=> (
    {...prev, [name]: value}
    ));

    
This tells JavaScript that our curly brackets refer to a new object to be returned. We use ..., the spread operator, to fill in the corresponding fields from our previous state. Finally, we overwrite the appropriate key with its updated value.

[name]: value

This Computed Property Name allows us to use the string value stored by the name variable as a property key.

const [currentState, stateSetter] = useState( initialState );

The currentState references the current value of the state and initialState initializes the value of the state for the component’s first render.

State setters can be called in event handlers.

define simple event handlers inline in our JSX and complex event handlers outside of our JSX.
