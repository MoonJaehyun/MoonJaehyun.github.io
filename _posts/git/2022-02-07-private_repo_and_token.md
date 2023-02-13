---
title:  '[GIT] Private Repo 생성과 ssh 토큰등록'
excerpt: "private repo, ssh, branch"

categories:
  - git
tags: [git, etc]

last_modified_at: 2022-02-07T08:06:00-05:00
classes: wide
---


### Private Repository 만들기

학교에서 하는 외부 과제를 함께 하기 위해 공동 repo를 만들어보았다😊 아무래도 그냥 보이는 것 보다는 private이 안전! 할 것 같아서 처음으로 private 레포를 생성해보았다.

생성방법은 기존에 repository 생성하는 것과 같은데 그동안 default였던 값을 private 으로 체크해주면 된다. 끄읏!

이제 이 레포는 외부에 보이지 않는다! 그렇다면 공동작업자는 어떻게 초대하느냐 인데..

구글링해보니 git이 또! 몇개월만에 디자인을 바꾼 것 같았다 ㅎㅎ 개발자들 열일하네..

그래도 메뉴 이름이 직관적이어서 보면 알 수 있을 것입니다😊(찡긋) 
아래 그림을 보면, 해당 private repo에 들어가서 Setting -> collaborators를 누르면 협동자(?)를 추가할 수 있는 페이지가 나온다

`Add people` 클릭!

![git_private](https://user-images.githubusercontent.com/53431568/152731015-0c70f470-03c4-4d3e-baad-0051c25e3dc5.png)

다음으로 깃계정 이름으로 사람을 찾을 수 있다. 잘 선택해서 추가하시길 바랍니다! 안그러면 애먼 사람한테 요청될수도!😂😂

![git_private_1 2](https://user-images.githubusercontent.com/53431568/152731194-a90bcc4a-a594-45ad-bca2-51a8b7e3f564.png)

여기까지 잘 왔다면 아래와 같은 화면을 맞이할 수 있을 것이다.

![git_private_2](https://user-images.githubusercontent.com/53431568/152731373-46ed2d89-d8ff-469a-918a-6c1daf48bec1.png)

### SSH 토큰 등록

이제 새로운 레포를 사용하기 시작했다면 ADD->COMMIT->PUSH 할 때 매번 계정이름과 비밀번호(토큰)를 쳐야하는 번거로움에 직면할 것입니다.

만약 매번 비밀번호를 치는 것이 번거롭지 않다면..! ~~(과연 번거롭지 않을 수 있나요..? ㅋㅋㅋ)~~

아래 1) 번으로 매번 비밀번호에  token 을 쳐주면 됩니다. ㅎ 설마 이런 사람있나요..?

나는 매번 치기 싫다! 자동으로 되면 좋겠다! 하시는 분은 2)번 부터 고고~

<br>

1) GITHUB 에서 Access Token 받기!

이 방법은 이미 포스팅 해놓았으므로 참고하기 => [[GIT token] 토큰으로 인증하기(git personal access token)](https://chaelin0722.github.io/git/token/)

2) 원격 레포에서 SSH Public key를 Git Hub에 등록하기


원격 공간에서 아래 명령어를 터미널에 쳐주세요!

~~~
ssh-keygen
cat ~/.ssh/id_rsa.pub
~~~

그러면 복잡한 key가 나올 것입니다! 그걸 그대로 복사!(copy)해주세요

그런 후에 본인의 private repo 에서 settings -> deploy keys 메뉴로 이동하면 아래와 같은 페이지가 나옵니다. `add deploy key` 클릭!
(저는 특정 repo만 SSH Key를 등록하기 위해 아래와 같이 하는 것입니다. 만약 본인의 계정 전체의 repo 에 대해 SSH Key를 등록하고자 한다면 다른 방법으로 하셔야 해요!


![image](https://user-images.githubusercontent.com/53431568/152732588-db152674-bcfc-404b-9d8f-6c6c62f4bd4c.png)

그러면 아래와 같이 나오는데, title엔 적당한 이름을 주고 key 에는 앞서 복사한 id_rsa public 키를 붙여 넣어줍니다. 

그리고 Allow write access를 체크해 준 후 `Add key` 클릭!

![image](https://user-images.githubusercontent.com/53431568/152732682-7474c14f-ea9c-49dd-bc50-c548a1ca6b6b.png)


끝!

인줄 알았으나 git 을 만들 때 Https로 만들었기 때문에 이걸 SSH로 전환시켜주어야 된다고 한다.

아래 명령어를 실행했을 때,

~~~
git remote -v
~~~

아래와 같이 나오지 않고 `origin https://github.com/chaelin0722/` 이런식으로 https 가 포함된 url이 나온다면,


![image](https://user-images.githubusercontent.com/53431568/152753740-605676c2-c433-4e57-83ed-9a720a95159e.png)


아래 명령어를 실행해 주면 된다.

~~~
git remote set-url origin git@github.com:chaelin0722/깃이름주소.git
~~~

commit, push도 아주 잘 된다

![화면 캡처 2022-02-07 174524](https://user-images.githubusercontent.com/53431568/152754425-a58594ac-c23b-4713-aede-3629c861cb89.png)

<br>

<br>

#### 참고

[1] [https://kibua20.tistory.com/88](https://kibua20.tistory.com/88)

