## 📍 Design System
디자인 시스템은 재사용 가능한 구성 요소와 패턴을 사용하여 대규모로 디자인을 관리하기 위한 완전한 표준 세트이다.

> [Design System - Laura Kalbag]('https://24ways.org/2012/design-systems/')

Components you might keep the same across viewports
- typeface
- base unit
- colour
- shape / form

Components you might differentiate across viewports
- grids
- layout
- font size
- measure (line length)
- leading (line height)

Content it must always be the same   

디자인 시스템의 핵심은 콘텐츠를 최적으로 표시하는 것이다. 콘텐츠를 위한 디자인을 해야한다. 
모든 디바이스에서 동일한 콘텐츠를 공유하고, 디자인 시스템 컴포넌트를 통해 콘텐츠를 표시하고 나타내는 것에 중점을 둬야한다.

## 📍 Atomic Design
Atomic design은 일관성과 확장성을 위해 디자인 시스템을 구축하는 방법이다.


1. Atoms : 웹 인터페이서에 적용되는 HTML tags, input or a button 등의 가장 작은 단위의 컴포넌트.   
색상 팔레트, 글꼴 같은 디자인 요소도 포함된다.

2. Molecules : Atoms의 조합으로, 더 복잡한 컴포넌트를 만들어낸다. 'do one thing and do it well'의 원칙을 따른다.

3. Organisms : Molecules의 조합으로, 페이지의 구성 요소를 만들어낸다. 이 단계에서 독립형, 휴대형, 재사용 가능한 구성 요소를 만들 수 있다.

4. Templates : Organisms의 조합으로, 페이지의 레이아웃을 만들어낸다.

5. Pages : 페이지는 템플릿의 구체화된 버전이다. 실제 콘텐츠가 포함된다.


---

## ✏️ 정리
- 공부한 내용   
    * [x] 디자인 시스템의 정의
    * [x] Atomic Design System


- 참고할 내용
    * [Atomic Design System]('https://github.com/bradfrost/patternlab')
