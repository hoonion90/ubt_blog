---
layout: post
title:  "javascript URI 정보 조회하기(가져오기)"
date:   2021-09-30 23:58:13 +0900
categories: WEB
excerpt_separator: <!--more-->
preview: y
---

## javascript URI 정보 조회하기

먼저 참고하면 좋은 내용 ==> 
[URI, URL, URN 개념](http://www.watu.me/blog/web/2021/09/26/URI,URL,URN-%EA%B0%9C%EB%85%90.html)

<!--more-->

### URI 전체 조회하기 
- input

``` javascript
window.location.href
```

- result

```
'http://www.watu.me/result?c=class_05'
```

### hostname 조회하기

- input

```javascript
window.location.hostname
```

- result

subdomain과 domain 그리고 TLD를 나타낸다. 그래서 다음과 같이 조회된다.

```
'www.watu.me'
```

### pathname 조회하기

- input

```javascript
window.location.pathname
```

- result

uri에서 pathname은 도메인 값 뒤의 '/path' 부분을 의미한다. 따라서 결과는 다음과 같다.

```
'/result'
```

### 프로토콜 조회하기

- input 

```javascript
window.location.protocol
```

- result

프로토콜로 http를 사용하고 있으므로 다음과 같이 조회된다.

```
'http:'
```

### +a assign()

- input

```javascript
window.location.assign("https://www.naver.com")
```

- reuslt

window.location에 네이버를 띄워준다.
따라서 네이버 페이지로 이동하는 것을 볼 수 있다.