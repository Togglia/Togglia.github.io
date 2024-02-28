---
title: Protocol and OSI7Layer
author: KHS
date: 2022-01-22 11:33:00 +0800
categories: [무선통신망공학, 1주차]
tags: [Network]
pin: true
math: true
mermaid: true
 
---
## Network
<hr>
통신분야에서 단말기 등을 접속하기 위해 사용되는 단말기기, 선로 및 교환기 등으로 구성되는 전송매체 

## CBN vs PBN
<hr>
- CBN(circuit-based network)
    
    
    - 전화망 (PSTN)
    - connection-oriented service
    - 자원점유방식 → BW사용
        - Qos(품질) 보장 // delay, loss, jitter(delay값이 다 다르다)
    - SS7(signal system #7)
        - signaling 위한 신호 처리 망
    
    단점 : 자원 사용의 비효율성 증가
    

- PBN(Packet-based network)
    
    
    
    - Internet
    - connection-less service
    - 자원(BW) 공유 방식 → 버퍼 사용 // Queueing
        - Qos 보장 X
        - Best-effort service

- Ring Back Tone
    
    일단 시스템 망과 시그널 전달 망은 다르다
    
    듣는 호출 쪽의 경험과, 전화 벨이 울리는 받는 쪽의 경험은 다르다는 점을 기억해야 합니다. 링 백 톤은 공중 교환 전화망(PSTN) 및 휴대전화 망의 기능으로, 호출자에게 고유하고 개인화 된 통화 경험을 제공
  

## Protocol
<hr>

- 통신을 위한 규약(약속) , 의사소통, IP, TCP, 케이블규격 등등
- 표준화 ( ISO,IEEE,IETF, ETSI(유럽표준), ITU, TTA …)
    - IEEE → 802.11(WLAN), 802.3(Ethernet)
- 프로토콜의 3대 요소
    - format
    - meaning
    - timing → 동기식, 비동기식


## OSI 7 Layer
<hr>
- ISO(Internation Organization for Standardization)
- 7개의 계층으로 이루어진 통신을 위한 프로토콜 스택
- peer to peer protocol stack



### 7계층 : Application(응용) Layer

- 목적 : 사용자의 편의성 제공, 프로그램
- GUI로 구성된 경우가 많다.
- 통신을 위한 통신 어플리케이션
- 프로토콜 → ex) HTTP,FTP

### 6계층 : Presentation(표현) Layer

- 목적  : 어떻게 Display 할 것인가??
- Codec(coding + decoding) 관련
- 압축, 암호화 → ex) avi, mp3, mp4

### 5계층 : Session(세션) Layer

- 목적 : 사용자의 구분, 누구와 통신 할 것인가?
- Session ID : 누구와 통신 할 것인지를 구분할 수 있도록 알려주는 구분자 ID → 유일성을 가진다.
    - ex) e-mail address([togglia@cbnu.ac.kr](mailto:togglia@cbnu.ac.kr)), Phone number(01011112222), URL
- Qusetion
    - MAC address와의 차이
        - MAC 주소는 네트워크 장치를 고유하게 식별하는 것이며, 물리적인 네트워크 계층에서 사용된다.
        - 세션 ID는 사용자 또는 세션을 논리적으로 식별하는 것이며, 소프트웨어 레벨에서 사용되며 사용자 활동을 추적하는 데 도움을 준다.
    - Session을 커넥션이라 생각하면 그 커넥션을 잡기 위한 ID
    - 영역에 따라 의미가 달라 → 실무에서는 연결성

### 4계층 : Transport(전송) Layer

- 목적 : Port에 따라서 어떻게 전송 할 것인가?
    - 어떤 Port로 전송 할 것인가?
- Port number : 어떤 프로토콜을 사용해서 전송할 것 인가를 구분
    - 0 ~ 1023 : well-Known port. 표준화 되어 있는 포트 (20 FTP, 23 Telnet, 53 DNS, 80 HTTP, 433 HTTPS)
    - 1024 ~ 49151 : registered prot. 상업적인 어플리케이션을 개발하는 회사들이 등록하여 사용하는 포트
    - 49152 ~ 65535 : dynamic port. 사용자(개발자) 자유롭게 즉흥적으로 할당하여 사용할 수 있는 포트
- UDP vs TCP
    - UDP : TCP 대비 프로토콜이 간결함. 가볍고 빠름, Qos 보장 X ( real-time service: 실시간 비디오)
    - TCP :  UDP 대비 프로토콜이 복잡함. 무겁고 느림. UDP 대비 QoS 일부분 보장
        - retransmission(응답이 오지 않아 재전송), timeout 특성을 가지고 흐름제어, 오류제어
        - non-real-time service: email 서비스, 문자 서비스

