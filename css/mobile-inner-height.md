# 모바일 화면 스크린 높이 구하기

모바일 환경에서 스크린 높이를 100vh로 설정했을 때, 생각과 다르게 화면에 스크롤이 생긴다.  
모바일 브라우저에서는 하단바와 상단바 높이가 더해져서 스크린 높이가 크게 잡힌다.

## 실제 스크린 높이로 100vh 설정하는 방법

### javascript + css로 해결하기

```javascript
let vh = window.innerHeight * 0.01;
document.documentElement.style.setProperty('--vh', `${vh}px`);
```

```css
body {
    height: 100vh;
    height: calc(var(--vh, 1vh) * 100);
}
```

react 코드로 작성하면 다음과 같다.

```javascript
  useEffect(() => {
    function setInnerHeight() {
      let vh = window.innerHeight * 0.01;
      document.documentElement.style.setProperty('--vh', `${vh}px`);
    }

    setInnerHeight();
    window.addEventListener('resize', setInnerHeight);
    return () => {
      window.removeEventListener('resize', setInnerHeight);
    };
  }, []);
```

