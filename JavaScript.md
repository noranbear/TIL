# JavaScript

> 2022-05-16 Day25 - JS_Day01
>
> 2022-05-17 Day26 - JS_Day02
>
> - 교재: HTML5 웹클라이언트.pdf

<br>

## 개요

JavaScript









---

## 1) JavaScript란

> 1996년 2월 Netscape 사가 자바언어를 기반으로 웹 브라우저에서 실행하는 스크립트 언어, JavaScript를 발표하였다.

- **스크립트 언어**이다 (자바와 다름).
  - 위에서 아래로 차례대로 실행된다.

- 브라우저에서만 동작한다.
- ECMAScript로 표준화되었다.
  - ECMA (Europe Computer Manufacture Association)
- 웹페이지(and HTML5)의 프로그램 부분을 담당한다.

<br>

- **JavaScript의 발전**
  - 2005년 AJAX 발표
  - 2006년 jQuery 발표

<br>

- **JavaScript의 필요성**

  - CSS를 자유롭게 변경 가능하다.

  - 이벤트 처리 및 행위 제어가 가능하다.
    - 입력된 데이터의 검정 작업이 가능해진다.

<br>

<br>

## 2) 구조 및 Syntax

### JavaScript 위치

- HTML 내부에 위치해 선언될 수 있는 **3가지 방법**이 있다.

  1. ```<head></head>``` 사이

     ```html
     <!DOCTYPE html>
     <html>
     <head>
     <script>
     // 버튼이 눌렸을 때, body에 있는 'Header'를 'replace text'로 바꾸는 함수.
     function h2(){
     	alert('Alert...........');
     	var h2 = document.querySelector('#hh2');
     	h2.innerHTML = 'replace text';
     };
     </script>
     </head>
     <body>
         <button onclick="h2();">Click</button>
         <h2 id="hh2">Header</h2>
     </body>
     ```
     
     <br>
     
   2. ```<body> ``` 안

      - ```<body></body>``` 태그 안에 존재할 때.
      - ```<body></body>``` 태그가 없지만 ```<body></body> ``` 안에 존재 할 때.
      
      ```html
      <script>
      // 버튼이 눌렸을 때, body에 있는 'Header'를 'replace text'로 바꾸는 함수.
      function h2(){
      	alert('Alert...........');
      	var h2 = document.querySelector('#hh2');
      	h2.innerHTML = 'replace text';
      };
      </script>
      
      <button onclick="h2();">Click</button>
      <h2 id="hh2">Header</h2>
      ```
      
  
  <br>
  
  3. 외부 파일
  
     -  JavaScript 파일
  
       ```html
       <script>
       // 버튼이 눌렸을 때, body에 있는 'Header'를 'replace text'로 바꾸는 함수.
       function h2(){
       	alert('Alert...........');
       	var h2 = document.querySelector('#hh2');
       	h2.innerHTML = 'replace text';
       };
       </script>
       ```
  
     - html 파일에서 외부 JS 파일 사용
  
       ```html
       <!DOCTYPE html>
       <html>
       <head>
       // js 파일 불러오기
       <script src="myScript.js"></script>
       </head>
       <body>
           <button onclick="h2();">Click</button>
           <h2 id="hh2">Header</h2>
       </body>
       </html>
       ```

<br>

### 중요 예제

> WEB > day05 > [js01.html]

1. ```window.onload``` 함수

   - 화면 출력 후 동작

2. 특정 영역에 String 값 출력

3.  웹 브라우저 콘솔에 log 출력: ```console.log```

   - DevTools > Console에서 확인 가능하다.
   - 연산값을 콘솔에다 찍어가며 확인하고 화면에 최종값만 보여주는 등으로 활용이 가능하다.

   ```html
   <script>
   // 1. 화면 출력 후 동작하는 함수
   window.onload = function(){
   	var i = 10;
   	var j = 20;
   	var result = i * j;
       // 3. 웹 브라우저 콘솔에 log를 출력한다.
   	console.log("i+j = " + result);
       
       // 2.1 h3라는 변수에 id가 'hh3'인 html문을 넣는다.
       var h3 = document.querySelector('#hh3');
       // 2.2 해당 html문의 태그 안의 부분에 result 변수 값을 넣어 출력한다.
       h3.innerHTML = result;
   };
   </script>
   
   <h2 id="hh3">Header3</h2>
   ```

   <br>

   <br>

## 3) Data Type과 Function

### Identifiers

- Java와 같음.

<br>

### Data Type

> WEB > day05 > [js02.html]

- JavaScript에서는 모든 변수선언을 var로 한다.

  ```html
  var i = 30;
  ```

- **Data Type의 종류 7개**

  1. **undefined**
     - 어떠한 데이터 타입도 선언되지 않은 상태.

      ```javascript
      var v;
      - type: undefined
      - value: undefined
      ```

  2. **number** (숫자)

		- 실수, 정수 모두 포함.
  
      ```javascript
      var num = 10.3;
      - type: number
      - value: 10.3
      ```

  3. **boolean**

        - true, false 의미.

        ```javascript
        var b = true;
        - type: boolean
        - value: true
        ```

  4. **string** (문자열)

        - 문자열, char 모두 표현.
        - " ", ' ' 모두 사용 가능.

        ```javascript
        var str = 'abc';
        - type: string
        - value: abc
        ```

  5. **array** (배열)

        - 데이터 타입은 object로 표현.
        - 다양한 타입 포함 가능.

        ```javascript
        var a = [1,2,3,4,5];
        - type: object
        - value: 1,2,3,4,5
        ```

  6. **object** (객체)

        - JSON

        ```javascript
        var obj = {id:'id01', name:'lee', age:10};	// 이런 게 JSON
        - type: object
        - value: [object Object]
        ```

  7. **function** (함수)

        - JS에서는 함수를 하나의 타입으로 선언하여 사용 가능.
        
        ```javascript
        var f = function(){		// 변수에다 함수 선언 가능
        return 333;
        };
        - type: function
        - value: 333
        ```
        
          

JavaScript 위치

- 자바 스크립트 실행 흐름

  - 위부터 아래로
  - alert가 일어나면 확인 누를 때까지 멈춰있음.

- 웹사이트 devTool에서 에러메시지와 라인을 확인 가능.

- Identifiers - p95

  - java와 같음

- - 

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