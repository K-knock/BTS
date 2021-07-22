# BlueBorne
- 블루투스 관련 프로세스는 모든 OS에서 높은 권한을 갖고 있다. 만약 공격할 프로세스를 Exploit하는 데에 성공한다면 기기를 통제할 수 있다. Blueborne이란 블루투스의 취약점을 악용하여 위의 방법대로 연결된 기기의 제어권을 획득하는 공격이다.
- ### 블루본의 위험성

    - 기기와 페어링되어 있지 않아도 된다.
    - 기기의 블루투스만 켜져 있다면 스니핑 공격을 통해 공격이 가능하다.
    - Window, Linux, iOS 등 여러 곳에서 취약점을 찾을 수 있었다.

# 관련 정보
- ### CVE 목록

    - CVE-2017-0781
        - 대상 : Android 4.4.4버전，5.0.2버전，5.1.1버전，6.0버전，6.0.1버전，7.0버전，7.1.1버전，7.1.2버전，8.0버전
        - 안드로이드 BNEF 서버에서 원격 코드를 실행할 수 있다.(RCE)
    - CVE-2017-0782
        - 대상 : Android 4.4.4버전，5.0.2버전，5.1.1버전，6.0버전，6.0.1버전，7.0버전，7.1.1버전，7.1.2버전，8.0버전
        - 안드로이드 BNEF 서버에서 원격 코드를 실행할 수 있다.(RCE)
    - CVE-2017-0785
        - 대상 : Android 4.4.4버전，5.0.2버전，5.1.1버전，6.0버전，6.0.1버전，7.0버전，7.1.1버전，7.1.2버전，8.0버전
        - 안드로이드 SDP 서버에서 공격자가 특정한 요청을 통해 취약점에 영향을 받는 부분의 정보를 유출하고, 블루투스 통신을 제어할 수 있다.
    - CVE-2017-0783
        - 대상 : Android 4.4.4버전，5.0.2버전，5.1.1버전，6.0버전，6.0.1버전，7.0버전，7.1.1버전，7.1.2버전，8.0버전
        - 안드로이드 PAN 설정 파일에서 나타났으며 정보 노출 취약점을 말한다. 이를 통해 중간자 공격(Man-In-The-Middle)이 가능하며, 블루투스 통신을 중간에서 통제할 수 있다.
    - CVE-2017-8628
        - 대상 : Microsoft Windows Server 2016，Windows Server 2008 SP2，Windows RT 8.1，Windows 8.1，Windows 7 SP1，Microsoft Windows 10，Windows 10 버전 1511，Windows 10버전 1607，Windows 10 버전 1703
        - 무선 범위 내에서 블루투스 스택에 스푸핑을 하여 중간자 공격이 가능하다.
    - CVE-2017-14315
        - 대상 : Apple iOS 7~9 버전
        - LEAP(Low Energy Audio Protocol) 구현 과정에서 오디오 명령 인증을 정확하게 검증되지 않은 상태로 대상 장치로 전송되어 힙 오버플로우가 발생할 수 있다.
    - CVE-2017-1000251
        - 대상 : Linux kernel 3.3-rc1 ~ 4.13.1버전
        - L2CAP 설정 응답 처리 과정에서 스택 오버플로우 취약점이 발생한다. 이를 통해 공격자의 원격 코드 실행이 가능하다.
    - CVE-2017-1000250
        - 대상 : BlueZ 5.46 및 이전 버전
        - BlueZ라는 Linux 블루투스 프로토콜 스택의 SDP 서버에서 검색 속성 요청을 처리할 때 정보노출 취약점이 발생한다. 블루투스 메모리의 중요한 정보를 탈취할 수 있다.
    - CVE-2017-1000410
        - 대상 : Linux 커널 3.3-rc1 버전 이상
        - L2CAP 명령 처리에서 스택 변수가 초기화되지 않아 발생하는 취약점이다. 공격자는 코드의 흐름을 조작하여 스택 변수의 데이터를 제어할 수 있다.
- Exploit
    - https://www.exploit-db.com/exploits/44554
    - https://www.exploit-db.com/exploits/44555
    - https://www.exploit-db.com/exploits/42762
- Paper
    - https://www.armis.com/research/blueborne/
    - https://www.krcert.or.kr/data/secNoticeView.do?bulletin_writing_sequence=26687&queryString=cGFnZT0zJnNvcnRfY29kZT0mc2VhcmNoX3NvcnQ9dGl0bGVfbmFtZSZzZWFyY2hfd29yZD0=
