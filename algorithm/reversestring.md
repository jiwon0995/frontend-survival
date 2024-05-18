# 문자열 역순으로 출력하기

## Problem

문자열이 주어졌을 때, 이를 역순으로 출력하기.

## Solution

1. reverse() 메서드를 사용하기

```javascript
function reverseString(str) {
  return str.split('').reverse().join('');
}
```

2. for loop 사용하기

```javascript
function reverseString(str) {
  let reversed = '';
  
  for(char of str) {
    reversed = char + reversed;
  }
  return reversed;
}
```

3. reduce() 메서드 사용하기

```javascript
function reverseString(str) {
  return str.split('').reduce((reversed, char) => char + reversed, '');
}
```

## Discussion

**reverse() 메서드 사용하기**

  문자열을 split() 메서드로 배열로 만들고, reverse() 메서드로 연순으로 만든 후 join() 메서드로 다시 문자열로 만들어 반환한다.
  문자열을 split()을 사용해 배열로 만들 수 있다는 점을 알게 되었다.
  간단하지만 문자열을 배열로 만든 후 다시 문자열로 만드는 과정이 비효율적!

**for loop 사용하기**

   for문을 사용해 문자열을 새로운 문자열에 역순으로 저장한다.
   기존에 많이 사용하던 방식인
   for(let i = 0; i < str.length; i++) 구문이 아닌
    for(char of str) 구문을 사용해 간단하게 문자열을 순회할 수 있다. (ES6에서 추가된 기능)

**reduce() 메서드 사용하기**

    아직 익숙하지 않은 reduce() 메서드...
    reduce() 메서드는 배열의 각 요소에 대해 주어진 함수를 실행하고 하나의 결과값을 반환한다.
    초기값을 빈문자열로 설정하고, 배열의 각 요소를 순회하며 문자열을 역순으로 만들어 반환한다.