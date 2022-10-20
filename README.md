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

