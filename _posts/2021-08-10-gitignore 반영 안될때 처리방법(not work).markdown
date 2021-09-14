---
layout: post
title:  "gitignore 반영 안될때 처리방법(not work)"
date:   2021-08-10 10:17:35 +0900
categories: linux
excerpt_separator: <!--more-->
preview: y
---

## .gitignore 파일을 변경할 때

다음은 Git가 항상 올바른 파일을 추적하는지 확인하기 위해 .gitgnore 파일을 변경할 때 주의해야 할 몇 가지 사항입니다.

<!--more-->

1. .gitignore 파일을 변경합니다.
1. $git rm -r --cached . 커맨드를 입력합니다.
1. $git add . 커맨드를 입력합니다.
1. $git commit -m "Commit message" 커밋합니다.





.git refresh,  .gitignore 새로고침, .gitignore refresh, .gitignore 반영 안될 때
.gitignore 적용 안될 때