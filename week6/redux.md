## Redux

// 상태

```js

// BaseStore.ts

export default 
```
state = {}

// reducer 함수
reducer = (state, action) => {
    switch (action.type) {
        case 'increase':
        return {
            ...state,
            count: state.count + 1
        };
        default:
        return state;
    }
    return {
        ...state,
    }
}

dispatch(action) => {
    this.state = this.reducer(this.state, action);
    this.publish();
}


## Reflect