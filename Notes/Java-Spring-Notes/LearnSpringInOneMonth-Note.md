# Learn Spring in one month - 筆記
Update：2022/11/23<br/>

* [CH0：初探](#ch0初探)
* [CH1：Annotation Modulize Introduction](#ch1annotation-modulize-introduction)
* [CH2：Spring Framework Inttroduction](#ch2spring-framework-inttroduction)

---

## CH0：初探

### Spring Framework
是一個基於Java(J2EE)的MVC架構(輕量級的開源框架)

<br>

### Reference
- https://ithelp.ithome.com.tw/articles/10259715
- https://sites.google.com/im.fju.edu.tw/web/spring-framework-web

<br>

---

## CH1：Annotation Modulize Introduction

### Spring 框架，三大核心

- IoC 控制反轉 (Inversion of Control)

    > 一種設計原則或概念

    ex. 將 new 的控制權交給Spring處理

- DI 依賴注入 (Dependency Inject)

    > 實現IoC概念的作法

    ex. 在Repository中不直接 new 物件使用，採用 @Autowired，讓Spring自動注入與管理

- AOP 面向導向程式設計 (Aspect-oriented programming)

    > 在程式的前(before) or 後(after) or 前後(around)，執行其他程式
    
    PS. 僅在指定的地方，額外執行其他程式，而不是以侵入式的方式將程式碼加在原本程式中

<br>

### Reference
#### Main
- https://ithelp.ithome.com.tw/articles/10265721 (DONE)
#### IoC / DI
- https://ithelp.ithome.com.tw/articles/10222289 (DONE)
#### AOP
- https://medium.com/appxtech/spring-aop%E7%99%BD%E8%A9%B1%E6%96%87-%E6%B7%BA%E8%AB%87spring-aop%E7%9A%84%E5%AD%B8%E7%BF%92%E5%88%86%E4%BA%AB-1985489d008 (DONE)

<br>

---

## CH2：Spring Framework Inttroduction

### Structure

> 核心容器 (Core Container)

- Spring-core

    包括控制反轉(IoC)與依賴注入(DI)

    > Spring IoC
    
    基於BeanFactory和ApplicationContext

    > Spring DI
    
    使用Spring框架創建對象時動態將其所依賴的對象注入到Bean中

- Spring-beans

    提供BeanFactory，代管對象皆為Bean

- Spring-context

    訪問定義和配置的媒介

- Spring-context-support

    可支援整合第三方套件到Spring的應用程序上

- Spring-expression

> AOP和Instrumentation

- Spring-aop

    提供符合 AOP 的編譯實例

- Spring-aspects

- Spring-instrument

> 消息

    提供對消息傳遞體系和協議的支持

> 數據訪問和整合

- Spring-jdbc

    提供 JDBC 串接底層的抽象層 (不建議直接使用)

- Spring-orm

    物件關聯對映(Object-Relational Mapping) API 提供整合層，包括 JPA、Hibernate、Mybatis

- Spring-oxm

    支援Java object 和 XML 來回轉換，如：JAXB、Caster、JiBX和Xstream

- Spring-jms

    Java消息傳遞服務(Java Message Service)
    
    > 生產者/消費者 (Producer/Consumer)

    > 推廣/訂閱 (Publish/Subscribe)

- Spring-tx

    用於實現特殊接口

> Web

- Spring-web

    基本的web開發整合功能，如：多文件上傳功能

- Spring-webmvc

    Web-Servlet，包括Web應用程序的SpringMVC和REST Web Service實現

- Spring-websocket

    提供WebSocket和SockJS整合

- Portlet

    提供Portlet環境下的MVC實現


> 測試

    支持使用JUnit或Mockito對Spring套件進行單元測試或整合測試

<br>

## Reference

### Main
- https://ithelp.ithome.com.tw/articles/10266484

### Other
- https://medium.com/learning-from-jhipster/13-%E7%94%9A%E9%BA%BC%E6%98%AF-jdbc-orm-jpa-orm%E6%A1%86%E6%9E%B6-hibernate-c762a8c5e112
- https://www.twblogs.net/a/5e522c7dbd9eee211680f079

<br>

---