# capstone-design_AR-manual

# 프로젝트 주제

  AR manual

---
# 제작 기간

  2023.03 - 2023.11 (4학년 1,2학기 종합설계 과목)

---
# 설계 목표

  Augmented Reality (증강현실, AR)를 이용하여 조립을 설명하는 AR Manual을 제작한다. 제품에 별도의 마커를 부착하지 않고도 AR 콘텐츠를 증강할 수 있다. 또한, 누구나 사용할 수 있도록 물체의 위치와 각도, 기울기 상관없이 제품을 카메라에 비추기만 하면 AR 콘텐츠가 증강한다. 기존의 설명서만으로는 조립이 어려웠던 소비자들은 제품에 맞춰 증강하는 3D 오브젝트를 이용한 시뮬레이션을 보고 누구나 쉽게 조립할 수 있다.

---
# 설계 배경(필요성)

  대부분의 조립이 필요한 제품에 동봉된 종이 설명서는 단순한 글과 그림으로만 표현되어 있어 조립에 어려움을 겪는 사람들이 많다. 또한, 제조사의 입장에서는 종이 자원의 낭비와 설명서 제작과 수정 등 관리에 필요한 지속적인 비용이 발생한다. 우리는 이러한 문제점을 해결하고자 AR을 이용한 사용 설명서를 제작하였다.

  시중에 있는 AR manual은 대부분 공장 기계 사용 설명이나 자동차 사용 설명서로 사용되어지고 있다.
이런 제품은 위치가 고정되어 있거나 움직이지 않기 때문에 별도의 마커를 부착하여 ar 콘텐츠를 증강한느 방식을 사용한다. 하지만 가구 조립과 같은 조립 설명서는 부품의 위치가 정해져 있지 않고 사용자가 어느 각도에서 촬영할지 모르기 때문에 별도의 마커를 이용하기엔 어렵고, 마커가 제품의 디자인을 해칠 수 있다.

![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/bffb8a87-e8ba-498f-aaf6-bb077341a1e8)
+ 공장에서 사용하는 예시. 기계 앞에 별도의 마커가 부착되어 있음. 기계는 고정

![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/279dc2b2-f7fb-4c15-a86a-969601bf9e69)
+ 관광지에서 사용하는 예시. 그림이 마커로 사용되고 있음. 표지판 고정

---
# 프로젝트 수행 도구

 + Unity
 + polycam
 + vuforia
 + C#

---
# 프로젝트 수행 과정

  ### 1) 3D 오브젝트 촬영
 polycam을 이용하여 모든 부품을 3D 오브젝트로 제작
     
 FBX파일과 OBJ 파일 2종류로 다운받아 사용
     
![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/2a4770b8-9e18-4413-a815-c954d7974d0e)
     + 제작한 3d 오브젝트

  ### 2) vuforia model target generator에서 모델 제작

   https://developer.vuforia.com/home -> vuforia 사이트
   
    > [generator 설정 과정]
    1) FBX 파일을 Vuforia의 Model Target Generator에서 불러옴. Model Up Vector에서 모델의 방향을 조절하기 위해 기준이 되는 축을 설정. 
    2) Model Unit. 모델 타겟의 크기는 실제 오브젝트의 크기와 일치해야 하므로 실제 크기와 가장 유사한 단위를 선택. 
    3) Coloring. 모델의 다양한 색은 추적 성능을 향상시키는데 도움. FBX 파일은 텍스처가 포함되어 있어 따로 하지않아도됨. 
    4) Complexity. 모델 권장 사항을 초과하는 복잡한 모델은 앱 성능에 해를 끼칠 수 있으므로 단순화 과정을 진행해야함. 이 프로젝트에서 제작한 모델은 모두 권장 사항을 초과하지 않아 단순화는 진행하지 않음. 
    5) Optimize Tracking. 모델에 대한 추적 최적화 모드를 선택하는 것. 반사성이 있고 질감이 없는 표면이 매끄러운 물체나 자동차를 모델로 만든다면 Low feature object, 대부분의 오브젝트는 default. 여기선 default를 선택. 
    6) Guide View. 모델들이 360°에서 추적할 수 있어야 하기에 Advanced View 선택. 그중 Full 360°선택. 설정 완료

완료 후 만들어진 DB를 학습시킨 후 unitypackge를 다운 받아 Unity에서 사용

  ![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/e7956dc2-c5bd-4c9d-bae1-c5a875ffabdb)
+ vuforia model target generator 설정 장면

  ### 3) Unity에서 UI 제작 및 오브젝트와 모델 배치

  ### 4) AR 콘텐츠 움직임을 위한 c# 스크립트 작성

  ### 5) QR 코드 인식 기능 제작

---
# 프로젝트 수행 결과
