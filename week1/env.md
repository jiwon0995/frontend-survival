### 개발 환경

#### 01. Node.js 설치   
fnm(Fast Node manager)으로 node를 최신 버전으로 설치   
   
#### 02. 개발 환경 세팅
 ```npm init -y```
 
 을 하면 이렇게 package.json이 생성된다.   
 package.json은 프로젝트의 정보를 담고 있는 파일이다.
 
 ```json
 {
  "name": "my-app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

.gitignore 파일을 만들고 git에 올라가면 안되는 파일을 추가해준다.

👉 [github gitignore]("https://github.com/github/gitignore", 'github gitignore')   

타입스크립트 설치하고 설정하기

```npm i -D typescript```

```npx tsc --init```   

타입스크립트 설정 파일 tsconfig.json이 생성된다.   
👉 [tsconfig.json reference]('https://www.typescriptlang.org/tsconfig', 'tsconfig.json')   

ESLint 설치하고 설정하기

```npm i -D eslint```

```npx eslint --init```   
   
시키는대로 잘 하면 .eslintrc.js 파일이 생성된다.

React 설치   
```npm i react react-dom```   
```npm i -D @types/react @types/react-dom```

테스팅 도구 설치
```
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom
```   
Parcel 설치   
```npm i -D parcel```   

기본세팅으로 필요한 패키지들을 설치 후 package.json의 scripts를 세팅해준다.    
```JSON
  "scripts": {
    "start": "parcel --port 8080",
    "build": "parcel build",
    "check": "tsc --noEmit",
    "lint": "eslint --fix --ext .js,.jsx,.ts,.tsx .",
    "test": "jest",
    "coverage": "jest --coverage --coverage-reporters html",
    "watch:test": "jest --watchAll"
  },
```   
설정한 script 명령어들은 ```npm run [script명]```으로 실행할 수 있다.   
🤘 기본 세팅이 끝났다! 🤘