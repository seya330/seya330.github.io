---
layout: post
title: "자바 ConcurrentModificationException"
date: 2020-06-26 17:24:33
categories: java
tag: java
comments:
---
##### java ConcurrentModificationException  
동일 List객체를 멀티스레드 환경에서 add 혹은 remove 시 발생 하거나  
List객체를 for 문을 돌리며 추가 혹은 제거시에도 발생.  

```
ex)
for(HashMap elem : list) {
		list.remove(elem);
    // break; 로 추후 진행하지 않을 시엔 발생하지 않는다.
}
```  
##### CopyOnWriteArrayList  
위와 같은 상황에서 오류가 발생하지 않는 List 구현체  
 - CopyOnWriteArrayList의 컨텐츠를 읽기 위해 어딘가에 전달할때  
 CopyOnWriteArrayList는 컨텐츠를 복사해서 전달한다.
 - read/write관련 성능상 이슈 및 멀티 스레드환경에서 의도치 않는 기능으로 작동할 수 있으니  
 개발할때 구조 자체를 신경써서 짜야 할 것 같다.
