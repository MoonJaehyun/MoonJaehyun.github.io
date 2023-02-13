---
title:  "[Jekyll] minimal-mistakes-theme에서 back to top버튼 만들기"
excerpt: "gitblog"

categories:
  - Blog
tags: [Blog, jekyll]

last_modified_at: 2021-07-02T11:00:00-05:00
classes: wide
---

글이 길어질 수록 맨 위로 한번에 올라가는 top 버튼이 필요해졌다.

다행히(?) minimal-mistakes-theme에서 제공해주는 top 버튼이 있어서 그대로 따라해 주었다 ㅎㅎ

순서는 다음과 같습니다!

### 1. `_sass/minimal-mistakes/_sidebar.scss`에서 아래 내용 삽입

삽입할 내용은 다음과 같다! 위치 조정은 마음대로 조절해주면 된다 ㅎㅎ

```scss
.sidebar__top {
  position: fixed;
  bottom: 1.5em;
  right: 2em;
  z-index: 10;
}
```

**삽입 후**의 모습이다! 👍

`_sidebar.scss`를 보면 다음과 같이 ========= 부분 **아래**에 추가해주면 된다.

```scss
/* ==========================================================================
   SIDEBAR
   ========================================================================== */

/*
   Default
   ========================================================================== */

.sidebar__top {
  position: fixed;
  bottom: 1.5em;
  right: 2em;
  z-index: 10;
}

.sidebar {
  @include clearfix();
  // @include breakpoint(max-width $large) {
  //   /* fix z-index order of follow links */
  //   position: relative;
  //   z-index: 10;
  //   -webkit-transform: translate3d(0, 0, 0);
  //   transform: translate3d(0, 0, 0);
  // }
  --생략--
```


### 2. `_layouts/default.html`에 내용 삽입

삽입할 내용 부분

```html
<aside class="sidebar__top">
<a href="#site-nav"> <i class="fas fa-angle-double-up fa-2x"></i></a>
</aside>
```

**삽입 후**의 모습이다. 

```<div id="footer" class="page__footer">``` 의 바로 **위**에 추가하면 된다. 


```html
--생략--
{% raw %}
    {% endif %}
    <aside class="sidebar__top">
    <a href="#site-nav"> <i class="fas fa-angle-double-up fa-2x"></i></a>
    </aside>
    <div id="footer" class="page__footer">
{% endraw %}
--생략--
```
<br>

### 3. 확인

아래 이미지 처럼 생긴 top 버튼이 생긴 것을 확인 할 수 있다! ㅎㅎ 😁😁 매우 간단한 작업이었다. 

![image](https://user-images.githubusercontent.com/53431568/124255550-40c89880-db65-11eb-8e18-7afa7515418c.png)

<br>

#### 참고

[1] [https://github.com/mmistakes/minimal-mistakes/issues/1731](https://github.com/mmistakes/minimal-mistakes/issues/1731)
