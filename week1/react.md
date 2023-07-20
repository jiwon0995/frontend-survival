### 🤔 _Thinking in React_

> 👉 [자주 읽어 보자!](https://react.dev/learn/thinking-in-react, "Thinking in React")

<br />
프로젝트를 시작하기 전 리액트로 어떻게 개발할지 계속 리마인드하면 좋을 과정인 것 같다.

<br />

> Step 0  
> Mock Data를 준비하자.  
> API로 받아올 데이터를 미리 준비해두고 컴포넌트를 만들기.

> Step 1  
> Component 쪼개기.  
> UI를 보고 컴포넌트를 어떻게 나누면 좋을지 생각하기.  
> 컴포넌트간의 계층구조 생각하기.  
> 컴포넌트에는 하나의 기능만 있는게 좋다고 한다. _(알지만..쉽지 않음)_

> Step 2  
> 미리 준비한 Mock Data와 컴포넌트를 붙여서 정적인 상태의 App 만들기.

> Step 3  
> State로 만들어줄 데이터 구분하기.  
> 동적으로 변하는 데이터와 아닌 데이터를 구분해주자.

> Step4
> State 위치 찾기.  
> 최소 공통 부모 컴포넌트를 찾아서 그 위치에 넣어주자.
> 리액트는 단방향 데이터 흐름이기 때문에 하나의 State가 여러 컴포넌트에서 사용된다면,  
> 해당 컴포넌트들의 부모를 찾아 State를 넣어주자.

> Step5  
> 하위 컴포넌트에서 상위 컴포넌트의 State값을 변경해야 한다면 `Props`로 `SetSate`를 넘겨주자.

<br />

습관으로 만들어두자! 무작정 시작하는 버릇 고쳐야지 🤔

<br />

---

<br />

👉 [더 읽어볼 것]('https://overreacted.io/ko/react-as-a-ui-runtime/', "React as a UI Runtime")  
👉 더 공부할 것 : 리액트 리랜더링

<br />
