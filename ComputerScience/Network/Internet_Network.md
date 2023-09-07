[인터넷 네트워크]


# IP(인터넷 프로토콜)
 1. 역할 
- 지정한 IP 주소에 데이터 전달
 - 패킷(Packet)이라는 통신 단위로 데이터 전달
 2. 한계
 - 비연결성 : 대상이 서비스, 패킷 전송 불능
 - 비신뢰성 : 패킷 소실, 패킷 전달 순서 문제 발생
 - 프로그램 구분 : 같은 IP에서 애플리케이션이 여러개면 구분 불가

 # PORT
- 0~65535 사용 가능
- 0~ 1023 : 사용하지 않는 것이 좋음
  
##### IP는 하나의 호텔 주소이고 PORT는 호텔 객실 번호이다.

# 인터넷 프로토콜 스택의 4계층

애플리케이션 계층 - HTTP, FTP
전송 계층 - TCP, UDP
인터넷 계층 - IP
네트워크 인터페이스 계층

# TCP/UDP

TCP(Transmission Control Protocol)
- 연결 지향(TCP 3 way handshake)
- 데이터 전달 보증
- 순서 보장

UDP(User Datagram Protocol)
- IP와 거의 같다
- PORT와 체크섬 정도만 추가
 - 애플리케이션에서 추가 작업 필요


# DNS(Domain Name System)
- 도메인 명을 IP주소로 변환
