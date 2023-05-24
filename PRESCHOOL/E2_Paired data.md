# Exploration 2. Paired Data!

## 2.1. Paired Data  

#### 인공지능 입문 프로젝트 - 숫자 손글씨 인식하기  
- 입력된 숫자 이미지와 정답 숫자 데이터를 활용해  
- 새로 들어우는 손글씨 숫자가 무엇인지 유추한다   
- 지도학습으로, 문제풀이가 쉽다

#### 지도학습에 사용되는 데이터, paired Data! 
입력과, 그 입력에 대한 정답이 쌍으로 주어지능 데이터이다.  
손글씨 인식기의 경우에는 (손글씨 숫자 이미지, 숫자)로 된 것이다.  

___
## 2.2. Image Classifier (이미지 분류기)

얼핏 보면 거의 똑같이 생긴 표범, 재규어, 치타의 무늬를 구분한다.  
마찬가지로 (이미지, 표범), (이미지, 재규어)와 같이 Paired Data가 있기 때문!


## 2.3. Object Detection/Tracking  

영상에서, 이미지에서 객체의 위치, 크기를 찾아 추적하는 알고리즘  
전체 이미지에서 (대상 부분, 대상)이라는 Paired Data가 사용된다.  

사람이 일일이 Pairing(labbeling) 하는 일이 과해 인공지능 프로그램이 대신 Labelling을 해주기도 한다.  

## 2.5. Pose Estimation  

사람 동작의 Skeleton 정보를 통해 어떤 동작인지 추정하는 알고리즘  
마찬가지로, 사람들이 만들어낸 Paired Data를 활용해 사람들의 움직임을 찾아낸다  

___
## 2.6. Paired Data 활용  

### Just Point it! (실제 프로젝트)  
1. 손으로 가리키는 이미지 1000~10000장을 촬영  
2. 손끝이 가리키는 단어를 *(단어 사진, 단어)*의 paired data로 입력 - 텍스트로 인식하는 OCR(Optical Character Recognition) 기술 활용

### Machine Translation (기계번역)  

## 2.7. 내가 가진 paired data?  

(책 제목, 책 카테고리), (하루동안 먹은 음식, 체중) 등  
어떤 Paired Data를 갖고 있는지, 가진 데이터로 무엇을 할 수 있을지?  
___
## 2.8. Teachable Machine 활용해 Paired Data 만들기  

엄지부터 약지까지, 손가락 구분하기!
