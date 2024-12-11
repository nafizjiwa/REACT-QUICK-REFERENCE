# REACT-QUICK-REFERENCE

### Objects in State

setProfile((prev)=> (
    {...prev, [name]: value}
    ));

    
This tells JavaScript that our curly brackets refer to a new object to be returned. We use ..., the spread operator, to fill in the corresponding fields from our previous state. Finally, we overwrite the appropriate key with its updated value.

[name]: value

This Computed Property Name allows us to use the string value stored by the name variable as a property key.
