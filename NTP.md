# 👨‍💻 NTP(_Network Time Protocol_)
* 네트워크로 연결되어 있는 컴퓨터들끼리 클록 시각을 동기화시키는데 사용되는 프로토콜이다.

* UDP 123번 포트 사용.

* 관리자가 직접 설정을 통해 시간을 변경할 수 있지만, 디바이스끼리의 오차가 발생할 확률이 있다.

      동일한 서버로부터 시간을 동기화 받도록 한다.

* Domain 내부의 특정 서버를 NTP서버로 구성하여 모든 디바이스들은 해당 서버로부터 시간을 동기화한다.

<img src="https://user-images.githubusercontent.com/62328584/105272979-bf480400-5bdd-11eb-94f2-95791e819d98.JPG" width="750px" height="550px"></img><br/>

* 개별 PC, 장비들은 다수의 NTP 서버와 Multicast 모드로 동작하며 시간 교정

* NTP 서버들은 상위계층 서버들과는 Client/Server 모드로 동작한다.

* 동일계층 서버들과는 대칭모드로 동작하며 시간 교정

* 최초 클럭 동기는 5~10분 동안 모두 6번의 시간 교환을 통해 이루어진다.

* 그 후 매 10분 마다 메세지 교환을 통해 클럭 수정

### **< NTP의 장점과 단점  >**

**장점**

▶데이터의 손실방지

        -각각의 PC시간을 가진 상태에서 문서의 저장, 수정을 하는 경우로 인한 데이터의 손실을 방지할 수 있다.
              
              
              
▶로그 분석효율

        -로그 분석시 서버 혹은 PC의 시간이 다르게 되면 신뢰도가 떨어진다.
        
▶예약된 작업 수행 용이

        -백업, 배치파일 등 예약된 작업을 수행할 때 PC와 서버의 시간이 다르다면 작업 수행에 문제 발생
        
**단점**

▶서버와 클라이언트가 연결되어 있어야 시간을 동기화할 수 있기 때문에 일반적으로 NTP서버는 외부 NTP서버를 참조한다.   
  때문에 보안상으로 취약한 부분이 발생할 수 있다. 이런 보안문제를 보완하기 위해 NTP서버를 직접 참조하지 않고,   
  별도의 Time Server를 이용하여 시간을 동기화한다.
  
    Time Server
    
         time.bora.net        제공 : LG U+ 
         time.nuri.net        제공 : 아이네트 호스팅 
         time.kriss.re.kr     제공 : KRISS(한국 표준 과학연구원) 
         time.nist.gov        제공 : NIST 
         time.windows.com     제공 : MS(마이크로소프트) 
         ntp.kornet.net       제공 : KT 

- - -

### **< NTP 계층구조  >**

**Stratum 0 (PRC)** : 세슘 원자시계, GPS, 표준주파수 방송국 등 (Primary Reference Clock)

**Stratum 1** : 위 Stratum 0 (PRC)에 동기화시킨 시간 서버(Primary Time Server)

    -물리적으로 PRC에 직접 연결시켜 기준 시간을 얻게되는 1차 타임 서버
    -전세계적으로 수백 이상의 공식적인 1차 타임서버가 운용 중

**Stratum 2 ~ 15** : NTP 서버를 경유할 때 마다 Stratum이 1씩 증가한다.

    -Stratum 2 부터는 계층적 트리 구조를 형성
    -상위 서버의 부하를 경감시킨다.
    -상위 NTP 서버와 동기화된 하나의 NTP 서버와 같은 Stratum에 있는 나머지 NTP 서버들은 Peer로 해서 동기화한다. 
    -사내 네트워크에는 외부 Stratum 2 서버와 연결시킨 Stratum 3 서버를 운용하여 다른 모든 사내 장비들이 이를 이용하게하면 된다.
    -보다 더 안정되게 운용하려면 직접 PRC에 연결시킨 Stratum 1을 운용할 수도 있음
    -일반 사용자들은 외부 Stratum 2 서버를 직접 이용하는 것이 유리하다.

### **< NTP 실습  >**

<img src="https://user-images.githubusercontent.com/62328584/106717581-43b96e80-6643-11eb-8d4b-c2f010ecff84.png" width="750px" height="300px"></img><br/>

<img src="https://user-images.githubusercontent.com/62328584/106825603-95580c80-66c8-11eb-8996-d789f4ff6e9e.png" width="750px" height="300px"></img><br/>

      1970-01-01 날짜로 설정되어 있음.
      ▶유닉스 시간: 유닉스 계열의 운영체제를 사용하는 컴퓨터에서 시간을 표시하는 방법이다. 1970년 1월 1일 0시 0분 0초 UTC에서부터 몇 초나 지났는지를 표시한다. 그레고리력을 따르지만 윤초는 따지지 않고 무시된다.

<img src="https://user-images.githubusercontent.com/62328584/106832229-9bec8100-66d4-11eb-950f-de8317e902d3.png" width="750px" height="400px"></img><br/>

      사용 중인 컴퓨터(192.168.0.197)를 ntp 서버로 설정 

<img src="https://user-images.githubusercontent.com/62328584/106832350-d0f8d380-66d4-11eb-8d03-d0b5518af71c.png" width="750px" height="300px"></img><br/>

<img src="https://user-images.githubusercontent.com/62328584/106847664-afa6e000-66f2-11eb-845c-f5205f524973.png" width="750px" height="250px"></img><br/>
