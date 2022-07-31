---
title:  "[Effective Java] 1. 생성자 대신 정적 팩터리 메서드를 고려하라"
excerpt: ""

categories:
  - java
tags:
  - [Java, effective java]

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

# 장점
1. 이름을 가질 수 있다. (반환 객체의 특성을 설명하기 좋음)
2. 호출시, 매번 새로운 인스턴스를 생성할 필요가 없다. (캐싱, 재활용 가능)  
  -> 싱글턴, 플라이웨이트 패턴 등에서 사용  
  -> 불변값 클래스에서 동치인 인스턴스를 하나뿐인것으로 보장 가능(a==b 일때만 a.equals(b) 가 성립)  
  -> 열거 타입에서 인스턴스가 하나만 만들어짐을 보장
3. 반환 타입의 하위타입 객체를 반환할 수 있음

# 단점
1. 상속을 하려면 public 이나 protected 생성자가 필요하다   
  -> 정적 팩토리 메서드 만드로는 하위 클래스를 만들 수 없다.  
2. 프로그래머가 찾기 어렵다. 
  -> 네이밍 규칙을 잘 따라야함.  
  - from : 매개 변수를 하나 받아서 해당 타입 인스턴스를 반환  
    ```Java
    Date d = Date.from(instant);
    ```
  - of : 여러 매개변수를 받아서 인스턴스를 반환
    ```Java
    Set<Rank> faceCards = EnumSet.of(jack, queen, king);
    ```
  - valueOf : from 과 of의 더 자세한 버전
    ```Java
    BigInteger prime = BigInteger.valueOf(Integer.MAX_VALUE);
    ```
  - instance 또는 getInstance : 같은 인스턴스임을 보장하지 않음. 
    ```Java
    StackWalker = luke = StackWalker.getInstance(options);
    ```
  - create 또는 newInstance : 매번 새로운 인스턴스를 생성해 반환
    ```Java
    Object newArray = Array.newInstance(classObject, arrayLen);
    ```
  - getType : getInstance와 같으나, 생성할 클래스가 아닌 클래스의 팩토리 메서드를 정의할 때 씀.  
              "Type"은 팩토리 메서드가 만환할 객체의 타입.
    ```Java
    FileStore fs = Files.getFileStore(path);
    ```
  - newType : newInstance와 같으나, 생성할 클래스가 아닌 다른 클래스의 팩토리 메서드를 정의할 때 씀.
    ```Java
    BufferedReader br = Files.newBufferedReader(path);
    ```
  - type : getType과 newType 의 간결한 버전
    ```Java
    List<Complaint> litany = Collections.list(legacyLitany);
    ```


    