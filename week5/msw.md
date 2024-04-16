# MSW

오프라인 환경이나 아직 백엔드 API가 없을 때, 실제 백엔드 API를 사용하는 것처럼 테스트 할 수 있는 서비스 워커의 기능을 활용.

## MSW 설치

``` npm i -D msw ```

## Setting

> 가짜 API 요청을 구현하기 위한 handler 코드를 만들어야 한다. rest api를 사용할 경우 'rest'를 import 한다.  

``` javascript
import { rest } from 'msw'

const BASE_URI = 'http://localhost:3000'

const handlers = [
    rest.get(`${BASE_URI}/products`, (req, res, ctx) => {
        const { products } = fixtures

        return res(
            ctx.status(200),
            ctx.json({products})
        )
    })
]

export default handlers
```

> ``` setupWorker() ``` 함수를 불러와서 서비스 워커를 생성해 주고 만든 handlers를 인자로 넘긴다.

``` javascript
// src/mocks/server.ts
import { setupServer } from 'msw/node'
import handlers from './handlers'

const server = setupServer(...handlers)

```

> jest에서 사용할 수 있도록 설정해주기

``` javascript
// src/setupTests.ts
import server from './mocks/server'

// jest 살행하면 바로 실행
beforeAll(() => server.listen({ onUnhandledRequest: 'error' }))

// 실행될 때 마다 초기화
afterEach(() => server.resetHandlers())

// jest 끝날 때
afterAll(() => server.close())
```
