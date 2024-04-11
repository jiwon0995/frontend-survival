# TDD

***내용 Update 중...!***

TDD(Test Driven Development)는 테스트를 먼저 만들고, 테스트를 통과할 수 있게 실제 코드를 작성한다.
JEST를 이용해 테스트 코드를 작성해보자.

``` js
// sample.text.ts

// 두 숫자를 더하는 test 코드 작성
text('add', () => {
  expect(add(1, 2)).toBe(3)
})

```

이렇게 먼저 테스트 코드를 작성 후, 해당 코드를 통화하는 실제 코드를 작성한다.

``` js
function add(x, y) {
  return x + y
}
```

## TDD 과정

TDD 과정은 다음과 같다.

1. 테스트 작성
2. 작성한 테스트를 통과할 수 있는 가장 빠른 방법으로 코드 작성
3. 테스트 수행
4. 테스트가 통과하면 작성한 코드 리팩토링
5. 테스트 수행
6. 테스트가 통과하면 완성

## TDD를 해야하는 이유

1. 기능의 요구사항을 명확하게 파악할 수 있다.
2. 개발 후 버그가 발생할 확률이 줄어들고, 유지보수가 쉬워진다.
3. 재사용성이 높은 코드를 작성할 수 있다.

## TDD 연습해보기

아샬님의 Jest를 이용한 TDD 예제로 연습을 해보자.

> 프로그래머스 '두 개 뽑아서 더하기'를 TDD로 풀어보기

1. Step 1 - 문제를 생각하면서 테스트 작성

``` js
test('sample', () => {
  expect(solve([2, 1, 3, 4, 1])).toEqual([2, 3, 4, 5, 6, 7])
});
```

2. Step 2 - `solve is not defined` error 해결하기

``` js
function solve() {
  return null;
}
```

3. Step 3 - 테스트 코드 빠르게 통과 시키기

``` js
function solve() {
  return [2, 3, 4, 5, 6, 7]
}

test('sample', () => {
  expect(solve([2, 1, 3, 4, 1])).toEqual([2, 3, 4, 5, 6, 7])
});
```

4. Step 4 - 중복 코드 제거하면서 코드 리팩토링 반복

간단한 테스트를 만들어 수정해본다.

``` js
test('simple', () => {
  expect(solve([1, 2, 3])).toEqual([3, 4, 5])
})
```

``` js
function solve(numbers) {
	if(numbers.length === 3) {
		return [3, 4, 5]
	}
}
```

다시 수정

``` js
function solve(numbers) {
	if(numbers.length === 3) {
		return [1 + 2, 1 + 3, 2 + 3]
	}
}
```

다시 수정

``` js
function solve(numbers) {
	if(numbers.length === 3) {
		return [
			numbers[0] + numbers[1],
			numbers[0] + numbers[2],
			numners[1] + numbers[2]
		]
	}
}
```

> 곧 업데이트 예정!
