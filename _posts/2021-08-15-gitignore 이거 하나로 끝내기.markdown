---
layout: post
title:  "gitignore 이거 하나로 끝내기"
date:   2021-08-15 22:00:33 +0900
categories: git
excerpt_separator: <!--more-->
preview: y
---

### .gitignore 파일

.gitignore 파일은 이름에서 느껴지듯이 git이 관리하지 않을 파일들을 지정해두는 파일이다.
프로젝트를 진행하다 보면 자동으로 생성되는 로그파일이나 외부 패키지, 깃에 공유되어서는 안되는 api키와 같은 내용이 작성된 .env 와 같은 파일들이 있을 것이다.
.gitignore 에 원격 저장소에 commit 하고 싶지 않은 내용을 작성해두면 git에서 그 내용을 읽어 해당하는 디렉토리 또는 경로 패턴에 위치한 파일들을 버전관리에서 무시하도록 해준다.
이 때, .gitignore 는 항상 .git 폴더가 위치한 루트 디렉토리에 존재해야 한다.

<!--more-->

### .gitignore 생성

.git 폴더가 있는 위치에 생성해주면 되는데, 윈도우의 경우 그냥 메모장으로 작성하여 txt파일이 아니라 모든 파일로 설정한 후에 파일명을 .gitignore 로 작성해주면 된다. 아니면 git bash 를 이용하여 해당 폴더로 이동한 뒤 vim .gitignore 명령으로 생성하여 작성해도 무방하다. 이후 버전관리를 하지 않을 목록을 작성하면 된다.

이 때, 이미 버전관리를 수행 중인 파일들을 .gitignore 에 작성하게 되면 git은 원래대로 그 파일들을 추적하게 된다. 이 경우에는 이미 버전 관리가 되고 있는 파일들을 수동으로 해당 파일들을 버전 관리에서 제외시켜주어야 한다. 다음의 명령어들을 사용하여 처리한다.

```
$ git rm -r --cached .

$ git add .

$ git commit -m "fixed untracked files"
$ git rm -r --cached . : 현재 Repository의 cache를 모두 삭제한다.
$ git rm -r --cached <filename> : 해당하는 파일을 원격 저장소에서 삭제한다.
$ git rm <filename> : 원격 저장소와 로컬 저장소에 있는 파일을 삭제한다.
$ git rm --cached <filename> : 원격 저장소에 있는 파일을 삭제한다. 로컬 저장소에 있는 파일은 삭제하지 않는다
-r 옵션 : 하위 디렉토리를 포함하여 모든 내용을 삭제한다.
```

이후 git add . 을 통해 .gitignore에 넣은 파일 목록들을 제외하고 다른 모든 파일을 다시 track하도록 설정한다.
위 작업 이후에는 반드시 커밋을 해준다. git commit -m "fixed untracked files"

### .gitignore 문법

~~~

패턴	설명
*	/ 를 제외한 모든 문자열과 매칭 (문자열 길이 0이상)
**	/ 를 포함한 모든 문자열과 매칭 (문자열 길이 0이상)
?	/ 를 제외한 하나의 문자와 매칭 (빈 문자 x)
[abc]	[] 안에 있는 모든 각각의 문자들과 매칭 (a또는 b또는 c 중에 하나)
{a, b, c}	{} 안에 있는 , 로 구분된 각각의 문자열들과 매칭
[^abc]	[] 안에 있는 모든 각각의 문자들을 제외한 문자들과 매칭
[a-z]	[] 안에서 - 사이에 있는 첫 문자와 마지막 문자 범위에 있는 모든 문자들에 대해 매칭 (a-z, A-Z, 0-9 등..)
/	/ 부터 시작하는 경로 패턴은 하위 디렉토리에 반복적으로 적용되지 않는다.
!	! 로 시작하는 패턴은 .gitignore에서 제외되며, 무시되지 않는다.
#	# 으로 시작하면 주석처리
.gitignore 파일은 Glob 패턴에 따라 작성이 된다. Glob 패턴은 와일드 카드 문자를 사용하여 일정한 패턴을 가진 파일 이름을 지정하기 위한 패턴이다. 정규표현식과 유사한 문법들이 많다.

~~~

### 작성 예시

```
# 확장자가 .js 인 파일은 무시
*.js

# .js 파일들은 모두 무시되지만, test.js만은 무시하지 않음
!test.js

# 현재 디렉토리에 있는 /test.js파일은 무시되지만,
# subDir/test.js 같이 특정 디렉토리 하위에 있는 test.js는 무시되지 않음
/test.js

# node_modules/ 디렉토리에 있는 모든 파일을 무시
node_modules/

# src/ 하위의 .js파일만 무시
src/*.js

# src/ 하위에 존재하는 모든 디렉토리의 .txt 파일을 무시
src/**/*.txt

# 현재 디렉토리와 그 하위 디렉토리 내에 존재하는 모든 .js 파일을 무시
/**/*.js

# 현재 디렉토리 내에 존재하는 모든 .js .ts 파일 무시
/*.{js, ts}

# 현재 디렉토리 내에 있는 ex1.js ex2.js ex3.js 파일 무시
/ex[1-3].js
```

참고로 개발 환경이나 언어를 입력하면 자동으로 해당하는 .gitignore 파일을 생성해주는 사이트가 있다.
https://www.toptal.com/developers/gitignore

출처 : https://kyu9341.github.io/Git/2020/08/23/git_gitignore/