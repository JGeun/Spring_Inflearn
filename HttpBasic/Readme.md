# Http Network 이론

---

#### [인터넷 네트워크]
- 인터넷 통신
- IP(Internet Protocol)
- TCP, UDP
- PORT
- DNS

##### 1.  IP
인터넷 프로토콜 역할  

  - 지정한 IP 주소(IP Address)에 데이터 전달
  - 패킷(Packet)이라는 통신 단위로 데이터 전달
  

IP 프로토콜의 한계 
  - 비연결성
      - <sub>패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송</sub>
  - 비신뢰성
      - <sub>중간에 패킷이 사라지면?</sub>
      - <sub>패킷이 순서대로 안오면?</sub>

  - 프로그램 구분
      - <sub>같은 IP를 사용하는 서버에서 통신하는 어플리케이션이 둘 이상이면?</sub>

##### 2. TCP, UDP
인터넷 프로토콜 스택의 4계층  
- 애플리케이션 계층: HTTP, FTP
- 전송 계층: TCP, UDP
- 인터넷 계층: IP
- 네트워크 인터페이스 계층

TCP 특징  
<sub>전송 제어 프로토콜(Transmission Control Protocol)
- <sub>연결지향 - TCP 3 way handshake (가상 연결)  
  <sub> 연결과정 - SYN: 접속 요청, ACK: 요청 수락
     - <sub> 1. SYN 
     - <sub> 2. SYN + ACK
     - <sub> 3. ACK
     - <sub> 4. 데이터 전송
- <sub>데이터 전달 보증
- <sub>순서 보장
- <sub>신뢰할 수 있는 프로토콜
- <sub>현재 대부분 TCP 사용

UDP 특징
<sub>사용자 데이터그램 프로토콜(User Datagram Protocol)
- <sub> 연결지향
- <sub> 순서 보장X
- <sub> 데이터 전달 및 순서가 보장되지 않지만, 단순하고 빠름
- <sub> IP와 거의 같다. + PORT + 체크섬 정도만 추가<br/>
- <sub> 애플리케이션에서 추가 작업 필요

PORT
- 0~65535 할당 가능
- 0~1023: 잘 알려진 포트, 사용하지 않는 것이 좋음 
    - FTP: 20, 21
    - TELNET: 23
    - HTTP: 80
    - HTTPS: 443
    
DNS  
<sub> 도메인 네임 시스템(Domain Name System)  
&nbsp;&nbsp;&nbsp;<sub>도메인 명을 IP주소로 변환