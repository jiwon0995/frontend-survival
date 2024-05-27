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
