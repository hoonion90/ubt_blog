---
layout: post
title:  "JAVASCRIPT 최대값, 최소값 구하기"
date:   2021-08-01 12:25:41 +0900
categories: javascript
---

## 변수 값 중 최대값, 최소값 구하기

```
let a = 11;
let b = 12;
let c = 10;

console.log(Math.max(a,b,c));
console.log(Math.min(a,b,c));
```

result

```
12
10
```

## 배열에서 최대값 구하기

```
let arr = ['11','12','10'];

console.log(Math.max.apply(null, arr));
console.log(Math.min.apply(null, arr));
```

result

```
12
10
```