## folder structor

/context
----/types.js
----/Auth
--------/authContext.js
--------/authReducer.js
--------/AuthState.js

### authContext.js file

import {createContext} from 'react';

const authContext = createContext();

export default authContext;

### AuthState.js file
