# anagrams

## problem

두 문자열이 주어졌을 때, 두 문자열이 서로 애너그램인지 판별하는 함수를 작성하기

## solution

``` javascript
function anagrams(stringA, stringB) {
    const aCharMap = buildCharMap(stringA)
    const bCharMap = buildCharMap(stringB)

    if (Object.keys(aCharMap).length !== Object.keys(bCharMap).length) {
        return false
    }

    for (let char in aCharMap) {
        if (aCharMap[char] !== bCharMap[char]) {
            return false;
        }
    }

    return true;
}

function buildCharMap(str) {
    const charMap = {};

    for (let char of str.replace(/[^\w]/g, '').toLowerCase()) {
        charMap[char] = charMap[char] + 1 || 1
    }
}
```

``` javascript
function cleanString(str) {
    return str.replace(/[^\w]/g, '').toLowerCase().split('').sort().join('');
}

function anagrams(stringA, stringB) {
    return cleanString(stringA) === cleanString(stringB)
}
```

## Description

- 문자열을 객체 key로 사용하여 문자열의 각 문자의 개수를 저장한 후 비교하는 방법
- str.replace(/[^\w]/g, '').toLowerCase().split('').sort().join('')
- 정규식을 사용하여 문자열에서 알파벳만 남기고 소문자로 변환한 후 정렬하여 비교
