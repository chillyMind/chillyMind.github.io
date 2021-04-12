---
title: 칠로그 시작
---

**Jeykll에 대한 첫 인상**
* 적은 공수로 정적 페이지를 구축할 수 있다.
* Admin의 UI가 담백하여, 처음 사용하는 사용자가 자연스럽게 사용할 수 있다.
* [Github Pages](https://pages.github.com/)와  궁합이 잘 맞는다.

**Jeykll 구축해보기**
ruby가 설치되어있어야한다. ( [Windows](https://rubyinstaller.org/downloads/) / [Others](https://www.ruby-lang.org/ko/documentation/installation/) )

```
gem install bundler jekyll
gem install bundler jekyll-paginate

bundle init
bundle add jekyll
bundle add jekyll-paginate

jekyll serve
```
서버가 시작되면, localhost:4000 으로 접근하여 페이지를 확인 할 수 있다.

**jekyll-admin 플러그인 추가하기**
Gemfile 파일에 아래 코드를 추가해준다

```
gem 'jekyll-admin', group: :jekyll_plugins
```

![](/public/img/2021_04_12_00.PNG)

서버가 시작되면, localhost:4000/admin 으로 접근하여 admin 페이지를 확인 할 수 있다.
