# Bleedingbit

**정의**

- TI사의 특정 칩을 사용한 제품에 한정된 취약점입니다.
- TI(Texas Instruments)의 Bluetooth Low Energy(BLE, 저전력 블루투스) 칩
- Texas Instruments BLE-STACK v2.2.1 for SimpleLink CC2640 and CC2650 devices
- **BLE란?**
    - Bluetooth Low Enery로 기존의 Bluetooth보다 훨씬 적은 전력을 사용하여 무선 통신 가능
    - Bluetooth4.0 이후의 버전들은 해당 용어로 대체되어 사용되기 도함
    - **통신방식**
        - Advertise(Broadcast) 모드 ⇒ 1 : N 통신 방식, 주로 디바이스가 자신의 존재를 알리거나 작은 양의 데이터 통신에 사용
        - Connection 모드 ⇒ 1 : 1 통신 방식, 디바스이간 Channel hopping 규칙을 정하고 통신하기 때문에 Advertise모드보다 안전하다.

# 관련 정보

- **CVE**
    - **CVE-2018-16986**
        - **개념**
            - 원격 공격자가 버퍼 오버플로우를 발생시키는 패킷을 보내는 것을 통하여 임의 코드를 실행 할 수 있습니다. RCE(Remote Code Execution) 취약점입니다.
        - **공격 과정**
            1. 공격자가 여러 BLE 브로드캐스트 패킷을 를 보냅니다. (advertising packets)
                - benign BLE broadcast messages 라는 키워드를 사용
                - 보안 솔루션에 걸리지 않는 패킷의 의미로 사용한 것 같습니다.
            2. 해당 패킷은 타깃의 BLE 칩 메모리에 저장됩니다. (해당 활동은 기존 보안 솔루션에 걸리지 않습니다.)
            3. 공격자는 특정 비트를 ON로 세팅하는 overflow packet을 전송합니다.
                - standard advertising packet with a subtle alteration
                - 표준 패킷에서 미묘하게 변경을한 overflow packet
                - 해당 비트는 실제로 필요한 공간보다 크게 할당하여 오버플로우를 유발합니다.
            4. 오버플로우에 의하여 공격자는 타깃 디바이스에 악성코드를 실행 또는 백도어를 설치
        - **취약점 발생하는 모델 명**
            - Cisco 1540 Aironet Series Outdoor Access Points
            - Cisco 1800i Aironet Access Points
            - Cisco 1810 Aironet Access Points
            - Cisco 1815i Aironet Access Points
            - Cisco 1815m Aironet Access Points
            - Cisco 1815w Aironet Access Points
            - Cisco 4800 Aironet Access Points
            - Meraki MR30H AP
            - Meraki MR33 AP
            - Meraki MR42E AP
            - Meraki MR53E AP
            - Meraki MR74
    - **CVE-2018-7080**
        - **개념**
            - TI 칩의 OAD 기능에 있는 취약점으로 업데이트를 위해서는 미리 설정된 암호가 필요한데, 문제는 해커가 이를 쉽게 알아낼 수 있습니다.
            - 암호를 통하여 정상적인 업데이트 트래픽을 훔쳐보거나 펌웨어를 분석할 수 있습니다.
            - 암호를 통하여 악의적인 펌웨어를 업로드하여 기기를 장악할 수 있습니다.
            - OAD(Over the Air firmware Download)로 무선 펌웨어 업데이트를 의미합니다.
        - **공격 과정**
            1. 소프트웨어 이미지에 대한 액세스 권한 획득 (ex. Aruba 웹사이트에서 다운로드)
            2. AP 하드웨어에 액세스하여 암호를 복구할 수 있습니다.
                - **AP** : Application Processor으로 CPU와 동일한 역할을 수행하는 모바일 기기 핵심 부품
        - **취약점 발생하는 모델 명**
            - Ti CC2650 0
            - Ti CC2642R 0
            - Ti CC2640R2F 0
            - Ti CC2640 0
            - Ti CC2541 0
            - Ti CC2540 0
            - Arubanetworks IAP-3xx 0
            - Arubanetworks Arubaos 8.3.0
            - Arubanetworks Arubaos 8.1.0.4
            - Arubanetworks Arubaos 8.1.0.3
            - Arubanetworks Arubaos 8.0
            - Arubanetworks Arubaos 6.5.4.2
            - Arubanetworks Arubaos 6.5.4.1
            - Arubanetworks Arubaos 6.5.4.0
            - Arubanetworks Arubaos 6.5.3.3
            - Arubanetworks Arubaos 6.5.3.2
            - Arubanetworks Arubaos 6.5.3.0
            - Arubanetworks Arubaos 6.4.4.16
            - Arubanetworks Arubaos 6.4.4.15
            - Arubanetworks Arubaos 6.4.4.0
            - Arubanetworks AP-3xx 0
            - Arubanetworks AP-203RP 0
            - Arubanetworks AP-203R 0

- **Exploit**
    - **CVE-2018-16986**
        - None
    - **CVE-2018-7080**
        - None
- **Paper**
    - [https://blog.alyac.co.kr/1965](https://blog.alyac.co.kr/1965)
    - [https://www.armis.com/research/bleedingbit/](https://www.armis.com/research/bleedingbit/)
    - [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-16986](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-16986)
    - [https://securitytracker.com/id/1042018](https://securitytracker.com/id/1042018)
    - [https://portswigger.net/daily-swig/row-brewing-over-bleedingbit-bluetooth-hack](https://portswigger.net/daily-swig/row-brewing-over-bleedingbit-bluetooth-hack)
    - [https://e2e.ti.com/support/wireless-connectivity/bluetooth-group/bluetooth/f/bluetooth-forum/742827/ble-stack-heap-overflow-issue](https://e2e.ti.com/support/wireless-connectivity/bluetooth-group/bluetooth/f/bluetooth-forum/742827/ble-stack-heap-overflow-issue)
    - [https://somenotes247.blogspot.com/2018/11/bleedingbit-le.html](https://somenotes247.blogspot.com/2018/11/bleedingbit-le.html)
    - [https://medium.com/@zoyi_product/bluetooth-low-energy-ble-84b03705ffca](https://medium.com/@zoyi_product/bluetooth-low-energy-ble-84b03705ffca)
    - [https://medium.com/@zoyi_product/bluetooth-low-energy-ble-84b03705ffca](https://medium.com/@zoyi_product/bluetooth-low-energy-ble-84b03705ffca)
    - [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-7080](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-7080)
    - [https://www.arubanetworks.com/assets/alert/ARUBA-PSA-2018-006.txt](https://www.arubanetworks.com/assets/alert/ARUBA-PSA-2018-006.txt)