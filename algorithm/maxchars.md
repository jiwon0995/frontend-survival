# max chars

## Problem

문자열이 주어졌을 때, 가장 많이 반복되는 문자를 반환한다.

## Solution

1. 객체를 순회하며 가장 많이 반복된 문자를 반환한다.

```javascript
function maxChar() {
 const charMap = {}
    let max = 0
    let maxChar = ''

    for(let char of str) {
        if(charMap[char]) {
            charMap[char]++
        } else {
            charMap[char] = 1
        }
    }

    for (let char in charMap) {
        if(charMap[char] > max) {
            max = charMap[char]
            maxChar = char
        }
    }

    return maxChar
}
```

## Discussion

**객체를 순회하며 가장 많이 반복된 문자를 반환한다.**

    객체에 문자열의 각 문자를 key로, 각 문자의 반복 횟수를 value로 저장한다.
