---
title: GSM & Handover
author: khs
date: 2024-02-01 12:00:00 +0800
categories: [무선통신망공학, 2주차]
tags: [Network,GSM,Handover]
pin: true
math: true
mermaid: true
 
---
## **Cellular 통신**

<hr>

- 이전의 무선통신
    - 고출력의 단일 안테나로써 넓은 지역을 커버
    - 주파수의 비효율적 사용
- Cellular 통신
    - 전체 서비스 지역을 여러 개의 단위(Cell)로 분할하여 망을 구성
    - 한정된 주파수 자원을 재사용
    - 주파수 재사용을 통한 많은 가입자 서비스 가능(용량의 증대)
    
    <img src = "https://raw.githubusercontent.com/Togglia/Togglia.github.io/main/_posts/image/20240201/Cellular.png" alt="Cellular" width = "100%" height = "70%">
    
<br>

## **이동통신 네트워크**

<hr>

<img src = "https://raw.githubusercontent.com/Togglia/Togglia.github.io/main/_posts/image/20240201/이동통신네트워크.png" alt="이동통신네트워크" width = "70%" height = "70%">

<br>

## **세대별 이동통신시스템 비교**

<hr>

<img src = "https://raw.githubusercontent.com/Togglia/Togglia.github.io/main/_posts/image/20240201/세대별이동통신시스템비교.png" alt="세대별이동통신시스템비교" width = "100%" height = "70%">

다중접속방식 

FDMA, TDMA, CDMA → 각각 handover 방법이 다름

<br>

## **1세대 이동통신**

<hr>

- AMPS(Advanced Mobile Phone Service)
    - 1983년 미국 시카고, Ameritech가 세계 최초 서비스 개통
    - 1984년 우리나라 도입
    - FDMA 사용(채널 대역폭 30KHz)

<br>

## **2세대 이동통신**

<hr>

- GSM 생성 계기
    - AMPS 이 후 유럽에서도 아날로그 방식이 여러 개 출현
    - 상호 호환성 문제
        - 각기 다른 변조 방식과 주파수 대역, 채널 대역폭 사용
    - 2세대(디지털) 이동통신 방식에 대한 표준화 필요성 대두
- 2세대 이동통신의 계기
    - 혼선으로 인한 품질전하, 낮은 주파수 재사용 효율, 폭발적 수요 등
    - 디지털 방식 기술 개발 요구

<br>

## **Digital이란?**

<hr>

- 비 연속적으로 변화하는 물리량
- 비 연속적 파형
- 0과 1

    <img src = "https://raw.githubusercontent.com/Togglia/Togglia.github.io/main/_posts/image/20240201/Digital_signal.png" alt="Digital_signal" width = "50%" height = "50%">
    

- 왜곡에 강함

    <img src = "https://raw.githubusercontent.com/Togglia/Togglia.github.io/main/_posts/image/20240201/recovering.png" alt="recovering" width = "100%" height = "50%">
    
<br>

# **GSM (Global System for Mobile communication)**

- Multiple Access : TDMA (Time Division Multiple Access)
- 표준기관 : ETIS (1991년)
- Peak data rate : 0.104Mbps
- 주요 서비스 음성, 문자
- 목적
    - 좋은 주관적 음성 품질
        - 통신 시스템이 사용자들에게 명확하고 이해하기 쉬운 고품질 음성 전송을 제공하는 중요성을 강조
    - 낮은 단말 및 서비스 비용
        - 최종 사용자 장치(단말) 및 제공되는 서비스와 관련된 비용을 최소화하여 넓은 범위의 사용자에게 경제적으로 제공하는 것을 목표
    - 국제 로밍 지원
        - 국제로 이동하더라도 통신 서비스를 연속적으로 이용할 수 있도록 하는 것을 강조
    - handhold terminals 지원 능력
        - 이동성이 있는 사용자에게 서비스를 제공하기에 유용
    - 다양한 새로운 서비스 및 시설 지원
        - 시스템이 다양한 새로운 서비스 및 시설을 지원하는 데 중점을 두고 있으며, 기술의 진보나 서비스 다양성을 통해 사용자에게 다양한 옵션을 제공
    - 주파수 효율성
        - 주파수 스펙트럼을 효율적으로 활용하여 네트워크의 성능을 극대화하려는 것을 강조
        - 많은 사용자를 지원하고 빠른 데이터 전송을 가능하게 함.
    - ISDN 호환성
        - **I**ntegrated **S**ervice **D**igital **N**etwork (**종합 정보 통신망**)
        - 기존의 공중 전화 망(Public Switched Telephone Network) 인프라에서 고속의 디지털 통신을 하기 위한 통신 규약
        - 디지털 통신 기술의 표준입니다. 이 목표는 시스템이 ISDN과 호환되도록 하는 것을 강조
        - 다양한 통신 서비스 및 시설을 통합하여 제공하는 데 중요한 역할
- GSM 네트워크 구조
    
    <img src = "https://raw.githubusercontent.com/Togglia/Togglia.github.io/main/_posts/image/20240201/GSM Network.png" alt="GSM Network" width = "100%" height = "50%">

<br>

## **MS(Moblie Station)**

<hr>

- ### **ME(Mobile equipment)**
    - terminal
    - IMEI(International Mobile Equipment Identity) → unique  ID
