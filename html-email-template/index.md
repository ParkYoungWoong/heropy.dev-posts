---
id: Y4FoEnQ
filename: html-email-template
title: HTML Email Template 만들기
createdAt: 2018-12-30
group: HTML
tags:
  - html
  - email
description:  
  서비스 이메일 푸쉬에 사용할 HTML Email Template를 제작하기 위해 필요한 내용들을 살펴봅니다. 표준 코딩이 아니기 때문에 주의해야 하는 중요한 개념들을 정리합니다. 
---

우리는 웹을 위해 HTML, CSS를 작성할 때 표준을 준수해야 합니다.
표준은 누구나 지켜야 하는 규칙이기 때문에 일종의 작성 가이드 역할을 할 수 있습니다.
그러나 이메일(Email)에는 표준이 없습니다.
수 많은 클라이언트의 랜더링 가능성을 고려해야 하며, 제공하는 이메일(서비스)의 성격에 따라 고려해야 하는 클라이언트가 늘어나거나 줄어들 수 있습니다.

<!-- toc -->

# HTML Email Template

다양한 랜더링 가능성을 고려하다 보면 `<div>` 태그나 `margin` 속성 같이 표준 코딩에서 자주 사용하는 개념을 사용할 수 없거나 거의 모든 부분에서 `<table>`, `<td>` 태그에 의존하므로 일반적인 표준 HTML과 CSS의 작성 방식으로는 이메일 템플릿을 소화하기 어렵습니다.

이메일 템플릿은 하위 호환성을 고려하는 것이 좋습니다.
특히 `<table>`를 사용하는 코딩에 익숙하다면 많은 도움이 될 것입니다.

## 이메일 클라이언트

HTML 이메일 템플릿을 제작할 때 고려해야 할 가장 일반적인 이메일 클라이언트 목록을 살펴봅시다.

### 모바일 이메일 클라이언트

Android 2.3 및 4.0
iPhone 5 iOS 6
iPhone 4S iOS 6
iPhone 3GS iOS 5
iPad 2 iOS 6
BlackBerry OS 4 & 5
Symbian S60
Windows Phone 7.5

### 데스크톱 이메일 클라이언트

Apple Mail 4, 5, 6
Lotus Notes 8.5
Lotus Notes 8
Thunderbird
Windows Live Mail
Outlook 2013 (v15)
Mac 용 Outlook 2011
Outlook 2010 (v14)
Outlook 2007 (v12)
Outlook 2003 (v11)
Outlook 2002 / XP (v10)
Outlook 2000 (v9)

### 웹 메일 클라이언트

AOL Mail (on any browser)
Gmail (on any browser)
Outlook.com (on any browser)
Yahoo! (on any browser)

## 준비하기

### DOCTYPE

