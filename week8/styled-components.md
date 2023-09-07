
## styled-components

### styled-components 개념

- Automatic critical CSS : styled-components는 페이지에 실제로 렌더링되는 컴포넌트에만 스타일이 적용되므로 불필요한 CSS를 제거할 수 있다.
- No class name bugs : 고유한 클래스 이름을 생성한다. 중복, 철자 오류에 대해 걱정할 필요가 없다.
- Easier deletion of CSS : 모든 스타일링이 특정 구성 요소에 연결되어 있어 명확하게 알 수 있다. 구성 요소가 사용되지 않고 삭제되면 스타일도 삭제된다.
- Simple dynamic styling : props를 전달하여 동적으로 스타일을 변경할 수 있다.
- Painless maintenance : CSS를 작성할 필요가 없으므로 유지 관리가 쉽다.
- Automatic vendor prefixing : CSS를 현재 표준에 맞게 작성하고 스타일 구성 요소가 나머지를 처리하도록 할 수 있다.

설치
```bash
npm i styled-components

npm i -D @types/styled-components @swc/plugin-styled-components
```
vscode-styled-components extention 설치

.swcrc 추가
```js
{
	"jsc": {
		"experimental": {
			"plugins": [
				[
					"@swc/plugin-styled-components",
					{
						"displayName": true,
						"ssr": true
					}
				]
			]
		}
	}
}
```

### 사용법

기본 사용법
```jsx
import styled from 'styled-components';

const Paragraph = styled.p`
    color: #00f;
`;

export default function Greeting() {
    return (
        <Paragraph>Hello, world!</Paragraph>
    );
}
```

```jsx
import styled from 'styled-components';

const Paragraph = styled.p`
    color: #00f;

    string {
        color: #f00;
    }
`;

export default function Greeting() {
    return (
        <Paragraph>Hello, world<strong>!</strong></Paragraph>
    );
}
```

스타일드 컴포넌트에 다른 스타일드 컴포넌트를 상속받아서 사용할 수 있다.

```jsx
import styled from 'styled-components';

const Paragraph = styled.p`
    color: #00f;

    string {
        color: #f00;
    }
`;

const BigParagraph = styled(Paragraph)`
    font-size: 2rem;
`;

export default function Greeting() {
    return (
        <BigParagraph>Hello, world<strong>!</strong></BigParagraph>
    );
}
```