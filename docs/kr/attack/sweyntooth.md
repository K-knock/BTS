# SweynTooth
#### BLE, LE ( Bluetooth low Energy )

	동력이나 에너지원, 통신 기능이 뛰어나지 않은 사물인터넷 장비들의 배터리 절약을 위해 고안된 기술

***
*SoC (System on a Chip) 제조사들은 위 기술을 구현하기 위해 BLE 소프트웨어 개발 키트를 운영하고 있는데,   
여기서 나온 취약점을 SwenynTooth 취약점이라고 부른다.*   
> *Harald Bluetooth*왕의 아들 *Sweyn Forkbeard*의 이름을 딴 것 
>      
> batch #1과 batch #2, 두 종류의 취약점 존재   
***
### batch #1

> **BLE SDK 자체의 결함**에 의해 발생 
> - 거의 모든 vendor들이 이미 펌웨어 업데이트 패치를 통해 보완함   
>   
> **취약점** : 12가지   
>   
> **공격 방식**   
> > *deadlocks* / *crashes* / *buffer overflows* / *completely bypass 	security*   
>   
> **vendor 목록**   
> - *Texas Instruments*
> - *NXP*
> - *Cypress*
> - *Dialog Semiconductors*
> - *Microchip*
> - *STMicroelectronics*
> - *Telink Semiconductor*   
***
### batch #2

> **affected BLE stacks**에 의해 발생    
> - 이를 사용하지 않도록 강하게 권고하고 있지만,   
이러한 내용이 잘 지켜지고 있는지에 대한 조사는 아직 이루어지지 않았음   
>   
> **취약점** : 5가지   
>   
> **공격 방식**   
> > deadlocks / crashes / partially bypass security   
>   
> **vendor 목록**   
> - *Texas Instruments*
> - *Espressif, Microchip*
> - *ON Semiconductor*
> - *Zephyr Bluetooth Stack*   
***

	crash
	 - 특정코드 또는 메모리 변조에 의해 발생 (bof)
	 - 보통, 자동으로 재시작 된다. (제품에 따라 다를 수 있다.)
	Deadlock 
	 - 단순히 BLE 연결에 영향을 준다.
	 - 보통 유저코드와 SDK 펌웨어 사이의 동기화 과정에서 일어난다.
	 - 보통, 정상적인 BLE 연결을 위해 사용자가 기기를 재부팅해야 한다.
	Security Bypass 
	 - 가장 치명적이다.
	 - 기기의 동작/서비스에 대한 임의의 읽기/쓰기 권한획득 가능

## 관련 정보
- CVE
	- CVE-2019-16336 
	> 사이프레스 PSoC4/6 BLE에서 발견된 ‘링크 레이어 길이 오버플로우(Link Layer Length Overflow)’ 취약점.    
	> 디도스와 원격 명령 실행 유발      
	- CVE-2019-17060 
	> NXP 장비에서 발견된 링크 레이어 마비 오류     
	> LID(Link Layer ID)가 0인 패킷 수신 시 BOF 가능     
	- CVE-2019-17061 
	> 사이프레스 장비에서 발견된 링크 레이어 마비 오류   
	> LID(Link Layer ID)가 0인 패킷 수신 시 BOF 가능        
	- CVE-2019-17517 
	> 소프트웨어 개발 키트 5.0.4 및 이하 버전이 탑재된 다이얼로그 DA14580 장비에서 발견된 취약점.   
	> 디도스 및 시스템 마비 유발   
	> L2CAP 페이로드 길이 제한이 없어서 buffer overflow 가능   
	- CVE-2019-17518 
 	> 다이얼로그 DA14680 장비에서 발견된 사일런트 길이 오버플로우(Silent Length Overflow) 취약점   
	> 디도스 및 시스템 마비 유발     
	- CVE-2019-17519 : NXP KW41Z 3.40 SDK에서 발견된 ‘링크 레이어 길이 오버플로우’ 취약점.   
	> 디도스와 원격 명령 실행 유발      
	- CVE-2019-17520 
	> 텍사스 인스트루먼트 CC2640R2 BLE-STACK-SDK에서 발견된 ‘돌발 공공 키 마비’ 취약점.    
	> 디도스 및 시스템 재가동 유발   
	> cause a denial of service   
	- CVE-2019-19192 
	> ST마이크로일렉트로닉스 WB55 SDK 1.3.0 및 이전 버전에서 발견된 취약점.       
	> 연속된 Attribute Protocol (ATT) 요청으로 교착상태 발생   
	> 장비를 완전 마비 상태로 만듦   
	- CVE-2019-19193 
	> 텍사스 인스트루먼트 CC2640R2 BLE-STACK과 CC2540 SDK에서 발견된 ‘부적절한 연결 요청’ 취약점   
	> 디도스 유발     
	> Invalid L2CAP Fragment   
	- CVE-2019-19194 
	> 텔링크 세미컨덕터의 SMP가 구현된 장비들에서 발견된 취약점.      
	> BLE 제품의 보안 장치를 완전히 회피하도록 함    
	> Zero LTK Installation   
	- CVE-2019-19195  
	> 마이크로칩 ATMSAMB11 BluSDK Smart 6.2 및 이전 버전에서 발견된 ‘부적절한 L2CAP 분할’ 취약점.   
	> 장비 원격 재가동 유발   
	- CVE-2019-19196 
	>텔링크 세미컨덕터의 BLE SDK에 영향을 주는 키 크기 오버플로우 취약점.
	> 장비를 완전 마비 상태로 만듦   
	- CVE-2020-10061 : Invalid Sequence Memory Corruption
 	- CVE-2020-10069 : Invalid Channel Map
 	- CVE-2020-13593 : DHCheck Skip
 	- CVE-2020-13594 : Invalid Channel Map*
 	- CVE-2020-13595   
   
	[각 취약점에 대한 기술적인 내용들](https://asset-group.github.io/disclosures/sweyntooth/disclosure.html#technical-description, "link")
***
- 스웨인투스 취약점들이 일으킬 수 있는 현상
1. 장비의 원격 기능 마비
2. BLE 통신 해제 및 마비
3. 보안 장치 우회
4. 장비 내 기능 및 서비스에 대한 임의 접근(읽기/쓰기)   
     
	**주로 2018~2019년에 출시된 IoT 장비들에 영향을 준다.**
***   
- Exploit
***
- Paper   
http://www.ti.com/lit/pdf/swra676      
https://asset-group.github.io/disclosures/sweyntooth/   
https://e2e.ti.com/support/wireless-connectivity/bluetooth/f/538/t/881879   