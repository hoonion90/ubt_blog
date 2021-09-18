---
layout: post
title:  "HEROKU 에 NODE.JS 로 배포하기"
date:   2021-07-14 18:24:41 +0900
categories: server
excerpt_separator: <!--more-->
preview: y
---

## HEROKU(헤로쿠,히로쿠)란?

헤로쿠 주식회사는 웹 애플리케이션 배치 모델로 사용되는 여러 프로그래밍 언어를 지원하는 클라우드 PaaS이다

<!--more-->

> Paas = Platform as a Service 서비스 단위로 제공하는 클라우드 컴퓨팅 서비스

ruby, python, java, nodejs, php, go 등 다양한 언어로 배포가 가능하다.


## HEROKU 설치

먼저 회원가입을 해주세요.

> [https://dashboard.heroku.com/](https://dashboard.heroku.com/)

회원가입, 이메일인증 이 완료되면 운영체제에 맞는 Heroku CLI를 설치합니다.

> [https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

## HEROKU 배포 준비

[##_Image|kage@Gy4YV/btrbIHu3ZHE/jr4wpUUdGNtZDi5Mzi0fw1/img.png|alignCenter|width="100%" data-origin-width="1388" data-origin-height="276" data-ke-mobilestyle="widthOrigin"|||_##]

create new app으로 앱을 생성해줍니다.  
커맨드창(cmd, bash 등)을 실행시켜 줍니다. 그리고 헤로쿠에 로그인해줍니다.

``` bash
$ heroku login
```

자신의 프로젝트 경로로 이동하여 init, 후 remote 설정해줍니다.

``` bash
$ cd my-project/
$ git init
$ heroku git:remote -a calm-oasis-26857
```

주의할 점 node.js로 서비스할 경우 배포 전에 package.json 을 생성해주어야 합니다.

``` bash
$npm init
```

## 배포하기

스태이징 처리, 커밋 처리하고 push 해주면 자동으로 배포가 됩니다.

``` bash
$ git add .
$ git commit -am "make it better"
$ git push heroku master
```

## $npm init 시 참고 (출처: [https://asource.tistory.com/5](https://asource.tistory.com/5))

npm init 실행 시 물어보는 것들입니다

-   name: (tests)  
    프로젝트 명을 기입합니다. 입력하지 않고 Enter를 입력할 경우 폴더명인 tests가 자동으로 기입됩니다..

-   version: (1.0.0)  
    진행 중인 프로젝트의 버전을 이야기하며, Enter를 입력할 경우 괄호 안의 내용이 자동으로 기입됩니다

-   description:  
    프로젝트에 대한 설명을 기입합니다. 프로젝트에 대한 내용이 없을 경우 공백으로 들어갑니다.

-   entry point: (index.js)  
    제작할 프로젝트의 시작할 실행 파일을 지정합니다. 통상적으로는 app.js라는 파일 명을 많이 쓰지만, 프로젝트 작성자 본인 마음입니다. 만약 입력하지 않고 Enter를 입력할 경우 괄호 안의 내용이 자동으로 기입됩니다.

-   test command:  
    프로젝트 생성 후 테스트로 입력할 메시지

-   git repository:  
    git저장소가 생성되어있고 github 이 연결되어있다면 자동으로 입력되지만 저장소를 사용하지 않는다면 넘어가셔도 됩니다.

-   keywords:  
    프로젝트에 대한 키워드를 입력합니다.

-   author :  
    프로젝트 작성자를 입력합니다.

-   license: (ISC)  
    저작권에 대한 정보를 기입하며 기본적으로는 ISC를 가 작성됩니다.  
    위정보를 모두 기입하면 package.json 파일을 생성합니다.