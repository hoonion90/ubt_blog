---
layout: post
title:  "지킬(jekyll) 사이트맵(sitemap.xml) 만들기"
date:   2021-07-02 12:25:41 +0900
categories: jekyll
excerpt_separator: <!--more-->
preview: y
---

## jekyll-sitemap

구글 콘솔에 등록할 지킬(jekyll)의 사이트맵(sitemap)을 만들어보자.
먼저 gem install을 수행해준다.

<!--more-->

```
$ gem install jekyll-sitemap
```

## Gemfile 편집

```
$ vi Gemfile
```

가장 하단에 gem 'jekyll-sitemap', '~> 1.4' 을 추가해준다.


## 올바른 sitemap을 위한 config 수정

도메인을 등록하여 사용 중이라면 반드시 url을 수정해준다.

```
$ vi _config.yml
```

저는 아래처럼 baseurl을 사용 중 입니다.
그리고 url을 반드시 사용하는 도메인으로 설정해줍니다.

```
baseurl: "/blog" # the subpath of your site, e.g. /blog
url: "http://www.watu.me" # the base hostname & protocol for your site, e.g. http://example.com
```

## jekyll 실행

```
JEKYLL_ENV=production bundle exec jekyll build
```

```
JEKYLL_ENV=production bundle exec jekyll serve
```

반드시 위와 같이 jekyll을 실행하여야만 정상적으로 도메인으로 사이트맵이 생성됩니다.

## 생성된 사이트 맵 경로

저의 경우는 http://www.watu.me/blog/sitemap.xml 의 경로에서 확인 할 수 있습니다.
이제 이 경로를 복사해서 구글 콘솔에 등록해주시면 됩니다.