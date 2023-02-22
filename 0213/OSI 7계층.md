# OSI 7계층(Open Systems Interconnection Reference Model)

여러 통신장비간 연결을 보장하기 위해 국제표준기구 iso가 발표한 네트워크 모델

네트워크 프로토콜이 통신을 하는 과정을 7단계로 나눈 것

OSI 7 계층을 나눈 이유는 통신이 일어나는 과정을 단계별로 알 수 있고, 7단계 중 특정한 곳에 이상이 생기면 다른 단계와 독립적으로 그 단계만 수정할 수 있기 때문



## 1계층 - 물리계층(Physical Layer)

![물리적 계층: 전송 케이블, 비트스트림, 수신 케이블](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1HQ1W5P4XAinIdM37DTu4U/900ccdceda346baf03ce8b9f977d2974/osi_model_physical_layer_1.png)

데이터 단위 : bit

OSI 가장 아래에 있는 계층으로 실제로 장치들을 연결하기 위한 물리적 장비가 포함된 계층

데이터를 비트 스트림으로 전기신호로 변환



## 2계층 - 데이터 링크 계층(Data Link Layer)

![데이터 연결 계층](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3MR4mPOwaos80t1annw7BG/8ea1c59ccfa1baf6e9738773daa30450/2-data-link-layer.svg)

데이터 단위 : frame

물리적인 네트워크를 통해 두 지점간의 신뢰성있는 전송을 보장하는 층

여기서 각 지점을 분리하는 방법으로는 모든 장치마다 1개씩 가지고 고유한 물리적인 주소인 맥주소를 활용

**동일한 네트워크** 내에서의 전송을 담당

오류제어와 흐름제어를 제공




## 3계층 - 네트워크 계층(Network Layer)

![네트워크 계층: 패킷 생성, 전송, 패킷 어셈블리](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3g2Hv0frHsql5SFauJL5EG/d8cede7b6a780e63413bd86de9eee7f9/osi_model_network_layer_3.png)

데이터 단위 : packet

**서로 다른 네트워크** 간 전송을 용이하게 하는 역할

네트워크의 여러개의 지점을 거칠 때 경로를 찾아 줌

데이터 전송 단위 패킷 > 패킷 단위로 데이터를 보내는 역할

라우터는 컴퓨터 네트워크 간의 데이터 패킷을 전송하는 네트워치 장치.

호스트에 IP번호를 부여하고 해당 도착지의 IP까지 최적의 경로를 찾아주는 것을 라우팅이라 함.

이때 경로를 찾을 때 IP 주소를 이용



## 4계층 - 전송계층(Transport Layer)

![전송 계층: 세그먼트, 전송, 리어셈블리](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3OlO75NcADGL3SmEADFDqd/723b8c7639c4e2e6b4febcbe7fd36e0e/osi_model_transport_layer_4.png)데이터 단위 : segment 

양 끝단의 사용자들이 송수신에 있어 신뢰성을 보장

서로 다른 두 네트워크간의 전송을 담당하는 계층

이 계층에서 신뢰성을 보장하여 상위 계층들이 전달의 유효성이나 효율성을 생각하지 않도록 부담을 덜어줌

세그멘테이션, 흐름제어, 오류제어 등을 제공

세그멘테이션 : 상위 계층의 데이터를 세그먼트라는 단위로 나누는 것을 의미 

흐름제어 : 데이터 전송량이 다른 두 기기에서 데이터를 주고 받을 때 데이터 전송량을 조절하는 것

오류제어 : 데이터 송신 시 손실이 없는지, 오류가 있다면 해당 데이터를 다시 전송




가장 많이 사용하는 전송계층이 TCP

TCP

- 신뢰성있는 전송을 보장
  - 패킷 손실, 중복, 순서를 보장
  - 하위계층인 IP계층의 신뢰성없는 서비스에 대해 신뢰성을 제공

UDP

- 신뢰성 없음
  - 보내고 나면 책임을 지지 않음
- 속도가 빠름 - 스트리밍 서비스에 적합







## 5계층 - 세션계층(Session Layer)

![세션 계층: 통신 세션](https://cf-assets.www.cloudflare.com/slt3lc6tev37/29mRrgK22AqJVlg2MMlD86/34d8f4071b6cc0d3b03c93f55e4d89b7/osi_model_session_layer_5.png)

양 끝단의 프로세스가 통신을 관리하기 위한 방법을 제공

통신관리 : 동기화나 TCP/IP의 세션설정

세션을 열고 닫고를 제공하는 메커니즘의 계층

세션복구 지원 - 체크포인드를 통해 동기화



## 6계층 - 표현계층(Presentation Layer)

![프레젠테이션 계층: 암호화, 압축, 번역](https://cf-assets.www.cloudflare.com/slt3lc6tev37/19L86neKKT8srUkOSe4rf7/ff4c91c94a1790651df7b48433913f59/osi_model_presentation_layer_6.png)

인코딩 및 데이터의  형식 차이를 조절

데이터의 변환, 압축, 암호과가 이루어지는 계층

표현되는 방법을 다루는 층

서로 다은 통신기기간 다른 인코딩을 사용할 수 있기때문에 해당 계층에서 데이터 변환이 이루어짐



## 7계층 - 어플리케이션 계층(Application Layer)

![애플리케이션 계층: 요청을 받아 필요한 형식으로 반환되는 콘텐츠](https://cf-assets.www.cloudflare.com/slt3lc6tev37/2rcDKpr4WLqoyAZ7GDKkyJ/7cab96402de7ac5465b86e617da3da4e/osi_model_application_layer_7.png)

응용프로세스를 직접 사용하여 직접적인 응용 서비스를 수행

http FTPm SMTP,Telnet 등의 프로토콜이 속한 계층







![img](https://t1.daumcdn.net/cfile/tistory/995EFF355B74179035)

# TCP/IP 프로토콜(Transmission Control Protocol/Internet Protocol)

미국 국방성에서 개발한 프로토콜 - OSI 7계층보다 개발 시기가 앞서

일반적으로 4계층으로 이루어짐.

계층을 묶는 기준에 차이는 있지만 OSI 7계층과 흡사한 구조를 가지고 있고 별개라고 생각할 수 없을만큼 밀접한 관계를 가짐 - OSI 계층 전체에서의 기능적인 표준에 기존의 TCP/IP 개념이 들어가 있음

둘 다  패킷을 이용해 통신하고 계층 구조를 가짐