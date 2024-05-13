# 모듈상태를 전역으로 관리하는 방법

리액트에서 모듈 상태를 전역 상태로 사용하는 방법

## 모듈 상태(module state) 살펴보기

모듈 상태는 모듈 수준에서 정의된 변수다. 함수 외부에서 정의된 변수를 모듈 상태라고 가정하고
예시 코드를 살펴보자.

``` javascript
let state = {
    count: 0;
}
```

해당 객체가 모듈 상태라고 할 때, 객체에 접근하고 상태를 변경하는 함수를 정의해보자.

``` javascript
export const getState = () => state

export const setState = (newState) => {
    state = newState
}
```

함수를 사용해 상태를 갱신할 수 있게 setState를 수정할 수 있다.

``` javascript
export const setState = (newState) => {
    state = typeof nextState === 'function' ? newState(state) : newState

setState((state) => {
    return {
        ...state,
        count: state.count + 1
    }
})
}
```

모듈 상태를 직접 정의하지 않고, 상태와 상태에 접근할 수 있는 함수가 내부에 있는 컨테이너를 만들 수 있다.

``` javascript
export const createContainer = (initialState) =>
{
    let state = initialState
    const getState = () => state
    const setState = (newState) => {
        state = typeof newState === 'function' ? newState(state) : newState
    }
    return { getState, setState }

}
```

컨테이너는 다음과 같이 사용할 수 있다.

``` javascript
const { getState, setState } = createContainer({ count: 0 })
```

## 리액트에서 모듈 상태 사용하기

구독으로 모듈 상태 구현하는 에제

``` javascript
type Store<T> = {
    getState: () => T;
    setState: (action: T | ((prev: T) => T)) => void;
    subscribe: (callback: () => void) => void;
}

const createStore = <T extends unknown>(
    initialState: T
): Store<T> => {
    let state = initialState
    const callbacks = new Set<() => void>();
    const getState = () => state
    const setState = (nextState: T | ((prev: T) => T))=> {
        state = typeof nextState === 'function' ? (nextState as (prev: T) => T)(state) : nextState;
        callbacks.forEach((callback) => callback())
    }
    const subscribe = (callback: () => void) => {
        callbacks.add(callback)
        return () => {
            callbacks.delete(callback)
        }
    }

    return { getState, setState, subscribe}
}
```

createStore 사용하기

``` javascript
import { createStore } from './store'

const store = createStore({ count: 0 })
store.setState({ count: 1})
store.subscribe(...)
```

store의 상태 값과 갱신 함수를 튜플로 반환하는 사용자 정의 훅을 만들 수 있다.

``` javascript
const useStore = (store) => {
    const [state, setState] = useState(store.getState());

    useEffect(() => {
        const unsubscribe = store.subscribe(() => {
            setState(store.getState())
        });
        setState(store.getState())
        return unsubscribe
    }. [store])

    return [state, store.setState]
}
```

useStore 사용하기

``` javascript
const [state, setState] = useStore(store)

const inc = () => {
    setState((prev) => ({
        ...prev,
        count: prev.count + 1
    }))
}

return (
    <div>
        <h1>{state.count}</h1>
        <button onClick={inc}>Increment</button>
    </div>
)
```
