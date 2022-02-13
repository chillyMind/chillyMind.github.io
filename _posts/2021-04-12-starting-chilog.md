---
layout: post
title: 칠로그 시작
tags: [Jekyll]
---

**Jekyll에 대한 첫 인상**
* 적은 공수로 정적 페이지를 구축할 수 있다.
* Admin의 UI가 담백하여, 처음 사용하는 사용자가 자연스럽게 사용할 수 있다.
* [Github Pages](https://pages.github.com/)와  궁합이 잘 맞는다.

**Jekyll 구축해보기**
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


만약 다음과같은 에러가 뜨면 Gemfile.lock을 지우고 다시 서빙해보면된다.
```
E:\workspace\chillog> jekyll serve
Traceback (most recent call last):
        10: from C:/Ruby27-x64/bin/jekyll:23:in `<main>'
         9: from C:/Ruby27-x64/bin/jekyll:23:in `load'
         8: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/jekyll-4.2.1/exe/jekyll:11:in `<top (required)>'
         7: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/jekyll-4.2.1/lib/jekyll/plugin_manager.rb:52:in `require_from_bundler'
         6: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/bundler-2.2.17/lib/bundler.rb:148:in `setup'
         5: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/bundler-2.2.17/lib/bundler/runtime.rb:26:in `setup'
         4: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/bundler-2.2.17/lib/bundler/runtime.rb:26:in `map'
         3: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/bundler-2.2.17/lib/bundler/spec_set.rb:163:in `each'
         2: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/bundler-2.2.17/lib/bundler/spec_set.rb:163:in `each'
         1: from C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/bundler-2.2.17/lib/bundler/runtime.rb:31:in `block in setup'
C:/Ruby27-x64/lib/ruby/gems/2.7.0/gems/bundler-2.2.17/lib/bundler/runtime.rb:302:in `check_for_activated_spec!': You have already activated ffi 1.15.1, but your Gemfile requires ffi 1.15.0. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
```
