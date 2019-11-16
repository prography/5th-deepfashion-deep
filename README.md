# Deep fashion deep learning


### 11/16 손주영 진행상항
**Target : 옷 이미지 39종류에대해서 딥러닝신경망을 이용하여 Image Classification과 Image Segmentaion을 진행한다**

**Done**
1. Custom Dataset : ImageForder사용
2. 신경망 
  - CNN: Backbone Network - MobileNetV2
  1) Image Classification : Backbone으로 수행
  2) Image Segmentation : MobilenetV2로는 구현 못하고 Resnet으로 Test해봄
    a. 이유1: 본 토이프로젝트에는 Segmentation기법중 instance segmentation이 필요하다 판단되어지나 논문의 경우 DeeplabV3를 활용하여 Sementic segmentation으로 함
    b. 이유2: Pytorch의 신경망 패키지에 mobilenet의 segmentation부분 없는것 같음torch -> torchvision -> segmentation -> 모바일넷 없음


**Todo**
1. MobilenetV2 Classification 코드 데스크탑에서 학습 (Need Desktop)
2. MobilenetV2를 활용한 Image Segmentation 구현 문의
3. Transfer Learning
