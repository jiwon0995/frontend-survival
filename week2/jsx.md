### 2주차 키워드

- React에서 JSX를 사용하는 목적
- Syntactic sugar
- React.createElement
- React Element
- React StrictMode

---

> JSX를 알아보기 전에...

### React Element
React Element는 React를 구성하는 가장 작은 단위이다. React DOM은 엘리먼트가 모여서 만들어진 엘리먼트 트리를 감지해서 DOM을 업데이트한다. React DOM이 업데이트 되는 부분은 Virtual DOM을 정리하면서 자세히 해야겠다. JSX를 알아보기 위해 여기서는 React Element가 리액트를 구성하는 요소라는 것만 알아두자.

``` const element = <h1>Hello, world!</h1>; ```

### React.createElement
React.createElement는 React Element를 만드는 메서드이다. 이 메서드로 react를 구성하는 요소들을 만들 수 있다.   
>React.createElement(component, props, ...children)

```javascript
function User({name}) {
    return <div>user name is {name}</div>
}
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(React.createElement(User, {name: 'Jiwon'}, null));
```

React.createElement 메서드로 User라는 Component를 화면에 랜더링 하는 과정이다. 화면에는 ```user name is Jiwon```이 출력된다.

### JSX
JSX는 React.createElement를 사용하지 않고도 React Element를 만들 수 있게 해주는 Javascript의 확장 문법이다. JSX를 사용하면 React Element를 더 직관적으로 작성할 수 있다. 한마디로 개발을 더 편하게 해주는 ```Syntactic sugar```이다.

> Syntactic sugar는 사람이 쉽게 이해할 수 있는 문법으로 변환해주는 문법이다.

```jsx
// JSX
<p>Hello, world!</p>
```

```javascript
// Javascript
React.createElement("p", null, "Hello, world!");
```

```jsx
// JSX
<p className="text">Hello, world!</p>
```

```javascript
// Javascript
React.createElement("p", { className: "text" }, "Hello, world!");
```

JSX는 자바스크립트 문법이 아니기 때문에 브라우저가 이해할 수 없다. 따라서 JSX를 사용하려면 JSX를 자바스크립트로 변환해주는 ```Babel```이라는 도구가 필요하다. Babel은 JSX를 React.createElement로 변환해준다. typescript를 사용하면 Babel을 사용하지 않아도 된다.

### JSX 문법
 1. 태그는 꼭 닫혀야 한다.   
  Why? JSX가 Javascript 객체로 변환될 때 정확히 시작과 끝을 알 수 있도록 해줘야 하기 때문이다.  
2. 두 개 이상의 태그는 하나의 태그로 감싸져 있어야 한다.
 why? 컴포넌트는 하나의 DOM 트리로 이루어져야 한다.  
3. JSX 안에서 자바스크립트 표현식을 사용할 수 있다.   
    JSX안에서 {}를 사용하면 자바스크립트 표현식을 사용할 수 있다.
4. JSX 안에서 if문, for문을 사용할 수 없다.   
    JSX는 자바스크립트 표현식이기 때문에 if문, for문을 사용할 수 없다. 하지만 삼항연산자는 사용할 수 있다.
5. JSX 안에서 주석을 사용할 수 있다.   
    ```{/* 주석 내용 */}```
6. JSX 안에서 class 대신 className을 사용해야 한다.   
7. JSX 안에서 style을 사용할 때는 객체 형태로 작성해야 한다.   
    ```<div style={{color: 'red'}}></div>```
8. JSX 안에서는 camelCase를 사용해야 한다.   
    ```<div tabIndex="0"></div>```

 ---

 ### 새롭게 알게된 점
 그동안 React에서 JSX를 당연하게 써왔다. 단순히 React에서 사용하는 문법으로 생각했는데 React가 아니여도 사용할 수 있고, 꼭 React에서 JSX를 사용하지 않아도 된다는 점을 알게 됐다. JSX로 만든 코드가 어떻게 Javascript로 변환되는지 알게됐고 랜더링과 어떻게 관계가 있는지 조금 이해가 된 것 같다. 랜더링이 내 의도와 다르게 동작할 때가 많았는데 Virtual DOM을 공부하면서 React가 어떻게 화면에 그려지고 랜더링 되는지 조금 더 이해할 수 있을 것 같다.

 ---

 ### 더 공부할 것
 - [ ] Virtual DOM
 - [ ] React StrictMode