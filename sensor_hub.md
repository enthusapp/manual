# SENSOR HUB
### 기본 동작
* 센서에 감지되는것이 없을 경우 DMX512M 가 PLAN1 로 설정됨
* 센서1 에 인체가 감지되면 DMX512 가 PLAN2 로 설정됨
* 센서2 에 인체가 감지되면 DMX512 가 PLAN3 로 설정됨
* 센서3 에 인체가 감지되면 DMX512 가 PLAN4 로 설정됨
* 센서1 ~ 3 에 인체가 감지되어 PLAN2 ~ 4 로 설정된 다음에 30 초가 지난 다음 또 다시 센서1 ~ 3 에 인체가 감지되면 PLAN2 ~ 4 로 다시 설정됨
* 센서1 ~ 3 에 인체가 감지되어 PLAN2 ~ 4 로 설정된 다음에 30 초가 지난 다음 센서가 감지되지 않으면 PLAN 1 로 다시 설정됨
* 센서1 ~ 3 에 인체가 감지되어 PLAN2 ~ 4 로 설정된 다음에 30 초 동안은 다른 센서의 입력을 무시함

### 추가 상세 동작
* 전원이 인가되면 센서 동작과 상관없이 DMX512M 가 PLAN1 로 설정됨
* 전원 인가 후 센서의 오동작을 막기위해 30 초동안은 센서의 감지를 무시함
* SENSOR HUB 의 상태 LED 가 센서 감지에 따라 다르게 표시됨
  * 센서 감지가 없을 경우: 빠르게 깜빡임
  * 센서1 감지: 빠르게 깜빡임 + 느리게 1 번 깜빡임
  * 센서2 감지: 빠르게 깜빡임 + 느리게 2 번 깜빡임
  * 센서3 감지: 빠르게 깜빡임 + 느리게 3 번 깜빡임
  
