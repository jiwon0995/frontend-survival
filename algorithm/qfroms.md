# q from s

## problem

스택 구조로 큐를 구현하기.

## solution

```javascript
class Stack {
  constructor() {
    this.data = [];
  }

  push(record) {
    this.data.push(record);
  }

  pop() {
    return this.data.pop();
  }

  peek() {
    return this.data[this.data.length - 1];
  }
}

class Queue {
    const constructor () {
        this.first = new Stack();
        this.second = new Stack();
    }

    add(record) {
        this.first.push(record);
    }

    remove() {
        while(this.first.peek()) {
            this.second.push(this.second.pop)
        }
        const record = this.second.pop();
        while(this.second.peek()) {
            this.first.push(this.second.pop());
        }
        return record;
    }

    peek() {
        while(this.first.peek()) {
            this.second.push(this.first.pop())
        }
        const record = this.second.peek()
        while(this.second.peek()) {
            this.first.push(this.second.pop())
        }
        return record
    }
}
```

## Discussion

- 큐는 FIFO(First In First Out)
- 스택은 LIFO(Last In First Out)
- 스택 두 개를 값을 옮겨가며 큐를 구현한다.
