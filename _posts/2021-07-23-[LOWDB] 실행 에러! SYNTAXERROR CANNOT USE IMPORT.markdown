---
layout: post
title:  "[LOWDB] 실행 에러?! SYNTAXERROR: CANNOT USE IMPORT"
date:   2021-07-23 19:37:41 +0900
categories: lowdb
---

## SyntaxError: Cannot use import statement outside a module

아래와 같은 에러가 발생한다면... 정답은 바로 Warning에 표시됩니다.  
To load an ES module, set "type": "module" in the package.json or use the .mjs extension.

```
$ node index.js
(node:2484) Warning: To load an ES module, set "type": "module" in the package.json or use the .mjs extension.
(Use `node --trace-warnings ...` to show where the warning was created)
D:\workspace\github\std_lowdb\index.js:1
import { join, dirname } from 'path'
^^^^^^

SyntaxError: Cannot use import statement outside a module
```

## .js파일을 .mjs 파일로 변경하여 처리한다.

원인은 아래에 설명하겠습니다.

```
$node index.js
```

```
$node index.mjs
```

## package.json 파일을 수정한다.

-   "type" : "module" 을 추가해줍니다.

```
{
  "name": "std_lowdb",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "dependencies": {
    "lowdb": "^2.1.0"
  },
  "devDependencies": {},
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/hoonion90/std_lowdb.git"
  },
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/hoonion90/std_lowdb/issues"
  },
  "homepage": "https://github.com/hoonion90/std_lowdb#readme",
  "type" : "module"
}
```

## 원인?!

해당 파일을 client단으로 인식하는지 서버단으로 인식하는지의 차이인가?  
package.json의 “type” 필드에 별도의 값이 없거나 “commonjs”로 설정되어 있으면 기본 모듈 처리 방식이 require를 사용하는 commonjs 방식으로 설정되기 때문, "type" : "module" 설정을 통하여 모듈 처리 방식이 import를 사용하는 es6 방식으로 변경하여 해결.

## 참고.

> [https://it-eldorado.tistory.com/92](https://it-eldorado.tistory.com/92)

파일 단위의 모듈화는 코드의 재활용성을 극대화시킴으로써 애플리케이션 개발의 생산성을 엄청나게 향상시킨다. 그런데 초창기 JavaScript는 모듈 시스템이라는 것을 갖추고 있지 않았다. 그나마 가지고 있는 것이라고는 'script' 태그를 통해 또 다른 JavaScript 소스 파일들을 서버에게 요청하는 방식이었는데, 각각의 'script' 태그에 의해 로드된 JavaScript 코드들은 사실상 하나의 파일 안에 작성된 것처럼 동작했다. 즉, 로드된 각 JavaSript 소스 파일마다 독립적인 파일 스코프를 가지고 있는 것이 아니라 하나의 전역 객체를 공유하는 방식이었던 것이다. 이로 인해 서로 다른 JavaScript 소스 파일에 존재하는 변수나 함수들이 같은 이름을 가짐으로써 충돌하는 문제들이 발생하기 매우 쉬웠다. 즉 모듈 시스템이란 것이 사실상 없었던 것이다.

이러한 배경에서 JavaScript를 클라이언트 사이드에서뿐 아니라 서버 사이드에서도 범용적으로 사용하기 위한 움직임까지 일어나면서, 모듈화는 JavaScript가 풀어야 할 핵심 과제가 되어 버렸다. 그래서 등장한 것이 바로 CommonJS와 AMD(Asynchronous Module Definition)이었다. 결국 JavaScript의 모듈화 방식은 크게 CommonJS와 AMD로 나뉘게 되었다. 이때 서버 사이드 JavaScript 런타임인 Node.js의 경우 모듈 시스템으로서 CommonJS를 채택하였다. 따라서 Node.js 환경에서는 모듈별로 독립적인 파일 스코프를 가진다는 것을 유추할 수 있다. 그리고 이와 같은 방식으로 브라우저에서 JavaScript를 모듈화 하기 위해서는 CommonJS 혹은 AMD를 기반으로 구현된 별도의 모듈 로더 라이브러리를 사용해야 했다. 이러한 상황에서, ES6부터는 브라우저 단에서도 쉽게 JavaScript의 모듈화가 가능하도록 모듈 시스템이 추가되었다. 따라서 오늘날 많은 브라우저들은 ES6 기반의 모듈 내보내기 및 불러오기 방식을 지원하고 있다.