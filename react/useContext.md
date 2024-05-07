# Context

컨텍스트는 공급자가 새로운 값을 갖게 되면 모든 컨텍스트 소비자는 새로운 값을 받고 리렌더링 된다.

## 컨텍스트 전파의 작동 방식

리액트에서 자식 컴포넌트가 리렌더링되는 이유는 두 가지다.  

1. 부모 컴포넌트가 리렌더링되었을 때
2. 컨텍스트가 변경되었을 때

컨텍스트 값이 변경되지 않았는데도 리렌더링이 발생하는 문제를 방지하려면,  
```memo```를 사용할 수 있다.  

memo를 사용해서 리렌더링을 방지하는 예제

``` javascript
const ColorContext = createContext('black')

const ColorComponent = () => {
    const color = useContext(ColorContext)

    // 랜더링 횟수 확인
    const renderCount = useRef(1)

    useEffect(()=> {
        renderCount.current += 1
    })

    return (
        <div style={{ color}}>
            Hello {color} (renders: {renderCount.current})
        </div>
    )
}
```

memo로 감싼 ColorComponent

``` javascript
const MemoizedColorComponent = memo(ColorComponent)
```

useContext를 사용하지 않는 컴포넌트 생성

``` javascript
const DummyComponent = () => {
    const renderCount = useRef(1);

    useEffect(() => {
        renderCount.current += 1;
    });

    return <div>Dummy (renders: {renderCount.current})</div>;
}
```

memo로 감싼 DummyComponent

``` javascript
const MemoizedDummyComponent = memo(DummyComponent)
```

부모 컴포넌트에서 컴포넌트 렌더링

``` javascript
const Parent = () => {
    <ul>
        <li><DummyComponent></li>
        <li><MemoizedDummyComponent></li>
        <li><ColorComponent></li>
        <li><MemoizedColorComponent></li>
    </ul>
}
```

App 컴포넌트에서 Parent 컴포넌트 렌더링

``` javascript
const App = () => {
    const [color, setColor] = useState('red')
    return (
        <ColorContext.Provider value={color}>
             <input value={color} onChange={(e)=> setColor(e.target.value)} />
            <Parent />
        </ColorContext.Provider>
    )
}
```

위 컴포넌트를 실행하면,

1. 처음에 모든 컴포넌트가 렌더링된다.
2. 텍스트 입력 필드에서 값을 변경하면 useState로 인해 App 컴포넌트가 리렌더링된다.
3. ColorContext.provider는 새로운 값을 받고, Parent 컴포넌트가 리렌더링된다.
4. DummyComponent는 리렌더링 되지만 MemoizedDummyComponent는 리렌더링 되지 않는다.
5. ColorComponent는 두 가지 이유로 리렌더링된다.  
    - 부모 컴포넌트가 리렌더링 됨
    - 컨텍스트가 변경 됨
6. MemoizedColorComponent는 컨텍스트가 변경됐기 때문에 리렌더링된다.

```memo```를 사용해도 컨텍스트 값이 변경되면 리렌더링을 막을 순 없다.

## 컨텍스트를 사용한 모범 사례

``` javascript

// 초기값이 null인 컨텍스트 생성
type CountContextType = [
    number,
    Dispatch<SetStateAction<number>>
]

const Count1Context = createContext<CountContextType | null>(null)
```

``` javascript
// Count1Provider를 정의해서 useState로 상태를 생성하고 컨텍스트에 제공
export const count1Provider = ({
    children
}: {
    children: ReactNode 
}) => {
    <Count1Context.Provider value={useState(0)}>
        {children}
    </Count1Context.Provider>
}
```

``` javascript
// Count1Context에서 값을 가져오는 커스텀 훅
export const useCount1 = () => {
    const value = useContext(Count1Context)
    if (value === null) throw new Error("Provider missing")
    return value
}
```

``` javascript
// Count2Context를 생성
const Count2Context = createContext<CountContextType | null>(null)

export const Count2Provider = ({
    children
}: {
    children: ReactNode
}) => {
    <Count2Context.Provider value={useState(0)}>
        {children}
    </Count2Context.Provider>
}

export const useCount2 = () => {
    const value = useContext(Count2Context)
    if (value === null) throw new Error("Provider missing")
    return value
}
```

``` javascript
// count1을 사용하고 카운트와 버튼을 보여주는 컴포넌트
const Counter1 = () => {
    const [count1, setCount1] = useCount1()
    return (
        <div>
            Count1: {count1}
            <button onClick={() => setCount1((c) => c + 1)}>+1</button>
        </div>
    )
}
```

``` javascript
// count2를 사용하고 카운트와 버튼을 보여주는 컴포넌트
const Counter2 = () => {
    const [count2, setCount2] = useCount2()

    return (
        <div>
            Count2: {count2}
            <button onClick={() => setCount2((c) => c + 1)}>+1</button>
        </div>
    )
}
```

``` javascript
const parent = () => {
    return (
        <div>
            <Counter1>
            <Counter1>
            <Counter2>
            <Counter2>
        </div>
    )
}
```

``` javascript
const App = () => {
    return (
        <Count1Provider>
            <Count2Provider>
                <Parent />
            </Count2Provider>
        </Count1Provider>
    )
}
```
