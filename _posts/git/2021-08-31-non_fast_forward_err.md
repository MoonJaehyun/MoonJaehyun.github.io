---
title:  '[GIT 에러] ! [rejected]  master -> master (non-fast-forward)'
excerpt: ""

categories:
  - git
tags: [git, etc]

last_modified_at: 2021-08-30T08:06:00-05:00
classes: wide
---

###  [rejected]  master -> master (non-fast-forward)) 에러 잡기

![image](https://user-images.githubusercontent.com/53431568/131433603-4b34dc31-84af-471b-ab79-141939c0c1ea.png)

이런 에러가 발생😅


### 원인

이 에러는 깃헙에 생성된 원격 저장소와 로컬에 생성된 저장소 간 공통분모가 없는 상태에서 병합하려는 시도로 인해 발생하는 문제라고 한다.

아마, push가 안되면서 master 브랜치를 생성하고 또 commit 하면서 내부적으로 꼬인것이 문제인것 같다.

git은 기본적으로 관련 없는 두 저장소를 병합하는 것은 불가능하고 한다. ㅎㅎ 그래서 계속 에러가..!

<br>

### 해결

만약 git pull을 시도하더라도 되지 않는다면..! `git pull` 먼저 꼭 해보자! 되는 경우도 있습니다.

git pull 시에 `–allow-unrelated-histories` 옵션을 추가하여 관련 없었던 두 저장소를 병합하도록 허용해주자

~~~ssh
git pull origin master --allow-unrelated-histories
~~~

이 이후에 나는 main branch 하나만 쓸거기 때문에 master 브랜치를 원격, 로컬 둘 모두에서 삭제해 주었다. 

만약, 이 이후 브랜치를 master로 한 상태에서 git add -> commit -> push 를 계속 진행하고 싶다면 merge 해주고 checkout 해주면 된다.

자세한 브랜치 변경 방법은 => [참고](https://chaelin0722.github.io/git/etc/remote_rejected_pre-receive_hook_declined/)

<br>
<br>
<hr>


#### 참고

[1] [https://www.zehye.kr/git/2019/10/27/11git_push_error/](https://www.zehye.kr/git/2019/10/27/11git_push_error/)
