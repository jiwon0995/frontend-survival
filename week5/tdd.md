## TDD

> TDD(Test Driven Development)는 테스트 코드를 먼저 만들고, 개발을 나중에 하는 테스트 주도 개발이다.   

> 새로운 기능을 추가하기 전에 해당 기능의 요구사항을 테스트 코드로 작성한다. 테스트를 통과하는 작은 단위의 코드를 작성하고,   
리팩토링을 한다. 이렇게 하면 문제 사항을 미리 발견할 수 있고, 코드의 유지보수가 쉬워진다.   

## TDD 순서

1. Red: 실패하는 테스트 코드를 먼저 작성한다.
2. Green: 테스트를 통과하는 프로덕션 코드를 작성한다.
3. Refactor: 테스트를 통과하는 프로덕션 코드를 리팩토링한다.

## TDD를 해야하는 이유

1. 기능의 요구사항을 명확하게 파악할 수 있다.
2. 개발 후 버그가 발생할 확률이 줄어들고, 유지보수가 쉬워진다.
3. 재사용성이 높은 코드를 작성할 수 있다.

---

## JEST

> JEST는 페이스북에서 만든 테스트 프레임워크이다.

## JES로 테스트하기

1. test함수로 개별 테스트 작성

```js
test("test 하려는 내용", () => {
    expect("테스트 대상").toBe("테스트 결과")
})

test("1 === 1", () => {
    expect(1).toBe(1)
})
```

2. describe함수로 테스트 그룹화

```js
const context = describe;

describe('add', () => {
	context('with no argument', () => {
		it('returns zero', () => {
			expect(add()).toBe(0);
		});
	});

	context('with only one number', () => {
		it('returns the same number', () => {
			expect(add(1)).toBe(1);
		});
	});

	context('with two numbers', () => {
		it('returns sum of two numbers', () => {
			expect(add(1, 2)).toBe(3);
		});
	});

	context('with three numbers', () => {
		it('returns sum of three numbers', () => {
			expect(add(1, 2, 3)).toBe(6);
		});
	});
});
```
