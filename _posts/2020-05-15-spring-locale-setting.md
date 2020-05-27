---
layout: post
title: "스프링 메세지 다국어 설정 방법(CookieLocaleResolver)"
date: 2020-05-15 19:38:28
categories: java spring
tag: java spring
comments:
---
> ##### 스프링 메세지 다국어 설정 방법  (CookieLocaleResolver)

```xml
<bean id="messageSource"
    class="org.springframework.context.support.ReloadableResourceBundleMessageSource">
    <property name="basename" value="classpath:messages" />
    <property name="defaultEncoding" value="UTF-8" />
</bean>

<bean id="localeChangeInterceptor"
    class="org.springframework.web.servlet.i18n.LocaleChangeInterceptor">
    <property name="paramName" value="lang" />
</bean>

<bean id="localeResolver"
    class="org.springframework.web.servlet.i18n.CookieLocaleResolver">
    <property name="defaultLocale" value="ko" />
</bean>

<bean id="handlerMapping"
    class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping">
    <property name="interceptors">
        <ref bean="localeChangeInterceptor" />
    </property>
</bean>
```  
1. 다국어 지원을 위한 MessageSource를 설정  
  - basename으로 지정한 경로에는 파일명_[언어]_[국가].properties 파일으로 지정한다.  
  - 사용자에게 지정돈 locale 값으로 메세지를 읽는다.  
    ex) messages_ko.properties, messages_en.properties  
2. Locale 변경을 위한 인터셉터 정의 (LocaleChangeInterceptor)  
3. 사용할 localeResolver 정의  
4. HandlerMapping 의 Interceptors 프로퍼티에 인터셉터를 설정  

위 설정에 의해 요청 파라메터 "lang" 에 설정된 값으로 로케일이 설정되며, 설정된 locale 정보는 쿠키에 저장된다.  
이후에 lang 파라메터가 없는 요청에 대해서는 요청에 포함된 locale 관련 쿠키정보를 사용하여 로케일이 설정된다.
