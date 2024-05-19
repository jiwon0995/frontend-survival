# 문자열 역순으로 출력하기

## Problem

주어진 문자열을 뒤집었을 때 똑같은 단어면 true, 아니면 false를 반환한다.

## Solution

1. reverse() 메서드를 사용하기

```javascript
function palindrome(str) {
   let reversed = str.split('').reverse().join('');

    return str === reversed;
}
```

1. every() 메서드 사용하기

```javascript
function palindrome(str) {
    return str.split('').every((char, index) => char === str[str.length - index - 1]);
}
```

3. reduce() 메서드 사용하기

```javascript
function palindrome(str) {
  let reversed =  str.split('').reduce((reversed, char) => char + reversed, '');

    return str === reversed;
}
```

## Discussion

**every() 메서드 사용하기**

   every() 메서드는 배열의 모든 요소가 주어진 함수로 구현된 테스트를 통과하는지 테스트한다.
   주어진 함수가 배열 요소마다 한 번씩 호출되어 true를 반환하면 true를 반환한다.
   문자열을 배열로 만들어 배열의 각 요소와 뒤집은 문자열의 각 요소를 비교한다.
   모든 요소가 같다면 true를 반환한다.