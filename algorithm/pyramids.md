# pyramids

## problem

n이 주어졌을 때, n의 길이만큼 피라미드를 출력하기
ex ) n = 3
```
  #
 ###
#####
```

## solution

```javascript
function printPyramid(n) {
    const midpoint = Math.floor((2 * n - 1) / 2)

    for(let row = 0; row < n; row++) {
        let level = ''

        for(let column = 0; column < 2 * n -1; colum++) {
            if(midpoint - row <= column && midpoint + row >= column) {
                level += '#'
            } else {
                level += ' '
            }
        }
    }
}
```

