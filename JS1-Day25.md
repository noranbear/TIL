# 05/16_JS Day01

> 2022-05-16 Day25
>
> 교재: HTML5 웹클라이언트.pdf

<br>

## 개요

Section 1. HTML5 - P3

Section 2. CSS - P41

Section 3. JavaScipt

[A](noranbear/Java/README.md/#날짜)

<br>

---

## 1) HTML5

### 	HTML5의 신규 기능

- ***WEB Storage** (or Local Storage)

  - 브라우저에 데이터베이스가 있다.
    - 화면에 있는 내용을 브라우저에 저장을 해서 가져올 수 있다.

- **Drag and Drop**

  - 웹 페이지에서 원하는 항목을 드래그 할 수 있게 해주는 API

- **Geolocation**

  - 웹에서 지도가 나온다.

  - 웹 부라우저가 현재 나의 위치를 알 수 있다.

    - 접속하고 있는 네트워크의 게이트웨이 위치를 알고 있는 것.

      -  ex) 현재 위워크 건물 와이파이를 쓰고 있으므로 위워크 건물에 있다고  판단.
    - GPS - 사용자 기기 사용
  
- **Canvas 2D**
  - 고퀄의 그래픽 게임을 이제 인스톨 없이 브라우저로도 할 수 있다.
  - 하지만, 아직 너무 무거운 게임은 불가하다.
- **Web Workers**
- **Indexed DB**
- **Web SQL Database**
- ***Server Sent Events (SSE)**
  - 새로고침 안해도 웹 브라우저 화면에 데이터가 자동 업데이트된다.
- ***Web Socket**
	- 	순수 웹 환경에서 실시간 양방향 통신을 위한 기능을 제공한다.
	- 	웹 서버와 웹 브라우저가 지속적으로 연결된 TCP라인을 통해 실시간으로 데이터를 주고 받을 수 있다.


- <u>HTML5 세가지 구성</u>

<br>

## 2) CSS3.0
  CSS - CSS 3.0 - P 75

  - N Screen
  - 반응형 웹

- JS - P82

  - 스크립트 언어 - 자바랑 다름
  - 브라우저에서만 동작

- What is JavaScript

  - ECMAScript
  - 2005년 AJAX
  - 향후 jQuery로 진화 2006년- 네이버는 안 씀

- 필요성

  - CSS 변경
  - 이벤트 처리
  - 웹 페이지의 모든 프로그램 부분

- 구조  및 Sytax

  - 위치 선언

    - <head></head> 사이

    - 문서안 - js01.html

    - External JavaScript

  - 자바 스크립트 실행 흐름

    - 위부터 아래로
    - alert가 일어나면 확인 누를 때까지 멈춰있음.

  - **window.onload - js01.html

  - 웹사이트 devTool에서 에러메시지와 라인을 확인 가능.

  - 특정 영역에 스트링 값 출력 - js01.html

  - 콘솔 log 출력 - js01.html

    - **console.log
    - devtools > console에 출력됨.
    - 연산값을 콘솔에다 찍어가며 확인하고 화면에 최종값만 찍을 수 있음

- Identifiers - p95

  - java와 같음

- data type 7개 - js02

  - Undefined
  - 숫자 (number)
  - 문자 (String)
  - Boolean
  - 배열 (array)
  - 객체 (obj)
    - JSON
  - 함수

  > html, css, js가 다 모여 웹 클라이언트가 구현된다.

- 함수

  - typeof: 변수의 타입을 가져온다.
  - Number(): number 타입으로 바꿈
  - parseInt(): 정수형으로 변경
  - parseFloat(): 실수형으로 변경
  - ==> 숫자가 아닐 경우 NaN 리턴 (not a number)

  > 화면에서 입력한 모든 값은 String 이다.

  - Number 함수
    - toString(): number를 String으로 변경
    - toFixed(): 특정 수까지 반올림하여 문자화
    - toPrecision(): 특정 수에서 반올림하여 문자화
  - Math class - js03.html
    - js도 자바처럼 기본적으로 주는 게 있다.
  - *Stirng functions - p 101 - js03.html

  > JS는 코드가 길어서 jQuery가 나옴
  >
  > js는 컴파일 언어가 아니어서 실행 후 에러 확인 가능 - devTool > console에서

  - array function
    - array.Length - js04.html
  - 함수 - js05.html
    - javaScript 리턴 타입 존재x
    - 항상 함수는 위에서 선언하고 밑에서 사용하자.
    - 자바와 다르게 argument 타입도 존재x
      - 모든 변수의 타입이 var이기 때문에 (var 생략됨 - 근데 var 쓰면 에러남 ㅋㅋㅋ)
    - ***함수의  스페셜 경우 -js05.html
      1. 함수 리턴
      2. 함수 argument
  - 계산기 - js06.html



- WS
  - js07.thml
  - 계산기 구현
    - 바로바로 계산되고 최종 결과값 나오기
    - 버튼