---
layout: post
title:  "nodejs에서 특정URI만 다른 포트로 포워딩시키기"
date:   2021-09-19 23:09:45 +0900
categories: javascript
excerpt_separator: <!--more-->
preview: y
---

nodejs에서 /blog/로 오는 요청에 대해서 4000포트로 포워딩 시켜주는 작업을 해보자.
저는 nodejs로 nodejs서버를 80포트로 돌리고 추가로 jekyll을 이용해서 /blog/로 오는 요청은 
4000포트의 루비로 동작시키는 jekyll로 포워딩 시켜줄 것이다.
<!--more-->

## http-proxy-middleware 사용

http-proxy-middleware 로 /blog/로 들어오는 요청을 처리할 수 있다.
우선 메인이되는 nodejs 서버(80)가 도메인(watu.me) 기본으로 설정되어 있고
4000의 지킬(jekyll) 블로그가 동작되고 있는 상황.

htttp 프록시 미들웨어를 사용하여 /blog/로 오는 요청은 4000포트로 전달해보자.

## 설치

``` bash
$ npm install --save-dev http-proxy-middleware
```

## 선언

- esm 방식

``` javascript
import { createProxyMiddleware } from 'http-proxy-middleware';

```

- common js 방식

``` javascript
const express = require('express');
const { createProxyMiddleware } = require('http-proxy-middleware');
```


## 처리

option router return에 아래처럼 포트까지 입력해준다.
그리고 해당 옵션으로 createProxyMiddleware 객체를 생성하여, /blog/로 오는 요청을 아래처럼 처리해준다.

``` javascript
const options = {
    changeOrigin: true,
    ws: true,
    router(req){return 'http://***.***.***.***:4000'} // 이 부분에 아이피 설정
}
const blogserver = createProxyMiddleware(options);
app.use('/blog/', blogserver);
```

끝, 설명이 자세하지 않으므로 추가 작업이 필요하다면 아래 링크에서 확인하도록 하자! 

> https://github.com/chimurai/http-proxy-middleware