# matrix spiral

## problem

정수 n을 입력받아 n x n 크기의 정수 행렬을 나선형(spiral)으로 채운 후 반환하기

## solution

```javascript
    function matrixSpiral(n) {
        const results = []

        for(let i = 0; i < n; i++) {
            results.push([])
        }

        let counter = 1
        let startColumn = 0
        let endColumn = n - 1
        let startRow = 0
        let endRow = n - 1

        while (startColumn <= endColumn && startRow <= endRow ) {
            for(let i = startColumn; i <= endColumn; i++) {
                result[startColumn][i] = counter
                counter++
            }
            startRow++

            for(let i = startRow; i <= endRow; i++) {
                result[i][endColumn] = counter
                counter++
            }
            endColumn--

            for(let i = endRow; i >= startRow; i--) {
                result[endRow][i] = counter
                counter++
            }
            endRow--

            for(let i = endRow; i >= startRow; i--) {
                result[i][startColumn] = counter
                counter++
            }
            startColumn++
        }

        return results
    }
```

## discussion

- return 값이 results 배열을 n x n 크기로 초기화한다.
- counter 변수를 사용해 1부터 n x n 까지 증가하는 값을 저장한다.
- startColumn, endColumn, startRow, endRow 변수를 사용해 행렬의 시작과 끝을 지정한다.
- while문을 사용해 startColumn이 endColumn보다 작거나 같고, startRow가 endRow보다 작거나 같을 때까지 반복한다.
- for문을 사용해 startColumn부터 endColumn까지 반복하며 값을 채운다.
