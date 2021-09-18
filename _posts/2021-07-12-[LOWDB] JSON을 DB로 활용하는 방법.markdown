---
layout: post
title:  "[LOWDB] JSON을 DB로 활용하는 방법"
date:   2021-07-12 13:05:11 +0900
categories: lowdb
excerpt_separator: <!--more-->
preview: y
---

비용을 들이지 않고 요즘 좋은 서비스들이 많아서 활용하여, 웹서비스를 개발해보려고 하였다.

웹서비스가 DB가 필요해서 json을 db로 활용하는 방법을 찾다가.. lowdb라는 것을 발견하였고 이를 활용하여

HEROKU와 node.js를 사용하여 기획한 웹 서비스를 개발해보려고 한다.

<!--more-->

## 먼저 node.js를 설치한다.

> [https://nodejs.org/ko/download/](https://nodejs.org/ko/download/)

[##_Image|kage@bB5ScS/btrbIIN4baK/7ojmlk42rbeKmL8ETJRok0/img.png|alignCenter|width="100%" data-origin-width="1040" data-origin-height="396" data-ke-mobilestyle="widthOrigin"|||_##]

본인의 OS에 맞는 node.js를 먼저 다운로드하여 설치한다.  
약관동의 후 NEXT..NEXT..

## lowdb 설치

> [https://github.com/typicode/lowdb](https://github.com/typicode/lowdb)

lowdb를 설치하고 사용하기 전에 먼저 경로를 생성해주자.  
ex> \\workspace\\project01\\  
콘솔창 (bash나 cmd)을 실행시켜서 해당 경로로 이동하여 npm install lowdb를 입력한다.

``` bash
$npm install lowdb
```

정상적으로 설치가 되면 main.mjs 파일을 하나 생성하여 아래의 코드를 넣어주자.

``` javascript
import { join, dirname } from 'path'
import { Low, JSONFile } from 'lowdb'
import { fileURLToPath } from 'url'

const __dirname = dirname(fileURLToPath(import.meta.url));

// Use JSON file for storage
const file = join(__dirname, 'db.json')
const adapter = new JSONFile(file)
const db = new Low(adapter)

// Read data from JSON file, this will set db.data content
await db.read()

// // If file.json doesn't exist, db.data will be null
// // Set default data
// db.data ||= { posts: [] }
db.data = db.data || { posts: [] } // for node < v15.x

// // Create and query items using plain JS
// db.data.posts.push('hello world')
// db.data.posts[0]

// // You can also use this syntax if you prefer
const { posts } = db.data
posts.push('hello world')

// // Write db.data content to db.json
await db.write()
```

파일을 저장하고 콘솔창을 실행시켜서 node main.mjs 를 입력한다.

``` bash
$ node main.mjs
```

경로에 db.json으로 다음과 같이 파일이 생성되면 정상적으로 완료가 된 것이다.

``` json
{
  "posts": [
    "hello world"
  ]
}
```