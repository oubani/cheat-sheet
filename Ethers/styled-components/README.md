# Styled components

## Basic Components

```javascript
import styled from "styled-compoenets";
export const Button = styled.button`
        height: 5px;
        ....
    `;
```

### Pass props to component

```javascript
    ...
    color: ${({color})=> color?color:"blue" }
```

### Effect and animations

```
    &:hover {
        color:'coral';...
    }
    &:active {
        color:'green';...
    }
```

### Access to childern inside a component

```
    &:hover {
        & label {
            color :'red'
        }
    }
```
