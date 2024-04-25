# 상태관리

> 요즘 제일 고민이 많은 상태관리에 대해 공부하며 정리한 내용입니다.  
> 참고 도서 : 리액트 훅을 활용한 마이크로 상태 관리 ( 다이시 카토 지음 )

## 마이크로 상태관리

범용적인 상태 관리 방법은 가볍고, 유연해야한다.
마이크로 상태관리는 다음과 같은 기본적인 상태 관리 기능이 필요한다.

1. 상태 읽기
2. 상태 갱신
3. 상태 기반 렌더링

그 외 추가적으로 필요한 기능들

1. 리렌더링 최적화
2. 다른 시스템과의 상호 작용
3. 비동기 지원
4. 파생 상태
5. 간단한 문법

다양한 마이크로 상태 관리 방법을 공부하고, 현재 프로젝트에 어떤 방법이 적합한지 고민해보자.

## React Hook

리액트에는 기본적으로 제공하는 상태관리 hook이 있다.  

1. useState
2. useReducer
3. useEffect

### useState

useState를 사용한 간단한 예제

``` javascript
// useState가 count의 상태를 관리한다.
const Component = () => {
    const [count, setCount] = useState(0);

    return (
        <div>
            {count}
            <button onClick={()=>{setCount(c => c + 1)}}>
            +1
            </button>
        </div>
    )
}
```

``` javascript
// useCount hook으로 분리
const useCount = () => {
    const [count, setCount] = useState(0);
    return [count, setCount];
}

const Component = () => {
    const [count, setCount] = useCount();

    return (
        <div>
            {count}
            <button onClick={()=>{setCount(c => c + 1)}}>
            +1
            </button>
        </div>
    )
}
```

useCount를 hook으로 분리하면 두가지 관점을 생각할 수 있다.

1. Component와 useCount가 분리되어 관심사가 분리된다.
2. useCount라는 이름으로 어떤 상태를 관리하는지 명확해졌다.

count를 사용하는 코드에 다른 코드가 추가되어도 Component는 아무 영향을 받지 않는다.  

useSate 상태 갱신하는 방법을 알아보자.

#### 값으로 갱신

state에 새로운 값을 넣어주면 상태가 변경된다. 주의할 점은 useState는 이전 값과 동일한 값이 들어오면 리렌더링이 되지 않는다.

``` javascript
// 깂이 변경되면 리렌더링이 된다.
const Component = () => {
    const [count, setCount] = useState(0);

    return (
        <div>
            {count}
            <button onClick={()=>{setCount(c => c + 1)}}>
            1로 변경
            </button>
        </div>
    )
}
```

``` javascript
// 처음 버튼을 눌렀을 때만 리런뎅이 되고, 그 이후에 버튼을 눌러도 리렌더링이 되지 않는다. 
const Component = () => {
    const [count, setCount] = useState(0);

    return (
        <div>
            {count}
            <button onClick={()=>{setCount(1)}}>
            1로 변경
            </button>
        </div>
    )
}
```

### useReducer

리듀서는 복잡한 상태에 유용하다.

``` javascript
// useReducer를 사용한 간단한 예제
const reducer = (state, action) => {
    switch(action.type) {
        case 'INCREMENT':
            return {...state, count: state.count + 1};
        case 'SET_TEXT':
            return {...state, text: action.text};
        default:
            throw new Error('unknown action type')
    }
}

const Component = () => {
    const [state, dispatch] = useReducer(
        reducer,
        { count: 0, text: 'hi'}
    );

    return (
        <div>
            {state.count}
            <button onClick={()=>dispatch({ type: 'INCREMENT' })}>
                Increment count
            </button>
            <input
                value={state.text}
                onChange={(e) => dispatch({ type: 'SET_TEXT', text: e.target.value})}
            />
        </div>
    )
}
```

useReduce 베일 아웃 발생시키기

``` javascript
const reducer = (state, action) => {
    switch(action.type) {
        case 'INCREMENT':
            return {...state, count: state.count + 1};
        case 'SET_TEXT':
            // state 자체를 변경하면 리렌더링이 되지 않는다.
            if(!action.text) {
                return state
            }
            return {...state, text: action.text};
        default:
            throw new Error('unknown action type')
    }
}
```

### useSate와 useReducer

useReducer를 이용한 useState 구현하기

``` javascript
    const useState = (initialState) => {
        const [state, dispatch] = useReducer(
            (prev, action) => 
            typeof action === 'function' ? action(prev) : action, initialState
        )
        return [state, dispatch];
    }
```
