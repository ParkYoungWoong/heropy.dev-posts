---
image: https://heropy.dev/postAssets/LWIk13/main.jpg
filename: html-elements
id: LWIk13
title: HTML 주요 요소와 속성, 한눈에 보기
createdAt: 2019-05-26
updatedAt: 2024-05-15
group: HTML
author:
  - ParkYoungWoong
tags:
  - HTML
description:
  웹 개발 프로젝트에 필요한 HTML 요소(Elements)와 속성(Attributes)에 대해 간단한 개요와 설명을 통해 웹 페이지를 설계하고 구현하는 데 필요한 정보를 알아봅니다. 이를 통해 웹 표준을 준수하는 동시에, 효과적이고 의미론적(Semantic) 마크업 구조를 구현할 수 있도록 돕습니다.
---

## 개요

웹 개발 프로젝트에 필요한 HTML 요소(Elements)와 속성(Attributes)에 대해 간단한 개요와 설명을 통해 웹 페이지를 설계하고 구현하는 데 필요한 정보를 알아봅니다.
이를 통해 웹 표준을 준수하는 동시에, 효과적이고 의미론적(Semantic) 마크업 구조를 구현할 수 있도록 돕습니다.

- HTML5 기준으로 작성합니다.
- 모든 브라우저에서 사용할 수 있어야 합니다.(IE 지원 불가는 별도 표시)
- Deprecated(더 이상 사용되지 않는) 요소나 속성은 제외합니다.
- 의미론적(Semantic)인 내용 위주로 작성합니다.
- 표시적 의미(화면에 표시되는 방식)로 사용되지 않음을 전제하므로 그에 대한 내용은 최대한 생략합니다.
- 빈 태그(Empty Tags)는 `<TAG />`와 같이 `/`를 포함하여 표시합니다.
- 해당 요소에 필수적으로 사용되어야 하는 속성(Required Attributes)은 설명에 `(필수)`를 표시합니다.(그 외는 모두 선택 속성)
- 개인적 경험에 의해 사용 빈도, 중요도, 난이도가 높은 요소는 강조/첨언 합니다.
- 개인적 경험에 의해 사용 빈도, 중요도, 난이도가 낮은 요소는 생략/간소화 합니다.

## 주요 범위 요소

HTML 문서의 기본 구조(범위)를 형성하는 요소입니다.
`lang` 속성은 전역 속성으로, `<html>`에서 사용하면 문서 전체의 언어를 지정합니다.

```html --caption=문서의 기본 구조
<!DOCTYPE html>
<html lang="ko">
  <head></head>
  <body></body>
</html>
```

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<html>` | HTML 문서의 범위를 지정. |  | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/html)
`<head>` | HTML 문서의 정보를 지정. |  | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/head)
`<body>` | HTML 문서의 구조를 지정. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/body)

## 메타데이터 요소

문서의 기본 정보를 지정하거나 다른 리소스와의 관계를 지정합니다. 
일부 메타데이터 요소는 브라우저와 검색 엔진 등에 제공하며 효과적인 SEO 최적화와 사용자 경험 향상에 기여합니다.
모두 `<head>` 요소 내에 포함돼야 합니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<title>` | 브라우저의 제목 표시줄이나 페이지 탭에 보여지는 문서의 제목을 지정. | | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/title)
`<base />` | HTML 문서에 포함된 모든 상대 URL들의 기준 URL를 지정.<br/>한 문서에 하나의 `<base />` 요소만 포함 가능.<br/>- `href`: 기준 URL<br/>- `target`: `target` 속성을 사용하는 요소(`<a>`)의 기본값 | | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/base)
`<link />` | 외부 리소스(HTML, CSS, Icon 등)의 연결 및 현재 문서와의 관계를 명시.<br/>- `rel`: (필수)현재 문서와 외부 리소스와의 관계([Link Types](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types))<br/>- `href`: 외부 리소스의 URL<br/>- `type`: 외부 리소스의 [MIME 타입](https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/MIME_types) | | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/link)
`<meta />` | 기타 메타데이터를 나타내기 위해 지정.<br/>(검색엔진이나 브라우저에 정보 제공)<br/>- `charset`: [문자인코딩 방식](https://www.iana.org/assignments/character-sets/character-sets.xhtml)<br/>- `name`: 메타 데이터의 이름([정보의 종류](https://developer.mozilla.org/ko/docs/Web/HTML/Element/meta#attr-name))<br/>- `http-equiv`: 서버/사용자 에이전트의 작동방식 변경에 대한 [지시](https://developer.mozilla.org/ko/docs/Web/HTML/Element/meta#attr-http-equiv)(HTTP 응답 헤더 제공)<br/>- `content`: `name`, `http-equiv`의 값 | | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/meta)
`<style>` | 문서나 문서 일부에 대한 스타일 정보(CSS)를 지정.<br/>- `type`: [MIME 타입](https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/MIME_types) | | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/style)  

