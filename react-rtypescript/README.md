# React with typescript

## Hooks

### UseReducer Hook

```
import React, { useReducer } from 'react';

type Actions = { type: 'add'; text: string } | { type: 'remove'; idx: number };

interface Todo {
text: string;
complited: Boolean;
}
type State = Todo[];

const TodoReducer = (state: State, action: Actions) => {
switch (action.type) {
case 'add':
return [...state, { text: action.text, complited: false }];
case 'remove':
return state.filter((\_, i) => i !== action.idx);

    	default:
    		return state;
    }

};
export const ReducerExemple: React.FC = () => {
const [todos, dispatch] = useReducer(TodoReducer, []);

    return (
    	<div>
    		{JSON.stringify(todos)}
    		<button
    			onClick={() => {
    				dispatch({ type:"remove",idx:5 });
                    dispatch({type:"add",text:"........"})
    			}}></button>
    	</div>
    );

};
```
