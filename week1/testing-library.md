# Testing Library

#### Testing Library

\


#### 🚀 _Jest_

\


> 👉 [공식문서 읽어라! 진짜루!!!]('https:/jestjs.io/docs/getting-started',/)

\


Jest와 함께 Bug 조지기! 🐛

\


> 테스트 코드를 짜본적 없는 나.. 괜찮은걸까? 🤔\
> 모르겠다면 _Given - When - Then_\
> 어떤 동작을 하고 어떤 결과를 얻어야 하는지 정확하게 인지하기.

\


기본 동작 익히기\
공식문서에 나와있는 예제를 따라해보자.

```Javascript
function sum(a, b) {
    return a + b;
}
test('add 1 + 2 to equal 3', () => {
    expect(sum(1, 2)).toBe(3);
});
```

\


test script를 실행해보자.

```
npm test
```

jest가 실행되면서 테스트 결과를 알려준다.

\


#### 🚀 _React Testing Library_

\


> 👉 [공식문서고고공식문서!]('https:/testing-library.com/docs/react-testing-library/example-intro',/)

\


> React Testing Library 설치하고 사용하기\
> UI를 테스트 할 수 있다.\
> 테스트 할 부분을 잘 구분할 줄 알아야 한다!

\


***

\


👉 [더 공부하기]('https:/www.betterspecs.org/'/)
