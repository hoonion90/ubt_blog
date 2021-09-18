---
layout: post
title:  "ubuntu에서 jekyll 돌리기"
date:   2021-06-28 10:29:13 +0900
categories: jekyll
excerpt_separator: <!--more-->
preview: y
---

## ubuntu Jekyll 을 설치하기

Jekyll 을 설치하기 전, 필요한 모든 의존요소를 가지고 있는지 확인해야 합니다.

``` bash
$ sudo apt-get install ruby-full build-essential zlib1g-dev
```

루트 사용자로 루비 젬을 설치하는 것은 피하는게 좋습니다. 
따라서, 일반 사용자 계정에 젬 설치 디렉토리를 설정할 필요가 있습니다. 

<!--more-->

## 환경변수 등록하기

다음 명령어들은 젬 설치 경로를 설정하는 환경설정 변수들을 ~/.bashrc 파일에 추가할 것입니다. 다음과 같이 실행하세요:

``` bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## 마지막으로, Jekyll 을 설치합니다

``` bash
$ gem install jekyll bundler
```

## jekyll을 설치할 경로로 이동하여 새 블로그 생성하기

``` bash
$ cd workspace
```

저는 workspace 안에 myblog로 생성해주겠습니다.

``` bash
$ jekyll new myblog
```

``` bash
$ cd myblog
```

build 해서 로컬 서버에서 사용할 수 있도록 합니다.

``` bash
bundle exec jekyll serve
```

아래 경로에서 테스트합니다.

[http://localhost:4000]


## ubuntu에서 백그라운드로 지킬(jekyll)을 실행할 때

nohup로 jekyll을 수행하면 정상적으로 돌아갈 줄 알았는데  문제가 있었다.
아래 글을 참고하도록 하자.

[2021-06-30-백그라운드에서 지킬(jekyll) 실행하기]


[http://localhost:4000]: http://localhost:4000
[2021-06-30-백그라운드에서 지킬(jekyll) 실행하기]: http://www.watu.me/blog/jekyll/2021/06/30/백그라운드에서-지킬(jekyll)-실행하기.html
