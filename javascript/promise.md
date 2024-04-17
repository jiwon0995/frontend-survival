# Promise

![goingSvt](https://pbs.twimg.com/media/FWewNGAUsAApFte?format=jpg&name=medium)

## promise란?

promise는 비동기 처리되는 작업에 사용된다. API 통신으로 서버에서 데이터를 가져올 때 같이 언제 끝날 수 없는 경우에 비동기 처리를 해야하는데, 그럴 때 promise를 반환한다.

## then, catch

promise는 then과 catch 메소드를 사용할 수 있다.  
promise는 세가지 상태를 가지고 있다.  

1. 대기(pending) : 초기 상태
2. 이행(fulfilled) : 성공적으로 완료
3. 거부(rejected) : 실패

```then()``` 메서드는 연산이 성공했을 실행이된다. then에 넣어둔 콜백함수가 실행되고, 첫번째 인자로 response 객체가 전달된다.  
```catch()``` 메서드는 연산이 실패했을 때 실행이된다. 연산이 실패한 이유가 인자로 전달된다.
