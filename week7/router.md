## 📍 Router

React Rout v6.4부터 지원하는 Router 객체   
App.js에서 RouterProvider를 사용하여 Router를 설정한다.

```jsx
import { Routes, Route, RouterProvider} from 'react-router-dom';

const routes = [
    { path: '/', element: <HomePage /> },
    { path: '/about', element: <AboutPage /> },
    
]

function Page() {
    return (
        <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/about" element={<About />} />
        </Routes>
    )
}

exprt default function App() {
    return (
        <RouterProvider router={router}>
            <Page />
        </RouterProvider>
    )
}
```

### Layout 나누기

layout을 지정하지 않으면 기본적으로 페이지 전체가 렌더링된다.
routes를 계층형을 구성하여 layout을 나눌 수 있다.

```js

function Layout() {
    return (
        <div>
            <Header />
            <div>
                <Outlet />
            </div>
            <Footer />
        </div>
    )
}

const routes = [
    {
        element: <Layout />,
        children : [
            { path: '/', element: <HomePage /> },
            { path: '/about', element: <AboutPage /> },
        ]
    }
]

```

### routes.test.tsx

```js

const context = describe;

descibe('App', () => {

    function renderRouter() {
        const router = createTestHistory(createMemorySource(routes, [path]));
        render (
            <RouterProvider router={router} />
        );
    }
    context('when the current path is '/'', () => {
        if('renders the home page', () => {
            renderRouter('/');
            screen.getByText(/Welcome/);
        });
    })
})

```

---

## ✏️ 정리
- 공부한 내용   
    * [x] router 객체 사용법
    * [x] router, layout 나누기
    * [x] router test 코드 작성법
