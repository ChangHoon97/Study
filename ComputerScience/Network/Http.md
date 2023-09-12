HTTP(HyperText Transfer Protocol)
 1. 클라이언트 서버 구조
	- 요청과 응답을 분리
 2. 무상태(Stateless)
	- 서버가 클라이언트의 상태를 보존하지 않음
	- 서버 확장에 유리(스케일 아웃)
	- 상태 유지는 최소한만 사용(브라우저 쿠키와 서버 세션)
3. 비연결성(connectionless)
	- 서버 자원을 매우 효율적으로 사용할 수 있음
	- TCP/IP 연결을 새로 맺어야 함(3 way handshake 시간 증가)
	- HTTP 지속연결(Persistent Connections)를 사용하여 시간 단축

HTTP 메시지
 1. 메시지 구조
	 시작 라인 -> 헤더 -> 공백 라인 -> 바디

시작 라인
request-line / status-line
request-line = (method) (request-target) (HTTP version)
메서드 : get, post, put, delete
요청 대상 : 절대 경로("/"로 시작하는 경로)

status-line = (HTTP version) (status-code) (reason-phrase)
reason-phrase = 상태코드를 이해할 수 있는 문구

헤더
header-field = (field-name) : (field-value)
ex) Host : www.google.co.kr
헤더 안에서는 공백 허용
HTTP 전송에 필요한 모든 부가정보

바디
실제 전송할 데이터


HTTP메서드

URI 설계에서 가장 중요한것은 리소스 식별
	- 리소스와 리소스 대상으로 하는 행위를 분리
	- 행위를 분리하는 것은 메서드로 분리한다

GET : 리소스 조회
POST : 요청 데이터 처리(주로 등록)
PUT : 리소스를 대체 없으면 생성(덮어쓰기)
PATCH : 리소스 부분 변경
DELETE : 리소스 삭제
HEAD : GET과 동일하지만 상태 줄과 헤더만 반환
OPTIONS : 대상 리소스에 대한 통신 가능 옵션을 설명(주로 CORS에서 사용)
CONNECT : 대상 자원으로 식별되는 서버에 대한 터널을 설정 (주로 사용X)
TRACE : 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행 (주로 사용X)

GET
	- 리소스 조회
	- 서버에 전달하고 싶은 데이터는 쿼리를 통해서 전달
	- 바디를 거의 쓰지 않는다
POST
	- 서버가 아직 식별하지 않은 새 리소스 생성
	- 요청 데이터 처리(프로세스 처리)
	- 다른 메서드로 처리하기 애매한 경우
	- 메시지 바디를 통해 서버로 요청 데이터 전달(글씨 굵게)
PUT
	- 리소스를 완전히 대체(덮어쓰기)
	- 클라이언트가 리소스 위치를 알고 있어야 한다

PATCH
	- 리소스를 부분 변경

DELETE
	- 리소스 삭제

메서드의 특성
안전 
	- GET
	- 리소스의 변화만을 고려한다
멱등(몇번을 호출하든 결과가 똑같다) 
	- GET, PUT, DLETE
	- 자동 복구 매커니즘에 사용할 수 있다
	- 멱등은 외부 요인으로 중간에 리소스가 변경되는 것 까지는 고려하지 않는다.
캐시가능(응답 결과 리소스를 캐시해서 사용해도 되는가?)
	- GET, HEAD, POST, PATCH
	- 실제로는 GET, HEAD 정도만 캐시로 사용



HTTP 메서드 활용

클라이언트에서 서버로 데이터 전송
데이터 전달 방식
	- 쿼리 파라미터를 통한 데이터 전송
	- 메시지 바디를 통한 전송
Content-Type : application/x-www-form-urlencoded
	- form의 내용을 메시지 바디에 담아서 전송
Content-Type : multipart/form-data
	- 파일 업로드 같은 바이너리 데이터 전송시 사용
Content-Type : application/json
	- 서버 to 서버, 앱 클라이언트, AJAX 사용
	- POST, PUT, PATCH 메시지 바디를 통해 데이터 전송
	- GET 쿼리 파라미터로 데이터 전달

HTML Form 전송은 GET, POST만 지원



HTTP API 설계 예시
https://restfulapi.net/resource-naming

HTTP 상태코드

1xx(Informational) : 요청이 수신되어 처리중
2xx(Successful) : 요청 정상 처리
3xx(Redirection) : 요청을 완료하려면 추가 행동이 필요
	- 302(Found) -> GET으로 변할 수 있음
	- 307(Temporary Redirect) -> 메서드가 변하면 안됨
	- 303(See Other) -> 메서드가 GET으로 변경
4xx(Client Error) : 클라이언트 오류(잘못된 문법 등)
5xx(Server Error) : 서버 오류


일시적인 리다이렉션
POST/REDIRECT/GET
	- POST로 주문후 응답으로 303(302)로 응답
	- Location에 결과화면 명시

 

HTTP 협상 : 클라이언트가 선호하는 표현 요청
- Accept: 클라이언트가 선호하는 미디어 타입 전달
- Accept-Charset : 클라이언트가 선호하는 문자 인코딩
- Accept-Encoding : 클라이언트가 선호하는 압축 인코딩
- Accept-Language : 클라이언트가 선호하는 자연 언어

선호하는 타입을 quality 값을 줘 우선순위를 둘 수 있다
ex) ko-KR,ko;q=0.9,en-US;q=0.8



쿠키
- 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청시 서버로 전달
- 모든 요청에 쿠키 정보 자동 포함


캐시
- 네트워크 사용량 감소
- 브라우저 로딩 속도 증가
- 빠른 사용자 경험
- cache-control: max-age=60 으로 캐시 유효시간 설정

검증헤더
1. Last-Modified
- Last-Modified: xxxxxxxxxxxx (응답)
- if-modified-since : xxxxxxxxxxxx (요청)
- 캐시 만료 후 서버에 재요청 시 데이터가 수정되지 않았을 때 304 Not Modified 응답 (HTTP Body가 없음)

2. ETag(Entity Tag)
- 캐시용 데이터에 임의의 고유한 버전 이름을 달아둠
- ETag만 보내서 같으면 유지, 다르면 다시 받기
- If-None-Match : xxxxxxxxxxxx (요청)
- ETag가 같다면 304 Not Modified 응답

캐시 제어 헤더
Cache-Control
- Cache-Control : xxxxxxx
- max-age : 캐시 유효시간(초 단위)
- no-cache : 데이터는 캐시해도 되지만, 항상 서버에 검증하고 사용
- no-store : 데이터에 민감한 정보가 있으므로 저장하면 안됨
- public : 응답이 public 캐시에 저장되어도 됨
- private : private 캐시에 저장해야 함(default)
- s-maxage ; 프록시 캐시에만 적용되는 max-age

확실한 캐시 무효화 응답
- Cache-Control: no-cache, no-store, must-revalidate
  Pragma : no-cache

no-cache 와 must-revalidate의 차이
- no-cache는 원 서버에 접근할 수 없는 경우 Error or 200 OK로 default 값 설정 가능
- must-revalidate는 원 서버에 접근할 수 없는 경우 504 Gateway Timeout 오류가 발생










