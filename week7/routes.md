## React Router
설치하기
```bash
npm i react-router-dom
```

### 📍 Routes & Route

```jsx
import { Routes, Route } from 'react-router-dom';

// path는 경로, element는 해당 경로에 렌더링할 컴포넌트

<Routes>
    <Route path='/' element={<Homepage />} />
    <Routes path='/about' element={<About />} />
</Routes>
```

### 📍 Browser Router
브라우저의 history API를 사용하여 URL을 관리하는 라우터.    
현재 url에 따라 UI를 업데이트한다. url 주소에 관련한 정보를 props로 조회 및 사용 가능하다.

```jsx
// main.tsx에 설정
import { BrowserRouter } from 'react-router-dom';

root.render((
    <React.StrictMode>
        <BrowserRouter>
            <App />
        </BrowserRouter>
    </React.StrictMode>
));
```

### 📍 Memory Router
테스트나 서버사이드 렌더링을 위해 메모리에 URL을 저장하는 라우터

```jsx
import { MemoryRouter } from 'react-router-dom';

import App from './App';

const context = describe;

describe('App', () => {
    context('when the current path is "/about"', () => {
        if('renders the about page', () => {
            render((
                <MemoryRouter initialEntries={['/about']}>
                    <App />
                </MemoryRouter>
            ));

            screen.getByText(/about page/);
        })
    })
});
```

---

## ✏️ 정리
- 공부한 내용   
    * [x] Routes와 Route를 이용한 페이지 라우팅
    * [x] BrowserRouter와 MemoryRouter의 차이점
    * [x] React Router의 기본적인 사용법

- 참고할 내용
    * [memory router](https://reactrouter.com/en/main/router-components/memory-router)
    * [react router test](https://github.com/remix-run/react-router/tree/main/packages/react-router/__tests__)