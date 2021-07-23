# KNOB(Key Negotiation Of Buletooth)

---

## 정의

공격자는 Man in The Middle 공격을 통해 요청을 중간에 낚아채서 암호화의 Entropy를 1로 낮춤으로써 손쉬운 무차별 공격을 가능하게 하는 취약점.

- 암호화키 엔트로피란?

    암호화키는 Seed라고 불리는 난수(Random Number)를 가지고 만들어지는데,
    이때 seed가 예측되기 어려울수록 그 암호의 엔트로피가 높다고 함.

    - Entropy가 1 byte라면 2^8의 경우의 수를 가지고,
    - Entropy가 16 byte 이면 2^128의 경우의 수를 가짐.

## 현황

- 2019년 제보됨
- 블루투스 5.1이하 버전 이후로 Entropy를 1~16이 아닌, 7~16으로 변경하는 방식으로 패치가 됨.

## 조건

1. 블루투스 디바이스끼리의 연결방식이 BR/EDR이어야 함.
2. 서로 간의 블루투스 디바이스는 이 결함에 취약한 블루투스 5.1 버전 이하여야 함.
3. 공격자는 페어링 동안 디바이스 간에 다이렉트로 전송을 막을 수 있어야 하고 공격은 페어링된 디바이스 연결의 협상 또는 재협상 동안 수행되야 함.

## 관련 정보

- CVE
    - [CVE-2019-950](https://nvd.nist.gov/vuln/detail/CVE-2019-9506)
- Exploit
    - None
- Paper
    - knob 정의 및 시행 관련 논문
        - [https://francozappa.github.io/publication/knob/slides.pdf](https://francozappa.github.io/publication/knob/slides.pdf)
- etc
    - Intel, Broadcom, Apple, Qualcomm등의 제조업체 블루투스 칩 취약
        - [https://www.usenix.org/system/files/sec19-antonioli.pdf](https://www.usenix.org/system/files/sec19-antonioli.pdf)
    - USENIX Security에서 19년 발표한 KNOB 공격 프레젠테이션의 비디오
        - [https://youtu.be/v9Xg9XcnNh0](https://youtu.be/v9Xg9XcnNh0)
