---
layout: post
title:  "jekyll 로컬 세팅시 타임존 에러 발생할 때 해결법"
date:   2020-05-09 13:05:00
categories: jekyll
tags: jekyll
comments: 
---
```
에러메세지 :
Dependency Error: Yikes! It looks like you don't have tzinfo or one of its dependencies installed. In order to use Jekyll as currently configured  
, you'll need to install this gem. If you've run Jekyll with `bundle exec`  
, ensure that you have included the tzinfo gem in your Gemfile as well.
```

해결법 :  
gemfile에 아래 텍스트를 추가한다.  
gem 'tzinfo'  
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