## 콘텐츠 구분 요소

문서의 각 콘텐츠 구조를 의미론적으로 구분하기 위해 사용합니다.
기능적 차이는 없습니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<h1>`<br/>`<h2>`<br/>`<h3>`<br/>`<h4>`<br/>`<h5>`<br/>`<h6>` | 문서의 정보 계층을 구조화.(Heading)<br/>문서나 구분된 영역의 제목을 지정, 문서의 목차.<br/>숫자가 낮을수록 높은 단계(중요한)의 제목.<br/>한 문서에 하나의 `<h1>` 요소만 포함 가능. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Heading_Elements)
`<header>` | 문서의 헤더를 지정.<br/>주로 로고, 제목, 검색 등을 포함. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/header)
`<footer>` | 문서의 푸터를 지정.<br/>주로 작성자, 저작권, 관련 문서 등을 포함. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/footer)
`<main>` | 문서의 주 콘텐츠를 지정.<br/>한 문서에 하나의 `<main>` 요소만 포함 가능. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/main)
`<article>` | 독립적으로 구분되거나 재사용 가능한 영역을 지정.<br/>매거진, 신문 기사, 블로그 등.<br/>Heading(`<h1>`) 요소를 포함하여 식별.<br/>작성일자와 시간을 `<time>`의 `datetime` 속성으로 작성. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/article)
`<section>` | 문서의 일반적인 영역을 지정.<br/>Heading(`<h1>` ~ `<h6>`) 요소를 포함하여 식별. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/section)
`<aside>` | 문서의 별도 콘텐츠를 지정.<br/>주로 광고나 기타 링크 등의 사이드바를 지정. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/aside)
`<nav>` | 다른 페이지 링크를 제공하는 영역을 지정.(Navigation)<br/>주로 메뉴, 목차, 색인 등을 지정. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/nav)
`<address>` | 연락처 정보를 제공하기 위해 포함하여 사용. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/address)
`<div>` | 본질적으로 아무것도 나타내지 않는 콘텐츠 영역을 지정.(Division) | `block` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)

```html --caption=제목과 함께 사용하는 섹션 구분
<section>
  <h2>Title</h2>
  <div>Contents1</div>
  <div>Contents2</div>
</section>
```

## 텍스트 콘텐츠 요소

텍스트를 구조화하고 의미를 부여합니다.
정보의 가독성과 접근성을 향상시키는 역할을 합니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<ol>` | 정렬된 목록을 지정.(Ordered List)<br/>자식으로 `<li>`만 포함 가능.<br/>항목 순서는 중요도를 의미할 수 있음.<br/>`start`: 항목에 매겨지는 번호의 시작 값<br/>`type`: 항목에 매겨지는 번호의 유형 | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/ol)
`<ul>` | 정렬되지 않은 목록을 지정.(Unordered List)<br/>자식으로 `<li>`만 포함 가능. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/ul)
`<li>` | 목록의 각 항목.(List Item)<br/>단독으로 사용할 수 없으며, `<ol>` 혹은 `<ul>` 자식으로 포함돼야 함.<br/>`value`: 항목의 순서를 지정. | `list-item` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/li)
`<dl>` | 용어와 정의(설명)의 그룹을 지정.(Description List)<br/>`<dt>`, `<dd>`만 포함 가능.<br/>키(key)/값(value) 형태를 표시할 때 유용. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/dl)
`<dt>` | 용어를 지정.(Definition Term) | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/dt)
`<dd>` | 정의(설명)를 지정.(Definition Details) | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/dd)
`<p>` | 하나의 문단을 지정.(Paragraph)<br/>일반적으로 정보통신보조기기 등은 다음 문단으로 넘어갈 수 있는 단축키를 제공함. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/p)
`<hr />` | 문단의 분리를 위해 지정.(Horizontal Rule)<br/>표현적 관점에서 수평선으로 표시되지만, 의미적 관점으로만 사용해야 함. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/hr)
`<pre>` | 서식이 미리 지정된 텍스트를 지정.(Preformatted Text)<br/>텍스트의 공백과 줄바꿈을 유지하며 표시할 수 있음.<br/>기본적으로 Monospace 글꼴로 표시됨. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/pre)
`<blockquote>` | 일반적인 인용문을 지정.(Block Quotation)<br/>-`cite`: 인용된 정보의 URL | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/blockquote)

