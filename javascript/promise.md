# Promise

![렛츠고](https://pbs.twimg.com/media/FWewNGAUsAApFte?format=jpg&name=medium)

## 비동기

promise를 알아보기 전에 promise가 필요한 이유를 먼저 알아보자.  
자바스크립트에서는 비동기로 동작하는 코드가 있다.  
비동기란 ***순서와 상관없이 실행*** 되는 코드를 말한다. 예제로 알아보자.

``` javascript
    let number = 0;

    setTimeout(() => { number + 10 }, 0)

    // number: 0
    console.log("number:", number)
```

setTimeout 함수는 비동기 함수이다. 시간을 0으로 설정했지만 console에 출력된 값은 0이다.  
setTimeout 함수의 콜백함수는 비동기로 작동한다. 단순히 0초가 지나고 콜백함수가 실행된 후 console이 출력될 것 같지만 사실은 그렇지 않다.  
setTimeout 함수는 콜백함수를 스케줄링한 다음, 타이머 id를 반환하고 종료된다. setTimeout 함수가 종료된 후 콜백함수가 실행되는 것이다. 비동기 코드는 기대와 다르게 동작할 가능성이 크다.  

## promise란?

promise는 비동기 처리되는 코드의 문제점을 극복하기 위해 ES6부터 도입된 빌트인 객체이다.

``` javascript
// promise 생성
const promise = new Promise((resolve, reject) => {
    // promise 함수의 콜백 함수 내부에서 비동기 처리 수행
    if (/* 비동기 처리 성공 */) {
        resolve()
    } else {
        reject() /* 비동기 처리 실패 */
    }
})

```

``` javascript
// javascript deep dive 예제
const promiseGet = url => {
    return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest()
        xhr.open('GET', url)
        xhr.send()

        // 비동기 처리가 되는 부분
        xhr.onload = () => {
            if(xhr.status === 200) {
                resolve(JSON.parse(xhr.response))
            } else {
                reject(new Error(xhr.status))
            }
        }
    })
}

promiseGet('https://test.com/post/1')
```

Promise 내부에서 비동기 처리가 성공하면 콜백 함수의 인수로 전달받은 resolve 함수를 호출하고, 실패하면 reject 함수를 호출한다.
Promise는 다음과 같이 세가지 비동기 처리 상태를 가지고 있다.

1. 대기(pending) : 초기 상태
2. 이행(fulfilled) : 성공적으로 완료
3. 거부(rejected) : 실패

## then, catch, finally

promise는 then과 catch 메소드를 사용할 수 있다.  
```then()``` 메서드는 연산이 성공했을 실행이된다. then에 넣어둔 콜백함수가 실행되고, 첫번째 인자로 response 객체가 전달된다.  
```catch()``` 메서드는 연산이 실패했을 때 실행이된다. 연산이 실패한 이유가 인자로 전달된다.

``` javascript
// promise 호출
new Promise(); 

new Promise(function(resolve, reject))
```
