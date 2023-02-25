---
title:  "[개발환경 구축] VsCode 설정 및 간단 사용법)"
excerpt: "IDE Setting"
toc : true
toc_sticky: true
categories:
  - aiestarterbook
tags: [VsCode, setting]

last_modified_at: 2023-02-20T08:06:00-05:00
classes: wide
---

sns_instagram 😄: m._.jaehyun 

(안되거나 질문 있을 시 디엠으로 부탁드려요. 🙏🙏🙏🙏🙏)

(https://www.instagram.com/m._.jaehyun/)

## 1. D2Coding체 설정

폰트 중에서도 d2coding체를 쓸 것이다.

d2coding체를 쓰는 이유는 기존에 사용하는 폰트는 영어로 하는 경우를 주로 사용하기 때문에 영어로만 코딩을 할 경우 좋으나 한글을 사용할 경우에는 장평이 좁아지기도해 가독성이 안 좋았다. 또한 특수 문자 같은 경우에도 더욱 구별이 잘되어서 코드에 사용하기에 편하다.

### 1-1. 폰트 다운로드 링크

- https://github.com/naver/d2codingfont/releases/tag/VER1.3.2

![Untitled](https://user-images.githubusercontent.com/86664178/220128233-a96048d5-8781-4553-af4f-b580e62f9723.png)


본인 같은 경우에는 Assets에서 가장 위에 압축파일을 다운 받았다.

압축을 풀게되면 아래와 같이 폴더가 나온다.

![Untitled 1](https://user-images.githubusercontent.com/86664178/220128285-bbe1c0b8-aaa4-46c4-9343-0f3475886914.png)


이중에서 원하는 폴더를 열고 font에 등록 시켜주면 된다.

 

### 1-2. 적용방법

window 키 - 설정 - 개인설정 - 글꼴

![Untitled 2](https://user-images.githubusercontent.com/86664178/220128354-5413bf59-1e79-48c3-a578-aa20e845fb91.png)


글꼴 찾아보기 및 설치

d2coding 파일 골라서 설치

![Untitled 3](https://user-images.githubusercontent.com/86664178/220128364-16c9a51b-e845-4c8f-b447-f8309d00ff88.png)


VsCode에서 좌측하단에 있는 톱니바퀴 - 설정

![Untitled 4](https://user-images.githubusercontent.com/86664178/220128380-edc3f2e9-03d1-429c-ad11-c40174e014bb.png)


font family 에서 글꼴을 d2coding으로 설정하면 적용된다.

![Untitled 5](https://user-images.githubusercontent.com/86664178/220128482-c4cb8f9b-dc14-479a-bd84-1faf48820bad.png)


## 2. VsCode 사용해보기.

### 2-1. py 파일 돌려보기

폴더에서 추가 버튼을 누르고 파일 생성

 print.py라는 파일을 만들었다.

```python
print("안녕하세요 저는 전 지능형시스템공학과 현 인공지능 공학과 휴학 중인 문재현이라고 합니다. 잘부탁드려요.")
```

![Untitled 6](https://user-images.githubusercontent.com/86664178/220128489-a8885e61-fc17-49a3-80b8-778001a6b120.png)


오른쪽 아래에 보면 인터프리터 선택이라고 되어있는데 ananconda에서 만들었던 가상환경을 선택해준다. F1을 눌러서 인터프리터를 선택해도되고 오른쪽 아래에 인터프리터 선택을 해서 가상환경을 선택해도 된다.

***인터프리터** : **프로그래밍 언어의 소스 코드를 바로 실행하는 컴퓨터 프로그램 또는 환경**

![Untitled 7](https://user-images.githubusercontent.com/86664178/220128491-d567f19a-0192-4fa4-b11d-123bd14bca12.png)


결과.

![Untitled 8](https://user-images.githubusercontent.com/86664178/220128623-73bbc242-7732-4ba4-96d6-4d40565500d9.png)


### 2.2 py 파일 돌려보기2 및 간단한 오류해결 법.

자주 보이는 error 메세지를 보고 해결하기 위해 모듈을 가져오는 import가 있는 코드를 해보겠다.

코드는 아래와 같다.

```python
import numpy as np
import cv2

image = np.zeros((300, 400), np.uint8)
image.fill(200)                     # 혹은 image[:] = 200

cv2.imshow("Window title", image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

아래의 코드들을 보면 노란 밑줄 두개가 쳐진 것을 볼 수 있다.

![Untitled 9](https://user-images.githubusercontent.com/86664178/220128630-930a9ca5-8b3c-4cb6-a983-9a05a4732fe0.png)


이 상태로 코드를 실행해보겠다.

코드를 실행하면 ModuleNotFoundError: No module named 'numpy’이라는 메세지를 받게 된다.

![Untitled 10](https://user-images.githubusercontent.com/86664178/220128632-97566f48-3fcc-4789-b760-9c986bd70ff1.png)


해결하기 위해 구글링을 해보겠다.

검색하니 터미널에 아래에 같이 실행하라 하였다.

```python
pip install numpy
```

![Untitled 11](https://user-images.githubusercontent.com/86664178/220128634-0f1c545e-11bb-44e1-a35b-79cab03486a8.png)


VsCode에 켜져 있는 가상환경에 설치할 것이므로 conda install numpy를 해주도록 하겠다. 혹은 가상환경이 켜진 상태라면 pip로 해도 된다.

y를 치고 엔터를 해주어 설치를 다하겠다.

![Untitled 12](https://user-images.githubusercontent.com/86664178/220128782-d773d935-868d-434f-b983-e3408de74521.png)


설치를 하고나니 노란 밑줄이 사라졌다.

![Untitled 13](https://user-images.githubusercontent.com/86664178/220128788-797fb115-3fed-4dcb-84ff-c658f993c779.png)


다시 실행해보겠다.

이번엔 ModuleNotFoundError: No module named 'cv2’라는 메세지를 받았다. 검색해보니

```python
pip install opencv-python
```

위 명령어를 실행하라 하였다.

둘다 설치하니 밑줄이 사라졌다.

![Untitled 14](https://user-images.githubusercontent.com/86664178/220128792-558a5de8-74de-4fa1-a651-31b3e6c00265.png)


결과.

![Untitled 15](https://user-images.githubusercontent.com/86664178/220128796-c029d895-03b4-4da2-bc84-59fb622b5b03.png)


esc키를 통해 닫을수 있는 윈도우 창 띄우기 코드를 성공적으로 실행시켰다.

sns_instagram 😄: m._.jaehyun 

(안되거나 질문 있을 시 디엠으로 부탁드려요. 🙏🙏🙏🙏🙏)

(https://www.instagram.com/m._.jaehyun/)