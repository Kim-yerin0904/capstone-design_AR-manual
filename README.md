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
  Unity에서 조립 화면의 UI를 제작. 의자의 조립 단계는 총 11단계. 각 조립 단계별로 Scene을 만들어 관리.
  
  ![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/ff881961-1ddf-4cc3-8804-7d34dc06907a)
+ Unity에서 제작한 2단계의 화면

   화면의 상단에는 현재 단계를 알 수 있도록 표시 (2/11)

  화면의 양옆에는 단계를 이동할 수 있는 버튼이 있음, 하단에는 현재 단계에 맞는 설명.

   ![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/e00fd5ad-07fc-4a71-98ac-fff8ceec3b72)
+ 모델과 오브젝트 배치 

 그리고 부품 인식 기능을 위해 전 단계에서 Model Target Generator로 제작한 unitypackage와 Polycam에서 다운받은 OBJ 파일을 Import. 위의 사진처럼 각 단계에 맞는 모델을 Model Target으로 Scene에 추가. 모델이 인식되면 부품의 색이 변하게 하려고 모델과 똑같은 오브젝트를 자식으로 추가하고 material을 변경. 또한 조립에 필요한 오브젝트가 증강하기 위해 증강해야 하는 부분에 부품 오브젝트를 자식으로 추가. 


  ### 4) c# 스크립트 작성

조립 화면에서 버튼을 이용하여 Scene을 이동하기 그림(8)과 같이 위해 SceneManagement의 SceneManger.LoadScene을 사용하여 각 장면으로 이동할 수 있는 함수를 생성.

![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/38343dae-191f-4744-a591-14cfa6e1290b)
+화면 전환 함수

   조립 설명 기능에서 부품 오브젝트가 조립 방향에 맞게 움직이게 하기 위한 C# 스크립트를 작성. Start 함수는 처음에 한 번만 호출되는 함수이고 Update 함수는 프레임마다 호출되는 함수이다. Start 함수가 호출되면 오브젝트의 현재 local 좌표를 minY 값으로 저장한다. minY 값에서 0.3f만큼 위를 maxY 값으로 정하였다. Update 함수에서는 오브젝트의 local 좌푯값의 y축값을 일정한 거리(적절한 속도를 정해 속도 * 시간을 하여 거리를 구함)를 sign 값에 곱해 더해준다. sign 값이 +1이라면 오브젝트가 위로 올라가고, -1이라면 밑으로 내려간다. 만약 현재 오브젝트의 local 좌푯값이 minY보다 작거나 maxY보다 크다면 sign 값에 –1을 곱해 오브젝트의 이동 방향을 바꾸어 준다.

  ![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/c55adc00-813d-4385-b3fa-495eed86da65)
+ 오브젝트 이동 스크립트
   

  ### 5) QR 코드 인식 기능 제작
   QR 코드는 설명서의 첫 장면의 이름인 chair_step1이라는 텍스트를 저장하여 생성하였다. QR 코든 인식은 Vuforia에서 제공하는 Barcode 기능을 사용하였다. Scene에 Vuforia Engine의 Barcode를 추가해 주고 C# 스크립트를 작성했다.
  
![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/c44b095a-13dc-40f5-9390-e7331b65fee4)
+ QR코드 인식 c# 스크립트

   화면에 띄울 텍스트와 연결하기 위해 barcodeAsText를 정의. Start 함수가 호출되면 바코드에 저장된 정보를 읽어온다. 그리고 Update 함수에서 바코드가 인식되고 바코드에 저장된 데이터가 있다면 barcodeAsText.text에 “설명서로 이동 중입니다. 잠시만 기다려 주세요.”라는 문구를 저장하고 바코드에 저장되어 있던 텍스트를 장면 전환 함수에 넣어 알맞은 장면으로 이동하도록 함.

  만약 바코드가 인식되지 않으면 barcodeAsText.text에 아무 텍스트도 저장하지 않아 텍스트가 뜨지 않도록 하였다. 스크립트를 완성한 후 Scene에 barcodeAsText와 연결할 TextMeshPro를 만들어 연결하였다. 아래 사진은 QR 코드 인식 장면의 UI이다. New Text라고 되어있는 부분이 barcodeAsText와 연결되어 있다.

  ![image](https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/7c841020-368e-4636-97d1-7b27c8c606f3)
+ QR 코드 인식 장면 UI
  
---
# 프로젝트 수행 결과
### 1) QR 코드 인식 기능
앱을 실행하면 가장 먼저 QR 코드를 인식하는 장면이 나온다. QR 코드가 화면에 비추게 되면 설명서로 이동 중입니다. 라는 문구가 뜨고 제품에 맞는 해당 설명서로 자동으로 이동하게 된다.

https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/941a7843-bd5e-42ac-9894-bc22d21f17c2
+ QR 코드 인식 영상

### 2) 부품 인식 기능
부품 인식 기능은 부품을 찾을 때 사용한다. 아래 영상에서는 시트 플레이트라는 부품을 찾고 있다. 카메라에 해당 부품이 비치게 되면 부품의 색이 바뀌면서 표시되어 부품을 쉽게 찾을 수 있다.

https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/89ef71a6-e738-4ba4-b3c3-6f953072b755
+ 시트 플레이트 인식 영상


### 3) 조립 설명 기능

조립 설명 기능은 부품 인식 기능으로 찾은 부품을 조립하기 위해 사용된다. 아래 영상을 보면 시트 플레이트와 시트 하단부를 조립하는 장면이다. 시트 하단부가 카메라에 비치게 되면 시트 플레이트와 나사들이 조립해야 할 위치에 증강한다. 또한 나사들이 조립 방향에 맞게 움직이며 화면만 보고 쉽게 조립할 수 있다.

https://github.com/Kim-yerin0904/capstone-design_AR-manual/assets/77713307/2b07769b-8712-4f47-a498-502091ea87cb
+ 시트 하단부+시트플레이트 조립 설명 영상

