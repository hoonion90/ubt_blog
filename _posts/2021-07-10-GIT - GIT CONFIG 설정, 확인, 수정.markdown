---
layout: post
title:  "GIT - GIT CONFIG 설정, 확인, 수정"
date:   2021-07-10 14:13:41 +0900
categories: git
excerpt_separator: <!--more-->
preview: y
---

## git config 확인하기

아래 명령어 중 하나로 간단하게 확인이 가능.

``` bash
$git config --list 
$git config -l
```
<!--more-->

RESULT

``` bash
$git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager-core
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
```

## git username, git useremail 설정하기

가장 많이 설정하는 username, useremail 설정을 하려면

``` bash
$git config --global user.name "fehoon"
$git config --global user.email "이메일@도메인.com"
```

## git config 삭제하기

설정한 config를 삭제하려면 --unset 옵션을 준다.

``` bash
$git config --unset --global user.name "fehoon"
$git config --unset --global user.email "이메일@도메인.com"
```