```html --caption=용어와 설명을 표시
<dl>
  <dt>Coffee</dt>
  <dd>Coffee is a brewed drink prepared from roasted coffee beans, the seeds of berries from certain Coffea species.</dd>
  <dt>Milk</dt>
  <dd>Milk is a nutrient-rich, white liquid food produced by the mammary glands of mammals.</dd>
</dl>
```

## 인라인 텍스트 요소

텍스트를 강조하거나 스타일을 적용해, 보다 가독성 높은 문서를 작성할 수 있습니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<a>` | 다른 URL로 연결할 수 있는 하이퍼링크를 지정.(Anchor)<br/>다른 페이지, 같은 페이지 위치(`#`, 해시 태그), 파일, 이메일 주소, 전화번호 등.<br/>- `download`: 이 요소가 리소스를 다운로드하는 용도로 사용됨을 의미<br/>- `href`: 링크 URL<br/>- `rel`: 현재 문서와 링크 URL의 관계([Link Types](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types))<br/>- `target`: 링크 URL의 표시(브라우저 탭) 위치<br/>- `type`: 링크 URL의 [MIME 타입](https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/MIME_types) | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/a)
`<abbr>` | 약어를 지정.(Abbreviation)<br/>주로 `title` 속성을 사용하여 전체 글자나 설명을 제공. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/abbr)
`<b>` | 문체가 다른 글자의 범위를 지정.(Bring Attention)<br/>특별한 의미를 가지지 않음.<br/>읽기 흐름에 도움을 주는 용도로 사용.<br/>다른 태그가 적합하지 않은 경우 마지막 수단으로 사용.<br/>기본적으로 글자가 두껍게(Bold) 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/b)
`<mark>` | 사용자의 관심을 끌기 위해 하이라이팅할 때 사용.(Mark Text)<br/>기본적으로 형광펜을 사용한 것처럼 글자 배경이 노란색(Yellow)으로 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/mark)
`<em>` | 단순한 의미 강조를 표시.(Emphasis)<br/>중첩할 수 있으며, 중첩될수록 강조 의미가 강해짐.<br/>정보통신보조기기 등에서 구두 강조로 발음됨.<br/>기본적으로 이탤릭체(Italic type)로 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/em)
`<strong>` | 의미의 중요성을 나타내기 위해 사용.(Strong Importance)<br/>기본적으로 글자가 두껍게(Bold) 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/strong)
`<i>` | 특별한 의미 없이, 평범한 글자와 구분(아이콘이나 특수기호 같은)하기 위해 사용.<br/>기본적으로 이탤릭체(Italic type)로 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/i)
`<dfn>` | 용어를 정의할 때 사용.(Definition)<br/>기본적으로 이탤릭체(Italic type)로 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/dfn)
`<cite>` | 창작물에 대한 참조를 지정.(Citation)<br/>책, 논문, 영화, TV 프로그램, 노래, 게임 등.<br/>기본적으로 이탤릭체(Italic type)로 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/cite)
`<q>` | 짦은 인용문을 지정.(Inline Quotation)<br/>긴 인용문을 지정할 경우 `<blockquote>`를 사용. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/q)
`<u>` | 밑줄이 있는 글자를 지정.(Underline)<br/>순수하게 꾸미는 용도의 요소로 사용.<br/>`<a>`와 헷갈릴 수 있는 위치에서 사용하지 않도록 주의.<br/>CSS `text-decoration: underline;` 사용을 권장함. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/u)
`<code>` | 컴퓨터 코드 범위를 지정.(Inline Code)<br/>기본적으로 Monospace 글꼴로 표시됨. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/code)
`<kbd>` | 텍스트 입력 장치(키보드)에서 사용자 입력을 나타내는 텍스트 범위를 지정.(Keyboard Input) | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/kbd)
`<sup>` | 위 첨자(`<sup>`)를 지정.(Superscripted text) | `inline` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/sup)
`<sub>` | 아래 첨자(`<sub>`)를 지정.(Subscript text) | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/sub)
`<time>` | 날짜나 시간을 나타내기 위한 목적으로 사용.<br/>- `datetime`: [유효한 날짜 문자](https://www.w3.org/TR/html51/infrastructure.html#dates-and-times) | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/time)
`<span>` | 본질적으로 아무것도 나타내지 않는 콘텐츠 영역을 지정. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/span)
`<br />` | 줄바꿈을 지정. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/br)