### 3계층 : Network(네트워크) Layer

- 목적 : 데이터 전송
- end-to-end (source-to-destination)
- IP address → 사물의 위치를 특정하지 못한다.
- IP (Internet Protocol)
- DNS ( Domain Name System) //엄연히 따지만 Session Layer에 해당
    - 상대편의 IP 주소를 알아오는 메커니즘
    - 계층적 → 세션 ID 로 IP address를 알아온다.
- 장비 : L3 Router
    - routing(forwarding)
    - forwarding table (최종 결과물)
    
       

### 2계층 : Data-link(데이터 링크) Layer

- 목적 : 데이터 전송
- hop-by-hop (per-hop behavior, smart phone-기지국) , 노드간 거리
- LLC(Logical Link Control)
    - 논리적 채널 관리 → 상위 계층과 하위 계층 간의 통신을 관리하고 안정적인 데이터 전달을 보장하는 데 도움을 준다.
    - TDMA(Time Division Multiple Access), CDMA
- MAC(Medium Access Control) //단일성, 유일성
    
    
    
    - Mac address
    - 고유한 하드웨어 주소
    - shared medium의 특성에 따라 유일한 주소인 MAC 주소가 필요함
    - IEEE
    - AB:CD:12:AC:BE:44
    - ARP (FF:FF:FF:FF:FF:FF broadcasting address) :
        - 네트워크 상에서 IP 주소를 물리적 네트워크 주소로 대응(bind)시키기 위해 사용되는 프로토콜
    - MAC switching
        - 이더넷 및 LAN (Local Area Network) 환경 내에서 데이터 프레임을 효율적으로 목적지로 전달하기 위한 네트워크 기술로, 이러한 프로세스는 각 장치의 네트워크 인터페이스 카드 (NIC)와 관련된 하드웨어 주소인 MAC 주소를 기반으로 전달 결정을 내린다.
    - VPN(virtual Private Network) : Logical MAC address를 부여 할 수 있음
- 장비
    - L2 Switch → ARP 기능 X : 네트워크 Protocol , 브릿지
    - MAC learning
        - 스위치가 네트워크에서 프레임을 효율적으로 전달하고 네트워크 장치 간의 통신을 관리하는 데 중요한 역할을 한다. 이 프로세스는 스위치가 어떤 장치가 어떤 포트에 연결되어 있는지 파악하고, 이를 기반으로 데이터 프레임을 올바른 목적지로 전달하는데 사용한다.
        - 프레임 수신 → 포트 연결 → 테이블 업데이트 → 포워딩 결정
    - ARP table
        - 네트워킹에서 사용되는 데이터 구조로, Local network segment에서 IP 주소와 해당 MAC (Media Access Control) 주소 간의 매핑을 제공한다. ARP 테이블은 일반적으로 컴퓨터, 라우터 및 스위치와 같은 장치에 의해 유지된다.

### 1계층 : Physical(물리) Layer

- 목적 : 데이터를 비트형태로 표현
    - 네트워크로의 하드웨어 전송
- ex) AM, FM, PSK, FSK →  modulation
- L1 장비
    - 허브: 물리적으로 성형구조, 논리적으로 버스 구조
    - 리피터: 신호증폭장치 (감쇄, 잡음)
- Topology: 망의 구성
    - Star, mesh, bus…

## 예시로 알아보는 계층
<hr>
예시 1
- User가 사용할 수 있는 장치(=단말기)
    - pc, smartphone
- kakao talk 다운로드->설치(L6, L4)->실행(L7)
- 로그인?->새로운 계정 생성(email, 전화번호)->전화번호로 카카오 가입
    - session ID(L5)
- 동기화
    - 내가 가진 주소록(전화번호부)을 가지고 친구목록 생성(Session ID와 연동)
- 스마트폰을 구입하고, 통신사에 가입하고(개통)
    - L3
- 스마트폰 제조사
    - L2,L1

---

예시 2 
- 카카오톡 실행(L7)-->철수를 주소록에서 찾고 철수(L5)와의

    대화창을 실행(L4)
    
- “안녕하세요” 입력->전송
    - L6 encoding
    - L5 철수의 session ID 를 가지고 L3 IP 주소를 획득(DNS)
    - L4 header encapsulation->L3 header encapsulation
    - 나의 스마트폰의 MAC, LTE 기지국(eNodeB) MAC 주소를 가지고 L2 header 생성. encapsulation
    - 비트 모듈레이션 후 물리적 신호로 변경하여 LTE 기지국(eNodeB)으로 패킷을 전송(L1)