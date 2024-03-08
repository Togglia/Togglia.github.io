---
title: LTE Handover
author: khs
date: 2024-02-05 18:00:00 +0800
categories: [무선통신망공학, 5주차]
tags: [Network]
pin: true
math: true
mermaid: true
 
---

## Content
<hr>

> - LTE Handover
> - UMTS Architecture

<br>

## **핸드오버 모델**
<hr>

  * Hard Handover (준비 - 실행 - 완료)

    ![Hard Handover Model](https://velog.velcdn.com/images/keviness0720/post/cf8f5d38-6adb-4d73-9b68-5f51ca5cef05/image.png)

<br>

## **패킷 손실 감소 방안**

<hr>

  * Bi-casting
    - 코어 네트워크의 게이트웨이(S-GW/P-GW)에서 두 기지국으로 동시 Bi-casting 하는 기술
      - Bi-casting 시점의 결정이 어려워 데이터 유실 가능
  * Do Nothing
    - 코어 네트워크의 게이트웨이에서 통신 path를 소스 셀로부터 타깃 셀로 단순히 스위칭 시키는 기술
  * Packet Forwarding
    - 소스 셀에서 패킷 데이터를 버퍼링한 후 타깃 셀로 포워딩하는 기술
      - 데이터 유실이 적어 선호

    ![Packet Forwarding](https://velog.velcdn.com/images/keviness0720/post/e92df3b6-07bd-488c-a845-40a152632849/image.png)

<br>

## **Packet forwarding 방식**
<hr>

  * Re-ordering 문제 발생
    - re-ordering-timer 사용

    ![Re-ordering Timer](https://velog.velcdn.com/images/keviness0720/post/7593da91-e5db-4e28-9a6b-4f6ecd9bbc1b/image.png)

<br>

## **LTE 핸드오버 시나리오**
  * HO Preparation phase(1~6)
  * HO Execution phase(7~9)
  * HO Completion phase(10~15)

  ![](https://velog.velcdn.com/images/keviness0720/post/f6e5e924-1253-4901-b215-520a01815219/image.png)

  ![](https://velog.velcdn.com/images/keviness0720/post/2154a8fd-c01a-495c-b744-a27092329e5c/image.png)

### **HO Preparation(1~6): 타깃 셀을 결정하고, 타깃 셀의 자원을 설정하는 단계**
  - 단계 1: 단말이 측정한 소스 기지국(S-eNB)의 수신 신호세기가 일정 임계치 이하로 떨어지고 타깃 셀(T-eNB)의 측정 수신세기가 일정 임계치 이상으로 증가하는 경우, 단말은 Measurement Report(1)를 소스 셀에 보냄
  - 단계 2: 소스 셀은 앞서 말한 3절의 인접 셀 탐색 기술과 무선자원관리(RRM) 기술의 지원을 통해 타깃 셀을 결정
  - 단계 3/4: 이후 소스 셀로부터 핸드오버 요청 (handover request, 3)을 수신한 타깃 셀은 주어진 태스크(4)를 차례로 수행
    - 예로, 핸드오버 호에 대한 수락제어(admission control), 단말 컨텍스트 정보 저장(store UEcontext), 새로운 단말 식별번호 할당(new C-RNTI), 그리고 타깃의 무선자원형상 구성(configure T-eNB) 등이 이에 해당함
  - 단계 5/6: 이후 타깃 셀은 태스크 수행결과에 대한 응답을 소스 셀에 통보하고(5), 소스 셀은 바로 이어 네트워크에서 내려 받은 다운링크 패킷 송출을 중지하고 버퍼에 쌓아 둠(6). 버퍼에 저장된 패킷은 X2 인터페이스상에 형성되는 GTP터널을 통하여 소스 셀에서 타깃 셀로 포워딩됨

### **HO Execution(7~9): 패킷을 포워딩하고 타깃 셀을 액세스하는 단계**
  - 단계 7/8: 소스 셀로부터 handover command 메시지(7)를 수신한 단말은 업링크 패킷의 전송을 중단하고 이를 버퍼에 저장(8).
  - 단계 9/9a: 이와 동시에 단말은 handover command 메시지에 실려온 타깃 액세스 정보를 이용하여 타깃 셀을 액세스하여 업링크 시각 동기화를 이루고 패킷 교환에 필요한 무자원을 요청한 다음, 그 응답을 받음(9/9a)

### **HO Completion(10~15): path switching을 행하고 소스 셀의 자원을 해제하는 단계**
  - 단계 10: 단말이 타깃 셀과 접속 완료한 후 이 완료 사실을 handover confirm 메시지(10)를 통해 코어 네트워크의 S-GW에 보고
  - 단계 12: S-GW는 소스 셀에서 타깃 셀로 path switching을 수행함(12).
  - 단계 13/15: 이후 소스 기지국에 할당된 모든 자원은 해제되며(13/14), 필요에 따라 위치 갱신과 라우팅 갱신 절차가 수행됨(15)

<br>

## **UMTS Architecture**

<hr>

![](https://velog.velcdn.com/images/keviness0720/post/91787064-9fb1-4fa4-96e2-3fcb09fbaa28/image.png)

<br>

**_참고자료 _**
> * 그림 출처: MIMO? 미모 아니면 마이모? : 네이버 블로그 (naver.com)
> * CA 개념 10 (그림 출처: 캐리어 어그리게이션 - 나무위키 (namu.wiki))
> * Ref.) LTE Network Architecture: Basic | NETMANIAS
> * Ref.) 송평중, 신연승 “네트워크 컨버전스를 위한 LTE Mobility management 기술” , 전자통신동향분석 제25권 제6호 2010. 12월
