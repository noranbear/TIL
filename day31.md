# Day31

- 2022-05-25
- **Kakaomap**으로 웹에서 지도 사용하기
- data (미완)

<br>

# 개요

- Web에 Map 추가
  - 마커에 마우스 이벤트 등록 - aj09.html
  - 여러 개의 마커에 이벤트 등록하기 + 응용 - aj10.html , aj11.html (미완)



- Data 가져와서 웹으로 보여주기 - aj12, 13(미완)

<br>

---

# WEB에 MAP 추가

- [Kakaomap API 사이트](https://apis.map.kakao.com/)
- Kakaomap API를 이용하여 웹사이트에 맵을 추가하고 기본적으로 제공되는 Sample 기능들을 사용해보자.

<br>

## 카카오에서 제공하는 다양한 맵 기능 이용하기

- 오버레이
  - 마커에 마우스 이벤트 등록 ([aj09.html](./day05/src/main/resources/templates/ajax/aj09.html)) 

<br>

### 0) 사용하기 전

#### Kakaomap 링크 걸기

- Kakaomap API를 사용하기 위해 우선 아래의 코드를 소스파일에 붙여 넣는다.
- ''*발급받은 APP KEY를 사용하세요''* 부분에 발급받은 APP KEY를 써넣는다.

```html
<script src="//dapi.kakao.com/v2/maps/sdk.js?appkey=발급받은 APP KEY를 사용하세요"></script>
```

- 사용하는 기능에 따라서 뒤에 ```&libraries=services``` 가 들어간다.

```html
<script src="//dapi.kakao.com/v2/maps/sdk.js?appkey=발급받은 APP KEY를 사용하세요&libraries=services"></script>
```

> aj09.html은 main.html의 center부분으로 들어가는 것이기 때문에 위의 링크를 aj09.html이 아닌 main.html에다가 추가했다.

<br>

### 1) 마커에 마우스 이벤트 등록

>  Kakaomap API 홈페이지 > Web >  sample > 오버레이 > 마커에 마우스 이벤트 등록 > JavaScript + HTML

- map이라는 영역 안에 지도를 생성한 후, 해당 위치에 마커를 생성한다.

- 마커에 마우스 오버: 인포윈도우를 보여준다.

- 마커에서 마우스 아웃: 인포윈도우를 없앤다.

- 마커 클릭: 페이지를 이동한다.

- 전체코드:

  ```javascript
  <style>
  /*div엔 언제나 width, height 필요*/
  #map{
  	width: 500px;
  	height: 400px;
  	border: 2px solid red;
  }
  </style>
  <script>
  // 화면이 로드되었을 때
  $(document).ready(function(){
  	// 1. 지도 생성 -----
  	var mapContainer = document.getElementById('map'); // 지도를 표시할 div 
      var mapOption = { 
          center: new kakao.maps.LatLng(33.450701, 126.570667), // 지도의 중심좌표
          level: 3 // 지도의 확대 레벨
      };
  
  	var map = new kakao.maps.Map(mapContainer, mapOption); // 지도를 생성합니다
  
  	
  	// 2. 마커 생성 -----
  	// 마커를 표시할 위치입니다 
  	var position =  new kakao.maps.LatLng(33.450701, 126.570667);
  
  	// 마커를 생성합니다
  	var marker = new kakao.maps.Marker({
  		position: position
  	});
  
  	// 마커를 지도에 표시합니다.
  	marker.setMap(map);
  	
  	
  	// 3. 인포윈도우 생성 -----
  	// 마커에 커서가 오버됐을 때 마커 위에 표시할 인포윈도우를 생성합니다
  	var iwContent = '<div style="padding:5px;">Hello World!</div><h3><a href="">Go</a></h3><img width="50px" src="img/background.png">'; 
  	// 인포윈도우에 표출될 내용으로 HTML 문자열이나 document element가 가능합니다
  
  	// 인포윈도우를 생성합니다
  	var infowindow = new kakao.maps.InfoWindow({
  	    content : iwContent
  	});
  	
  	
  	// 4. 인포 윈도우 넣기 -----
  	// 마커에 마우스오버 이벤트를 등록합니다
  	kakao.maps.event.addListener(marker, 'mouseover', function() {
  	  	// 마커에 마우스오버 이벤트가 발생하면 인포윈도우를 마커위에 표시합니다
  	    infowindow.open(map, marker);
  	});
  
  	// 마커에 마우스아웃 이벤트를 등록합니다
  	kakao.maps.event.addListener(marker, 'mouseout', function() {
  	    // 마커에 마우스아웃 이벤트가 발생하면 인포윈도우를 제거합니다
  	    infowindow.close();
  	});
  	
  	// +. 클릭 이벤트 더하기
  	// 마커에 클릭 이벤트를 등록합니다
  	kakao.maps.event.addListener(marker, 'click', function() {
  		// 마커에 클릭 이벤트가 발생하면 페이지를 이동합니다
  		location.href="aj06";
  	});
  
  });
  </script>
  
  
  <h1>AJ09 Main</h1>
  
  // 지도가 생성될 영역
  <div id="map"></div>
  
  ```

<br>

#### Sample 코드 복붙하기

- 화면이 로드될 때 지도를 생성할 것이다.
	```javascript
  $(document).ready(function(){
      // Sample 코드 복붙해서 넣을 곳
  });

- 1. **지도** 생성

  ```javascript
  var mapContainer = document.getElementById('map'); // 지도를 표시할 div 
  var mapOption = { 
      center: new kakao.maps.LatLng(33.450701, 126.570667), // 지도의 중심좌표
      level: 3 // 지도의 확대 레벨
  };
  
  var map = new kakao.maps.Map(mapContainer, mapOption); // 지도를 생성합니다
  ```

- 2. 지도 위에 **마커** 생성

    ```javascript
    // 마커를 표시할 위치입니다 
    var position =  new kakao.maps.LatLng(33.450701, 126.570667);
    
    // 마커를 생성합니다
    var marker = new kakao.maps.Marker({
        position: position
    });
    
    // 마커를 지도에 표시합니다.
    marker.setMap(map);
    ```
  
- 3. **인포윈도우** 생성
     - ```iwContent = <div>Hello World!</div>```에 원하는대로 링크, 이미지, 스타일을 html문의 형태로 더할 수 있다.
  ```javascript
  // 마커에 커서가 오버됐을 때 마커 위에 표시할 인포윈도우를 생성합니다
  var iwContent = '<div style="padding:5px;">Hello World!</div><h3><a href="">Go</a></h3><img width="50px" src="img/background.png">'; 
  // 인포윈도우에 표출될 내용으로 HTML 문자열이나 document element가 가능합니다
  
  // 인포윈도우를 생성합니다
  var infowindow = new kakao.maps.InfoWindow({
      content : iwContent
  });
  
- 4. 마커에 **인포윈도우** 붙이기
  
     > 마우스오버나 마우스아웃과 같이 마우스를 사용하는 이벤트들은 모바일에선 적용하지 못한다는 것을 고려하자.
  ```javascript
  // 마커에 마우스오버 이벤트를 등록합니다
  kakao.maps.event.addListener(marker, 'mouseover', function() {
      // 마커에 마우스오버 이벤트가 발생하면 인포윈도우를 마커위에 표시합니다
      infowindow.open(map, marker);
  });
  
  // 마커에 마우스아웃 이벤트를 등록합니다
  kakao.maps.event.addListener(marker, 'mouseout', function() {
      // 마커에 마우스아웃 이벤트가 발생하면 인포윈도우를 제거합니다
      infowindow.close();
  });
  ```
  
- 5. 마커에 **클릭 이벤트** 붙이기
  ```javascript
  // 마커에 클릭 이벤트를 등록합니다
  kakao.maps.event.addListener(marker, 'click', function() {
      // 마커에 클릭 이벤트가 발생하면 페이지를 이동합니다
      location.href="aj06";
  });
  ```





 - 여러개의 마커에 이벤트 등록하기 1 -aj10 - 응용
   - 맵 중앙 이동
      - map을 diplaymap에 생성하고 gomap에서 썼을 때 에러가 당연히 난다.- 없는 애 썼기 때문

- 라이브러리
