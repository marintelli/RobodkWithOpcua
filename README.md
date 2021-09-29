# RobodkWithOpcua
RoboDk 에 연동할 OPC UA Client Demo
# 주요 코드 ->  [시연 영상 바로가기](https://youtu.be/6orZOy-wD4U)

![](https://images.velog.io/images/marintelli/post/1f5a22e7-ce44-4b07-b184-523acb504110/image.png)



![](https://images.velog.io/images/marintelli/post/9a769637-df2e-4dc7-935f-77b0698f9cb5/image.png)


# WHAT IS RoBoDK? 로보DK 가 뭔데? 

로보DK는 캐나다에 있는 ETS 대학(ETS University)의 '코로(CoRo)'라는 실험실에서 분사한 기업으로 지난 2015년 설립됐다. 국제적으로 계속해서 성장 중이며 합리적인 가격으로 고급 산업용 로봇 시뮬레이션 소프트웨어를 공급하는 데 힘쓰고 있습니다.

RoboDK는 시뮬레이션과 오프라인 프로그래밍을 위한 소프트웨어이며, 오프라인 프로그래밍은 특정 로봇 팔과 제어기에 사용하기 위한 로봇 프로그램을 만들고, 시뮬레이션하고 작업 코드를 만드는 일을 합니다. RoboDK는 윈도우 버전뿐만 아니라 맥, 리눅스, 안드로이드 버전까지 있다고 합니다. 

# Features

* (심지어 라즈베이 파이에도 설치 가능한) 크로스 플랫폼 시뮬레이션 환경을 제공
![](https://images.velog.io/images/marintelli/post/6e0a87f3-00d1-4fcd-811d-071e03d1ab2e/image.png)
* 저렴한 가격의 오픈소스 기반

![](https://images.velog.io/images/marintelli/post/65cc7c29-9145-408b-b7cb-6aabda438783/image.png)

* 현대 언어 Python, Matlab, 비쥬얼스튜디오(C# API)등 현대적인 언어  사용 가능  
->로봇제조사들은 주요한 프로그래밍언어를 바꾸는 것을 극도로 조심한다. C++ 이후의 현대적인 언어는 로보틱스 프로그래밍에서 사용되지 않는 경향이 강하다.
![](https://images.velog.io/images/marintelli/post/b7bb230a-ac6f-470f-a134-db6f1981771d/image.png)

*  OPC-UA 실제 로봇과 통신하기 위해 OPC-UA플러그인으로 서버와 클라이언트 까지도 제공합니다. 
![](https://images.velog.io/images/marintelli/post/6f269ec8-0642-4d1d-89c8-4a7a59b09ad0/image.png)

# Robo DK 에서 OPC UA 테스트를 해보도록 하겠습니다. 


## RoboDK에서 OPC UA 서버환경 설정


![](https://images.velog.io/images/marintelli/post/b473957d-791c-4122-ba56-a8c48d35804d/image.png)

Tool - plugin - opcUA를 체크 

![](https://images.velog.io/images/marintelli/post/1de38ea5-26c3-4402-ae91-db4a805535b5/image.png)

 네비게이션 바의 OPC - UA 서버로드를 켜줍니다. 

![](https://images.velog.io/images/marintelli/post/a74a6d97-d670-408d-ad7f-f29f47584ca4/image.png)

구글링 키워드 "UA EXPERT" 검색하여 ua expert를 다운받습니다. 

![](https://images.velog.io/images/marintelli/post/1d3693e4-1646-4107-b659-f103a99f1d16/image.png)

ua expert를 실행 시킨뒤 servers 우클릭 "add" 창을 띄웁니다. 
![](https://images.velog.io/images/marintelli/post/510ef73e-968a-46f7-90f1-5bd9a06a0d2a/image.png)

또 다시 locaL을 우클릭하여서, Add server 창으로 들어간다. 
![](https://images.velog.io/images/marintelli/post/30d4d45c-c020-4104-8b50-29a3fe91fa72/image.png)

Edit URL을 클릭하여서 

![](https://images.velog.io/images/marintelli/post/591b31be-7181-4187-93e9-40284a36eb17/image.png)

처음 ROBODK에서 opc ua setting 시에 "opc.tcp://localhost:4840" 을 입력해줍니다. 

![](https://images.velog.io/images/marintelli/post/23225dd8-047f-43e8-a4c9-92abc70c1555/image.png)

추가된 서버를 '우클릭', 'Connect' 버튼을 클릭하면 다음과 같이 OPC-UA 통신을 위한 준비가 완료 됩니다. 

![](https://images.velog.io/images/marintelli/post/3317bbf2-025a-4aa3-9720-7148bfd02a57/image.png)
OPCUA 데이터의 구조는 [OPCUA 데이터의 구조 자세히 알아보기 링크 ](https://red-nose-cousin.tistory.com/4)를 참고할 수 있습니다.


![](https://images.velog.io/images/marintelli/post/b6d29b2d-9852-4f02-9f15-522cf30402a4/image.png)

RoboDK의 경우는 getJointStr과 setJointStr을의 메서드 콜을 통해서 


![](https://images.velog.io/images/marintelli/post/7c62b729-ecbf-4aa6-b0df-64936ac03585/image.png)

하이라이트된 축의 값을 받아오기도, 설정하기도 하는 구조로 되어있습니다. 


## UA CIENT에서 현재 RoboDK 의 로봇 6축값 가져오기
![](https://images.velog.io/images/marintelli/post/3f038fa7-067e-444a-8e4a-a40eb6df4c9d/image.png)

로보DK의 현재 6축 값을 가져오기 위해서는 getJointStr을 우클릭 한 후에

![](https://images.velog.io/images/marintelli/post/4b70da72-e7b6-4252-84e8-fb85a5df31a7/image.png)

Robot Name 란에 로봇 이름을 입력하고 CAll 하면 
![](https://images.velog.io/images/marintelli/post/307d9760-63a3-42bd-b29d-cb157b6c9460/image.png)

로봇의 6축에 대한 축값들을 가져올 수 있습니다. 

## UA CLINET 에서 ROBODK의 로봇 6축 설정하기

![](https://images.velog.io/images/marintelli/post/1005161e-434b-4380-aa28-923a36295ad3/image.png)

setJointsStr 을 우클릭하여서 Call 클릭합니다.
![](https://images.velog.io/images/marintelli/post/b079de01-25f7-47d7-8b13-33210d8df030/image.png)

Robot name 에 ROBODK의 로봇 이름과
Joints 란에는 원하는 축값들을 입력한 후 'Call버튼을 클릭하면

![](https://images.velog.io/images/marintelli/post/31f5e44c-6612-4d63-8a03-7f0cfa90bc41/image.png)

RoboDK에 해당 값이 전달이 됩니다.

# 결론

![](https://images.velog.io/images/marintelli/post/e59e0ede-3af4-40af-ada3-7903572a580f/image.png)

ROBODK의 OPC UA date model은 getJointsSTr setJointsStr의 메소드를 통해서 통신합니다. 

---
