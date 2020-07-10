---
layout: post
title: "git amend 사용방법"
date: 2020-07-10 17:49:33
categories: git
tag: git
comments:
---
 > ##### amend 명령어를 이용하여 커밋 메세지 변경
 >> amend 명령어는 로컬 커밋에서만 사용할 것! remote에 사용시 오류 발생  
  
```
 - 커밋메세지 변경
git commit --amend -m "new commit message"  
 
 - 커밋시 파일 하나 추가
git add filename  
git commit --amend --no-edit  

 - 커밋시 작성자명 변경  
git commit --amend --author "Author Name <Author Email>"
```



<a href="https://medium.com/@Dongmin_Jang/git-%EC%96%B4%EB%96%BB%EA%B2%8C-git-%EC%A0%84%EB%AC%B8%EA%B0%80%EA%B0%80-%EB%90%98%EB%8A%94%EA%B0%80-amend-rebase-3d3d31acbe5a">-- 출처 --</a>