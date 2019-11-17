# Deep fashion deep learning
---------------------------------------------------------------------------------------------------------------
## 11/17 : Image Classification구현 Pair Programming
#### 목표 : Image Classification - MobileNetV2, Transfer Learning을 활용한 Multi-Labeling</br></br>
#### 참석자: 홍예지, 손주영 (서울대 입구역, 14시 - 17시)</br></br>
#### 진행사항(요약) 
    - MultiLabeling을 위해 출력 라벨 Type을 각각의 Class를 one-hot인코딩 하여 1차원 벡터로 만든뒤 더하는 형태로 구현한다. 
    - Image Classification의 Backborn모델(MobileNetV2) 구현 성공
#### 진행사항(상세내용) </br>
##### 1. MultiLabeling에 대한 출력 라벨Type idea회의 </br>
 1) 결론: One-Hot벡터 형태, 각 클래스의 항목들의 라벨링을 각각 더해서 더하는 형태 </br>
      - syle클래스 11개 라벨링 + season클래스 4개 라벨링..... </br>
      - 예상되는 클래스의 벡터 형태
      - class = [1,0,0,0,0,1,0,0,0,0,0,0,1......]
      - len(class) = style항목의 라벨링 개수 + season항목의 라벨링 개수+ color항목의 라벨링 개수+ type항목의 라벨링 개수
 2) 의견들  </br>
     - 예지 의견 : class정의를 dictionary 형태로 구현하자
       - class = {'style':['office/formal','dandy'.....],'season':['winter','all'....]}
     - 주영 의견 : 각 Class를 쪼개서 one hot 형식으로 tensor를 더한다. 출력차원을 늘리는 형태
       - class = [1,0,0,0,0,1,0,0,0,1,0,0,0,0,0,1,0,0,0,........]
       - 즉, 각 클래스의 style항목(11개라벨링), season항목(4개라벨링), color항목(...), category항목(..), type항목(...) 총 5개의 형태이고 각각의 클래스항목당 라벨링 수를 더하는 방식. 

        
##### 2. Classification 모델 논의 
    - 각자 11/16일 ProtoType구축당시, 예지는 MobileNet구현에 문제가 있었고, 주영은 TransferLearning에 구현에 문제가 있었다. 
    - 우선 MobileNetV2 + TransferLearning에 구현 가능성에 대해 논의하였다.
    - 그 결과 MobileNetV2 구현에 성공(Code로 구현 성공)하였다.
    - TransferLearning아직 구현 못함. (시간 부족 ㅠㅠ)

##### 3. Action Item 
    - DataSet검토하기
     - DeepFashion2: https://drive.google.com/drive/folders/125F48fsMBz2EF0Cpqk6aaHet5VH399Ok 
     - c_datasets_V2.0만든 후 Review 
     - DeepFashionAttribute파일 검토 : http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion/AttributePrediction.html
    - One-Hot벡터 구현(Multi-Labeling을 위한) 
    - TransferLearning부분 


------------------------------------------------------------------------------------------------------------------------

## 11/16 : Prototype용 Model 구축

#### 1. 기술 스택 : Pytorch 1.3.1, MobileNetV2 + Transfer Learning, DeepLabV3 </br>
#### 2. Model 구현 </br>
    - Image Classification : MobileNetV2, Transfer Learning을 활용한 Multi-Labeling
    - Image Segmentation : Segmentation 구현. 
#### 3. 결과.</br>
    - 주영: 
        - Image Classification: MobileNetV2구현, Single Labeling 구현. 
            - 뒷단에 TrnasferLearning 구현 실패 : 이유. 아직 이해 불가. 
            - Multi Labeling구현 실패 : 이유. idea 없없음. 
        - Image Segmentation : ResNet을 활용하여 Instance Segmentation 구현 (MobileNetV2 논문에는 SimenticSegmentation부분만 있어서 구현하지 않음)
    - 건호:
        - Image Classification: MobileNetV2구현 + Transferlearning 구현 성공.  
            - 뒷단에 TrnasferLearning 구현 여부 확인 필요 : 이유. 구현은 했다고 하나 accuracy가 증가하지 않았다고 함.
            - Multi Labeling구현 실패 : 이유. idea없었음. 
        - Image Segmentation : MobileNetV2 + DeebLabV3를 활용하여 Simentic Segmentation 구현
        - Fixel깨지는 현상 발생. 정확도 많이 떨어짐. 
        - 해결방안: DataSet의 문제.. (이건 사실 노가다 해야함..)
    - 예지:
        - Image Classification: ResNet + TransferLearning구현 성공
            - Multi Labeling구현 성공. 
            - MobileNet구현 실패 : MobileNet 이해도 
        - Image Segmentation : 구현 실패
#### 4. Action Item 
   1) 예지, 주영 : Image Classification구축 (~11/20)
   2) 건호 : Image Segmentation 구축(~11/20)
