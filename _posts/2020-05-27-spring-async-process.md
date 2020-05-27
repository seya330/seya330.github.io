---
layout: post
title: "스프링 비동기 프로세스(Callable, DeferredResult, Http Streaming)"
date: 2020-05-27 23:15:17
categories: java spring
tag: java spring
comments:
---
> ##### Callable  
Callable Interface는 추상 메서드가 하나 있는 FunctionalInterface 이다.  
Callable 을 Controller 에서 리턴하는 경우, 이 프로세스는 보통의 값들을 반환하는 것 대신에  
컨트롤러는 java.util.concurrent.Callable 을 먼저 반환하고, Spring에서 관리하는 별도  
Thread에서 값을 반환한다.  

```java
@RequestMapping("example")
public Callable<String> example() {
  return new Callable<String>() {
      public String call() throws Exception {
        return "example";
      }
  };
}
```  

람다식 형태  
```java
@RequestMapping("example")
public Callable<String> example() {
  return () -> {
    return "example";
  };
}  
```  
- Controller는 Callable 객체를 바로 리턴한다.
- Spring MVC는 내부 TaskExecutor에게 해당 작업을 전달한다.
- DispatherServlet 그리고 모든 필터들은 Servlet Container Thread에서 벗어나지만 response는 여전히 열려있는 상태이다.
- Callable은 결과를 생성하고 Spring MVC는 Servlet container에게 재 요청을 진행한다.
- DispatcherServlet은 Callable에게서 반환된 결과값을 가지고 다시 작업을 진행시킨다.

> ##### DeferredResult  

DeferredResult 도 또한 다른 Thread로 부터 생산된 값을 반환하는 것은 동일하다. 하지만 이 Thread가 Spring MVC에서 관리되는 것은 아니다.  
동작에 대해 예를 들면 JMS message, scheduled task 등과 같은 외부 의 몇몇 이벤트로 부터 생상된 된 response를 반환해야 하는 경우에 사용된다.  
이는 long polling 방식이라고도 하는데, 특정 작업이 진행이 되거나 이벤트가 완료된 후에 요청을 했던 client에게 값을 전달하는 방식이다.  

```java
@RestController
public class AsyncController {
  @Autowired
  AsyncService asyncService;

  @RequestMapping(method=RequestMethod.GET, path="/tests")
  public DeferredResult<List<String>> readTests() {
    final DeferredResult<List<String>> result = new DeferredResult<>();
    asyncService.getTestsEventually(result);

    return result;
  }
}
```  

```java
@Service
public class AsyncService {
  private static Logger logger = LoggerFactory.getLogger(AsyncService.class);
  private static final String TEST_STRING = "test";
  private List<String> testRepository;

  public AsyncService() {
    testRepository = new ArrayList<>();
    for (int i = 0; i < 5; i++) {
      testRepository.add(TEST_STRING + i);
    }
  }

  @Async
  public void getTestsEventually(final DeferredResult<List<String>> deferredResult) {
    if (logger.isDebugEnabled()) {
      logger.debug("return test list");
    }

    deferredResult.setResult(testRepository);
  }
}
```  
 - DeferredResult를 만들어서 return  
 - 비동기 작업을 처리하고나서 직접 DeferredResult 객체에 DeferredResult.setResult()로 결과값을 넘겨주면 Response로 돌려줌  
 
