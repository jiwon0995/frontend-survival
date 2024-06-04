# vowels

## problem

주어진 문자열에 있는 모음의 개수를 반환하기.
모음은 a, e, i, o, u

## solution

```javascript
function vowels (str) {
    const matches = str.match(/[aeiou]/gi);
    return matches ? matches.length : 0;
}
```

```javascript
function vowels (str) {
    const checker = ['a', 'e', 'i', 'o', 'u'];
    let count = 0;

    for(let char of checker.toLowerCase()) {
        if(checker.includes(char)) {
            count++;
        }
    }

    return count;
}
```

## description

- 정규표현식을 사용하여 모음을 찾아내어 배열로 반환한다. 정규식 표현을 알아두면 좋을 듯.
- 반복문을 사용하여 모음을 찾아내어 count를 증가시킨다.
