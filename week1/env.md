# 개발 환경 세팅하기

목표 : Node.js 환경에서 개발하기 위한 세팅이 익숙해질 때 까지 해보자

마지막 업데이트 : 2023. 12. 28

## 01. Node.js 설치

fnm(Fast Node manager)으로 node를 최신 버전으로 설치  
현재 LTS 버전 : 20.10.0

설치할 수 있는 버전 확인  
```bash fnm ls-remote```  
LTS 버전 설치 후 기본 버전으로 설정

```bash
fnm install --lts
```

## 02. 개발 환경 세팅

1.프로젝트 폴더 생성 후 해당 폴더로 이동

```mkdir [폴더명]```

```cd [폴더명]```

2.package.json 파일 자동 생성  

 ```npm init -y```

3.gitignore 파일을 만들고 git에 올라가면 안되는 파일을 추가해준다.

용량이 큰 node_modules 폴더와 .env 파일을 추가해준다.  
github이 만들어놓은 gitignore 파일을 참고하면 좋다.

👉 [github gitignore]("https://github.com/github/gitignore", 'github gitignore')

4.타입스크립트 설치하고 설정하기

-D 옵션은 개발용으로 설치한다는 뜻  
package.json에 dependencies와 devDependencies가 있는데, -D 옵션은 devDependencies에 설치된다.

```npm i -D typescript```

tsconfig.json 파일 생성  
npx는 npm 패키지를 실행시켜주는 도구이다.

```npx tsc --init```

타입스크립트 설정 파일 tsconfig.json이 생성된다.

👉 [tsconfig.json reference]('https://www.typescriptlang.org/tsconfig', 'tsconfig.json')

5.ESLint 설치하고 설정하기

```npm i -D eslint```  

환경에 맞게 설정해준다.  
```npx eslint --init```

6.React 설치 하기  
```npm i react react-dom```  
```npm i -D @types/react @types/react-dom```

7.테스팅 도구 설치 하기

```bash
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom@5.16.4
```  

jest.config.js 파일 생성 후 설정해준다.  
👉 [jest.config.js reference]('https://github.com/ahastudio/CodingLife/blob/main/20220726/react/jest.config.js', 'jest.config.js')  

8.Parcel 설치 하기  

```npm i -D parcel```

9.기본세팅으로 필요한 패키지들을 설치 후 package.json의 scripts를 세팅해준다.

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

10.기본 파일들을 생성해준다.

```bash
mkdir src
touch src/main.tsx
touch src/App.tsx
touch src/App.test.tsx
touch src/components
```

11.vscode/settings.json 파일을 생성하고 아래 내용을 추가해준다.

```JSON
{
    "editor.rulers": [
        80
    ],
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "trailing-spaces.trimOnSave": true
}
```

🤘 기본 세팅이 끝났다! 🤘
