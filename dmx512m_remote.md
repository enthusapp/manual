### DMX512M PLAN
DMX512M 컨트롤러는 여러개의 연출 시나리오를 저장하고 있습니다. 각 연출 시나리오는 LCD 상에 PLAN 번호로 표시됩니다. DMX512M 의 PLAN 은 제품 외관에 있는 버튼을 통해 변경하거나 제어 통신포트를 통해 제어가 가능합니다. 제어 통신포트의 설정과 PLAN 선택을 위한 프로토콜은 아래와 같습니다.

### 통신 포트
DMX512M 에는 중앙 하단에 있는 RS-485 포트와 좌측하단의 USB-Serial 포트로 구성된 두개의 제어 통신포트가 있습니다.
제어 통신 프로토콜은 동일하며, 속도가 다릅니다.

##### Remote 통신포트 설정
RS-485, **9,600 bps**, no parity, 8 bits, no flow control

##### USB-Serial 통신포트 설정
**250,000 bps**, no parity, 8 bits, no flow control

### PLAN 선택 프로토콜
아래 표에 있는 STX 에서 ETX 까지의 데이터를 DMX512M 에 입력하면 PLAN 이 변경됩니다.

| 명칭(Byte 개수) | **Code**                  | **예) PLAN 1 을 선택**     | **예) PLAN 2 을 선택**     |
| :------------: | :-----------------------: | :-----------------------: | :-----------------------: |
| STX(1)         | 0x02                      | 0x02                      | 0x02                      |
| HEADER(4)      | 0xFA FF FF F9             | 0xFA FF FF F9             | 0xFA FF FF F9             |
| PLAN Number(1) | 0 ~ plan_max              | **0x00**                  | **0x01**                  |
| FOOTER1(8)     | 0x00 00 00 00 00 00 00 01 | 0x00 00 00 00 00 00 00 01 | 0x00 00 00 00 00 00 00 01 |
| SUM(1)         | sum                       | **0xF4**                  | **0xF5**                  |
| FOOTER2(1)     | 0xF7                      | 0xF7                      | 0xF7                      |
| ETX(1)         | 0x03                      | 0x03                      | 0x03                      |

* plan_max: 100
* sum = STX + HEADER + ... + FOOTER1: STX 에서 FOOTER1 까지 바이트 단위 데이터의 합
* 예) PLAN 1 을 선택 할때의 sum: **0xF4** = 0x02 + 0xFA + 0xFF + 0xFF + 0xF9 + 0x00 ... + 0x01
* 예) PLAN 2 을 선택 할때의 sum: **0xF5** = 0x02 + 0xFA + 0xFF + 0xFF + 0xF9 + 0x01 ... + 0x01
* 예) PLAN 3 을 선택 할때의 sum: **0xF6** = 0x02 + 0xFA + 0xFF + 0xFF + 0xF9 + 0x02 ... + 0x01
* 예) PLAN 4 을 선택 할때의 sum: **0xF7** = 0x02 + 0xFA + 0xFF + 0xFF + 0xF9 + 0x03 ... + 0x01
* 예) PLAN 5 을 선택 할때의 sum: **0xF8** = 0x02 + 0xFA + 0xFF + 0xFF + 0xF9 + 0x04 ... + 0x01
* 예) PLAN 6 을 선택 할때의 sum: **0xF9** = 0x02 + 0xFA + 0xFF + 0xFF + 0xF9 + 0x05 ... + 0x01

### PLAN 선택 프로토콜 테스트 방법
LCD 창 초기 화면에서 MENU 버튼을 눌러 PLAN 번호를 확인할 수 있습니다. PLAN 선택 프로토콜 입력후에 START PLAN 번호가 변경된 것을 확인 할 수 있습니다.

![running plan 사진](./plan_change.png)

### Example Application
https://github.com/enthusapp/NodeSerial