- ### **SIM(Subscriber Identity Module)** 
    → **사용자가 이동될 때, 서비스에 접속이 가능하게해주는**
    - SIM 카드(SIM card)는 사용자가 특정 단말기와 무관하게 구독한 서비스에 액세스할 수 있도록 개인 이동성을 제공
    - IMSI(International Mobile Subscriber Identity) → **그럼 어떻게 하는거지?? IMSI사용**
        - 사용자를 시스템에 식별하기 위해 사용되는 중요한 식별자
        - IMSI와 IMEI는 서로 독립적으로 작동
    
    SIM 카드는 IMSI를 통해 사용자를 식별하고, 이것은 사용자의 서비스 구독 및 인증에 필요한 정보를 저장하는 데 사용된다. 
    
    동시에 IMEI는 특정 모바일 장치를 식별하고, 이것은 사용자의 단말기를 식별하는 데 사용된다. 이것은 사용자가 이동성을 유지하면서 여러 다양한 단말기를 사용할 수 있도록 한다.

<br>

## **BSS(Base Station Subsystem)**

<hr>

- ### **BTS(Base Transceiver Station) → 기지국**
    - BTS는 무선송수신기(radio transceivers)를 가진다.
        - 셀을 정의하고 휴대 전화와 무선 링크 프로토콜을 처리하는 역할 수행
- BSC(Base Station Controller) →기지국 컨트롤러
- MSC와 BTS 사이의 모든 제어 기능과 물리적 링크를 제공
- BSC는 하나 이상의 BTS의 무선자원을 관리
- 무선 채널 설정, 주파수 호핑, 핸드오버 등을 처리
- **BSC는 MS와 Mobile Service Switching Center간의 연결(MSC)**

<br>

## **NS(Network Subsystem)**

<hr>

- ### **MSC(Mobile services Switching Center)**
    - PSTN(public switched telephone network) 또는 ISDN(Integrated Services Digital Network)의 일반 스위칭 노드와 같은 역할
        - PSTN : 세계의 공중 회선교환전화망망들이 얽혀있는 전화 망으로 세계의 공공 [I](https://ko.wikipedia.org/wiki/IP)P 기반 패킷 교환 망인 인터넷과 방식이 매우 닮아 있다.
    - **로밍 가입자에 대한 등록, 인증, 위치 갱신, 핸드오버, 통화 라우팅 등의 모바일 가입자를 처리**
    - HLR 및 VLR은 MSC와 함께 GSM의 통화 routing 및 로밍 기능을 제공
- ### **HLR(Home Location Register) → DB의 역할**
    - HLR에는 해당 GSM 네트워크에 등록된 **각 가입자의 모든 관리 정보와 모바일의 현재 위치**가 포함
- ### **VLR(Visitor Location Register)**
    - VLR에는 통화 제어에 필요한 **HLR에서 선택한 관리 정보**가 포함
- ### **EIR(Equipment Identity Register) →장비정보**
    - EIR은 네트워크 상의 모든 유효한 **모바일 장비의 목록을 포함하는 데이터베이스**
- ### **AuC(Authentication Center) → 인증센터**
    - AuC는 각 가입자의 SIM 카드에 저장된 비밀키 사본을 저장하는 보호 데이터베이스로, 무선 채널을 통한 인증 및 암호화에 사용
- ### **GIWU(Global System for Mobile Communications Interworking Unit)**
    - GIWU는 데이터 통신을 위해 다양한 네트워크에 인터페이스를 제공하는 하드웨어와 소프트웨어로 구성
    - GIWU를 통해 사용자는 통화 중 음성과 데이터를 번갈아 사용할 수 있으며, GIWU 하드웨어 장비는 MSC/VLR에 물리적으로 위치
    - 다른 망과 네트워킹하기 위해 사용, 인터페이스 역할

<br>

# **Handover**

- GSM에서 Handover 하는 4가지 방법
- 이동통신 가입자가 이동 중에도 자유롭게 서비스를 사용할 수 있도록 기지국과 기지국 사이에서 끊김 없이 서비스가 가능하게 하는 기술

<br>

## **Types of Handover : 이동하는 구간에 따라 나눔**
<hr>

- Intra Cell Handover
- Inter Cell, intra BSC handover
- Inter BSC, Intra MSC handover
- Inter MSC handover
    
    <img src = "https://raw.githubusercontent.com/Togglia/Togglia.github.io/main/_posts/image/20240201/Handover.png" alt="Handover" width = "100%" height = "50%">
    
    하나의 BSC는 여러개의 BTS를 관리할 수있다.
    

### **Intra Cell Handover**

- 동일한 셀 내에서, 협대역 간섭이 특정 주파수에서 전송을 불가능하게 만들 수 있을 때 발생 → BSC는 반송파 주파수를 변경하기로 결정

### **Inter Cell, intra BSC handover**

- GSM 시스템 내의 일반적인 핸드오버이며, MS가 한 BTS에서 다른 BTS로 이동하지만 동일한 BSC의 제어권 내에 있을 때 발생
- BSC는 새로운 BTS에서 핸드오버를 수행하고 새로운 라디오 채널을 할당한 후 이전 BTS를 해제

### **Inter BSC, Intra MSC handover**
- BSC는 제한된 수의 BTS를 제어하기 때문에 GSM 시스템은 BSC 간에 핸드오버를 수행
- 이러한 형태의 핸드오버는 MSC에 의해 제어
- 다른 BSC가 관리하는 BTS로 옮길 때 MSC가 컨트롤한다.

### **Inter MSC handover**

- 서로 다른 두 MSC에 속한 두 BTS 간에도 핸드오버가 필요할 수 있으며, 두 MSC가 함께 핸드오버를 수행
- MSC가 바뀌는 경우, 그 밑이 전부 다 변경