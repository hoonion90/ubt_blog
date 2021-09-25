---
layout: post
title:  "Spring(스프링)과 Spring Boot(스프링부트) 차이"
date:   2021-09-26 00:37:43 +0900
categories: WEB
excerpt_separator: <!--more-->
preview: y
---

## Spring과 Spring boot
스프링과 스프링부트의 차이점이 뭘까 ?
Spring은 Spring Framework를 가르킨다 둘 사이의 차이점에대해서 정리해보자
<!--more-->

## Spring (Spring Framework)
- 스프링 프레임워크를 간단하게 스프링(spring)이라고도 부른다.
- 대한민국 공공기관의 웹 서비스 개발 시 사용을 권장하는 전자정부 표준프레임워크의 기반 기술로 쓰임.
- 경량 컨테이너
- IoC(Invention of Control: 제어 역행)
- Di(Dependency Injection: 의존성 주입) 
- AOP(Aspect-Oriented Programming: 관점지향 프로그래밍)

## Spring Boot
- 스프링 프레임워크는 기능이 많고 환경설정이 복잡하다. 이에 어려움을 느끼는 사용자들을 위해 나온 것이 스프링 부트이다.
- 스프링 프레임워크를 사용하기 위한 설정의 많은 부분들이 자동화 되어 사용자가 편리하게 활용할 수 있도록 돕는다.
- 스프링부트 starter dependency만 추가하면 바로 API 정의, Tomcat 또는 jetty로 웹 애플리케이션 서버를 실행할 수 있다.
- 스프링 홈페이지의 이니셜라이저를 사용하면 바로 실행 가능한 코드를 만들어 준다.
- 실행환경, 의존성 관리, 인프라 등은 신경 쓸 필요없이 바로 코딩을 시작할 수 있도록 해준다.

## Spring Framework 와 Spring Boot의 차이점
- Spring Boot는 Embeded Tomcat을 사용하기 때문에 tomcat을 설치하거나 매번 버전관리의 수고로움을 덜어준다.
- starter를 통항 dependency 자동화 - 각각의 dependency 들의 호환성을 일일이 맞춰줘야하는 어려움이 많았는데 이 부분을 많이 덜어 줌.
- XML 설정이 필요없다.
- jar file을 이용해 자바 옵션만으로 손쉽게 배포가 가능하다.
- Spring Actuaor를 이용한 애플리케이션의 모니터링과 관리를 제공한다.

## Spring Boot starter
- 특정 목적을 달성하기 위한 의존성 그룹
- 메이븐(prom.xml)이나 그레이들(build.gradle)에 'spring-boot-starter-data-jpa'만 추가하면 spring boot가 그에 필요한 라이브러리들을 알아서 받아온다.
- starter 명명 규칙
> srping-boot-starter-*
