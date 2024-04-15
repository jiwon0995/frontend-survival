# React Testing Library

React 컴포넌트를 사용자 입장에 가깝게 테스트할 수 있는 라이브러리

## BDD(Behavior Driven Development)

BDD란? 행위 주도 개발이다. 행위 주도 개발이 도대체 뭔가..? 한국말인데 너무 어렵다.  
기본 개념을 이해하는데 도움이 된 영상  
[TDD, BDD?](https://tv.kakao.com/v/414004682)

기획단계에서 만들어진 사용자 경험을 코드로 옮겨서 테스트 하는 과정을 BDD라고 한다.

- Given(주어진 환경 - 사용자가 로그인을 하려고 할때)
- When(행위 - 이름을 입력하는 Input창에 이름을 입력하면)
- Then(결과 - 입력한 이름이 화면에 보여진다)

BDD는 TDD에서 파생된 개념으로 BDD 테스트로 유저 시나리오를 검증하고, 시나리에서 사용된 모듈은 TDD로 작성된다.
BDD 테스트 케이스로 시나리오 검증을 하다보면 기획단계에서 누락된 부분도 찾을 수 있다.

## Test Code 작성해보기

범용으로 사용할 수 있는 Text입력 filed를 만드는 연습

``` javascript
import {render, screen} from '@testing-library/react'
import TextField from './Textfield'

test('TextField', ()=> {

    //given
    const label = 'Name'
    const text = 'Tester'
    const setText = () => {}

    //when
    <TextField
        label={label}
        placeholder=''
        text={text}
        setText={setText}
    />

    //then
    screen.getByLabelText('Name')
    
})
```

given 단계에서 필요한 값을 준비해주고, 해당 값을 TextField에 넣었을 때 기대하는 화면을 테스트한다.

좀 더 다양한 테스트 케이스 추가하기

``` javascript
import { render, screen, fireEvent } from '@testing-library/react'

import TextField from './TextField'

const context = describe

describe("TextField", () => {

    const label = 'Name'
    const text = 'Tester'
    const setText = jest.fn()

    // 초기화 해주기
    beforeEach(() => {
        setText.mockClear()
    })
    // when
    // 중복되는 함수 꺼내기
    function renderTextField() {
        render((
            <TextField
                label={label}
                text={text}
                setText={setText}
            />
        ))
    }

    //then
    if('render an input control', () => {
        renderTextfield()

        screen.getByLabelText('Name')
    })

    context('when user types text', () => {
        if('calls the change handler', () => {
            renderTextField()
            //when
            fireEvent.change(screen.getByLabelText(label), {
                target: {
                    value: 'New Name',
                }
            })
            //then
            expect(setText).toBeCalledWith('New Name')
        })
    })
})

```

테스트 코드를 만드는건 정말 어려워..!