```html --caption=약어를 표시
Using <abbr title="HyperText Markup Language">HTML</abbr> is fun and easy!
```

```html --caption=창작물 참조를 표시
<cite>The Scream</cite> by Edward Munch. Painted in 1893.
```

```html --caption=키보드 입력을 표시
<p><kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>K</kbd></p>, <kbd>ESC</kbd>
```

```html --caption=위/아래 첨자로 수학식을 표시
X<sup>4</sup> + Y<sup>2</sup>, H<sub>2</sub>O
```

```html --caption=날짜를 표시
<p>
  The Cure will be celebrating their 40th anniversary on
  <time datetime="2018-07-07">July 7</time> in London's Hyde Park.
</p>
```

## 텍스트 수정 요소

텍스트의 추가, 수정, 삭제를 표시해, 변경 사항을 명확하게 전달합니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<ins>` | 새로 추가된(변경된) 텍스트의 범위를 지정.(Inserted Text)- `cite`: 변경을 설명하는 리소스의 URI<br/>- `datetime`: 변경이 일어난 [유요한 날짜 문자](https://www.w3.org/TR/html51/infrastructure.html#dates-and-times) | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/ins)
`<del>` | 삭제된(변경된) 텍스트의 범위를 지정.(Deleted Text)<br/>- `cite`: 변경을 설명하는 리소스의 URI<br/>- `datetime`: 변경이 일어난 [유요한 날짜 문자](https://www.w3.org/TR/html51/infrastructure.html#dates-and-times) | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/del)

## 멀티미디어 요소

이미지, 오디오, 비디오 등 다양한 멀티미디어 콘텐츠를 웹 페이지에 삽입할 수 있습니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<img />` | 이미지를 삽입.<br/>- `src`: 이미지 URL<br/>- `alt`: 이미지 대체 텍스트<br/>- `width`: 이미지 가로 너비<br/>- `height`: 이미지 세로 너비<br/>- `srcset`: 브라우저에게 제시할 이미지 URL과 원본 크기의 목록을 정의<br/>- `sizes`: 미디어 조건과 해당 조건일 때 이미지 최적화 크기의 목록을 정의 | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/img)
`<audio>` | 소리 콘텐츠(MP3)를 삽입.<br/>`autoplay`가 지정된 경우, `preload`는 무시됨.<br/>- `autoplay`: 준비되면 바로 재생<br/>- `controls`: 제어 메뉴를 표시<br/>- `loop`: 재생이 끝나면 다시 처음부터 재생<br/>- `preload`: 페이지가 로드될 때 파일을 로드할지의 지정(힌트 제공)<br/>- `src`: 콘텐츠 URL<br/>- `muted`: 음소거 여부 | `inline` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio)
`<video>` | 동영상 콘텐츠(MP4)를 삽입.<br/>- `autoplay`: 준비되면 바로 재생<br/>- `controls`: 제어 메뉴를 표시<br/>- `loop`: 재생이 끝나면 다시 처음부터 재생<br/>- `muted`: 음소거 여부<br/>- `poster`: 동영상 썸네일 이미지 URL<br/>- `preload`: 페이지가 로드될 때 파일을 로드할지의 지정(힌트 제공)<br/>- `src`: 콘텐츠 URL<br/>- `width`: 동영상 가로 너비<br/>- `height`: 동영상 세로 너비 | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/video)
`<figure>` | 이미지나 삽화, 도표 등의 영역을 지정. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/figure)
`<figcaption>` | `<figure>`에 포함되어 이미지나 삽화 등의 설명을 표시.(Figure Caption) | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/figcaption)

