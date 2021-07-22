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
    - CVE-2019-16336 : cause a denial of service
    - CVE-2019-17060 : LID(Link Layer ID)가 0인 패킷 수신 시 BOF 가능
    - CVE-2019-17061 : LID(Link Layer ID)가 0인 패킷 수신 시 BOF 가능
    - CVE-2019-17517 : L2CAP 페이로드 길이 제한이 없어서 buffer overflow 가능
    - CVE-2019-17518 : buffer overflow
    - CVE-2019-17519 : buffer overflow
    - CVE-2019-17520 : cause a denial of service
    - CVE-2019-19192 : 연속된 Attribute Protocol (ATT) 요청으로 교착상태 발생
    - CVE-2019-19193
    - CVE-2019-19194
    - CVE-2019-19195
    - CVE-2019-19196
    - CVE-2020-10061
    - CVE-2020-10069
    - CVE-2020-13593
    - CVE-2020-13594
    - CVE-2020-13595
- Exploit
- Paper