---
layout: default
title: JDBC, JSP, Servlet, 웹 페이지 이동 방식, Cookie Vs Session
parent: Web
nav_order: 1
---

# JDBC, JSP, Servlet, 웹 페이지 이동 방식, Cookie Vs Session

## 목차
[1. JDBC](#JDBC) <br>
[2. jsp VS Servlet](#jsp-VS-Servlet) <br>
[3.웹 페이지 이동 방식](#웹-페이지-이동-방식) <br>
[4.Cookie VS Session](#Cookie-VS-Session) <br>

---

## JDBC
- Java Database Connectivity
- 자바 프로그램이 데이터베이스와 연결되어 데이터를 주고 받을 수 있게 하는 프로그래밍 인터페이스
- 응용프로그램램과 DBMS 간의 통신을 중간에서 번역하는 역할

## jsp VS Servlet
- 둘 다 java를 베이스 (html과 java를 합쳐  씀)
- 기능의 차이는 없고 역할의 차이만 있음.

### Servlet 
- 웹 기반의 요청에 대한 동적인 처리가 가능한 Server Side에서 돌아가는 Java Program
- **Java 코드** 안에 HTML 코드 (하나의 클래스)
- 웹 개발을 위해 만든 표준
- data processing(Controller)에 좋다.
    - DB와의 통신, Business Logic 호출, 데이터를 읽고 확인하는 작업 등에 유용.
- Servlet이 수정된 경우 Java 코드를 컴파일(.class 파일 생성)한 후 동적인 페이지를 처리.
    - 전체 코드를 업데이트하고 다시 컴파일하고 재배포 작업 필요 **개발 생산성 저하**

### JSP
- Java 언어를 기반으로 하는 Server Side 스크립트 언어
- **HTML 코드** 안에 Java 코드 
- Servlet을 보완하고 기술을 확장한 스크립트 방식 표준
    - Servlet 기능 + 추가적인 기능
- presentation(View)에 좋음.
- 요청 결과를 나타내는 HTML 작성에 유용.
- JSP가 수정된 경우 WAS가 알아서 처리**(쉬운 배포)**

## jsp/Servlet : GET/POST 방식에 따른 구현 방식 이해

---

## 웹 페이지 이동 방식 

### forward 방식<br>
- 링크 똑같음, request, response 유지
    - 최초에 호출한 URL 표시,  이동한 페이지의 URL 정보 확인 불가
- dispatcher 방식에 forward가 포함
-시스템에 변화가 생기지 않는 단순 조회 요청(글 목록 보기, 검색) 

### redirect 방식
- 링크 다름, response 삭제
    - URL을 지시된 주소로 바꾸고 해당 주소로 이동
    - 다른 웹 컨테이너에 있는 주소로 이동, 새로운 페이지에서 Request와 Response객체가 **새로이 생성**
- 시스템에 변화가 생기는 요청(회원가입, 글쓰기 등) 


### 참고 - Spring
- Spring에도 forward/redirect 방식 있음. 

---
## Cookie VS Session

### 쿠키와 세션을 사용하는 이유
 - HTTP 프로토콜의 특징이자 **약점을 보완**하기 위해 사용  
    - **Connectionless 프로토콜 (비연결지향)**<br>
    클라이언트가 서버에 요청(Request)을 했을 때, 그 요청에 맞는 응답(Response)을 보낸 후 연결을 끊는 처리방식<br>
    - **Stateless 프로토콜 (상태정보 유지 안함)**<br>
        클라이언트의 상태 정보를 가지지 않는 서버 처리 방식
        하지만 실제로는 데이터 유지가 필요한 경우가 많다.<br>
       -> **쿠키와 세션을 사용하는 이유**

### Cookie
 - Http의 일종
 - 특정 사이트 방문 시, 사이트의 서버에서 **사용자의 컴퓨터에 저장**하는 작은 기록 정보 파일
 - 필요 시 정보를 참조하거나 재사용
 - 세션보다 빠르다.
 - 저장 형식 : text

### Session
 - 일정 기간동안 같은 사용자(브라우저)로부터 들어오는 일련의 요구를 하나의 상태로 보고, 
 그 상태를 일정하게 유지시키는 기술.
 - 일정 시간은 웹 브라우저를 통해 웹 서버에 접속한 시점으로부터 웹 브라우저를 종료하여 연결을 끝내는 시점 
- **방문자가 웹 서버에 접속해 있는 상태**를 하나의 단위 = 세션 
- 쿠키보다 보안이 좋다.
- 저장 데이터에 제한이 없다.
- 저장 형식 : Object

### 왜 세션과 쿠키를 같이 사용하는가?
: 세션은 서버 저장, 즉 소모 자원이 상당.<br>
자원관리 차원에서 쿠키와 세션을 병행 사용 가능.<br>
서버 자원 낭비 방지, 웹사이트 속도 높임.

---
참고문헌<br>
[https://shs2810.tistory.com/18](https://shs2810.tistory.com/18)<br>
[https://gmlwjd9405.github.io/2018/11/04/servlet-vs-jsp.html](https://gmlwjd9405.github.io/2018/11/04/servlet-vs-jsp.html)<br>
[https://mangkyu.tistory.com/51](https://mangkyu.tistory.com/51)<br>
[https://hahahoho5915.tistory.com/32](https://hahahoho5915.tistory.com/32)