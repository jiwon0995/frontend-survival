## 📍 Navigation

### Web APIs - History


```js
const handleClick = (event) => {
    // 이벤트를 막아준다.
    event.preventDefault();
    // 매개변수로 상태, 제목, 주소를 받는다.
    window.history.pushState(null, null, '/');
}
``` 

### Link
react router dom에서 제공하는 Link 컴포넌트를 사용하면 페이지를 새로고침하지 않고도 페이지를 이동할 수 있다.

```js
import { Link } from 'react-router-dom';

<Link to="/">Home</Link>
```

### NavLink
NavLink는 'active', 'pending' 상태를 알 수 있다. 두 상태는 boolean 값으로 true, false를 반환한다.
상태에 따라 스타일을 지정할 수 있다. css, className, style 속상 전부 사용 가능하다.

```js
import { NavLink } from 'react-router-dom';

<NavLink to="/" active={}>Home</NavLink>
```

### Navigate
Navigate는 특정 경로로 이동시키는 컴포넌트이다. Redirect와 비슷하지만 Navigate는 특정 조건에 따라 페이지를 이동시킬 수 있다.

```js
import { Navigate } from 'react-router-dom';

<Navigate to="/"  />
```

### useNavigate
useNavigate hook을 사용하여 특정 경로로 이동시킬 수 있다.

```js
import { useNavigate } from 'react-router-dom';

const navigate = useNavigate();

const handleClickLogout =()=> {
    navigate('/');
}

<button type="button" onClick={handleClickLogout}>Log out</button>
```

useNavigate hook option

- replace: true로 설정하면 이동한 페이지를 history에 남기지 않는다.
- state: 이동한 페이지에 state를 전달한다.
- preventScrollRest: true로 설정하면 이동한 페이지에서 스크롤 위치를 유지한다.
- relative: 'path'로 설정하면 현재 경로를 기준으로 이동한다.

## ✏️ 정리
- 공부한 내용   
    * [x] react router에서 페이지 이동하는 여러가지 방법