```html --caption=이미지와 설명을 표시
<figure>
  <img src="milk.jpg" alt="A milk">
  <figcaption>Milk is a nutrient-rich, white liquid food produced by the mammary glands of mammals.</figcaption>
</figure>
```

## 내장 콘텐츠 요소

외부 콘텐츠나 다른 웹 페이지를 현재 문서에 통합해, 웹 페이지의 기능을 확장하고 사용자에게 추가 정보를 제공할 수 있습니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<iframe>` | 다른 HTML 페이지를 현재 페이지에 삽입.<br/>- `name`: 프레임의 이름<br/>- `src`: 포함할 문서의 URL<br/>- `width`: 프레임의 가로 너비<br/>- `height`: 프레임의 세로 너비<br/>- `allowfullscreen`: 전체 화면 모드 사용 여부<br/>- `frameborder`: 프레임 테두리 사용 여부<br/>- `sandbox`: 보안을 위한 읽기 전용으로 삽입 | `inline` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)
`<canvas>` | [Canvas API](https://developer.mozilla.org/ko/docs/Web/HTML/Canvas)이나 [WebGL API](https://developer.mozilla.org/ko/docs/Web/API/WebGL_API)를 사용하여 그래픽이나 애니메이션을 랜더링.<br/>- `width`: 캔버스의 가로 너비<br/>- `height`: 캔버스의 세로 너비 | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Canvas/Tutorial/Basic_usage)

```html --caption=유튜브 동영상을 삽입하는 예제
<iframe width="1920" height="765" src="https://www.youtube.com/embed/bdPug9IWz-g" frameborder="0" allowfullscreen></iframe>
```

## 스크립트 요소

문서에서 자바스크립트 등의 스크립트(코드)를 직접 포함하거나 참조할 때 사용합니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<script>` | 스크립트 코드를 문서에 포함하거나 외부 스크립트 참조.<br/>- `async`: 스크립트의 비동기적(Asynchronously) 실행 여부<br/>- `defer`: 문서 파싱(구문 분석) 후 작동 여부<br/>- `src`: 참조할 외부 스크립트 URL<br/>- `type`: [MIME 타입](https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/MIME_types) | `none` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/script)
`<noscript>` | 스크립트를 지원하지 않는 경우에 삽입할 HTML을 정의. | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/noscript)

## 표 콘텐츠 요소

