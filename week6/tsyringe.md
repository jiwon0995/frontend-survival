## 🎲 TSyringe
TSyringe는 의존성 주입(Dependency Injection)을 위한 라이브러리이다. 

---   

### 📍 의존성 주입(Dependency Injection)
여러 컴포넌트가 있을 때, 하나의 컴포넌트가 다른 컴포넌트의 기능을 사용하거나 참조할 때, 의존성이 생긴다.   
의존성 주입은 이런 의존성을 느슨하게 만들어주는 디자인 패턴이다.

### 📍 의존성 주입의 장점

- 컴포넌트 간의 의존성이 줄어들어 독립적으로 개발이 가능해진다.
- 컴포넌트를 분리하고 재사용하기 쉬워진다.
- 모의 객체를 사용해 테스트하기 쉬워진다.

---

### 📍 reflect-metadata

practice code

```js
// store/Store.ts
import 'reflect-metadata';

@singleton()
export default class Store {
    count = 0;

    listeners = new set();

    update() {
        this.listeners.forEach((listeners) => {
            listeners();
        })
    }

    addListener(listener) {
        this.listeners.add(listener);
    }

    removeListener(listener) {
        this.listeners.delete(listener);
    }
}

// component/CountControl.tsx
import { container } from "tsyringe";
import Store from "../store/Store";

export default function CountControl() {
    const store = container.resolve(Store);

    const handleClickIncrease = () => {
        store.count += 1;
        store.publish();
    }

    const handleClickDecrease = () => {
        store.count -= 1;
        store.publish();
    }

    return (
        <div>
        <button onClick={handleClickIncrease}>
            Increase
        </button>
         <button onClick={handleClickDecrease}>
            Decrease
        </button>
        </div>
    )
}
```

```js
// component/Counter.tsx
import { container } from "tsyringe";
import Store from "../store/Store";

export default function Counter() {
    const store = container.resolve(Store);
    // 강제 리랜더링 해주는 함수
    const forceUpdate = useForceUpdate();

    store.forceUpdates.add(forceUpdate);

    useEffect(() => {
        store.addListener(forceUpdate);
        return () => {
            store.removeListener(forceUpdate);
        }
    }, [store, forceUpdate])

    return (
        <div>
            <p>{store.count}</p>
        </div>
    )
}
```

```js
// App.test.tsx
import { render, screen, fireEvent } from '@testing-library/react';
const context = describe;

describe('APP', () => {

    beforeEach(() => {
        container.clearInstances();
    })

    context('when press increase button once', () => {
        test('counter', () => {
            render(<APP />);
    
            fireEvent.click(screen.getByText('Increase'));
    
            const elements = screen.getAllByText('1');
            expect(elements).toHaveLength(1);
        })
    })
})
```

---

## 📍 singleton (싱글톤)
싱글톤 패턴은 생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나이고,   
최고 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴한다.

- 하나의 객체만 존재한다
- 프로그램 내에서 해당 객체를 공유해서 사용한다.

---

## ✏️ 정리
- 공부한 내용   
    * [x] tsyringe를 사용해 기본적인 의존성 주입을 구현하기   
    * [x] 싱글톤 패턴이 무엇인지 알기

- 더 공부할 것   
    * [ ] tsyringe practice code를 반복해서 연습 후 익히기