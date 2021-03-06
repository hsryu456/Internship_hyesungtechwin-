# 🔧 NMS(_Network Management System_)
* 컴퓨터 네트워크 또는 네트워크들을 모니터링하고 관리하는데 사용되는 하드웨어와 소프트웨어의 조합을 총칭한다.

    네트워크 상의 장비를 모니터링하고 이슈에 대한 발빠른 처리를 위해서 트래픽을 실시간으로 저장하고 가시적인 도표 등으로 보여주는 관리 솔루션

* 개별 네트워크 구성요소(Network Element:NE) 들은 구성요소 관리시스템(Element Management System)에 의해 관리된다.

* 관리 작업에는 네트워크 인벤토리의 발견, 디바이스 상태 모니터링, 시스템 성능에 영향을 미치는 상태에 대한 경고, 문제의 식별 및 출처의 파악과 함께 가능한 솔루션의 제공 등이 있다.

* NMS 에서는 이러한 작업을 수행하기 위해 다양한 프로토콜을 사용한다. 예를 들어, **SNMP 프로토콜**은 네트워크 계층의 디바이스로부터 정보를 수집하는데 사용된다.

    SNMP 패킷을 전송하여 장비들이 문제가 없는지 체크

* NMS에서 관리하는 모니터링 항목은 다음과 같다.

    -CPU: CPU가 급증할 경우 장비 접근불가 및 비정상 작동의 가능성이 있다.   
    -Memory: 과도한 메모리 점유, 누수 등으로 비정상 작동하는 경우 이벤트 탐지 누락 가능성있음   
    -Disk: 디스크 사용량 초과로 인한 로그 적재 불가 가능성   
    -Traffic: 트래픽 급증, 급감에 따른 서비스 장애 가능성

* Cacti(오픈소스), MRTG(오픈소스), PRTG(상용 툴) 등이 주로 쓰인다.

<img src="https://user-images.githubusercontent.com/62328584/105142514-0aaad580-5b3e-11eb-9122-6b8438661c2a.JPG" width="400px" height="400px"></img><br/>