데이터를 구조화된 표 형태로 표현해, 정보를 체계적이고 이해하기 쉽게 정리합니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<table>` | 표를 지정.<br/>- `border`: 표 테두리 두께 | `table` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table)
`<tr>` | 표의 행을 지정.(Table Row) | `table-row` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr)
`<th>` | 표의 머리글 칸을 지정.(Table Header)<br/>- `abbr`: 열에 대한 간단한 설명<br/>- `headers`: 관련된 하나 이상의 다른 머리글 칸 `id` 속성 값<br/>- `colspan`: 확장하려는(병합) 열의 수<br/>- `rowspan`: 확장하려는(병합) 행의 수<br/>- `scope`: 자신이 누구의 '머리글 칸'인지 명시 | `table-cell` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th)
`<td>` | 표의 일반 칸을 지정.(Table Data)<br/>- `headers`: 관련된 하나 이상의 다른 머리글 칸 `id` 속성 값<br/>- `colspan`: 확장하려는(병합) 열의 수<br/>- `rowspan`: 확장하려는(병합) 행의 수 | `table-cell` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td)
`<caption>` | 표의 제목을 지정.<br/>열리는 TABLE 태그 바로 다음에 작성.  | `table-caption` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/caption)
`<colgroup>` | 열의 집합(Column Group).<br/>- `span`: 연속되는 열 수 | `table-column-group` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup)
`<col>` | 열을 지정.(Column)<br/>`<colgroup>`의 자식 요소로 사용.<br/>- `span`: 연속되는 열 수 | `table-column` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/col)
`<thead>` | 표의 머리글을 지정.(Table Head) | `table-header-group` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/thead)
`<tbody>` | 표의 본문을 지정.(Table Body) | `table-row-group` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tbody)
`<tfoot>` | 표의 바닥글을 지정.(Table Foot) | `table-footer-group` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tfoot)

```html --caption=표 요소 예시
<table>
  <caption>Fruits</caption>
  <colgroup>
    <col span="2" style="background-color: yellowgreen;">
    <col style="background-color: tomato;">
  </colgroup>
  <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>F123A</td>
      <td>Apple</td>
      <td>$22</td>
    </tr>
    <tr>
      <td>F098B</td>
      <td>Banana</td>
      <td>$19</td>
    </tr>
  </tbody>
