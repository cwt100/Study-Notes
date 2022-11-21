# Learn Spring in one month - 筆記
Update：2022/11/18<br/>

* [CH0：初探](#ch0初探) [DONE]
* [CH1：Annotation Modulize Introduction](#ch1annotation-modulize-introduction) [DONE]

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


---
