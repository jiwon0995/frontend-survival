## Basic inline style
JavaScript 객체를 활용하여 스타일 지정

```jsx
// style을 객체로 지정 
const style = {
    color: '#00f',
}
<p style={style}>
```

```jsx
// 직접 객체를 지정
<p style={{color: '#00f'}}>
```

```js
// 조건에 따라 스타일 지정
const dearMode = false;

function primaryColor() {
    return darkMode ? '#fff' : '#000';
}

export default function App() {
    return (
        <p style={{color: primaryColor()}}>
    );
}
```

## CSS in JS
javascript를 이용해서 style component를 만들어서 사용하는 방법

다양한 라이브러리

- styled-components
- emotion
- JSS
- Tailwind CSS