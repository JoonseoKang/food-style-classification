# 음식 스타일 분류기 만들기  
image classifier model을 이용해서 음식 스타일 구분하기  

## 1. Image Crwaling
구글 이미지 검색을 활용해서 원하는 음식 사진 검색해서 폴더 만들고 저장하기

```
$ python image_crawling.py
```

To add：

1. ```--searh_word=str```, e.g.```--searh_word='korean food'``` 검색하고 싶은 키워드 입력

2. ```--number=int```, e.g.```--number='500'``` 저장하고 싶은 이미지 개수 입력

3. ```--dir=str```, e.g.```--dir=korean``` 이미지 저장할 디렉토리 지정

## 2. fine tuning
vgg 16으로 한식 vs 이탈이아 음식 분류 모델 학습. transfer learning의 경우 정확도가 40% 였지만 fine tuning후에 80% 까지 향상되었다.  
vgg16말고 다른 모델로 정확도 향상 시켜보고 음식 분류에 특화된 모델이 있는지 찾아볼 계획.  

## 3. EfficientNet
ImageNet에서 좋은 성능을 보이고 pretrain된 모델이 공개되어있는 efficientnet을 사용하여 예측해보기

```
$ pip install efficientnet_pytorch
```

```
from efficientnet_pytorch import EfficientNet
model = EfficientNet.from_pretrained('efficientnet-b0', num_classes = 2)
```

- acc_b0 90% 
- acc_b7 50%
