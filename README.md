
# velodyne_puck_viewer
## velodyne의 VLP-16 PUCK 뷰어 프로그램

puck에서 나오는 UDP 패킷을 분석,  point cloud 데이터로 변환한 뒤 3D 그래픽 패키지를 이용해 시각화했다.

*언어는 파이썬*
*환경은 윈도10*

![그림1](https://user-images.githubusercontent.com/57425658/132470356-31537533-f514-40f4-9588-78a3fbb1f74b.gif)
<p align="center" style="color:gray">
    뷰어 프로그램 작동모습(사무실 전경)  
</p>



![그림3](https://user-images.githubusercontent.com/57425658/132470406-ed5e7c80-9246-4c6a-a7c0-ec85969c3852.gif)
<p align="center" style="color:gray">
    라이다로 촬영한 사무실 전경 (좌)veloview (우) 직접 작성한 프로그램 비교 
</p>
 
작동방법의 경우, **server** 프로그램을 먼저 돌려준 뒤, **client** 프로그램을 돌려주면 된다

**server** 프로그램은 라이다에서 나오는 패킷을 받아 point cloud로 변환해준 뒤 client에 socket으로 쏴준다

**clint** 프로그램은 point cloud 데이터를 받아 3D 그래픽으로 표현해준다

  
![그림2](https://user-images.githubusercontent.com/57425658/132470478-a7a13ee2-dd2e-44a1-b9fd-9f62d7dd61ea.gif)
<p align="center" style="color:gray">
    작동하는 과정  
</p>

![image](https://user-images.githubusercontent.com/57425658/132467558-01cc1d53-f34c-4dbe-9148-25495bbb8cb4.png)
<p align="center" style="color:gray">
    프로그램 개요
</p>

UDP Ethernet packets.docx : 패킷 구조와 패킷 내 데이터가 의미하는 걸 정리한 파일 

관련 포스팅 : https://cjung.tistory.com/15
