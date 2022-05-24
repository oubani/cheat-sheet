# redux toolkit

## 1 - create store

```
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './features/Counter/counterSlice';

export default configureStore({
	reducers: {
		counter: counterReducer,
	},
});
```

## 2 - create counter reducer or slice

```
import {createSlice} from '@reduxjs/toolkit';
export const counterSlice = createSlice({
    name:'counter',
    initialState:{
        value:5,
    }
    reducers : {
        increment : (state)=> {state.value+=1},
        incrementByAmount : (state,payload)=> {state.value+=payload},
    }
})

// export reducers
export { increment,incrementByAmount}  = counterSlice.actions;

export value

export selectCount = state => state.counter.value

export default counterSlice.reducer

```

## 3 - use in component

import reducers actions from
reducer and useSelector and use dispatch from React

```
import {useDispatch, useSelector} from 'react-redux'
import {increment ,selectCount ....} from '....'

in Compornenet () {

    //getDate
    const count = useSelector(selectCount);
    const dispatch = useDipatch();

    in jsx

    (<> {count}  () => dispatch(increment())  </>  )

}


```
