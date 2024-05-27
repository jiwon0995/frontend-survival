# chunk

## Problem

숫자로 된 배열과 숫자를 입력받아서 배열을 입력받은 숫자만큼 나누어서 배열로 반환하는 함수를 구현하기

## Solution

```javascript
function chunk(array, size) {
    const chunked = [];

    for (let element of array) {
        const last = chunked[chunked.length - 1];

        if (!last || last.length === size) {
            chunked.push([element])
        } else {
            last.push(element)
        }
    }

    return chunked
}
```

``` javascript
function chunk() {
    const chunked = [];
    let index = 0;

    while (index < array.length) {
        chunked.push(array.slice(index, index + size));
        index += size;
    }

    return chunked;
}
```

## Discussion

쉬운 문제라고 생각했는데 last가 chunked를 참조하고 있다는걸 이해 못 해서 오래걸림...
last가 chunked를 참조하고 있기 때문에 last를 수정하면 chunked도 수정된다.
잘 기억해두자
