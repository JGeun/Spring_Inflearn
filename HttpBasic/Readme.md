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
    - 400 Bad Request: 클라이언트의 요청에 잘못된 문법 등으로 서버가 요청을 수행할 수 없음
         - 요청 구문, 메세지 등등 오류
         - 클라이언트는 요청 내용을 다시 검토하고, 보내야함
         - ex) 요청 파라미터가 잘못되거나, API 스펙이 맞지 않을 때
    - 401 Unauthorized: 클라이언트가 해당 리소스에 대한 인증이 필요함
         - 인증(Authentication) 되지 않음
         - 401 오류 발생시 응답에 WWW-Authenticate 헤더와 함께 인증 방법을 설명
         - 참고
             - 인증(Authentication): 본인이 누구인지 확인, (로그인)
             - 인가(Authorization): 권한부여 (ADMIN 권한처럼 특정 리소스에 접근할 수 있는 권한, 인증이 있어야 인가가 있음)
             - 오류 메세지가 Unauthorized 이지만 인증되지 않음 (이름이 아쉬움)
    - 403 Forbidden: 서버가 요청을 이해했지만 승인을 거부함
         - 주로 인증 자격 증명은 있지만, 접근 권한이 불충분한 경우
         - ex) ADMIN 등급이 아닌 사용자가 로그인은 했지만, ADMIN 등급의 리소스에 접근하는 경우
    - 404 Not Found: 요청 리소스를 찾을 수 없음
         - 요청 리소스가 서버에 없음
         - 또는 클라이언트가 권한이 부족한 리소스에 접근할 때 해당 리소스를 숨기고 싶을 때
    - 중요! 클라이언트가 이미 잘못된 요청, 데이터를 보내고 있기 때문에, 똑같은 재시도가 실패함
- 5xx (Server Error) : 서버 오류, 서버가 정상 요청을 처리하지 못함, 재시도하면 성공할 수도 있음
    - 500 Internal Server Error: 서버 문제로 오류 발생, 애매하면 500 오류
         - 서버 내부 문제로 오류 발생
         - 애매하면 500 에러
    - 503 Service Unavailable: 서비스 이용 불가
         - 서버가 일시적인 과부하 또는 예정된 작업으로 잠시 요청을 처리할 수 없음
         - Retry-After 헤더 필드로 얼마뒤에 복구되는지 보낼 수도 있음
</sub>