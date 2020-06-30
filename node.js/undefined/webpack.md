---
description: 번들러 웹팩 설정하기
---

# webpack 설정

## 웹팩 기초 배우기

가장 많이 쓰이는 번들러이다. CommomJS, AMD, ES6 Module 포맷을 지원한다. 자바스크립트, CSS, Image 리소스도 관리할 수 있다.Minify, Uglify, Banner, CSS Preprocess, Code Spliting, Dynamic imports, tree shaking등 기능을 제공한다.

소스코드 [https://github.com/JunH-K/webpack-example](https://github.com/JunH-K/webpack-example)

### webpack 설치 및 실행

빈 프로젝트를 만들고 커맨드를 실행하여 설치, 실행한다. node.js 설치가 되어있어야 하며 없다면 설치한다.

[https://nodejs.org/ko/](https://nodejs.org/ko/)

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

### 웹팩 기본 사용법

기본적으로 모듈의 시작이 되는 파일을 작성한다. src/index.js 이 시작파일이고 엔트리 파일이라고 한다. 이 시작점 파일에서 다른 모듈을 불러와 보자.먼저 불러올 모듈을 작성하고 index.js 파일에서 불러온다.

```javascript
// src/hello.js
export default function hello() {
  return '헬로우 웹팩';
}
```

```javascript
// src//index.js
import hello from "./hello";

hello();

```

### package.json에 스크립트 추가

webpack 실행 스크립트를 package.json에 작성하여 편하 실행한다.

package.json 

```javascript
  "scripts": {
    "bundle": "webpack --mode=development",
    "production": "webpack --mode=production"
  },
```

webpack 오른쪽 mode는 실행시 옵션이다. 옵션마다 다르게 동작한다. 실행은  
npm run bundle, npm run production으로 한다.

* development
  * 개발용 모드
  * 소스맵 제공
* production 
  * 배포용 모드
  * 코드 압축, 난독화
  * 최적화를 통해 번들크기를 줄인다.

> 번들링된 js 파일을 index.html에서 불러온다.

 여러 js 파일이 하나의 main.js 로 만들어 졌기 때문에 index.html에서 main.js 한개 파일만 불러오면 된다.

/index.html

```markup
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>

<script src="./dist/main.js"></script>
</body>
</html>

```

### 번들링 자동화

현재는 코드 수정 시 npm run bundle을 재실행해야 다시 번들 파일이 만들어지기 때문에 번거롭다. 자동으로 번들링되게 옵션을 추가한다.

package.json

```javascript
  "scripts": {
    "bundle": "webpack --watch --mode=development",
    "production": "webpack --mode=production"
  },
```

추가 후 npm run bundle을 재 실행하면 이제는 js 파일 수정시 자동으로 재컴파일 된다.

### 웹팩 설정파일 다루기

번들링에 관한 옵션을 따로 설정할 수 있다.

#### 설정 파일 생성 및 사용

프로젝트 루트에서 webpack.config.js 파일을 생성한다. 그후 모듈을 내보낸다. 번들링을 진행하면 옵션에따라 다르게 번들링 파일이 생성된다.

#### 설정 옵션

* Entry

모듈의 첫 시작점. 시작점을 기준으로 index.js 에 포함된 모듈과 라이브러리가 모 번들링 된다. 

/webpack.config.js

```javascript
module.exports = {
  entry: './src/index.js'
};
```

* Output

번들링 된 파일 위치와 이름을 지정한다. npm run bundle 을 실행하면 dist/main.js로 번들링된 파일이 생성된다. filename을 바꾸면 새로운 파일이 생성되며 기존에 번들링된 파일은 지워지지 않는다. 지워주는 모듈을 설치하면 이전 번들링된 파일을 자동으로 지울 수 있다.

```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js'
  }
};
```

* Loaders

webpack은 기본적으로 자바스크립트 파일만 인식한다. 로더는 다른 타입의 파일도 처리할 수 있도록 모듈로 변환해주는 도구이다.

모듈 예시

* ES2015 import
* CommonJS의 require\(\)
* AMD define, require
* CSS/Sass/Less @import
* 스타일시트 url\(\)
* HTML의 &lt;img src&gt;

css-loader를 사용하여 CSS 파일을 모듈로 사용하는 방법  
CSS파일을 모듈화 할 수 있다. @import, url\(\)을 해석하여 모듈로 만든다.

1. 로더 설치

```text
npm install -D css-loader
```

2. css 파일생성 \(src/css/style.css\)

```css
body{
 background-color: lime;
}
```

3. css 파일 포함하기

index.js 파일에 import 구문으로 최상단에 css를 import 한다. 시작점에 포함해야 모듈로 변환된다.

```text
import './css/style.css'
```

4. webpack 로더 옵션 수정

module.rules에 로더의 규칙을 정의한다. 로더명은 use에 test속성에는 해당로더를 적용하려는 파일 확장자를 정규식 형태로 지정한다.

```javascript
  module: {
    rules: [
      {
        test: /\.css$/,
        use: 'css-loader'
      }
    ]
  }
```

5. 번들링 실행

```text
npm run bundle
```

dist/main.js 를 살펴보면 style.css가 포함되어 있는것을 볼 수 있다.

![](../../.gitbook/assets/image%20%282%29.png)

[https://webpack.js.org/loaders/](https://webpack.js.org/loaders/)

* Plugins

플러그인은 모듈 변환 외에 더 다양한 처리를 할 수 있는 도구를 제공한다. 번들 최적화, 에셋관리등을 할 수 있다.

HtmlWebpackPlugin, CleanWebpackPlugin 사용법

HtmlWebpackPlugin은 HTML 파일을 생성하고, script 태그로 번들링된 모든 파일을 HTML에 삽입해 준다. CleanWebpackPlugin 은 특정 폴더를 지워주는 플러그인으로 빌드 폴더를  정리할때 사용한다.

1. 플러그인 설치

```text
npm install --D html-webpack-plugin clean-webpack-plugin
```

2. webpack.config.js에 추가

```javascript
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const CleanWebpackPlugin = require('clean-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js'
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: 'css-loader'
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin(),
    new CleanWebpackPlugin(['dist'])
  ]
};

```

