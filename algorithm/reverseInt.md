# 숫자 역순으로 출력하기

## Problem

Int가 주어졌을 때, 이를 역순으로 출력하기.

ex) 
123 -> 321
-123 -> -321
-900 -> -9

## Solution

1. 문자열로 변환 후 reverse() 메서드 사용하기

```javascript
function reverseInt(n) {
  const reversed = n.toString().split('').reverse().join('');

  return parseInt(reversed) * Math.sign(n);
}
```

## Discussion

**parseInt**

    parseInt() 함수는 문자열 인자를 파싱하여 특정 진수(수의 진법 체계에서 기준이 되는 값)의 정수를 반환한다.
    문자열로 변환한 숫자를 역순으로 만들어 반환하기 위해 사용했다.

**Math.sign()**

    Math.sign() 함수는 주어진 숫자의 양수, 음수, 0 여부를 나타내는 부호를 반환한다.
    음수인 경우 -1, 양수인 경우 1, 0인 경우 0을 반환한다.
    이를 통해 음수인 경우 -1을 곱해주어 음수를 유지할 수 있도록 했다.
