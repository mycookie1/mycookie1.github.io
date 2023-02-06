---
layout: post
title:  "websocket"
category: Project
tags: [Chatting, spring, websocket]
---
Messeenger만들기 프로젝트 중 메세지를 주고 받는 과정에서 어려움을 겪었다.
상대방과의 대화 내용에 변경이 있는지 계속 서버와 통신해야 할지, 변경이 있다면 특정 클라이언트에게 알림을 보내야하는지 고민하였다.
그러던 중 'websocket'을 발견했다.

## Websocket
HTTP에서 매번 요청을 보내 데이터를 수신하는 것과 다르게 (비연결성)
초기 연결 후 연결된 상태에서 지속적으로 정보를 교환한다.
- 양방향 통신
- HandShake  -> 하나의 TCP 커넥션으로 Full Duplex를 제공
- 클라이언트와 서버 중 하나가 종료되거나 시간초과가 발생할 때 까지 연결을 유지한다
- wss 프로토콜을 통해 암호화

### websocket 이전
클라이언트에서 변경사항을 확인하기 위해 주기적으로 요청
- polling 방식
- 필요하지 않은 상황에서 통신 발생

클라이언트가 길게 접속하도록 허용
- long polling 방식
- event가 발생하면 클라이언트에게 알려줌
- 일정시간이 지나면 다시 요청을 보내 연결
- 'socket.Io'
- 그래도 연결과 해제를 반복하기 때문에 오버헤드 발생

## SSE(Server Sent Event)
WebSocket에 대해 공부하다 보니 자주 나오는 내용이라 정리해본다.
- SSE는 웹소켓과 달리, Client가 Server로부터 데이터만 받을 수 있는 방식입니다.
- SSE는 별도의 프로토콜을 사용하지 않고 HTTP 프로토콜만으로 사용할 수 있기 때문에 구현이 용이합니다.
- 접속에 문제가 있으면 자동으로 재연결 시도하지만, 클라이언트가 close해도 서버에서 감지하기 어렵습니다.

## 결론
polling, long polling, webSocket, SSE 각각의 장단점이 존재한다.
잘 생각하고 사용하자!


