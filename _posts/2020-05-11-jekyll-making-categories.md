---
layout: post
title: "jekyll 카테고리 만들기"
categories: jekyll
date: 2020-05-11 22:46:13
tags: jekyll
comments:
---
{% raw %}
#### 1. 카테고리 클릭시 리스트 표출 페이지 만들기  
 - 카테고리 페이지가 공통으로 사용할 리스트 표출 페이지를 만든다.(리스트 양식은 직접 작성)  
 - 해당 파일을 _layouts/category.html 로 만든다.(2번에서 layout을 category 로 지정 할 것이기 때문.)  

#### 2. 카테고리 페이지 만들기  
 - /category/지정할 카테고리명.md  
 - md 파일의 헤더에 layout: category,  
 - title: 지정할 카테고리 명 으로 지정.  

#### 3. 카테고리 목록 만들기  
카테고리를 조회 할 수 있는 navigator 를 만든다.  
```
<ul>  
    {% assign pages_list = site.pages %} -- 전역 페이지들을 가지고 온다.  
    {% for node in pages_list %} -- 가져온 리스트들 for loop  
      {% if node.title != null %}  
        {% if node.layout == "category" %} -- 리스트의 각 페이지중 layout 이 category 로 지정되어 있는 목록만 가져온다.(1번에서 만든 카테고리 페이지들)  
          <li><a class="category-link {% if page.url == node.url %} active{% endif %}" -- 카테고리 링크 생성  
          href="{{ site.baseurl }}{{ node.url }}">{{ node.title }}</a></li> -- 1번에서 title 로 지정한 텍스트가 navigator 에 보여진다.  
        {% endif %}  
      {% endif %}  
    {% endfor %}  
</ul>  
```
{% endraw %}
