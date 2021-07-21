# BLESA

**정의**

- BLESA는 BLE Spoofing Attacks의 준말로, 블루투스 연결이 재차 성립되는 과정에서 발동
    - **재연결의 경우?**
        - 이미 블루투스를 통하여 페어링된 두 개의 장비 중 하나가 연결 범위 벗어났다가 다시 연결되는 현상
    - **Spoofing Attacks 란 ?**
        - 누군가 또는 무언가가 누군가 또는 무언가인 것처럼 가장하여 시스템에 액세스하거나 데이터를 훔치거나 신뢰를 얻으려는 시도

**BLE 보안 레벨**

- **Level 1** : 평문 통신
- **Level 2** : 암호화를 하여 통신
- **Level 3 and 4** : 암호화 및 사용자 인증하여 통신

**블루투스 패어링 방법**

- **No I/O interfaces :** 보안 레벨 Level 2
- **With I/O interfaces :** 보안 레벨 Level 3 and 4

## 관련 정보

- CVE
    - **CVE-2020-9770**

        **취약점 발생하는 모델**

        - **Name** : LinuxLaptop | **OS** : Ubuntu18.04 | **BLE Stack** : BlueZ 5.48
        - **Name** : Google Pixel XL | **OS** : Android 8.1 , 9 , 10 | **BLE Stack** : Fluoride
        - **Name** : iPhone8 | **OS** : iOS 12.1 , 12.4 , 13.3.1 | **BLE Stack** : iOS BLE Stack

        **사후 인증하는 상품에 대한 공격과정 (해석)**

        - **정상적인 재연결의 과정**
            1. 클라이언트는 서버에 연결 요청을 보냅니다.
            2. 연결된 후 battery Level(권한 lv. 2 필요)을 요청을 보냅니다. 이 때 요청 권한 lv. 1
            3. 서버는 권한 레별이 낮다는 에러 메세지를 보냅니다. 
            4. 에러 메시지를 받은 클라이언트는 암호화(권한 상승 2로) 합니다.
                - 클라이언트와 서버가 패어링 동안에 비밀키가 생성되었기 때문
            5. 클라이언트는 다시 battery Level을 요청을 합니다.
            6. 서버는 battery Level을 반환합니다.

        - **비 정장적인 재연결의 과정**
            1. 공격자가 우선 서버의 MAC addr을 복제합니다. 그러고 자신이 서버라고 다량의 브로드캐스트를 보냅니다.
            2. 클라이언트는 서버에 재 연결할 때 공격자한테 연결됩니다.
            3. 클라이언트는 서버(공격자)에게 연결 요청을 보냅니다.
            4. 연결된 후 battery Level(권한 Lv.2 필요)을 요청을 보냅니다. 이 때 요청 권한 Lv.1
            5. 서버(공격자) 클라이언트한테 거짓의 battery Level을 보냅니다. 
            6. 클라이언트는 해당 정보를 옳은 정보로 받아들입니다.

        **사전 인증하는 상품에 대한 공격 과정(해석)**

        - **정상적인 재연결의 과정**
            1. 클라이언트는 서버에 연결 요청합니다.
            2. 연결 된 후 암호화가 가능한지 확인합니다.
            3. 그 후 클라이언트트 서버에 battery Level(권한 Lv.2 필요) 요청합니다. 이 때 요청 권한 Lv.2
            4. 서버는 필요한 권한과 요청 권한을 확인 후 battery Level를 클라이언트한테 보냅니다.
            5. 클라이언트는 해당 값을 받게됩니다.

        - **비 정상적인 재연결의 과정**
            1. 공격자는 여전히 서버의 MAC addr을 복제 후 자신이 서버라고 다량의 브로드캐스트를 보냅니다.
            2. 클라이언트는 서버(공격자)에 연결 요청합니다.
            3. 연결 된 후 암호화가 가능한지 확인합니다.
            4. 서버(공격자)는 암호키가 없으므로 암호화 실패라는 에러 메시지를 보냅니다.
                - 암호화 인증이 실패되었지만 여전히 연결되므로 Lv.1(평문)으로 통신하게 됩니다.
            5. 클라이언트는 서버(공격자)에 battery Level(권한 Lv.2 필요) 정보를 요청합니다. 이 때 요청 권한 Lv.1
            6. 서버(공격자)는 클라이언트한테 거짓의 battery Level를 클라이언트한테 보냅니다.
            7. 클라이언트는 해당 값을 받게 됩니다.
- Exploit
    - None
- Paper
    - 공격 과정 영어원본
        - [https://www.usenix.org/system/files/woot20-paper21-slides-wu.pdf](https://www.usenix.org/system/files/woot20-paper21-slides-wu.pdf)
        - [https://www.youtube.com/watch?v=wIWZaSZsRc8&t=22s](https://www.youtube.com/watch?v=wIWZaSZsRc8&t=22s)
    - etc
        - [https://www.boannews.com/media/view.asp?idx=91250](https://www.boannews.com/media/view.asp?idx=91250)
        - [https://www.usenix.org/conference/woot20/presentation/wu](https://www.usenix.org/conference/woot20/presentation/wu)
        - [https://bugzilla.redhat.com/show_bug.cgi?id=1879820](https://bugzilla.redhat.com/show_bug.cgi?id=1879820)