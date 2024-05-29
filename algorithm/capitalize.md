# capitalize

## Problem

주어진 문자열의 첫 글자를 대문자로 변환하기.
ex) 'hello there' -> 'Hello There'

## Solution

```javascript
function capitalize(str) {
    const word = [];

    for (let char of str.split(' ')) {
        word.push(char[0].toUpperCase() + char.slice(1));
    }
    return word.join(' ');
}
```

```javascript
function capitalize(str) {
    const word = str[0].toUpperCase();

    for(let i = 1; i < str.length; i++) {
        if(str[i - 1] === " ") {
            word += str[i].toUpperCase();
        } else {
            word += str[i]
        }
    }

    return word
}
```

## Description

- 문자열을 공백으로 나눠 배열에 저장한 후 각 단어의 첫 글자를 대문자로 변환해 join
- 문자열의 첫 글자를 대문자로 변환한 후 반복문을 통해 이전 문자가 공백인 경우 대문자로 변환

