---
layout: post
title: "jekyll 에서 사용하는 Liquid 언어"
date: 2020-05-12 20:46:13
category: jekyll
tag: jekyll
comments:
---
<style>
table:nth-of-type(1) {
    display:table;
    width:50%;
}</style>
{% raw %}
> ##### Liquid 변수형  

 - String  
 - Number  
 - Boolean  
 - Nil (null을 Liquid 에선 Nil 이라고 하는듯??)  
 - Array  

> ##### 변수 선언 방법  

{% assign 변수명 = "Hello World" %} -- String 형  
{% assign 변수명 = 1 %} -- Number형  
{% assign 변수명 = false %} -- Boolean형  
Nil 형은 변수 선언이 되어 있지 않는 값을 조회할때(null)  
Array형은 직접 선언할 수는 없지만 아래와 같이 간접적으로 선언은 가능하다.  
{% assign myArrStr = "apple,banana,orange" | split: "," %}  

> ##### 변수 출력방법  

{% assign tempText = "Hello!" %}  
{{tempText}}  
출력
```

Hello!
```
줄바꿈 처리 없이 출력  
{%- assign tempText = "Hello!" -%}  
{{tempText}}  
```
Hello!
```  


> ##### Liquid 조건문에 변수형 true/false 반환  

{%  endraw %}


| 값          | 조건 true/false |
|---------|-----------------|
| true        | truthy          |
| false       | falsy           |
| nil         | falsy           |
| string      | truthy          |
| 0           | truthy          |
| integer     | truthy          |
| float       | truthy          |
| array       | truthy          |
| empty array | truthy          |
| page        | truthy          |
| EmptyDrop   | truthy          |

> table 만들기 주소 : <https://www.tablesgenerator.com/markdown_tables>
