---
title: "Jekyll의 Minimal Mistakes Theme 적용 Guide"
date: 2018-11-11 08:10:00 -0400
categories: Minimal-Mistakes Guide Developer
---

# GitHub io Minimal Mistakes 적용하기

참조의 사이트를 통해서 기본 구조를 포크하거나 다운로드 받음.



## 1. Config.yml

전체적인 블로그에 해당 테마를 적용하기위한 설정을 변경하는 파일.

```yaml
remote_theme           : "mmistakes/minimal-mistakes"
minimal_mistakes_skin    : "default" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise" - 테마 선택 가능(공식 홈페이지 참조)
```



## 2. Author정보 설정하기

Profile 이미지는 config.yml의 author.avatar 의 값을 지정함으로써 지정할 수 있음.

Image를 로컬에 저장하기 위한 경로는 : /assets/images

```yaml
author:
  name             : "Suji Woo, Wooni"
  avatar           : "/assets/images/Wooni.jpeg"
  bio              : "Hello :) This is Wooni. <br /> I'm developer at Coupang."
  location         : "Seoul, Korea"
  email            : "sjchu91@gmail.com"
```



## 3.  _drafts

_posts에는 실제로 포스트할 포스트를 저장하는 반면, _drafts에는 현재 작성중인 포스트에 대해서 저장하고 Git을 통해 관리할 수 있음.



## 4.  _posts

실제로 포스트 될 포스트를 저장하는 폴더.
포스트의 파일명은 "{year}-{mm}-{dd}-{file name : space is "-"}" 규칙을 따른다.



## 5. 포스트(.md)

실제로 게시물에 포함될 내용을 작성하는 포스트.
상단의 메타정보를 포함할 수 있음.
더욱 편리하게 작성하기 위해 [Typora](https://typora.io/)를 추천

```tex
title : post의 title이 될 제목
data : 작성 할 날짜
categories : 해당 포스트가 포함되는 카테고리를 분류(구분자는 Space)
```



## 6. Css Override

실제로 기본의 css가 적용되면서, 화면의 크기에 따라 글씨체나 화면의 비율이 정해져 있음.
하지만 해당 css들을 오버라이드 할 수 있음.

css를 오버라이드 하기 위한 경로는 : /assets/css/main.scss

```scss
---
# Only the main Sass file needs front matter (the dashes are enough)

---

@charset "utf-8";

@import "minimal-mistakes/skins/{{ site.minimal_mistakes_skin | default: 'default' }}"; // skin
@import "minimal-mistakes"; // main partials

# Page의 padding을 0으로 바꿈
.page {
	padding-right: 0px !important;
} 

# font-size change
.page__content {
	font-size: 16px;
}
```



# 참조

Minimal Mistakes - https://mmistakes.github.io/minimal-mistakes/



