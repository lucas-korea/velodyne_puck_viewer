# velodyne_puck_viewer
velodyne의 VLP-16 PUCK 뷰어 프로그램


벨로다인의 16ch짜리 라이다 'puck'에 대해서 알아보겠다. 정식 모델명은 VLP-16 PUCK.

이름을 보고 움찔할 수도 있다. 벨로다인이 아직 근본 없던 시절 웃자고 했던 작명이 아닐까.. 싶다 그렇지 않고서야 이런 오해의 소지가 다분한 이름이 나올 리가.

출시 당시 pcuk의 가격은 891 달러, 2018년 가격을 절반으로 내리겠다고 [공표](http://www.lumisol.co.kr/sub/media/bellow.asp?mode=view&bid=1&idx=168)했고 차량용 라이다 중에선  가격도 싸고 성능도 준수한 가성비 모델로 평가된다. (동사 회사 128ch짜리 alpha prime은 8500만 원 이하) 따라서 수많은 연구실, 대학교, 기업에서 라이다 연구개발용으로 puck을 많이 구매하였고, 이때 구매했던 장비들이 지금도 쓰이면서 가장 대중적인 라이다로 자리 잡았다. 당장 우리 센터에 내가 알고 있는 것만 5개가 넘으니 뭐..

라이다는 대학시절부터 이름은 종종 들어봤는데, 기능도 솔직히 잘 몰랐고 자율주행에 쓰이는 경우가 많다는 얘기만 막연히 듣고 (뭔가 이름도 멋있고 그래서) 관심을 가지게 됐다. 

우연찮게 취직하고 나서 라이다를 이용해 개발해야 하는 업무를 맡게 되면서 여러 가지로 다뤄볼 수 있게 되었고, 결과물을 정리하고 공유하고자 한다. 

puck에서 나오는 UDP 패킷을 분석,  point cloud 데이터로 변환한 뒤 3D 그래픽 패키지를 이용해 시각화했다.

언어는 파이썬

환경은 윈도10

![image](https://user-images.githubusercontent.com/57425658/132467450-5627bd4a-25bb-4f55-9272-c47e65d8bc05.png)*뷰어 프로그램 작동모습(사무실 전경)*


여러가지 색깔이나 크기 같은 옵션을 넣을 수 있으나, 그럴 경우 위와 같이 너무 느려지는 단점이 있다. (아래 그림과 비교하면 fps 차이가 난다) 아무래도 파이썬을 이용해 실시간 그래픽 표현은 쉬지 않은 듯하다.. 여하튼 아래 그림에서 보이는 veloview(제조사에서 직접 제공해주는 뷰어 프로그램)와 비슷한 모습까지 표현은 가능하다. 

![image](https://user-images.githubusercontent.com/57425658/132467465-173d4ce7-fb90-43a8-8e78-e4449d252ef3.png)*라이다로 촬영한 사무실 전경 (좌)veloview (우) 직접 작성한 프로그램 비교*


작동방법의 경우, **server** 프로그램을 먼저 돌려준 뒤, **client** 프로그램을 돌려주면 된다

**server** 프로그램은 라이다에서 나오는 패킷을 받아 point cloud로 변환해준 뒤 client에 socket으로 쏴준다

**clint** 프로그램은 point cloud 데이터를 받아 3D 그래픽으로 표현해준다

3d 그래픽 코드에서 로드가 많이 걸려 딜레이가 생겨 패킷을 불규칙적으로 받는 문제가 있었다. 한 프로그램 내에서 스레드로 해결하려 했는데 잘 안됐고, server-client로 프로그램 두 개를 돌려 스레드와 같은 효과를 냈다(맞나? ㅋㅋ) 

<center>
  
![image](https://user-images.githubusercontent.com/57425658/132467536-37ead8c8-6c7c-4992-a075-0dcd059656b4.png)*작동하는 과정*

![image](https://user-images.githubusercontent.com/57425658/132467558-01cc1d53-f34c-4dbe-9148-25495bbb8cb4.png)
{:.image-caption}
*프로그램 개요"
</center>

코드는 깃헙에 올려놨다 [여기](https://github.com/lucas-korea/velodyne_puck_viewer)

UDP Ethernet packets.docx는 구현하는 과정에서 패킷 구조와 패킷 내 데이터가 의미하는 걸 정리한 파일이다. 출처는 velodyne에서 제공해주는 'User Manual and Programming'이라는 이름의 매뉴얼이다. 주로 여기서 참고하긴 했지만, 다른 매뉴얼도 많고 도움이 다 되므로 다 참고하는 게 좋다. 