</table>
```

## 양식 요소

사용자에게 데이터를 입력받고 처리하는 양식을 구성합니다.
이를 통해 사용자와의 상호작용을 가능하게 하고, 데이터를 수집하고 처리할 수 있게 합니다.

요소 | 설명 | 표시 특성 | 참조
--|--|--|--
`<form>` | 웹 서버에 정보를 제출하기 위한 양식 범위를 정의.<br/>- `action`: 전송한 정보를 처리할 웹페이지의 URL<br/>- `autocomplete`: 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부<br/>- `method`: 서버로 전송할 [HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html) 방식<br/>- `name`: 고유한 양식의 이름<br/>- `novalidate`: 서버로 전송시 양식 데이터의 유효성을 검사하지 않도록 지정<br/>- `target`: 서버로 전송 후 응답받을 방식을 지정 | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/form)
`<input />` | 사용자에게 입력 받을 데이터 양식.<br/>- `autocomplete`: 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부<br/>- `autofocus`: 페이지가 로드될 때 자동으로 포커스<br/>- `checked`: 양식이 선택되었음을 표시<br/>- `disabled`: 양식을 비활성화<br/>- `form`: `<form>`의 `id` 속성 값<br/>- `list`: 참조할 `<datalist>`의 `id` 속성 값<br/>- `max`: 지정 가능한 최대 값<br/>- `min`: 지정 가능한 최소 값<br/>- `maxlength`: 입력 가능한 최대 문자 수<br/>- `multiple`: 둘 이상의 값을 입력 할 수 있는지 여부<br/>- `name`: 양식의 이름<br/>- `placeholder`: 사용자가 입력할 값의 힌트<br/>- `readonly`: 수정 불가한 읽기 전용<br/>- `step`: 유효한 증감 숫자의 간격<br/>- `src`: 이미지의 URL<br/>- `alt`: 이미지의 대체 텍스트<br/>- `type`: 입력 받을 데이터의 종류<br/>- `value`: 양식의 초기 값<br/>- `type=button`: 일반 버튼<br/>- `type=checkbox`: 체크박스<br/>- `type=color`: 색상<br/>- `type=email`: 이메일<br/>- `type=file`: 파일<br/>- `type=hidden`: 보이지 않지만 전송할 양식<br/>- `type=image`: 이미지 제출 버튼<br/>- `type=number`: 숫자<br/>- `type=password`: 비밀번호<br/>- `type=radio`: 라디오 버튼<br/>- `type=range`: 범위 컨트롤<br/>- `type=reset`: 초기화<br/>- `type=search`: 검색<br/>- `type=submit`: 제출 버튼<br/>- `type=tel`: 전화번호<br/>- `type=text`: 일반 텍스트<br/>- `type=url`: 절대 URL | `inline-block` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
`label` | 라벨 가능 요소([labelable](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content_categories#Form_labelable))의 제목(Caption).<br/>`for` 속성으로 라벨 가능 요소를 참조하거나 콘텐츠로 포함.<br/>- `for`: 참조할 라벨 가능 요소의 `id` 속성 값 | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/label)
`button` | 선택 가능한 버튼을 지정.<br/>- `autofocus`: 페이지가 로드될 때 자동으로 포커스<br/>- `disabled`: 버튼을 비활성화<br/>- `form`: `<form>`의 `id` 속성 값<br/>- `name`: 폼 데이터와 함께 전송되는 버튼의 이름<br/>- `type`: 버튼의 타입 | `inline-block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/button)
`textarea` | 여러 줄의 일반 텍스트 양식.<br/>- `autocomplete`: 사용자가 이전에 입력한 값으로 자동 완성 기능을 사용할 것인지 여부<br/>- `autofocus`: 페이지가 로드될 때 자동으로 포커스<br/>- `disabled`: 양식을 비활성화<br/>- `form`: `<form>`의 `id` 속성 값<br/>- `maxlength`: 입력 가능한 최대 문자 수<br/>- `name`: 양식의 이름<br/>- `placeholder`: 사용자가 입력할 값의 힌트<br/>- `readonly`: 수정 불가한 읽기 전용<br/>- `rows`: 양식의 줄 수 | `inline-block` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea)
`fieldset` | 양식의 관련 요소들을 그룹화.<br/>- `disabled`: 그룹 내 모든 양식 요소를 비활성화<br/>- `form`: 그룹이 속할 하나 이상의 `<form>`의 `id` 속성 값<br/>- `name`: 그룹의 이름 | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/fieldset)
`legend` | `<fieldset>`의 제목을 지정. | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/legend)
`select` | 드롭다운 목록을 지정.<br/>- `autofocus`: 페이지가 로드될 때 자동으로 포커스<br/>- `disabled`: 양식을 비활성화<br/>- `form`: `<form>`의 `id` 속성 값<br/>- `multiple`: 여러 옵션을 선택할 수 있는지 여부<br/>- `name`: 양식의 이름<br/>- `size`: 한 번에 보여지는 옵션의 수 | `inline-block` | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select)
`datalist` | 자동완성 목록을 지정.<br/>- `id`: `<input>`의 `list` 속성과 바인딩 | `none` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/datalist)
`optgroup` | `<option>`을 그룹화.<br/>- `disabled`: 그룹을 비활성화<br/>- `label`: 그룹의 이름 | `block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/optgroup)
`option` | 드롭다운이나 자동완성 목록의 옵션을 지정.<br/>- `disabled`: 옵션을 비활성화<br/>- `label`: 표시될 옵션의 제목<br/>- `selected`: 옵션이 선택되었음을 표시<br/>- `value`: 양식으로 제출될 값 | `inline` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/option)
`progress` | 작업의 완료 진행률을 표시.<br/>- `max`: 작업의 총량<br/>- `value`: 작업의 진행량 | `inline-block` | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/progress)

```html --caption=입력 요소의 다양한 데이터 타입 지정
<input type="button" />
<input type="checkbox" />
<input type="file" />
<input type="text" />
```

```html --caption=라벨 가능 요소의 참조와 포함
<!-- 라벨 가능 요소를 참조 -->
<input type="checkbox" id="user-agreement" />
<label for="user-agreement">동의하십니까?</label>

<!-- 라벨 가능 요소를 포함 -->
<label>
  <input type="checkbox" />
  동의하십니까?
</label>
```

```html --caption=같은 목적의 양식을 그룹화
<form>
  <fieldset>
    <legend>Coffee Size</legend>
    <label>
        <input type="radio" name="size" value="tall" />
        Tall
    </label>
    <label>
        <input type="radio" name="size" value="grande" />
        Grande
    </label>
    <label>
        <input type="radio" name="size" value="venti" />
        Venti
    </label>
  </fieldset>
