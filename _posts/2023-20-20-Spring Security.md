---
layout: post
title:  "Spring Securtiy"
category: Spring
tags: [security]
---
## Spring Security란?
Spring Security는 Spring기반 애플리케이션의 보안을 담당하는 스프링 하위 프레임워크이다.
Spring Security는 '인증(Authentication)'과 '권한(Authorization)'에 대한 부분을 Filter의 흐름에 따라 처리를 하고 있다.
많은 보안 관련 옵션들을 제공해주어 개발자가 보안 로직을 하나씩 작성하지 않아도 되는 장점이 있다.

## 인증(Authentication)과 권한(Authorization)

### 인증(Authentication)
사이트에 접속하려는 자가 누구인지 확인하는 절차이다. (사용자가 본인인지 확인)
UsernamePassword를 통한 인증을 할 수 있다. (Session관리, Token관리)
SNS로그인을 통한 인증 위임을 할 수도 있다.
### 인가, 권한(Authorization)
사용자가 어떤 일을 할 수 있는지 권한 설정하는 절차이다.
특정 페이지/리소스에 접근할 수 있는지 권한을 판단한다.
Secured, PrePostAuthorize 어노테이션으로 쉽게 권한 체크를 할 수 있다.
비즈니스 로직이 복잡한 경우 AOP를 이용해 권한 체크를 해야한다.
인증(Authentication)절차를 거친 후에 권한(Authorization)절차를 진행하게 된다.
Spring Security에서는 이러한 인증과 인가를 위해 Principal을 아이디로, Credential을 비밀번호로 사용하는 Credential 기반의 인증 방식을 사용한다.

Principal(접근 주체): 보호받는 Resource에 접근하는 대상
Credential(비밀번호): Resource에 접근하는 대상의 비밀번호