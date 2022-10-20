# readyforcs


## var, let, const 차이점
*var는 function-scoped이고, let, const는 block-scope임

```js
// 이미 만들어진 변수이름으로 재선언했는데 아무런 문제가 발생하지 않는다.
var a = 'test'
var a = 'test2'

// hoisting으로 인해 ReferenceError에러가 안난다.
c = 'test'
var c
```  

호이스팅으로 인해 javascript parser가 var c를 상위로 끌어올려서 c에 'test'가 할당된 것으로 올바르게 나타낸다.  

```let```과 ```const```를 사용할 경우 위의 문제를 해결하여 코드의 직관성을 높일 수 있다.  
```let```은 변수에 재할당이 가능하고,  
```const```는 변수 재선언, 재할당이 불가능하다.


## 브라우저에 URl을 입력했을 때 발생하는 일
1) 브라우저의 URL 파싱
![image](https://user-images.githubusercontent.com/41901043/196886535-837416b1-6711-4cf6-aff8-155942eb36b0.png)  
URL을 입력받은 브라우저는 URL의 구조(protocol, url, port)를 해석한다.  

2) HSTS 목록 조회
http strict transport security의 약자로, http를 허용하지 않고 https를 사용하는 연결만 허용하는 기능  

3) url을 ip 주소로 변환  
도메인 주소를 IP주소로 변환해주는 DNS(Domain Name System) 서버에 요청해 해당 URL을 IP주소로 변환

4) 라우터를 이용해 해당 서버 게이트웨이까지 이동  

5) 대상 서버와 TCP 소켓 연결
3-way-handshake 과정을 통해 tcp 소켓을 연결하고, https 요청일 경우 서로 암호와 통신을 위한 TLS 핸드쉐이킹 과정이 추가되어 암호화 통신을 진행할 수 있다.


## 클로저
간단하게 클로저는 자신이 생성될 때의 환경을 기억하는 함수를 말한다.
함수와 그 함수가 선언된 렉시컬 환경의 조합이며, 렉시컬이란 소스 코드 내에서 변수가 선언된 위치를 말하며, 렉시컬 스코프란 코드 블록 내에서 변수에 접근할 수 있는 범위를 뜻한다. 

## 이벤트 루프
자바스크립트에서 특정 함수를 호출할 때, 해당 함수는 콜 스택에 저장되어 stack 순서대로 출력된다.  
시간이 오래걸리는 작업이 섞여있을 경우 블록킹이 발생하게 되는데 이를 개선하기 위해 비동기 콜백을 사용하며, 브라우저의 web APIs의 콜백 큐에 해당 비동기 해당 함수를 전달해서 처리하는 것을 이벤트 루프라고 말한다.

## .foreach와 .map의 차이

```foreach```
배열의 요소를 반복, 각 요소에 대한 콜백을 실행, **값을 반환하지 않음**  

```js
const a = [1, 2, 3];
const doubled = a.forEach((num, index) => {
  // num나 index로 무언가 합니다.
});

// doubled = undefined
```

```map```
배열의 요소를 반복, 각 요소에서 함수를 호출해 결과로 새 배열을 작성해 각 요소를 **새 요소에 매핑**

```js
const a = [1, 2, 3];
const doubled = a.map((num) => {
  return num * 2;
});

// doubled = [2, 4, 6]
```
결과가 필요하지만 원본 배열을 변경하고 싶지 않으면 ```.map()```을 사용하고 단순히 배열을 반복할 필요가 있다면 ```forEach```를 사용한다




