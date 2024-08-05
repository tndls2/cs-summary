📍[OSI 7 Layer](#osi-7-layer)   
📍[TCP/IP 4 Layer](#tcpip-4-layer)   
📍[TCP](#tcp)   
📍[UDP](#udp)   

# 🎟 TCP
## OSI 7 Layer
네트워크 통신의 구성을 7계층으로 나눈 네트워크 표준 모델

![osi 7 layer](https://www.lifewire.com/thmb/li3H7yhEr-D8Vo6MC1Hymi_AvDk=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/OSImodel-8d93f19d50e543348f82110aa11f7a93.jpg)   


1계층(물리계층) ~ 7계층(응용 계층)의 각 계층을 지날 때 마다 `Header`가 붙게되고 수신측에서는 역순으로 `Header` 분석

**✅ 1계층 - 물리 계층(Physical Layer)**

주로 전기적, 기계적, 기능적인 특징을 이용하여 통신 케이블로 데이터를 전송하는 물리적인 장비로 구성되어 있음 <br>
- 데이터 전송 단위 : 비트(Bit)
- 장비 : 허브, 리피터

**✅ 2계층 - 데이터 링크 계층(DataLink Layer)**

물리 계층을 통해 송신/수신 되는 정보의 흐름을 관리하여 안전한 통신 흐름 관리 <br>
프레임에 물리적 주소(Mac Address)를 부여하고 `에러검출`, `재전송`, `흐름제어` 수행 <br>
- 데이터 전송 단위 : 프레임(Frame)
- 장비 : 브릿지, 스위치

**✅ 3계층 - 네트워크 계층 (Network Layer)**

데이터를 목적지까지 안전하고 빠르게 전달하는 역할 <br>
라우터(Router)를 통해 경로를 선택하고 주소를 정하고(IP) 경로에 따라 패킷을 전달하는데 `IP 헤더`가 붙음<br>
- 데이터 전송 단위 : 패킷(Packet)
- 장비 : 라우터, L3 스위치

**✅ 4계층 - 전송 계층(Transport Layer)**

두 지점간에 신뢰성 있는 데이터를 주고 받게 해주는 역할<br>
이 계층에서는 port번호와 전송방식(TCP/UDP) 결정하여 `TCP 헤더`가 붙음 <br>
- 데이터 전송 단위 : Segment(TCP) / Datagram(UDP)
- 장비 : 방화벽

**✅ 5계층 - 세션 계층(Session Layer)**

TCP/IP 세션 체결, 포트번호를 기반으로 통신 세션이 구성됨<br>
두 지점간의 프로세스 및 통신하는 호스트간에 연결을 유지하여 통신<br>
- 데이터 전송 단위 : Data

**✅ 6계층 - 표현 계층(Presentation Layer)**

전송하는 데이터의 표현 방식을 결정함 <br>
`암호화` 하거나, 데이터 변환하거나 파일을 `인코딩` 하는 등의 결정 <br>
ex) JPEG, MPEG, GIF, ASCII 등 <br>
- 데이터 전송 단위 : Data

**✅ 7계층 - 응용 계층(Application Layer)**

최종 목적지로 응용 프로세스와 직접 관계를 맺으며 일반적인 응용 서비스 실행 <br>
일반적으로 사용자가 가장 가깝게 보는 계층 <br>
ex) Chrome, explore 등<br>
- 데이터 전송 단위 : Data

## TCP/IP 4 Layer

OSI 7 Layer 계층들 중 몇개를 묶어서 4계층의 인터넷 프로토콜 으로 표현한 것

![tcp/ip 4 layer](https://velog.velcdn.com/images%2Fcgotjh%2Fpost%2F52907c8c-c149-4943-ad21-3996f44f912f%2F995EFF355B74179035.jpg)   

**✅ 1계층 - 네트워크 인터페이스 계층(Network Interface Layer)**

물리 계층과 데이터 링크 계층에 해당 <br>
물리적인 주소로 MAC 사용
- 프로토콜 : Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11), HDLC, PPP, LLC

**✅ 2계층 - 인터넷 계층 (Internet Layer)**

네트워크 계층에 해당 <br>
네트워크상 최종목적지까지 정확하게 연결되도록 `연결성` 제공
- 프로토콜 : IP, ICMP, ARP, RARP

**✅ 3계층 - 전송 계층(Transport Layer)**

전송 계층에 해당 <br>
IP와 Port를 이용하여 프로세스와 통신 <br>
통신 노드간의 연결을 제어하고 `신뢰성 있는 데이터 전송` 담당
- 프로토콜 : TCP, UDP

**✅ 4계층 - 응용 계층(Application Layer)**

세션계층, 표현계층, 응용계층에 해당 <br>
사용자로부터 데이터를 처음 받는 곳이고 프로그램이 동작하는 계층 <br>




애플리케이션들이 데이터를 교환하기 위해 사용하는 프로토콜을 정의
- 프로토콜
    - Telnet, FTP, HTTP, POP, SMTP (TCP)
    - DHCP, SNMP, DNS (UDP)
