# BlueMirror
*유비쿼터스 무선 기술을 뒷받침하는 Bluetooth Core 및 Bluetooth Mesh 사양에서 발생한 취약점.*
1.  Bluetooth 페어링 프로세스 중에 합법적인 장치를 가장할 수 있음(impersonation attacks)
2. AuthValue의 공개를 허용 ..등
## 관련 정보
- CVE
    - CVE-2020-26555
    
        **(in.핀 페어링 프로토콜)**
        - 취약점 : Bluetooth BR/EDR PIN 페어링 절차.
        
        - 공격 : 장치의 BD_ADDR을 스푸핑하여 피해장치에 연결.
             
             ⇒  공격자는 키를 알지 못하더라도 암호화된 nonce를 반영 가능.
             
             ⇒ PIN코드를 모르는 상태에서 페어링 완료.

        - 영향 : Bluetooth 핵심 사양 버전0B ~ 5.2를 지원하는 장치.
        - 조건 : 공격 장치가 연결 및 결합 가능한 BR/EDR 레거시 페어링을 지원하는 취약한 장치의 무선 범위 내에 있어야 함.
        - 'Pin Pairing Protocol 사칭' 취약점에 대한 Bluetooth SIG 선언문

            [https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/impersonation-pin-pairing/](https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/impersonation-pin-pairing/)
            
            
    - CVE-2020-26556
        - 취약점 : AuthValue가 무작위로 선택되더라도 프로비저닝 절차에서 AuthValue를 식별할 수 있음.
        - AuthValue를 식별하는 법

            ⇒ 프로비저닝 절차 시간이 초과되기 전에 충분히 무작위 AuthValue에 대한 무차별 대입 공격.

            - 단, 프로비저닝 절차 시간이 초과되기 전에 완료되어야 하며, 이 경우 상당한 리소스가 필요할 수 있음.

        if) 공격자가 프로비저닝 절차가 시간 초과되기 전에 사용된 AuthValue를 식별할 수 있으면 ⇒ 프로비저닝 작업을 완료하고 NetKey를 얻을 수 있음.

        - '가단성 커밋' 취약점에 대한 Bluetooth SIG 선언
          [https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/malleable/](https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/malleable/)
    - CVE-2020-26557
        - 취약점 : 메시 프로비저닝 절차속, 프로비저닝을 관찰하거나 참여하는 공격자가 **(1)AuthValue가 고정된 값**을 가지거나, **(2)예측 가능**하게 선택되거나, **(3)낮은 엔트로피**로 선택(→ 경우의수 줄어듬)되는 경우.
        - 공격 : 무차별 대입 공격 가능

            +) 공격자 - AuthValue식별 + 프로비저닝 장치와 프로비저닝된 장치 모두에 인증 ⇒  MITM(manipulator-in-the-middle)공격 가능.

        - 'Bluetooth 메시 프로비저닝의 예측 가능한 AuthValue로 인해 MITM' 취약점에 대한 Bluetooth SIG 선언

            [https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/predicatable-authvalue/](https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/predicatable-authvalue/)
    - CVE-2020-26558
    
        (in. Passkey Entry Protocol)
        - 취약점 :  Bluetooth LE 및 BR/EDR 보안 페어링 과정 속, 공개 키와 인증을 반영하여 (패스키 인증 절차에서) 페어링 중에 사용된 패스키를 근처의 중간자 공격자가 식별하도록 허용 가능.
        - 공격 : 활성 공격자가 이전 장치 없이 초기 장치를 가장.
             - 공격자 : passkey 인증 절차에서, MITM역활을  수행.

                ⇒ 조작된 일련의 응답을 사용

                ⇒ 페어링 절차의 각 라운드에서  페어링 개시자가 선택한 무작위로 생성된 패스키의 각 비트 결정 가능.

        - 영향
             1. 블루투스 코어 사양 2.1~5.2
             2. BR/EDR 보안 단순 페어링, 블루투스 코어 사양 4.1~5.2
             3. BR/EDR 보안 연결 페어링, 블루투스 코어 사양 4.2~5.2

            ⇒ a,b,c에서 LE보안 연결 페어링을 지원하는 장치.

        - '암호 입력 프로토콜 사칭' 취약점에 대한 Bluetooth SIG 선언

             [https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/passkey-entry/](https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/passkey-entry/)
    
    - CVE-2020-26559
   
        (in. 메시프로비저닝 절차)
        - 취약점 : 메시 프로비저닝 절차에는 AuthValue에 대한 액세스 권한 없이 프로비저닝된 공격자가 무차별 대입 없이 AuthValue를 직접 식별할 수 있음.
        - 공격
            - AuthValue가 없는 장치가 AuthValue를 무차별 대입하지 않고도 프로비저닝을 완료 가능.
            - AuthValue를 사용하는 경우
                ⇒ 공격자는 Provisioner의 공개 키, 프로비저닝 확인 값, 임의의 값을 획득하고 프로비저닝 절차에 사용할 공개 키를 제공하여 직접 계산

        - (bluez: 커널: Bluetooth 메시 프로비저닝에서 인증값 누출)에 대한 추적 버그

            [https://bugzilla.redhat.com/show_bug.cgi?id=1969615](https://bugzilla.redhat.com/show_bug.cgi?id=1969615)

        - 'AuthValue Leak' 취약점에 대한 Bluetooth SIG 설명

             https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/authvalue-leak/
    - CVE-2020-26560


      
        (in. Bluetooth 메시 프로비저닝)
      - 취약점 : 메시 프로비저닝 절차속, Provisioner의 인증 증거를 반영하는 주변 장치가 AuthValue를 소유하지 않고 인증을 완료 가능.
      - 공격
      
          메시 프로비저닝 절차를 통해 AuthValue에 대한 지식이 없는 공격자가 프로비저닝되는 장치를 스푸핑.
          
          ⇒ 조작된 응답을 사용하여 AuthValue를 소유하고 유효한 NetKey 및 잠재적으로 AppKey 발급 가능.
      - 공격 조건
        1. 공격 장치가 Mesh Provisioner의 무선 범위 내 존재. 
        2. 무선으로 프로비전되는 장치의 ID를 스푸핑하거나 프로비져너가 제어하는 서브넷에 직접 프로비전되어야 함.
      - 참조 : 'Bluetooth Mesh Provisioning의 명의 도용 공격' 취약점에 대한 Bluetooth SIG 성명서
        [https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/impersonation-mesh/](https://www.bluetooth.com/learn-about-bluetooth/key-attributes/bluetooth-security/impersonation-mesh/)
- Exploit
- Paper
