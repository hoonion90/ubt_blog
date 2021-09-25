---
layout: post
title:  "URI, URL, URN 차이"
date:   2021-09-26 00:28:13 +0900
categories: WEB
excerpt_separator: <!--more-->
preview: y
---

## 라우팅 (페이지 라우팅)

클라이언트로부터 요청받은 URL과 VIEW를 매칭시켜주는 것
사전적인 의미 그대로 특정한 URL에 대해 특정한 뷰로 연결 시켜주는 역할.

<!--more-->

## URL과 URI 그리고 URN

```
http://www.google.co.kr:80/blog/uri.php?url=urn#top
-Protocol
-------Subdomain
----------Domain
-----------------ccTLD(Country Code)
--------------------TLD(Top Level Domain)
-----------------------Port
--------------------------Path
-----------------------------------Page
---------------------------------------Extension
-----------------------------------------Parameter
--------------------------------------------------Anchor
```

## URI (Uniformed Resource Identifier)
- 인터넷 자원 고유 식별자

## URL (Uniformed Resource Locator)
- Protocol 포함
- 해당자원의 위치, Path를 의미
- 일반적으로 사이트의 도메인을 의미함.

## URN (Uniformed Resource Name)
- Protocol 포함 X
- 해당 자원의 이름을 의미
- 독립적인 자원 지시자
- Page 이후 부분까지 포함.
