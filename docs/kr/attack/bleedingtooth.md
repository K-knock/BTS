# BleedingTooth
: Linux Bluetooth 하위 시스템의 일련의 제로 클릭 취약점으로, 근거리에서 인증되지 않은 원격 공격자가 취약한 장치에서 커널 권한으로 임의의 코드를 실행할 수 있음.

- 리눅스 블루투스 프로토콜인 BlueZ에서 발견된 취약점.

    <span style="color:gray">(#BlueZ : 리눅스 블루투스 장비를 프로그래밍하기 위한 라이브러리. BlueZ를 통해 통신장비를 스캐닝)</span>

- '블루투스 전파가 닿을 만 한 거리'에 공격자와 피해자가 피해자의 블루투스 주소를 알아낼 경우 악성 l2cap 패킷을 보냄으로써 디도스 공격을 하거나 커널 권한을 얻을 수 있음.
- 완화하는 방법
    1. Linux 커널에서 커널 모듈을 블랙리스트에 올려 Bluetooth 기능을 비활성화.
    2. 하드웨어 내에서 또는 BIOS 수준에서 Bluetooth를 비활성화 -> 커널이 Bluetooth 하드웨어가 시스템에 있는지 감지할 수 없기 때문에 효과적인 완화를 제공

## 관련 정보
- CVE
   - ***CVE-2020-12351***<br> 
        : blueZ의 부적절한 입력유효성검사로 인해 인증되지 않은 사용자가 잠재적으로 인접 액세스를 통해 권한상승 가능.
        - 취약한 패키지<br>
            LINUX(PTS) v-4.9.228-1
        
    - ***CVE-2020-12352***<br>
      : blueZ의 부적절한 액세스 제어로 인해 인증되지 않은 사용자가 잠재적으로 인접 액세스를 통해 정보공개를 활성화할 수 있음.
      - 인증 과정을 통과하지 않은 사용자가 장비 근처에서 정보에 접근할 수 있게 해준다. 사용자의 블루투스 주소(BD_ADDR)를 알고 있으면 커널 스택 정보를 취득할 수 있게 된다.
 
    - ***CVE-2020-24490***<br>
      : BlueZ의 부적절한 버퍼 제한으로 인해 인증되지 않은 사용자가 잠재적으로 인접 액세스를 통해 서비스 거부를 활성화할 수 있습니다.<br>
      (인증 과정을 통과하지 않은 사용자가 장비 근처에서 디도스 공격을 할 수 있게 해준다. 경우에 따라 임의 코드 실행 공격도 가능하게 된다.)
      - 기술 <br>
        Linux 커널의 Bluetooth HCI 이벤트 패킷파서가 특정 크기의 이벤트광고를 제대로 처리하지 않음.<br> 
              ⇒ 힙 기반의 버퍼오버플로 발생<br>
              ⇒ 인접 범위의 원격 공격자는 이를 사용해 서비스거부를 일으키거나 임의코드를 실행할 수 있음.<br>
      - 이 취약점의 가장 큰 위협은 기밀성, 무결성 및 시스템 가용성이 있음.
      - 영향 : BlueZ를 지원하는 모든 Linux 커널 버전
          - 취약 ⇒ 리눅스(PTS) - 4.9.228-1
          - fixed ⇒ 리눅스(PTS) - 4.9.272-2, 4.19.194-1, 4.19.194-3, 5.10.40-1, 5.10.46-2

    - ***CVE-2020-25661***<br>
      : Linux 커널의 Bluetooth 구현이 A2MP CID로 L2CAP 패킷을 처리하는 방식에서 발견. 이 결함으로 인해 인접 범위에 있는 원격 공격자가 시스템을 충돌시켜 서비스 거부를 일으키거나 특수하게 조작된 L2CAP 패킷을 전송하여 시스템에서 잠재적으로 임의 코드를 실행할 수 있음.

      - 영향
        : Red Hat Enterprise Linux 8.3 GA 커널 버전 kernel-4.18.0-240.el8(및 커널 rt-4.18.0-240.rt7과 같은 이 릴리스에서 파생된 모든 커널)
      - A2MP의 스택 기반 정보 누출
          <br>[https://github.com/google/security-research/security/advisories/GHSA-7mh3-gq28-gfrq]                  
    - ***CVE-2020-25662***<br>
      : Linux 커널의 Bluetooth 스택 구현이 특정 AMP 패킷을 처리할 때 스택 메모리 초기화를 처리하는 방식에서 발견. 이 결함은 인접 범위에 있는 원격 공격자가 특수하게 조작된 AMP 패킷을 전송하여 시스템의 스택 메모리의 작은 부분을 누출할 수 있도록 함.
      - 영향 : Linux 8.3 GA kermels
      - 이 문제에 대한 커널 추적 버그 생성 ->
        [https://bugzilla.redhat.com/show_bug.cgi?id=1888440]
      - 패치 관련 : A2MP : 모든 멤버가 초기화 되지 않는 문제 수정패치 
      <br>-> #[https://lore.kernel.org/linux-bluetooth/20200806181714.3216076-1-luiz.dentz@gmail.com/#r]
      
- Exploit
  - Linux 커널 5.4 bleedingTooth 원격 코드 실행 (Linux 커널 버전 5.4 BleedingTooth 블루투스 제로 클릭 개념 증명 원격 코드 실행 익스플로잇 – 12351,12352)<br>
   ⇒ [https://packetstormsecurity.com/files/162131/Linux-Kernel-5.4-BleedingTooth-Remote-Code-Execution.html](https://packetstormsecurity.com/files/162131/Linux-Kernel-5.4-BleedingTooth-Remote-Code-Execution.html)
- Paper
   - https://packetstormsecurity.com/files/161229/Kernel-Live-Patch-Security-Notice-LSN-0074-1.html
