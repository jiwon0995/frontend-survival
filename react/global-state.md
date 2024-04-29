# 전역 상태

전역 상태는  

- 싱글턴이며, 특정 컨텍스트에서 상태가 하나의 값을 가지고 있다는 것을 의미한다.
- 공유 상태이며, 이는 상태 값이 다른 컴포넌트 간에 공유되는 것을 의미하지만, 자바스크립트 메모리상에서 단일 값일 필요는 없다. 싱글턴이 아닌 전역 상태는 여러 값을 가질 수 있다.
  
싱글턴이 아닌 전역 상태 예제

``` javascript
const createContainer = () => {
    let base = 1;
    const addBase = (n) => n + base
    const changeBase = (b) => { base = b }
    return { addBase, changeBase }
}

const container1 = createContainer()
const container2 = createContainer()

container1.changeBase(10)

console.log(container1.addBase(2)) // 12
console.log(container2.addBase(2)) // 3

```

해당 예제에서 base가 각 컨테이너에 격리돼 있기 때문에 container1과 container2는 서로 영향을 주지 않는다.

## 전역 상태가 필요할 때

1. props로 전달하기 어려운 상태
2. 이미 리액트 외부에 상태가 있을 때

### prop을 전달하는 것이 적절하지 않을 때

컴포넌트 트리에서 멀리 떨어진 두 컴포넌트가 상태를 공유해야 할 경우, 여러 단계로 구성된 컴포넌트를 통해 props를 전달하는 작업은 번거롭다. 상태가 변경될 경우 중간 컴포넌트도 리렌더링되어 성능에 영향을 줄 수 있다.
