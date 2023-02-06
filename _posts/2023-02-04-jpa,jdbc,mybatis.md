---
layout: post
title:  "JPA, JDBC, MyBatis"
category: Project
tags: [Chatting, paging, project]
---
jdbc와 jpa를 사용해본 경험이 있지만 정말 사용해본 경험'만' 있기에 정리를 해보려고 한다.

## 영속성
우리는 현재의 데이터를 미래에도 사용할 수 있도록 저장해야한다.
램에 휘발성으로 저장되는 데이터가 아니라, 프로그램에 꺼졌다 켜져도 남아 있는 데이터가 필요하다.
이러한 특성을 영속성이라 한다.

### persistence layer
- 프로그램 아키텍쳐에서 데이터에 영속성을 부여해주는 계층

### Persistence Frame Work
- jdJDBC 프로그래밍의 복잡함이나 번거로움 없이 간단한 작업만으로 데이터베이스와 연동되는 시스템을 빠르게 개발할 수 있으며 안정적인 구동을 보장한다.
- SQL Mapper 와 ORM 으로 나누어져있다.

## SQL Mapper vs ORM
---------------------------
### SQL Mapper
- sql <- 맵핑 -> Object 필드
- sql문장으로 직접 데이터를 다룬다. -> sql문을 명시해야 함
- ex) jdbc template, MyBatis

### ORM
- 데이터베이스 데이터 <- 맵핑 -> Object 필드
- 객체와 관계형 데이터베이스의 데이터를 자동으로 맵핑
- SQL Query가 아니라 직관적인 코드로 데이터 조작, 객체간의 관계를 바탕으로 SQL문 자동생성

## jdbc
- JDBC는 DB에 접근할 수 있도록 Java에서 제공하는 API이다.
    - 모든 Java의 Data Access 기술의 근간
    - 즉, 모든 Persistence Framework는 내부적으로 JDBC API를 이용한다.
- JDBC는 데이터베이스에서 자료를 쿼리하거나 업데이트하는 방법을 제공한다.

## JPA
- 자바 ORM 기술에 대한 API 표준 명세로, Java에서 제공하는 API이다.
- 자바 플랫폼 SE와 자바 플랫폼 EE를 사용하는 응용프로그램에서 관계형 데이터베이스의 관리를      표현하는 자바 API이다.
- 즉, JPA는 ORM을 사용하기 위한 표준 인터페이스를 모아둔 것이다.

기존에 EJB에서 제공되던 엔터티 빈(Entity Bean)을 대체하는 기술이다.
JPA 구성 요소 (세 가지)
- 1) javax.persistance 패키지로 정의된 API 그 자체
- 2) JPQL(Java Persistence Query Language)
- 3) 객체/관계 메타데이터
사용자가 원하는 JPA 구현체를 선택해서 사용할 수 있다.
- JPA의 대표적인 구현체로는 Hibernate, EclipseLink, DataNucleus, OpenJPA, TopLink Essentials 등이 있다.
이 구현체들을 ORM Framework라고 부른다.

-----------------------------
## jdbc template
- SQL Mapper
- JDBCTemplates는 내부에서 지원해주는 메서드를 통해서 데이터를 처리하기 때문에 좀 더 쉽고 간결하게 코드를 작성 할 수 있다.

## mybatis
- SQL Mapper
장점
- SQL에 대한 모든 컨트롤을 하고자 할때 매우 적합하다.
- SQL쿼리들이 매우 잘 최적화되어 있을 때에 유용하다.
단점
- 애플리케이션과 데이터베이스 간의 설계에 대한 모든 조작을 하고자 할 때는 적합하지 않다.
- 애플리케이션과 데이터베이스 간에 서로 잘 구조화되도록 많은 설정이 바뀌어야 하기 때문이다.

## Hibernate
- ORM
장점
- 객체지향적으로 데이터를 관리할 수 있기 때문에 비즈니스 로직에 집중 할 수 있으며, 객체지향 개발이 가능하다.
- 테이블 생성, 변경, 관리가 쉽다. (JPA를 잘 이해하고 있는 경우)
- 로직을 쿼리에 집중하기 보다는 객체자체에 집중 할 수 있다.
- 빠른 개발이 가능하다.
단점
- 어렵다. (많은 내용이 감싸져 있기 때문에 알아야 할 것이 많다.)
- 잘 이해하고 사용하지 않으면 데이터 손실이 있을 수 있다. (persistence context)
- 성능상 문제가 있을 수 있다. (이 문제 또한 잘 이해해야 해결이 가능하다.)