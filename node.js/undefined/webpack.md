# Webpack

가장 많이 쓰이는 번들러이다. CommomJS, AMD, ES6 Module 포맷을 지원한다. 자바스크립트, CSS, Image 리소스도 관리할 수 있다.Minify, Uglify, Banner, CSS Preprocess, Code Spliting, Dynamic imports, tree shaking등 기능을 제공한다.

> webpack 설치 및 실행

빈 프로젝트를 만들고 커맨드를 실행하여 설치, 실행한다.

1. package.json 생성

```bash
npm init
```

2. 설치

```text
npm install --dev webpack webpack-cli
```

3. index.js 생성 

package.json과 같은 레벨에 src/index.js 파일을 생성하고 웹팩을 실행한다.

```text
npx webpack --mode development
```

아무설정이 없으면 기본으로 dist 폴더에 번들링된 main.js 가 생성된다.

