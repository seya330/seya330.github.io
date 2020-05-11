---
layout: post
title: "jekyll 언어 공부 메모"
date: 2020-05-11 20:40:13
categories: jekyll
tags: jekyll
comments:
---
#### jekyll 변수
{% raw %}
site: 사이트정보 + _config.yml의 환경설정 정보  
page: 페이지 관련 정보 + 머리말에 설정된 변수  
layout: 레이아웃 관련 정보 + 머리말, 레이아웃의 머리말에 설정한 사용자 변수도 포함  
content: 레이아웃 파일 내, 포스트 또는 페이지로 감싸진 렌더링된 컨텐츠  
paginator: 이변수는 환경설정 옵션(paginate)가 설정되어 있을때 사용할 수 있다.  
{% endraw %}

site.time : 현재 시간 (jekyll 명령을 실행한 시간).  
site.pages : 모든 페이지 목록.  
site.posts : 시간 역순의 모든 포스트 목록.  
site.related_posts : 처리중인 파일이 포스트인 경우에, 최대 10 개의 연관 포스트 목록이 이 변수에 할당된다. 디폴트로 가장 최신 포스트 10 개를 가리킨다. 느린 속도를 감수하고 고품질의 결과를 얻으려면, jekyll명령을 --lsi (Latent Semantic Indexing) 옵션과 함께 실행한다. 단, GitHub Pages 가 사이트를 생성할 때는 lsi 옵션을 지원하지 않는다.  
site.static_files : 정적 파일 (다시 말해, Jekyll 의 변환기나 Liquid 렌더러가 처리하지 않는 파일들) 전체 목록. 모든 파일은 다섯 가지 속성을 갖고 있다: path 와 modified_time, name, basename, extname.  
site.html_pages : .html 로 끝나는 site.pages 목록의 하위 세트.  
site.html_files : .html 로 끝나는 site.static_files 목록의 하위 세트.  
site.collections : 모든 콜렉션 목록 (포스트 포함).  
site.data : _data 디렉토리에 있는 YAML 파일에서 읽어들인 데이터 목록.  
site.documents : 각 콜렉션의 모든 문서 목록.  
site.categories.CATEGORY : CATEGORY 카테고리에 속한 모든 포스트 목록.  
site.tags.TAG : TAG 태그가 붙은 모든 포스트 목록.  
site.url : _config.yml 에 설정한 사이트의 URL. 예를 들어, 환경설정 파일에 url: http://mysite.com 라는 내용이 있으면, Liquid 변수 site.url 로 이 값에 접근할 수 있다. 개발 환경에서는 한 가지 예외가 있는데, 개발 환경에서 jekyll serve 를 실행하면 site.url 은 host 와 port, SSL 관련 옵션으로 설정된다. 기본값은 url:http://localhost:4000 이다.  
site.[CONFIGURATION_DATA] : 명령행이나 _config.yml 을 통해 설정된 모든 변수들은 site 변수를 통해 사용할 수 있다. 예를 들어, 환경설정 파일에 foo: bar 가 있다면, site.foo 와 같이 Liquid 로 접근할 수 있다. watch 모드가 켜진 경우에도 _config.yml 파일의 변경사항은 자동으로 적용되지 않기 때문에, 변경된 변수를 적용하려면 Jekyll 을 재시작해야 한다.  


{{}}출력시 | 뒤의 것은 출력 방식을 뜻한다  
```
{% raw %}
ex) {{ post.date | date_to_string}}  
{{ "/assets/css/style.css" | relative_url }} 로 입력시 관련된url로 변환되어 입력되어짐  
{% endraw %}
```