</form>
```

```html --caption=선택 메뉴를 표시
<select>
  <optgroup label="Coffee">
    <option>Americano</option>
    <option>Caffe Mocha</option>
    <option label="Cappuccino" value="Cappuccino"></option>
  </optgroup>
  <optgroup label="Latte" disabled>
    <option>Caffe Latte</option>
    <option>Vanilla Latte</option>
  </optgroup>
  <optgroup label="Smoothie">
    <option>Plain</option>
    <option>Strawberry</option>
    <option>Banana</option>
    <option>Mango</option>
  </optgroup>
</select>
```

```html --caption=자동완성 목록을 표시
<input type="text" list="fruits">

<datalist id="fruits">
  <option>Apple</option>
  <option>Orange</option>
  <option>Banana</option>
  <option>Mango</option>
  <option>Fineapple</option>
</datalist>
```

```html --caption=작업의 진행률을 표시
<progress value="70" max="100">70 %</progress>
```

## 전역 속성

모든 HTML 요소에서 공통으로 사용할 수 있는 전역 속성(Global Attributes)입니다.

속성 | 설명 | 참조
--|--|--
`id` | 문서 전체에서 고유한 식별자(idenifier, ID)를 정의. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/id)
`class` | 공백으로 구분된 요소의 별칭을 지정. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/class)
`style` | 요소에 적용할 CSS를 선언. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/style)
`title` | 요소의 정보(설명)을 지정. | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/title)
`lang` | 요소의 언어([ISO 639-1](https://ko.wikipedia.org/wiki/ISO_639-1_%EC%BD%94%EB%93%9C_%EB%AA%A9%EB%A1%9D))를 지정. | [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/lang)
`data-*` | 사용자 정의 데이터 속성을 지정.<br/>HTML에 JS에서 이용할 수 있는 데이터를 저장하는 용도. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/data-*)
`draggable` | 요소가 [Drag and Drop API](https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API)를 사용 가능한지 여부를 지정. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/draggable)
`hidden` | 요소를 숨김. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/hidden)
`tabindex` | `Tab`키를 이용해 요소를 순차적으로 포커스 탐색할 순서를 지정.<br/>- [대화형 콘텐츠(Interactive Content)](https://developer.mozilla.org/ko/docs/Web/Guide/HTML/Content_categories#%EB%8C%80%ED%99%94%ED%98%95_%EC%BD%98%ED%85%90%EC%B8%A0)는 기본적으로 코드 순서대로 탭 순서가 지정됨.<br/>- 비대화형 콘텐츠에 `tabindex="0"`을 지정하여 대화형 콘텐츠와 같이 탭 순서를 사용.<br/>- `tabindex="-1"`을 통해 포커스는 가능하지만 탭 순서에서 제외 가능.<br/>- `tabindex="1"` 이상의 양수 값은 논리적 흐름을 방해하기 때문에 사용을 추천하지 않음. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/tabindex)
`contenteditable` | 요소의 사용자 편집 여부를 지정. | [MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/contenteditable)

```html --caption=각 요소의 언어를 지정
<p lang="en">This paragraph is English</p>
<p lang="ko">이 단락은 한글입니다.</p>
<p lang="fr">Ce paragraphe est défini en français.</p>
```

```html --caption=사용자 정의 데이터 속성을 지정
<div id="me" data-my-name="Heropy" data-my-age="851">Heropy</div>

<script>
  const meEl = document.getElementById('me')
  console.log(meEl.dataset.myName) // 'Heropy'
  console.log(meEl.dataset.myAge) // '851'
</script>
```

```html --caption=드래그앤드롭 가능
<div draggable="true">The element to drag.</div>
```

```html  --caption=양식 요소를 숨긴 상태로 '전송'만 가능
<form id="hidden-form" action="/action" hidden>
  <!-- 숨겨진 양식.. -->
</form>
<button form="hidden-form" type="submit">전송</button>
```

```html --caption=포커스 탐색 순서를 지정
<h1 tabindex="0">Sign In</h1>
<label>Username: <input type="text"></label>
<label>Password: <input type="password"></label>
<label>PS: <input type="text" tabindex="-1"></label>
<input type="submit" value="Sign In">
```