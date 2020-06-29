---
layout: post
title: "jquery DeferredResult"
date: 2020-06-29 15:01:12
categories: javascript
tag: javascript
comments:
---
 > ##### 함수의 비동기 실행을 위한 jQuery 객체 Deferred
 
자바스크립트에서 함수 비동기 처리를 사용하기 쉽게 구현된 jQuery 객체

```
var asyncFunc = function(param) {
	//비동기 처리를 위한 Deferred 객체 선언
	var dfd = $.Deferred();
	
	//오래 걸리는 함수 실행
	
	//반드시 dfd의 promise 리턴
	return dfd.promise();
};

//Promise 실행 방법 1
asyncFunc(parameter).done(function(data) {
		// resolve가 실행된 경우(성공), resolve 함수에 전달된 값이 data로 들어온다.
	})
	.fail(function(error) {
		// reject가 실행된 경우(실패), reject 함수에 전달된 값이 error로 들어온다.
	})
	.always(function() {
		//성공하던 실패하던 항상 실행된다.
	});
	

//Promise 실행 방법2

asyncFunc(parameter).then(function(data) {
	// resolve가 실행된 경우(성공), resolve 함수에 전달된 값이 data로 들어온다.
}, function(error) {
	// reject가 실행된 경우(실패), reject 함수에 전달된 값이 error로 들어온다.
}).then(function() {
	//성공하던 실패하던 항상 실행된다.
});


// $.when을 이용하여 여러개 비동기 프로세스 동시에 처리하도록 처리
//asyncFunc1의 resolve 값은 result1로, asyncFunc2의 resolve 파라미터는 result2 로 들어온다.
$.when(asyncFunc1(), asyncFunc2()).done(function(result1, result2) {
  console.log(result1, result2);
});
```


<a href="https://api.jquery.com/category/deferred-object/">jQuery Deferred docs</a>