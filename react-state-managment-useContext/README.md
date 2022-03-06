## folder structor

/context  
----/types.js  
----/Auth  
--------/authContext.js  
--------/authReducer.js  
--------/AuthState.js

### authContext.js file

create context then export it

import {createContext} from 'react';

const authContext = createContext();

export default authContext;

### AuthState.js file

import types, Context and reducer files;

``

### authReducer.js file

import types;

const authReducer = (action, state) => {

````
switch (actions.type) {
case LOGIN:
return {
...state,
auth: true,
};
case LOGOUT:
return {
...state,
auth: false,
};

    	default:
    		state;
    }

}

```

export default authReducer
```
````
