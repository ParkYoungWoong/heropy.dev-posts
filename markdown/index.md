---
id: 7aOtsvU
filename: markdown
title: MarkDown 사용법 총정리
date: 2017-09-30
group: Markdown
video: true
level: 3
tags:
  - markdown
  - html
---

마크다운(MarkDown)에 대해서 알고 계신가요?
파일 확장자가 `.md`로 된 파일을 보셨나요?
웹 개발을 하면서 아마 `README.md`라는 이름의 파일을 한 번은 보셨을텐데, 이 파일이 마크다운 문법으로 작성된 파일 입니다.

사용법이 매우 쉽고, 빠르게 문서를 정리할 수 있습니다.
물론 모든 HTML 마크업을 대신할 수 없기 때문에 지나친 의존보다는 쉽고 빠르게 작성하는 용도로 사용하세요.
마크다운과 비슷한 형태로 문법이 좀 더 복잡하지만 확장자가 `.adoc`인 [AsciiDoc](http://asciidoctor.org/docs/asciidoc-syntax-quick-reference/#tables) 문법도 있습니다. 좀 더 다양한 형태의 문서를 만들 수 있지만, 문법이 좀 더 복잡하고 지원 플랫폼이 적습니다.

우선 문법이 쉽고 다양한 플랫폼을 지원하는 마크다운 문법을 배우세요.
30분이면 충분합니다.

<!-- toc -->

# 마크다운(MarkDown)에 대해서

## 마크다운의 장점

1. 문법이 쉽다.
1. 관리가 쉽다.
1. 지원 가능한 플랫폼과 프로그램이 다양하다.

## 마크다운의 단점

1. 표준이 없어 사용자마다 문법이 상이할 수 있다.
1. 모든 HTML 마크업을 대신하지 못한다.

## 마크다운의 사용

메모장부터 전용 에디터까지 많은 곳에서 활용할 수 있습니다.
문법이 쉽기 때문에 꼭 전용 에디터를 사용할 필요는 없습니다만, 마크다운 코드의 하이라이트 효과를 원한다면 전용 에디터가 좋은 선택이 될 것 같네요.
저는 평소 [Atom](https://atom.io)을 사용하고 있습니다.
혹은 마크다운 문법을 지원하는 모든 곳에서 사용할 수 있으며, 일반 블로그나 워드프레스 외 [Slack](https://slack.com/)이나 [Trello](https://trello.com/) 같은 서비스에서 메세지를 작성하듯 사용할 수도 있습니다.
화면에 표현되는 스타일(CSS)은 설정에 따라 달라집니다.
HTML과 마찬가지로 눈에 보이는 스타일은 무시하고 각 문법의 의미로 사용하세요.

# 마크다운 문법(syntax)
  
## 제목(Header)

`<h1>`부터 `<h6>`까지 제목을 표현할 수 있습니다.

```markdown
# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
```

제목1(h1)과 제목2(h2)는 다음과 같이 표현할 수 있습니다.

```markdown
제목 1
======

제목 2
------
```

## 강조(Emphasis)

각각 `<em>`, `<strong>`, `<del>` 태그로 변환됩니다.

밑줄을 입력하고 싶다면 `<u></u>` 태그를 사용하세요.

```markdown
이텔릭체는 *별표(asterisks)* 혹은 _언더바(underscore)_를 사용하세요.
두껍게는 **별표(asterisks)** 혹은 __언더바(underscore)__를 사용하세요.
**_이텔릭체_와 두껍게**를 같이 사용할 수 있습니다.
취소선은 ~~물결표시(tilde)~~를 사용하세요.
<u>밑줄</u>은 `<u></u>`를 사용하세요.
```

이텔릭체는 *별표(asterisks)* 혹은 _언더바(underscore)_를 사용하세요.
두껍게는 **별표(asterisks)** 혹은 __언더바(underscore)__를 사용하세요.
**_이텔릭체_와 두껍게**를 같이 사용할 수 있습니다.
취소선은 ~~물결표시(tilde)~~를 사용하세요.
<u>밑줄</u>은 `<u></u>`를 사용하세요.

## 목록(List)

`<ol>`, `<ul>` 목록 태그로 변환됩니다.

```markdown
1. 순서가 필요한 목록
1. 순서가 필요한 목록
  - 순서가 필요하지 않은 목록(서브) 
  - 순서가 필요하지 않은 목록(서브) 
1. 순서가 필요한 목록
  1. 순서가 필요한 목록(서브)
  1. 순서가 필요한 목록(서브)
1. 순서가 필요한 목록

- 순서가 필요하지 않은 목록에 사용 가능한 기호
  - 대쉬(hyphen)
  * 별표(asterisks)
  + 더하기(plus sign)
```  

1. 순서가 필요한 목록
1. 순서가 필요한 목록
  - 순서가 필요하지 않은 목록(서브) 
  - 순서가 필요하지 않은 목록(서브) 
1. 순서가 필요한 목록
  1. 순서가 필요한 목록(서브)
  1. 순서가 필요한 목록(서브)
1. 순서가 필요한 목록

- 순서가 필요하지 않은 목록에 사용 가능한 기호
  - 대쉬(hyphen)
  * 별표(asterisks)
  + 더하기(plus sign)

## 링크(Links)

`<a>`로 변환됩니다.

```markdown
[GOOGLE](https://google.com)

[NAVER](https://naver.com "링크 설명(title)을 작성하세요.")

[상대적 참조](../users/login)

[Dribbble][Dribbble link]

[GitHub][1]

문서 안에서 [참조 링크]를 그대로 사용할 수도 있습니다.

다음과 같이 문서 내 일반 URL이나 꺾쇠 괄호(`< >`, Angle Brackets)안의 URL은 자동으로 링크를 사용합니다.
구글 홈페이지: https://google.com
네이버 홈페이지: <https://naver.com>

[Dribbble link]: https://dribbble.com
[1]: https://github.com
[참조 링크]: https://naver.com "네이버로 이동합니다!"
```

[GOOGLE](https://google.com)

[NAVER](https://naver.com "링크 설명(title)을 작성하세요.")

[상대적 참조](../users/login)

[Dribbble][Dribbble link]

[GitHub][1]

문서 안에서 [참조 링크]를 그대로 사용할 수도 있습니다.

다음과 같이 문서 내 일반 URL이나 꺾쇠 괄호(`< >`, Angle Brackets)안의 URL은 자동으로 링크를 사용합니다.

구글 홈페이지: https://google.com
네이버 홈페이지: <https://naver.com>

[Dribbble link]: https://dribbble.com
[1]: https://github.com
[참조 링크]: https://naver.com "네이버로 이동합니다!"

## 이미지(Images)

`<img>`로 변환됩니다.
링크과 비슷하지만 앞에 `!`가 붙습니다.

```markdown
![대체 텍스트(/images/7aOtsvU/alternative text)를 입력하세요!](http://www.gstatic.com/webp/gallery/5.jpg "링크 설명(title)을 작성하세요.")

![Kayak][logo]

[logo]: http://www.gstatic.com/webp/gallery/2.jpg "To go kayaking."
```

![대체 텍스트(alternative text)를 입력하세요!](http://www.gstatic.com/webp/gallery/5.jpg "링크 설명(title)을 작성하세요.")

![Kayak][logo]

[logo]: http://www.gstatic.com/webp/gallery/2.jpg "To go kayaking."

### 이미지에 링크

마크다운 이미지 코드를 링크 코드로 묶어 줍니다.

```markdown
[![Vue](/7aOtsvU/vue.png)](https://kr.vuejs.org/)
```

[![Vue](/7aOtsvU/vue.png)](https://kr.vuejs.org/)

## 코드(Code) 강조

`<pre>`, `<code>`로 변환됩니다.
숫자 1번 키 왼쪽에 있는 <code>`</code>(Grave)를 입력하세요

### 인라인(inline) 코드 강조

```markdown
`background`혹은 `background-image` 속성으로 요소에 배경 이미지를 삽입할 수 있습니다.
```

`background`혹은 `background-image` 속성으로 요소에 배경 이미지를 삽입할 수 있습니다.

### 블록(block) 코드 강조

<code>`</code>를 3번 이상 입력하고 코드 종류도 적습니다.

<pre>
<code class="markdown">
```html
&lt;a href="https://www.google.co.kr/" target="_blank"&gt;GOOGLE&lt;/a&gt;
```

```css
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
function func() {
  var a = 'AAA';
  return a;
}
```

```bash
$ vim ./~zshrc
```
 
```python
s = "Python syntax highlighting"
print s
```
 
```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```
</code>
</pre>

```html
<a href="https://www.google.co.kr/" target="_blank">GOOGLE</a>
```

```css
.list > li {
  position: absolute;
  top: 40px;
}
```

```javascript
function func() {
  var a = 'AAA';
  return a;
}
```

```bash
$ vim ./~zshrc
```
 
```python
s = "Python syntax highlighting"
print s
```
 
```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```

## 표(Table)

`<table>` 태그로 변환됩니다.
헤더 셀을 구분할 때 3개 이상의 `-`(hyphen/dash) 기호가 필요합니다.
헤더 셀을 구분하면서 `:`(Colons) 기호로 셀(열/칸) 안에 내용을 정렬할 수 있습니다.
가장 좌측과 가장 우측에 있는 `|`(vertical bar) 기호는 생략 가능합니다.

```markdown
| 값 | 의미 | 기본값 |
|---|:---:|---:|
| `static` | 유형(기준) 없음 / 배치 불가능 | `static` |
| `relative` | 요소 자신을 기준으로 배치 |  |
| `absolute` | 위치 상 부모(조상)요소를 기준으로 배치 |  |
| `fixed` | 브라우저 창을 기준으로 배치 |  |

값 | 의미 | 기본값
---|:---:|---:
`static` | 유형(기준) 없음 / 배치 불가능 | `static`
`relative` | 요소 **자신**을 기준으로 배치 |
`absolute` | 위치 상 **_부모_(조상)요소**를 기준으로 배치 |
`fixed` | **브라우저 창**을 기준으로 배치 |
```

값 | 의미 | 기본값
---|:---:|---:
`static` | 유형(기준) 없음 / 배치 불가능 | `static`
`relative` | 요소 **자신**을 기준으로 배치 |
`absolute` | 위치 상 **_부모_(조상)요소**를 기준으로 배치 |
`fixed` | **브라우저 창**을 기준으로 배치 |  

## 인용문(BlockQuote)

`<blockquote>` 태그로 변환됩니다.

```markdown
인용문(blockQuote)

> 남의 말이나 글에서 직접 또는 간접으로 따온 문장.
> _(네이버 국어 사전)_

BREAK!

> 인용문을 작성하세요!
>> 중첩된 인용문(nested blockquote)을 만들 수 있습니다.
>>> 중중첩된 인용문 1
>>> 중중첩된 인용문 2
>>> 중중첩된 인용문 3
```

인용문(blockQuote)

> 남의 말이나 글에서 직접 또는 간접으로 따온 문장.
> _(네이버 국어 사전)_

BREAK!

> 인용문을 작성하세요!
>> 중첩된 인용문(nested blockquote)을 만들 수 있습니다.
>>> 중중첩된 인용문 1
>>> 중중첩된 인용문 2
>>> 중중첩된 인용문 3

## 원시 HTML(Raw HTML)

마크다운 문법이 아닌 원시 HTML 문법을 사용할 수 있습니다.

```markdown
<u>마크다운에서 지원하지 않는 기능</u>을 사용할 때 유용하며 대부분 잘 동작합니다.

<img width="150" src="/images/7aOtsvU/4.jpg" alt="Prunus" title="A Wild Cherry (Prunus avium) in flower">

![Prunus](/7aOtsvU/4.jpg)
```

<u>마크다운에서 지원하지 않는 기능</u>을 사용할 때 유용하며 대부분 잘 동작합니다.

<img width="150" src="http://www.gstatic.com/webp/gallery/4.jpg" alt="Prunus" title="A Wild Cherry (Prunus avium) in flower">

![Prunus](http://www.gstatic.com/webp/gallery/4.jpg)

## 수평선(Horizontal Rule)

각 기호를 3개 이상 입력하세요.

```markdown
---
(Hyphens)

***
(Asterisks)

___
(Underscores)
```

---
(Hyphens)

***
(Asterisks)

___
(Underscores)

## 줄바꿈(Line Breaks)

```markdown
동해물과 백두산이 마르고 닳도록 
하느님이 보우하사 우리나라 만세   <!--띄어쓰기 2번-->
무궁화 삼천리 화려 강산<br>
대한 사람 대한으로 길이 보전하세
```

동해물과 백두산이 마르고 닳도록
하느님이 보우하사 우리나라 만세
무궁화 삼천리 화려 강산
대한 사람 대한으로 길이 보전하세

> 일반 줄비꿈이 동작하지 않는 환경(설정 및 버전에 따라)의 경우, '2번의 띄어쓰기'나 `<br>`를 활용할 수 있습니다.