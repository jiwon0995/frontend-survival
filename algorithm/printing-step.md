# printing step

## problem

정수 n이 주어졌을 때, n의 길이만큼 "#"과 " "을 출력하기

## solution

```javascript
function printStep(n) {
    for(let i = 1; i <= n; i++) {
        let str = ''
        for(let j = 1; j <= n; j++) {
            if(j <= i) {
                str += '#'
            } else {
                str += ' '
            }
        }
        console.log(str)
    }
}
```

