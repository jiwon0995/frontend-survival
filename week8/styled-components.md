
## styled-components

설치
```bash
npm i styled-components

npm i -D @types/styled-components @swc/plugin-styled-components

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

기본 사용버
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