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
<sub>

  - 비연결성
    <sub>
      - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송
    </sub>


  - 비신뢰성
    <sub>
      - 중간에 패킷이 사라지면?<br/>
      - 패킷이 순서대로 안오면?
    </sub>


  - 프로그램 구분
    <sub>
      - 같은 IP를 사용하는 서버에서 통신하는 어플리케이션이 둘 이상이면?
    </sub>
</sub>
        

##### 2. TCP, UDP
인터넷 프로토콜 스택의 4계층  

<sub>

- 애플리케이션 계층: HTTP, FTP
- 전송 계층: TCP, UDP
- 인터넷 계층: IP
- 네트워크 인터페이스 계층

</sub>

<br/>

TCP 특징  

<sub>
전송 제어 프로토콜(Transmission Control Protocol)


- 연결지향 - TCP 3 way handshake (가상 연결)  
  <sub>
    연결과정 - SYN: 접속 요청, ACK: 요청 수락
  
       1.SYN  
       2 SYN + ACK  
       3 ACK  
       4 데이터 전송  
  
   </sub>
  
- 데이터 전달 보증
- 순서 보장
- 신뢰할 수 있는 프로토콜
- 현재 대부분 TCP 사용
</sub>
  
UDP 특징

<sub>

사용자 데이터그램 프로토콜(User Datagram Protocol)

 <sub>

- 연결지향
- 순서 보장X
- 데이터 전달 및 순서가 보장되지 않지만, 단순하고 빠름
- IP와 거의 같다. + PORT + 체크섬 정도만 추가<br/>
- 애플리케이션에서 추가 작업 필요

 </sub>

</sub>

PORT

<sub>

- 0~65535 할당 가능
- 0~1023: 잘 알려진 포트, 사용하지 않는 것이 좋음 
    - FTP: 20, 21
    - TELNET: 23
    - HTTP: 80
    - HTTPS: 443
</sub>
    
DNS  
<sub> 

도메인 네임 시스템(Domain Name System)  
=>도메인 명을 IP주소로 변환

</sub>

<br/>

#### [URI와 웹 브라우저 요청 흐름]
##### URI(Uniform Resource Identifier)
<sub>

"URI는 URL-로케이터(locator), URN-이름(name) 또는 둘 다 추가로 분류될 수 있다."

</sub>

<br/>

#### 상태코드

<sub>
클라이언트가 보낸 요청의 처리 상태를 응답해서 알려주는 기능

- 1xx (Informational): 요청이 수신되어 처리중
- 2xx (Successful) : 요청 정상 처리
     - 200 ok
     - 201 Created  
       요청 성공해서 새로운 리소스가 생성됨
     - 202 Accepted  
       요청이 접수되었으나 처리가 완료되지 않았음
     - 204 No Content  
        서버가 요청을 성공적으로 수행했지만, 응답 페이로드 본문에 보낼 데이터가 없음.
  
- 3xx (Redirection) : 요청을 완료하려면 추가 행동이 필요
    - 300 Multiple Chocies
    - 301 Moved Permanently 
        - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음(MAY)
    - 302 Found
        - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음(MAY)
    - 303 See Other
        - 리다이렉트시 요청 메서드가 GET으로 변경
    - 304 Not Modified
    - 307 Temporary Redirect
        - 리다이렉트시 요청 메서드와 본문 유지(요청 메서드를 변경하면 안된다. MUST NOT)
    - 308 Permanent Redirect
        - 리다이렉트시 요청 메서드와 본문 유지(처음 POST를 보내면 리다이렉트도 POST 유지)
- 4xx (Client Error) : 클라이언트 오류, 잘못된 문법 등으로 서버가 요청할 수 없음
- 5xx (Server Error) : 서버 오류, 서버가 정상 요청을 처리하지 못함
</sub>