[Doctype](https://www.w3.org/wiki/Choosing_the_right_doctype_for_your_HTML_documents)은 이메일 클라이언트에게 HTML 유형을 알려주고 [W3C Validator](https://validator.w3.org/) 같은 도구를 사용하여 HTML 품질 검사를 할 수 있습니다.
XHTML 1.0 Transitional doctype을 사용하면 이메일 클라이언트에서 신뢰할 수 있는 방식으로 유효성을 검사하고 이메일 렌더링에 도움이 됩니다.

일부 이메일 클라이언트는 제공하는 Doctype을 자신의 Doctype으로 대체합니다.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

</html>
```

### Head

텍스트와 특수 문자가 올바르게 표시되도록 문자 인코딩 방식(`UTF-8`)을 설정합니다.
Doctype을 XHTML로 설정했기 때문에 `Content-Type` 선언을 포함해야 합니다.

추가로 제목(title), 디바이스의 화면 영역([viewport](https://www.w3schools.com/css/css_rwd_viewport.asp))에 대해 설정합니다.
XHTML은 빈(Empty) 태그는 반드시 닫아야(`/`) 합니다. (`<link/>`, `<img/>`, `<br/>`)

```html
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <title>HTML Email Template</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
</head>
```

### Body

일부 이메일 클라이언트는 `<body>`를 제거합니다.
따라서 가장 바깥쪽에서 `<body>` 대신 사용될 Container로 `<table>`를 생성합니다.
Style 적용을 위해 `id="bodyTable"`을 추가합니다.

이메일 템플릿의 가로 너비로 600px은 가장 안전한 최대 가로 너비이며, 다양한 해상도의 이메일 클라이언트에 최적화되어 있습니다.
800px까지는 실용적인 상한선으로 넘지 않는 것이 좋습니다.

```html
<body>
  <!-- OUTERMOST CONTAINER TABLE -->
  <table border="0" cellpadding="0" cellspacing="0" width="100%" id="bodyTable">
    <tr>
      <td>

        <!-- 600px - 800px CONTENTS CONTAINER TABLE -->
        <table border="0" cellpadding="0" cellspacing="0" width="600">
          <tr>
            <td>

            </td>
          </tr>
        </table>

      </td>
    </tr>
  </table>
</body>
```

### Style

인라인 작성 방식을 추천하지만 편의성을 위해 일부 스타일은 `<style>`로 작성해 포함하거나 나중에 인라인 작성으로 옮길 수 있습니다.
만약 NPM을 사용할 수 있는 환경이라면 `<link>`로 연결된 CSS 파일이나 `<style>`로 더 쉽게 작성하고, [inline-email](https://www.npmjs.com/package/inline-email) 같은 라이브러리를 통해 추후 간단하게 인라인 방식으로 병합할 수 있습니다.

```html
<style type="text/css">
  /* GENERAL STYLE RESETS */
  body, #bodyTable { width:100% !important; height:100% !important; margin:0; padding:0; }
  #bodyTable { padding: 20px 0 30px 0; background-color: #ffffff; }
  img, a img { border:0; outline:none; text-decoration:none; }
  .imageFix { display:block; }
  table, td { border-collapse:collapse; }
</style>
```

다음과 같이 클라이언트 규약에 일부 규칙을 추가하여 몇 가지 단점을 수정할 수 있습니다.

> 다음 규칙은 추후 인라인 방식으로 병합할 경우를 대비해 사용 직전에 별도 포함해야 합니다.

```html
<style type="text/css">
  /* CLIENT-SPECIFIC RESETS */
  /* Outlook.com(Hotmail)의 전체 너비 및 적절한 줄 높이를 허용 */
  .ReadMsgBody{ width: 100%; }
  .ExternalClass{ width: 100%; }
  .ExternalClass, .ExternalClass p, .ExternalClass span, .ExternalClass font, .ExternalClass td, .ExternalClass div { line-height: 100%; }
  /* Outlook 2007 이상에서 Outlook이 추가하는 테이블 주위의 간격을 제거 */
  table, td { mso-table-lspace: 0pt; mso-table-rspace: 0pt; }
  /* Internet Explorer에서 크기가 조정된 이미지를 렌더링하는 방식을 수정 */
  img { -ms-interpolation-mode: bicubic; }
  /* Webkit 및 Windows 기반 클라이언트가 텍스트 크기를 자동으로 조정하지 않도록 수정 */
  body, table, td, p, a, li, blockquote { -ms-text-size-adjust: 100%; -webkit-text-size-adjust: 100%; }
</style>
```

## 작성하기

### table, tr, td

이메일의 구조를 정상적으로 제공하려면 `<div>`를 사용하지 않고 `<table>`로 작성해야 합니다.
일반적으로 'TABLE 코딩'이라 불리는 이 방법은 중첩된 테이블을 많이 사용하기 때문에 TABLE 구조의 마크업이 완료된 후 스타일을 입히는 것이 좋습니다.

> 수정이 까다롭기 때문에 레이아웃이 확정된 후 작업하는 것이 좋습니다.

`<thead>`, `<tbody>`, `<colgroup>`과 같은 `<table>`과 관련된 다른 태그들을 피하는 것이 좋습니다.
가장 가볍고 안전한 방법은 `<table>`, `<tr>`, `<td>` 이 3개의 태그만 활용하는 것입니다.

### HTML 속성 및 인라인 스타일

일부 이메일 클라이언트는 `<head>`를 제거하거나 `<style>`를 제대로 지원하지 않습니다.
따라서 HTML 속성으로 테이블을 구조화하는 것이 좋습니다.

특히 `<table>`은 다음과 같이 초기화해서 사용하는 것이 좋습니다.

```HTML
<table border="0" cellpadding="0" cellspacing="0" width="100%"></table>
```

#### table

속성 | 값 | 의미
--|--|--
border | `1`<br/>`0` | 선의 유무
cellpadding | Pixels | 셀(td)의 내부 여백
cellspacing | Pixels | 셀의 사이의 너비
width | Pixels<br/>`%` | 테이블의 가로 너비

#### td

속성 | 값 | 의미
--|--|--
align | `left`<br/>`right`<br/>`center`<br/>`justify`<br/>`char` | 셀의 내용을 수평 정렬
valign | `top`<br/>`middle`<br/>`bottom`<br/>`baseline` | 셀의 내용을 수직 정렬
bgcolor | HEX Colors | 셀의 색상(ex> `#ffffff`)
width | Pixels<br/>`%` | 셀의 가로 너비
height | Pixels<br/>`%` | 셀의 세로 너비

인라인 스타일이란 `<td style="color: #ff0000;">`과 같이 HTML 속성으로 스타일을 작성하는 것을 말합니다.
이를 사용하면 `<style>`를 제대로 지원하지 않는 경우 유용하며 추천하는 방법입니다.

> 인라인 스타일은 스타일 우선순위가 높기 때문에 `<style>`나 외부 CSS 파일과 혼합해서 사용할 경우 덮어써지는 경우가 많으니 주의합니다.

### 중첩 테이블

많은 경우 `colspan`, `rowspan` 속성 지원이 되질 않습니다.
따라서 다음과 같이 셀을 병합(Merge)하는 방식은 피해야 합니다.

![Table data colspan](/Y4FoEnQ/html_email_template_table_colspan.jpg)

```HTML
<table border="0" cellpadding="0" cellspacing="0" width="100%">
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td colspan="3"></td>
  </tr>
</table>
```

테이블을 중첩해 병합된 것과 같은 효과를 만들 수 있습니다.
좀 더 복잡하지만 거의 모든 이메일 클라이언트에서 안전하게 랜더링 됩니다.

![Nested Table data](/Y4FoEnQ/html_email_template_table_nested.jpg)

```html
<table border="" cellpadding="0" cellspacing="0" width="100%">
  <tr>
    <td>
      <table border="" cellpadding="0" cellspacing="0" width="100%">
        <tr>
          <td></td>
          <td></td>
          <td></td>
        </tr>
      </table>
    </td>
  </tr>
  <tr>
    <td>
      <table border="" cellpadding="0" cellspacing="0" width="100%">
        <tr>
          <td></td>
          <td></td>
        </tr>
      </table>
    </td>
  </tr>
  <tr>
    <td>
      <table border="" cellpadding="0" cellspacing="0" width="100%">
        <tr>
          <td></td>
        </tr>
      </table>
    </td>
  </tr>
</table>
```

### 색상

호환성을 위해 `#ffffff`처럼 작성하는 Hexadecimal Colors를 사용합니다.
RGB, RGBA, HSV 같은 색상은 일부 이메일 클라이언트에서 지원하지 않습니다.

> `#fff`와 같은 축약형은 사용하지 않도록 주의합니다.

CSS `background` 속성보다는 HTML `bgcolor` 속성을 이용하세요.

```html
<td bgcolor="#ff0000"></td>
```

### 단일 클래스

`class` 속성의 값을 다중으로 작성하지 마세요.
하나의 단일 값으로 작성해야 합니다.

```html
<!-- MULTIPLE VALUES -->
<td class="table-data description bold"></td>

<!-- SINGLE VALUE -->
<td class="description"></td>
```

### CSS 속성

다음과 같이 CSS 단축 속성을 사용하지 마세요.

```css
td {
  font: 16px / 1.4 Arial, sans-serif;
}
```

개별 속성을 사용하세요.

```css
td {
  font-size: 16px;
  line-height: 1.4;
  font-family: Arial, sans-serif;
}
```

### 이미지

HTML 이메일에 이미지를 사용할 수 있지만 몇 가지 주의사항이 있습니다.

- 절대경로를 사용
- 용량은 250kb 미만으로 유지
- 가로/세로 너비(width, height)를 입력
- 대체 텍스트(alt)를 입력

이미지를 제거하는 일부 이메일 클라이언트를 위해 `width`, `height`, `alt` 속성을 꼭 입력하세요.

```html
<img src="http://via.placeholder.com/200x100" alt="Some image" width="200" height="100">
```

#### 고정 이미지 삽입

많은 경우 `<table>`은 반응형 레이아웃에 적합하지 않기 때문에 고정된 레이아웃을 유지하여 작성하는데, 일부 이메일 클라이언트에서는 지정한 너비와 상관없이 디바이스 너비로 표시되도록 수정되는 경우가 있습니다.
이럴 때는 지정한 너비와 같은 너비의 이미지를 삽입하여 문제를 해결할 수 있습니다.

단순히 지정한 테이블의 너비를 유지할 용도로 사용하는 것이기 때문에 화면에 표시되지 않도록 다음과 같이 설정합니다.

```HTML
<td style="font-size: 0; line-height: 0; height: 0;" height="0">
  <img alt="" src="http://via.placeholder.com/600x1" style="display: block;" width="600" height="0"/>
</td>
```

Desktop Gmail(Chrome)에서 확인한 이메일 레이아웃은 다음과 같습니다.

![HTML Email template desktop](/Y4FoEnQ/html_email_template_desktop.jpg)

Mobile Gmail(Android)에서 확인한 레이아웃에는 변화가 있습니다.
의도한 결과가 아니라면 Text 줄바꿈이나 각 셀의 너비가 임의 조정되는 등의 문제가 있을 수 있습니다.

![HTML Email template mobile](/Y4FoEnQ/html_email_template_mobile.jpg)

고정 이미지를 삽입하면 Desktop에서 확인한 레이아웃과 동일하게 표시할 수 있습니다.
단, 이 경우 전반적인 화면 축소를 고려해야 합니다.

> 600px을 기준으로 했다면 전반적인 화면 축소는 별문제가 되지 않을 것입니다.

![HTML Email template mobile use to fixed image](/Y4FoEnQ/html_email_template_mobile_use_to_fixed_image.jpg)

### 여백

CSS의 `margin`은 사용할 수 없습니다.
대신 `padding`과 셀의 너비로 여백을 생성할 수 있습니다.

`padding`을 사용할 경우 top, bottom, left, right 값을 모두 작성해야 합니다.

```html
<td style="padding: 0 0 30px 0"></td>
```

조금 불편할 수 있지만, 사실 가장 안전한 방식은 다음과 같이 개별 속성을 사용하는 것입니다.

```html
<td style="padding-top: 0; padding-right: 0; padding-bottom: 30px; padding-left: 0;"></td>
```

만약 CSS Pre-processor로 SCSS를 사용한다면 중첩 속성을 이용해 편리하게 작성할 수 있습니다.

```scss
td {
  padding: {
    top: 0;
    right: 0;
    bottom: 30px;
    left: 0;
  }
}
```

내부 여백이 아닌 외부 여백을 활용할 경우는 여백 위치(여백으로 사용할)에 빈 셀을 추가합니다.
빈 셀은 공백 문자(`&nbsp`)를 가지고 있습니다.

```html
<!-- HORIZONTAL MARGIN 30px -->
<td width="30" style="font-size: 0; line-height: 0;">&nbsp;</td>

<!-- VERTICAL MARGIN 30px -->
<tr>
  <td height="30" style="font-size: 0; line-height: 0;">&nbsp;</td>
</tr>
```

### Text

`<font>`, `<b>`, `<i>`, `<u>` 같은 스타일을 내포하는 태그와 같이 사용하면 더 안전합니다.

```html
<style type="text/css">
  .bold {
    font-weight: bold;
  }
</style>
<td>
  HTML <b class="bold">이메일</b> 템플릿
</td>
```

스타일과 `<font>`를 함께 쓰는 것은 링크의 기본색인 파란색이 절대로 나타나지 않게 하기 위한 최선의 방법입니다.

```html
<td>
  <a href="https://google.com" target="_blank" style="color: #ff0000;"><font color="#ff0000">GOOGLE</font></a>
</td>
```

그러나 `<p>`, `<h1>`, `<h2>`... 같은 단락, 제목 태그는 사용하지 마세요.
이는 이메일 클라이언트 전체에서 스타일 일관성이 없이 랜더링 되며 수정하기 매우 까다롭습니다.

> 대부분의 경우 `<td>`로 작성하면 됩니다.

### 조건부 주석(Conditional Comments)

`mso`(Microsoft Outlook) 키워드를 조건부 주석에 사용할 수 있습니다.

```html
<td>
  <!--[if mso]>
    OUTLOOK CONTENTS
  <![endif]-->
  <!--[if !mso]>
    NON-OUTLOOK CONTENTS
  <![endif]-->
  <!--[if (gte mso 9)|(IE)]>
    GREATER THAN EQUAL OUTLOOK 9 or INTERNET EXPLORER
  <![endif]-->
</td>
```

- Outlook 2000: Version 9
- Outlook 2002: Version 10
- Outlook 2003: Version 11
- Outlook 2007: Version 12
- Outlook 2010: Version 14
- Outlook 2013: Version 15

| 기호 | 뜻 | 예시 | 예시 해석 |
|:---:|:---:|:---:|:---:|
| `!` | 부정<br/>(not) | `<!--[if !IE]><![endif]-->` | IE브라우저가 아닐 때 |
| `lt` | 작다, 미만<br/>(less than) | `<!--[if lt IE 9]><![endif]-->` | IE9 미만 |
| `lte` | 작거나 같다, 이하<br/>(less than equal) | `<!--[if lte IE 8]><![endif]-->` | IE8 이하 |
| `gt` | 크다, 초과<br/>(greater than) | `<!--[if gt IE 6]><![endif]-->` | IE6 초과 |
| `gte` | 크거나 같다, 이상<br/>(greater than equal) | `<!--[if gte IE 7]><![endif]-->` | IE7 이상 |
| `&` | 그리고<br/>(and) | `<!--[if (gt IE 6) & (lte IE 9)]><![endif]-->` | IE6 초과 ~ IE9 이하 |
| <code>&#124;</code> | 또는<br/>(or) | - | - |

### 방탄 버튼(Bulletproof Buttons)

많은 경우 테이블에는 이미지 버튼이 사용되어 왔습니다.
하지만 이미지 버튼은 이메일 클라이언트가 이미지 사용을 제거하는 경우 링크가 동작하지 않는 중요한 이슈가 발생하게 됩니다.
이런 경우 Microsoft VML(Vector Markup Language)를 통해서 해결하는 방법이 있습니다.

```html
<td>
  <!--[if mso]>
    <v:roundrect xmlns:v="urn:schemas-microsoft-com:vml" xmlns:w="urn:schemas-microsoft-com:office:word" href="https://google.com" style="height: 40px; v-text-anchor: middle; width:200px;" arcsize="50%" strokecolor="#1caeba" fillcolor="#2bcae3">
      <w:anchorlock/>
      <center style="color:#147e94;font-family:sans-serif;font-size:13px;font-weight:bold;">Button</center>
    </v:roundrect>
  <![endif]-->
  <a href="https://google.com"
  style="background-color: #2bcae3; border: 1px solid #1caeba; border-radius: 20px; color: #147e94; display: inline-block; font-family: sans-serif; font-size: 13px; font-weight: bold; line-height: 40px; text-align: center; text-decoration: none; width: 200px; -webkit-text-size-adjust: none; mso-hide: all;">Button</a>
</td>
```

하위 호환성을 고려하는 조금 더 쉬운 방법이 있습니다.
단, 버튼 전체 영역을 링크 범위로 설정할 수 없습니다.

```html
<td bgcolor="#2bcae3" align="center" width="200" style="border: 1px solid #1caeba; border-radius: 20px; -webkit-text-size-adjust: none;">
  <a href="https://google.com" style="color: #147e94; font-family: sans-serif; font-size: 13px; font-weight: bold; line-height: 40px; text-decoration: none;"><font color="#147e94">Button</font></a>
</td>
```

![Bulletproof Buttons](/Y4FoEnQ/html_email_template_bulletproof_button.jpg)

## 검증

작업한 문서를 [W3C Validator](https://validator.w3.org/)에서 검사합니다.
XHTML에 익숙하지 않다면 특히 검사 결과를 잘 살펴봐야 합니다.

# 참고 자료(References)

https://templates.mailchimp.com/development/html/
https://webdesign.tutsplus.com/tutorials/what-you-should-know-about-html-email--webdesign-12908
https://www.campaignmonitor.com/css/text-fonts/font-face/
https://litmus.com/community/learning/13-foundations-email-coding-101