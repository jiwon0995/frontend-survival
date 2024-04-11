# App Router

Next 13 버전에 추가된 App Router 방식은 기존에 사용하던 Page Router 방식과 어떻게 다른지 알아보자.

## 폴더 구조

Page Router에서 page 폴더안에서 라우터를 만들었다면 App Router 방식에서는 app 폴더안에서 라우터를 생성한다.

``` bash
    -app
        -dashboard
            -settings
                -page.tsx
```

root 폴더인 `app` 폴더안에 생성된 폴더는 프로젝트의 경로가 된다.
위에 있는 폴더 구조의 url 경로는 다음과 같다.
`domain.com/dashboard/settings`

App Router에서는 특별한 기능을 하는 기본 파일들을 제공한다.
`layout`, `page`, `loading`, `not-found`, `error` 해당 내용도 자세히 정리할 예정이다.

### 동적라우팅

동적라우팅 폴더를 만드는 방식은 Page Router와 동일하다.
대괄호([])로 만든 폴더는 Next가 동적라우팅 폴더로 인식한다.

``` bash
    -app
        -product
            -[id]
```

해당 폴더 구조는 다음과 같은 url로 접근할 수 있다.
`domain.com/product/1` product 세그먼트 뒤에는 어떤 값이 와도 url 경로로 인식된다.
동적 세그먼트는 `page`, `layout` 등에서 props로 접근이 가능하다.

``` js
    // routing : app/product/[id]
    // url : domain.com/product/1
    export default function ProductDetailPage(props) {
        console.log("props:", props)
        return (
            <ProductDetailComponent>
        )
    }

    // 출력 : { params: { id: '1' }, searchParams: {} }
```

### 그룹 라우터

app 폴더안에 생성된 폴더는 url 경로로 인식되지만 라우터를 그룹으로 묶어서 url 경로에 포함되지 않게 할 수 있다.
Next 문서에서는 그룹 라우터를 다음과 같은 상황에서 유용하게 사용할 수 있다고 소개한다.

- Organizing routes into groups e.g. by site section, intent, or team.
- Enabling nested layouts in the same route segment level:
  - Creating multiple nested layouts in the same segment, including multiple root layouts
  - Adding a layout to a subset of routes in a common segment

같은 레벨의 세그먼트가 똑같은 layout을 공유할 때 유용하게 사용할 수 있을 것같다.
(layout에 대해서는 더 자세히 다룰 예정)

괄호로 만든 폴더안에 있는 폴더는 그룹 라우팅으로 인식된다.

``` bash
    -app
        -(shop)
            -product
                -page.js
            -account
                -page.js
```

`product` 와 `account`는 같은 레벨의 세그먼트로 인식되고, shop은 url 경로에 아무 영향도 주지 못한다.
각자 `domain.com/product`, `domain.com/account` 으로 경로가 설정된다.

``` bash
    -app
        -(shop)
            -layout.js // product
            -product
                -page.js
            -account
                -page.js
```

`product`와 `account`는 `(shop)`안에 있는 layout.js를 공유할 수 있다.

### Page

Page Route 방식에는 url 경로가 될 폴더안에 index 파일을 만들어 줬다면 App Router에서는
page 파일을 만들어 준다.

``` bash
    -app
        -product
            -page.js
```

``` js
// `app/product/page.js` 
 export default function ProductListPage() {
    return <h1>Product List page </h1>
 }
```

### Layout

Layout은 같은 route 안에서 공유할 수 있는 UI이다.
여러 page가 공통으로 사용하는 UI가 있다면 layout.js 파일안에 넣어주면 된다.

``` js
    export default function RootLayout({children}:{children: React.ReactNode}) {
        return (
            <html lang="en">
                <body>
                    <main>{children}</main>
                </body>
            </html>
        )
    }
```

Next는 layout을 먼저 랜더링 한 후, 해당 경로에 맞는 컴포넌트를 랜더링한다.
/product 경로로 이동하면 화면은 다음과 같이 랜더링된다.

``` js
    <RootLayout>
        <ProductList />
    </RootLayout>
```

layout은 중첩으로 사용할 수 있다. route 폴더안에 layout 파일을 생성하면 같은 경로에 있는 페이지들은
같은 layout을 공유하게 된다. 다음 폴더구조에서 product/about 경로로 이동하면 다음과 같이 랜더링된다.

``` bash
    -app
        -page.js
        -layout.js
        -product
            -page.js
            -layout.js
            -about
                -page.js

```

``` js
    <RootLayout>
        <ProductLayout>
            <Product>
                <About />
            </Product>
        </ProductLayout>
    </RootLayout>
```
