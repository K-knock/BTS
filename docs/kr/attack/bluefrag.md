# BlueFrag

**정의**

- Android 운영체제의 Bluetooth에서의 원격코드 실행 취약점입니다.
- **자세한 설명**
packet_fragmenter.cc의 reassemble_and_dispatch에서 잘못된 범위 계산으로 인해 범위를 벗어난 쓰기(overflow로 인한 overwirte)가 가능하여, 이로 인해 추가 실행 권한이 필요 없이 Bluetooth를 통해 원격 코드가 실행될 수 있는 취약점입니다. (악용에는 블루투스 사용자의 상호 작용이 필요하지 않습니다.)

# 관련 정보

- **CVE**
    - **CVE-2020-0022**
        - **설명**
        packet_fragmenter.cc의 reassemble_and_dispatch에서 잘못된 범위 계산으로 인해 범위를 벗어난 쓰기가 가능합니다. 이로 인해 추가 실행 권한이 필요 없이 Bluetooth를 통해 원격 코드가 실행될 수 있습니다. 악용에는 사용자 상호 작용이 필요하지 않습니다.
        - **취약점이 적용되는 모델**
            - 안드로이드 8.0 ~ 9.0 은 취약점을 악용한 공격이 가능.
            - 안드로이드 10 은 기술적인 이유로 취약점을 이용한 공격은 불가능, 그러나 취약점은 존재.
            - 안드로이드 8.0 이하 버전은 영향을 받을 수 있지만 평가되지 않았음.
        - **Exploit Code**
            1. [https://github.com/kimbo/bluefrag](https://github.com/kimbo/bluefrag) 
            2. [https://insinuator.net/2020/04/cve-2020-0022-an-android-8-0-9-0-bluetooth-zero-click-rce-bluefrag/](https://insinuator.net/2020/04/cve-2020-0022-an-android-8-0-9-0-bluetooth-zero-click-rce-bluefrag/) 
            3. [https://github.com/marcinguy/CVE-2020-0022](https://github.com/marcinguy/CVE-2020-0022)
            4. [https://github.com/Polo35/CVE-2020-0022](https://github.com/Polo35/CVE-2020-0022) 
            5. [https://packetstormsecurity.com/files/156891/Android-Bluetooth-Remote-Denial-Of-Service.html](https://packetstormsecurity.com/files/156891/Android-Bluetooth-Remote-Denial-Of-Service.html)

- paper
1. [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-0022](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-0022)
2. [https://insinuator.net/2020/02/critical-bluetooth-vulnerability-in-android-cve-2020-0022/](https://insinuator.net/2020/02/critical-bluetooth-vulnerability-in-android-cve-2020-0022/)
