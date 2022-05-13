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

`
const AuthState = ({children}) => {
const initialState = {
isAuth:false,
user:null
}

    	<!-- initial reducer -->
    	const [state,dispatch] = useReducer(AuthReducer,initialState);

    	<!-- actions -->

    	const login = async (email,password) => {
    		response
    		dispatch({type:LOGIN,payload:{user}})
    	}
    	return (<AuthContext.Provider> {children} </AuthContext.Provider>)

    }

export default AuthState
`

### authReducer.js file

import types;

const authReducer = (action, state) => {

`
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
    		return state;
    }

}

`

export default authReducer

```

```

## Wrapp App with AuthState
