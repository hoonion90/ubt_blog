---
layout: post
title:  "[LOWDB] 기존 값 + 1(INCREASE BY 1) UPDATE"
date:   2021-08-08 21:04:23 +0900
categories: lowdb
excerpt_separator: <!--more-->
preview: y
---

## lowdb의 업데이트(lodash 활용)

assign 외에 update를 사용하여 기존 값을 연산하여 처리 가능하다.

<!--more-->

```
_.update(object, path, updater)
```

이 방법은 설정할 값을 생성하는 \_.set것을 허용한다는 점을 제외하고 는 같습니다 updater. 생성 \_.updateWith을 사용자 정의하는 데 사용 합니다 path. 는 updater: 하나 개의 인수로 호출 (값) .

참고: 이 메서드는 object를 update 합니다.

### Since

4.6.0

### Arguments

object (Object) : 수정할 객체입니다.  
path (배열|문자열) : 설정할 속성의 경로입니다.  
updater (Function) : 업데이트된 값을 생성하는 함수입니다.  
return  
(객체) : 반환 object합니다.

### EXAMPLE

```
var object = { 'a': [{ 'b': { 'c': 3 } }] };

_.update(object, 'a[0].b.c', function(n) { return n * n; });
console.log(object.a[0].b.c);
// => 9

_.update(object, 'x[0].y.z', function(n) { return n ? n + 1 : 0; });
console.log(object.x[0].y.z);
// => 0
```

### lowdb 이슈 발췌

You may want to try [https://lodash.com/docs/4.17.4#update](https://lodash.com/docs/4.17.4#update)

```
db.update('count', n => n + 1)
  .write()
```

You can also use set, if you need to set a particular value:

```
db.set('count', someValue)
  .write()
```