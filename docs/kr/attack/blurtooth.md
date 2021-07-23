# BLURtooth

---

## 정의

블루투스 4.2~5.0버전에서 구현된 CTKD(Cross-Transport Key Derivation)를 통해 해당 장치의 인증키를 훼손하거나 일부 버전에서는 완전히 덮어 쓸 수 있는 취약점

- CTKD(Cross-Transport Key Derivation)란?

    교차 전송 키 파생 CTKD은
    BLE(키보드, 마우스 등 저전력)을 BD/EDR(파일 등 고전력)으로 변경 시 페어링을 2번 하는 것이 아니라 한쪽의 키를 다른 쪽에서 사용(AES-CMAC방식을 통한 16 byte 생성)함으로써 암호화의 엔트로피를 감소시킴.

## 현황

- 블루투스 SIG에서 20년 해당 취약점을 보고
- 블루투스 5.1 이상 버전에선 CTKD 제한이 의무화되어 있기 때문에 블루투스 공격을 받지 않음

## 조건

1. 공격 대상이 BR/EDR 및 LE 전송을 모두 지원해야 함
2. 공격 대상이 CTKD 제한 의무화가 되어 있지 않은 블루투스 4.2~5.0 버전이어야 함 
3. 공격 장치가 취약한 Bluetooth 장치의 무선 범위 내에 있어야 함

## 관련 정보

- CVE

    [CVE-2020-15802](https://nvd.nist.gov/vuln/detail/CVE-2020-15802)

- Exploit
    - None
- Paper
    - mitm(중간자 공격) 가능함을 증명 논문
        - [https://arxiv.org/ftp/arxiv/papers/1203/1203.4649.pdf](https://arxiv.org/ftp/arxiv/papers/1203/1203.4649.pdf)
    - Just Works를 통한 페어링
        - [https://www.bluetooth.com/blog/bluetooth-pairing-part-4/](https://www.bluetooth.com/blog/bluetooth-pairing-part-4/)

- etc
    - chromecast등의 고전력을 smartwatch급의 저전력으로 낮출 수 있음
        - [https://gizmodo.com/bluetooth-unveils-its-latest-security-issue-with-no-se-1845013709](https://gizmodo.com/bluetooth-unveils-its-latest-security-issue-with-no-se-1845013709)
