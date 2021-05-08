---
title: "Data Augmentation Paper Review"
published: true
---

# Methods

## Cutout [[Link]](https://arxiv.org/pdf/1708.04552.pdf)

Dropout과 비슷한 효과를 낸다. 연속된 영역의 정보를 없앤다.
이미지의 local feature보다 global feature를 더 잘 이용하게 해준다.

## GridMask [[Link]](https://arxiv.org/abs/2001.04086)

CutOut은 연속된 영역을 지운다. 하지만 연속된 영역을 많이 지우는 것은 손해다.
따라서 연속된 영역의 보존과 정보의 삭제 사이의 합의점을 찾자.

이를 위해 격자 방식의 삭제를 제안한다.

## LA [[Link]](http://ieeexplore.ieee.org.ssl.webgate.khu.ac.kr:8090/stamp/stamp.jsp?tp=&arnumber=9319662)

CNN은 local feature에 과도하게 의존한다. Adversarial Attack이 그 예이다.
따라서 local feature에 의존적이지 않고 global feature에 더 의존하게 하는 많은 방법들이 연구되고 있다.
하지만 이 논문에서는 local feature에 의존하는 local bias 현상을 적극적으로 활용한다.
다양한 Local image의 변환을 통해 성능의 향상을 꽤한다.

많은 것을 배운 논문이다.

## SaliencyMix [[Link]](https://openreview.net/pdf?id=-M0QkvBGTTq)

CutMix는 불필요한 정보가 합성될 여지가 있다.
SaliencyMix는 Saliency를 이용해 중요한 정보를 추출한 뒤 합성한다.
하지만 논문을 구현한 코드를 보니, 첫번째 이미지의 Saliency 정보를 모든 이미지에 적용한다.
좀 의문이 가는 부분이다.

## Random Erase [[Link]](https://arxiv.org/abs/1708.04896)

Random한 크기를 영역을 잡아서 장애물을 만든다. 이 점이 CutOut과 차별되는 점이다.
Random Erase는 CutOut과는 다르게 삭제된 영역 안을 평균값이나 랜덤값으로 채운다.

## Rand-augment [[Link]](https://openaccess.thecvf.com/content_CVPRW_2020/papers/w40/Cubuk_Randaugment_Practical_Automated_Data_Augmentation_With_a_Reduced_Search_Space_CVPRW_2020_paper.pdf)

Auto-augment의 경량화 벼전이다. N번의 변환을 수행하고 K개의 변환이 존재한다. 따라서 K^N의 경우의 수가 있다. N번의 이미지 변환 방법을 유니폼 디스트리뷰션으로 랜덤하게 적용한다.

# Summary

내가 크게 이 방법들을 분류하면 세가지 정도로 분류할 수 있을 것 같다.

1. Dropout 류
2. Label Smoothing 류
3. Grobal vs Local 류

Dropout을 이미지 변형으로 구현하려고 한 것이 Cutout, Random Erase 등이다.
Label Smoothing을 좀 더 합리적으로 구현하려고 한 것이 Mix 류이다.
Local bias를 줄이거나 활용하는 것이 나머지 방법들이다.

