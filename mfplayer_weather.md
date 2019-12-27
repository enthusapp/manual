<img src="MFPlayer Weather Event.png" />

### 날씨 정보 수집 MFPlayer 구조
기상청 제공 날씨 정보 API 는 접속 횟수, 보안키 유효기간 등의 제한이 설정되어 직접적으로 사용이 불가능합니다.
따라서 별도의 날씨 정보 수집 서버를 구축하여 MFPlayer 에서 자유롭게 날씨 정보를 사용할 수 있도록 하였습니다.

### MFPlayer
웹을 통해 다양한 정보를 활용하여 경관 조명 장치 (ex. LED Line Bar) 에 연출을 나타내는 경관 조명 제어 장치입니다.
DMX 표준 프로토콜 사용하여 조명을 제어하며, 날씨 정보에 따른 연출 선택이 가능합니다.

### Amazon Web Service
웹서버 및 IoT 구축을 위한 서비스를 제공합니다.
또한 보안 및 상시 전력에 대한 기본 인프라 제공하기 때문에 빠르고 안정적인 시스템 구축이 가능합니다.

### 날씨 정보 수집 Micro Service
Amazon Web Service 에서 제공하는 소형 서버 어플리케이션 입니다.
정해진 시간마다 정의한 동작을 수행할 수 있습니다.
기상청에서 제공하는 공공데이터 API 를 활용하여 특정시간마다 날씨 예보를 수신하여 Cloud 에 저장합니다.

### Cloud
Amazon Web Service 에서 제공하는 데이터 저장 공간입니다.
MFPlayer 에서 항시 접근 가능할 수 있으며, 보안 접근을 위한 설정도 가능합니다.

### 방화벽을 통한 Cloud 접속
MFPlayer 는 Cloud 에서 제공하는 API 를 이용하여 접속합니다.
TLS v1.2 의 암호화를 이용하여 MFPlayer 와 Cloud 사이의 통신을 보호하고, HTTP port 를 활용하기 때문에 방화벽, NAT 의 영향을 받지 않습니다.
