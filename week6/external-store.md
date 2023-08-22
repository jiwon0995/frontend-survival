## 👀 관심사의 분리

관심사 분리는 프로그램을 작은 단위로 나눠서 각 단위가 하나의 관심사(UI, 비지니스 로직 수행, data access 등)에만 집중하도록 만드는 것이다.   

- 작은 단위로 나누면 유지보수와 테스트가 쉬워진다.
- 코드 재사용성이 높아진다.

---

## 📍 Layered Architecture

계층화 아키텍쳐는 관심사 분리에 사용되는 아키텍쳐다.    
각 계층은 관심사로 분리되어 있고, 하위 계층은 상위 계능의 기능을 사용할 수 없다.

<br/>

### Layer

<span style="color:lightgreen">Presentation Layer</span> :   
- 유저와 가장 가까운 계층
- 유저의 입력을 받고, 유저에게 결과를 보여준다.
- UI를 담당한다.   

<span style="color:lightgreen">Business Layer</span> :   
- Presentation Layer에서 얻은 데이터로 비지니스 로직을 수행한다.   

<span style="color:lightgreen">persistence Layer</span> :   
- DB와 상호작용(CRUD)을 책임진다.   

<span style="color:lightgreen">Database Layer</span>:    
- 실제 Database를 관리한다.

---

## 📍 Flux Architecture

Flux는 Facebook에서 클라이언트-사이드 웹 어플리케이션을 위해 만든 아키텍쳐다.
단반향 데이터 흐름을 활용해 React를 보완하는 역할을 한다.

<br/>

### Flux의 구성요소
- Dispatcher : 적잘한 store로 action을 전달한다.
- Store : 받은 action에 따라 상태를 변경. 상태 변경을 알린다.
- View : store의 상태를 반영한다.
- Action : 이벤트/메세지 객체 같은 것

### 구조와 데이터 흐름
<img src="/public/flux.png" width="350px" title="" ></img>

<br/>

<img src="/public/flux-2.png" width="350px" title=""></img>

---

## 📍 useReducer
useReducer를 통해 함수 컴포넌트의 상태를 업데이트할 수 있다.

practice code

```js
// hooks/useForceUpdate.ts
import {  useState, useCallback } from "react"

export default function useForceUpdate() {
    const [, setState] = useState({})
    return useCallback (() => setState({}), [])
}

// components/Counter.tsx
import useForceUUpdate from "../hooks/useForceUpdate";

const state = {
    count: 0
}

function increase() {
    state.count += 1;
}


export default function Counter() {
    const forceUpdate = useForceUUpdate()

    const handleClick = () => {
        increase()
        forceUpdate()
    }
    
    return (
        <div>
            <p>{state.count}</p>
            <button type="button" onClick={handleClick}></button>
        </div>
    )
}
```
- useForceUpdate를 hook으로 분리해 컴포넌트의 상태를 업데이트해야 하는 경우에 사용할 수 있다.
- Counter 컴포넌트안에서도 UI와 비지니스 로직을 분리해준다.
- useCallback을 사용해 함수를 캐싱해준다. useForceUpdate가 리렌더링 될 때마다 새로운 함수가 생성되는 것을 방지한다. 바뀌는 경우에는 의존성 배열에 추가해준다.

---

## 📍 useCallBack

- useCallback은 리렌더링 사이에 함수를 캐싱해주는 react hook이다.
- useCallback(fn, dependencies)
    - fn : 캐싱할 함수가 들어간다. 렌더링 이후 의존성 배열이 변경되지 않으면 동일한 함수를 제공한다. 
    - dependencies : 의존성 배열이다. 의존성 배열에 있는 값이 변경되면 함수가 새로 생성된다.


---

## ✏️ 정리
- 공부한 내용   
    [x] 관심사의 분리의 중요성과 필요한 이유    
    [x] 관심사의 분리를 잘 하기위한 Layered Architecture   
    [x] Flux Architecture의 구성요소와 데이터 흐름   
    [x] useReducer가 무엇인지, 어떻게 사용하는지   
    [x] useCallback의 정의

- 더 공부할 것   
    [] 코드를 Layered Architecture로 리팩토링해보기