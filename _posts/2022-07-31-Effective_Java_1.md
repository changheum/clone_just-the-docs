---
title:  "[Effective Java] 1. 생성자 대신 정적 팩터리 메서드를 고려하라"
excerpt: ""

categories:
  - java, effective java
tags:
  - [Java]

toc: true
toc_sticky: true
 
date: 2022-07-31
last_modified_at: 2022-07-31
---

# 생성자 대신 정적 팩터리 메서드를 고려하라
정적 팩토리 메서드(static factory method) : 클래스의 인스턴스를 반환    
```java
// (ex) boolean 기본타입의 박싱 클래스(boxed class) 의 일부
public static Boolean valueOf(boolean b) {
  return b ? Boolean.TRUE : Boolean.FALSE;   
}
```

