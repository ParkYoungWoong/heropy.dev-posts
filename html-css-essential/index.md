---
id: TTEiUup
filename: html-css-essential
title: 입문자에게 추천하는 HTML, CSS 첫걸음
createdAt: 2019-04-24 00:00:00
thumbnail: html
group: HTML
tags:
  - html
  - css
---

<!-- toc -->

# 개요

웹(Web)을 구성하는 HTML, CSS, JS의 이해와 학습은 단순히 기술을 배우는 것으로 그치지 않고 웹과 모바일 그리고 IT 전반의 과거, 현재, 미래를 이해하는 데 많은 도움을 줍니다.
그리고 실무적으로 Product를 보다 구조적인 관점에서 볼 수 있는 능력을 키울 수 있습니다.
특히 Product 개발과 관련해 밀접하게 협업하는 기획, 디자인, 기술 영업 등의 직군에서 많은 도움이 될 수 있습니다.
이런 이유로 여러 기업에서 비전공자에게 개발 경험을 요구하는 경우가 상당히 많아졌습니다.

HTML, CSS를 학습하기 전에 필요한 지식을 최대한 정리했습니다.

> 조금 어렵다고 판단되는 내용은 건너뛰어도 좋습니다!  

## HTML, CSS 그리고 JavaScript

![HTML](/css/images/vendor_icons/html5.png)

HTML(Hyper Text Markup Language)은 페이지에 제목, 문단, 표, 이미지, 동영상 등을 정의하고 그 구조와 의미를 부여하는 정적 언어로 웹의 구조를 담당합니다.
HTML으로 화면을 예쁘게 만들려고 시도하지 마세요!(그렇게 할 수도 없지만..)
온전히 튼튼한 구조(Semantic)를 만드는 것에만 집중해야 합니다.

![CSS](/css/images/vendor_icons/css3.png)

CSS(Cascading Style Sheets)는 마크업 언어(HTML, XML 등)가 실제 표시되는 방법(색상, 크기, 폰트, 레이아웃 등)을 지정하여 콘텐츠 구조를 꾸며주는 정적 언어로 웹의 시각적인 표현을 담당합니다.
예쁘게 만드는 것만 집중할 수 있습니다.
적당한 크기와 아름다운 색상, 원하는 위치를 지정하는데 집중할 수 있습니다.

![JavaScript](/css/images/vendor_icons/javascript.png)

JS(JavaScript)는 콘텐츠를 바꾸고 움직이는 등 페이지를 동적으로 꾸며주는 역할을 하는 프로그래밍 언어로 웹의 동적 처리를 담당합니다.
JS는 HTML과 CSS를 동원해서 그들의 업무(구조, 시각적 표현 등)도 담당할 수 있지만, 그들만큼 잘하진 못하기 때문에(성능적으로) 되도록 동적 처리에만 집중해야 합니다.

집을 지을 때 골조 전문, 미장 전문, 인테리어 전문 등 효율적인 작업을 위해 각 분야가 나뉘듯 웹 페이지를 제작할 때 각 언어의 역할을 다른 언어가 대체하지 않도록 주의해야 하며, 각 역할이 제대로 수행되도록 구조적, 기술적으로 언어(코드)를 최적화시킬 필요가 있습니다.
(많은 입문자가 실전 과정으로 넘어갈 때 이 3가지의 단순한 역할을 도대체 왜 하나하나 파일과 폴더별로 구분하고 더 복잡하게 작성하는지 의아해하지만, 이는 언급한 것처럼 더욱 규모가 크고 복잡한 웹 페이지를 만들 때 구조적, 기술적으로 최적화하는 과정이며 유지/보수, 확장성, 생산성 등을 위해서 꼭 필요합니다. 이런 과정 자체를 이해하고 익숙해지는 것이 학습할 때 매우 중요합니다. **단, 아직은 너무 어렵게 생각할 필요가 없습니다!**)

다음은 HTML, CSS, JS가 담당하는 역할을 시각적으로 표현한 사이트입니다.
각 언어의 역할을 이해하는 데 도움이 될 것입니다.

![HTML-CSS-JS 스크린샷](/images/screenshot/html-css-starter/html-css-js-site-screenshot.jpg)
[HTML-CSS-JS](https://html-css-js.com/)

### 웹 표준

웹 표준(Web Standard)이란 '웹에서 사용되는 표준 기술이나 규칙'을 의미하며 W3C의 권고안에서 나온 기술들이 여기에 해당합니다.
이 표준 기술들을 기준으로 웹 브라우저들(크롬, IE, 사파리 등)이 만들어지는데, 브라우저를 만드는 업체(구글, MS, 애플 같은)에서 표준 기술을 해석하는 차이, 새로운 기술 삽입([표준화 제정 단계](https://wit.nts-corp.com/2013/10/16/280)에 따른) 등으로 조금은 다르게 구동되는 브라우저가 생기게 됩니다.
지금은 거의 사라졌지만 ActiveX, Flash 같은 기술은 표준이 아닙니다.

> 대부분의 경우 표준화 제정 단계의 '권고안(REC)'에 해당하는 기술을 표준이라고 생각하시면 쉽습니다.

### 크로스 브라우징

![웹 브라우저들](/images/screenshot/html-css-starter/browsers.jpg)

> 오른쪽부터 구글 크롬, MS 엣지, 모질라 파이어폭스, 오페라, 이스트소프트 스윙, 네이버 웨일, MS IE, 애플 사파리

크로스 브라우징(Cross Browsing)은 위에서 설명한 것처럼 조금은 다르게 구동되는 여러 브라우저에서 동일한 사용자 경험(같은 화면, 같은 동작 등)을 줄 수 있도록 제작하는 기술, 방법 등을 말합니다.
대부분의 브라우저는 최대한 웹 표준을 준수해서 제작되기 때문에 문제 되는 경우가 적지만 MSIE(마이크로소프트 인터넷 익스플로어) 브라우저는 ~~웹 표준 따위.., 제멋대로 만들어져 있기 때문에~~ 여러 의미에서 표준화하기 쉽지 않은 브라우저입니다.
그래서 IE에서도 동작하게 하는 것을 크로스 브라우징이라고 부르기도 합니다.(대부분의 경우 IE에서 문제가 없으면 다른 브라우저는 OK!)

> 2016년 봄에 네이버에서 ['내 PC의 보안을 위협하는 구버전 익스플로러 이제 그만 헤어지자!'](https://campaign.naver.com/goodbye_ie10/)라는 캠페인을 했었습니다.

### 웹 접근성

웹 접근성이란 정상적인 웹 콘텐츠 사용이 가능한 일반 사용자부터 고령자, 장애인 같은 신체적, 환경적 조건에 제한이 있는 사용자를 포함해 모든 사용자들이 동등하게 접근할 수 있는 웹 콘텐츠를 제작하는 방법을 말합니다.
청각 장애인을 위해 영상에 자막을 넣거나, 마우스를 사용할 수 없는 사람들을 위해 키보드를 통해서도 웹을 이용할 수 있게 하거나(혹은 그 반대), 이미지에 대체 텍스트를 제공하는 간단한 방법들까지 모두 웹 접근성에 해당합니다.
아래 링크에 접근성에 대한 지침이나 제작기법 등의 문서가 상세하게 정리되어 있으니 참고하세요.

[웹 접근성 연구소](https://www.wah.or.kr:444/Accessibility/define.asp)
[한국형 웹 콘텐츠 접근성 지침 2.1](https://www.wah.or.kr:444/Participation/guide.asp)
[웹 콘텐츠 제작기법](https://www.wah.or.kr:444/Participation/technique.asp)

> 웹의 힘은 그것의 보편성에 있다. 장애에 구애 없이 모든 사람이 접근할 수 있는 것이 필수적인 요소이다.
> __팀 버너스 리 경 - 웹의 창시자__

#### 정보 통신 보조기기

장애인의 경우 다음과 같은 정보 통신 보조기기를 통해 웹 콘텐츠에 접근할 수 있어야 합니다.
이런 보조기기는 개인 구매 혹은 정부 기관이나 장애인 복지시설에서 임대하여 사용할 수 있습니다.

![정보 통신 보조 기기들](/images/screenshot/html-css-starter/assistiv_technology.jpg)

- 한손 사용자용 키보드: 편마비 장애인을 위해 한손으로 타이핑하게 디자인되어있는 키보드
- 큰 키 키보드: 키보드의 입력 버튼을 크게 만들어 손 떨림이나 상지 기능에 장애가 있는 분에게 적합하며, 키가드가 있어 오타를 방지할 수 있는 특수 키보드
- n-Abler 조이스틱: 팔의 움직임이 원활하지 못해 일반 마우스를 사용하기 어려운 분들을 위한 조이스틱 마우스
- SmartNav: 상지 및 하지를 사용하기 어려운 분들이 머리의 움직임을 통해(적외선 및 난반사 스티커 활용) 컨트롤할 수 있는 특수 마우스
- 소리 알리미: 소리 정보를 불빛과 진동으로 알려주는 청각장애인용 무선신호기

#### 웹 접근성 품질인증 마크

![웹 접근성 품질인증 마크](/images/screenshot/html-css-starter/web_access_mark.jpg)

장애인 및 고령자가 웹 사이트 이용에 불편이 없도록 웹 접근성 표준을 준수한 우수 사이트에 대해 품질을 인증하고 마크를 부여하는 제도로써 「국가정보화기본법」제32조의2 및 동법 시행규칙 제3조의3에 의거 과학기술정보통신부가 지정한 웹 접근성 품질인증 기관을 통해 심사 및 인증을 받을 수 있습니다.
서면 심사와 기술 심사 등을 거쳐 페이지 수에 따라 기본 100만원 이상의 심사 비용을 지불해야 합니다.

> 현실적으론 개인이나 중소기업 사이트에서 획득하기는 쉽지 않습니다.

## 웹 개발을 위한 에디터

포토샵, 스케치3 같은 한정된 툴에 종속되는 웹앱 디자인 등과는 다르게 웹 개발은 툴에 대한 종속성이 거의 없습니다.
심지어 메모장을 사용해도 상관없지만, 개발 퍼포먼스를 생각해서 좋은 에디터를 고르는 것을 추천합니다.
HTML, CSS, JS를 위한 웹 개발(프론트엔드, Node.js) 에디터 중 실무에서 많이 사용되는 크로스 플랫폼(Windows, macOS) 에디터들을 간단하게 소개합니다.

> 다음은 모두 좋은 에디터들입니다.
> 주관적인 관점에서 작성했으니 참고만 하시고 모두 한 번씩 써본 후 자신에게 맞는 에디터를 선택하시길 바랍니다.

### Sublime Text

![Sublime Text Icon](/images/screenshot/html-css-starter/logo_sublime_text.jpg)

https://www.sublimetext.com/

상대적으로 가볍고 성능 저하가 적은 편이라고 합니다.
많이 써보지 않아서 평가는 생략합니다.
무료입니다.

### Atom

![Atom Icon](/images/screenshot/html-css-starter/logo_atom.jpg)

https://atom.io/

깃헙(GitHub)에서 만든 텍스트 에디터입니다.
확장 기능도 충분하고 외국에선 인기가 많다고 합니다.
(2018년 깃헙이 MS에 인수되었는데 Atom의 미래는?)
Windows에서의 사용은 아쉬운 부분이 많네요.
macOS에서는 문서 작업 시 자주 사용합니다.
무료입니다.

### Brackets

![Brackets Icon](/images/screenshot/html-css-starter/logo_brackets.jpg)

http://brackets.io/

어도비(Adobe)에서 만든 텍스트 에디터입니다.
Creative Cloud 제품군이 아니고 오픈소스로 풀려 있습니다.
Live Preview 기능이 기본으로 제공되는 등 시각적인 결과물을 확인하는데 특화되어 있으나(역시 어도비!) 확장 기능이나 특히 성능 최적화에 대해선 아쉬운 감이 있습니다.(역시 어도비..)
무료입니다.

### VS Code

![VS Code Icon](/images/TTEiUup/logo_vs_code.jpg)

https://code.visualstudio.com/

VS Code(VisualStudio Code)는 마이크로소프트(MS)에서 만든 텍스트 에디터입니다.
가볍게 시작할 수 있고 확장 기능이 상당히 많습니다.
2018 Stack Overflow 설문조사에서 에디터 인기도 1위를 기록했다고 하네요.
무료입니다.

### WebStorm

![WebStorm Icon](/TTEiUup/logo_webstorm.jpg)

https://www.jetbrains.com/webstorm/

JetBrain에서 만드는 [통합 개발 환경(IDE)](https://ko.wikipedia.org/wiki/%ED%86%B5%ED%95%A9_%EA%B0%9C%EB%B0%9C_%ED%99%98%EA%B2%BD) 프로그램 중 하나입니다.
별도의 확장 기능이 거의 필요 없으며 대부분의 프로젝트를 바로 시작할 수 있습니다.
한 번 쓰면 다른 에디터로 넘어가기 어려울 정도로 편한 권장 프로그램이지만 유료라는 게 함정.
단, 학생 라이선스를 얻으면 무료로 사용하실 수 있고 30일 평가판도 있으니 여유가 있다면 써보시길 권장합니다.

> 구독형 프로그램으로 [개인 라이선스](https://www.jetbrains.com/webstorm/buy/#edition=personal)는 1년 $59입니다. 비싼 편은 아니라고 생각합니다.

## VS Code 설치 및 설정

저는 무료 프로그램으로 VS Code를 선택했습니다.(회사에서는 WebStorm을 사용합니다)
설치부터 단축키 사용, 확장 기능 등 웹 개발을 위한 에디터를 준비합시다!

### 설치

자신의 운영체제(Windows, macOS, Linux)에 맞는 Stable 버전을 설치하세요.
별도 설정값을 무시하고 다음/다음을 눌러 진행하세요.

![VS Code 다운로드](/TTEiUup/vs_code_download.jpg)

#### 인터페이스

![VS Code Interface](/TTEiUup/vs_code_interface.jpg)

### 확장 기능(Extensions)

![사용자 인터페이스에서 확장 기능 아이콘](/TTEiUup/vs_code_extensions_icon.jpg)

다른 에디터도 동일하지만 VS Code는 확장 기능을 제공하며 최초 설치한 버전에서 제공하지 않는 다양한 확장 기능을 외부에서 다운로드받아(설치) 연결 후 사용할 수 있습니다.(대부분 에디터 자체에서 확장 기능을 검색할 수 있습니다)
에디터의 버전업 과정에서 자체적으로 흡수하는 기능도 있을 수 있으므로 몇몇 확장 기능은 에디터의 버전에 따라 이미 지원하고 있을 수 있으니 해당 기능이 제공되는지 확인하고 설치하시는 것을 추천합니다.

#### Korean Language Pack for Visual Studio Code

VS Code의 거의 모든 메뉴가 한국어로 변경됩니다.

#### Beautify

코드 가독성을 위해 코드 작성 스타일을 (아름답게) 수정합니다.
입문자들에게 적극 추천합니다.

1. `Preferences > Keyboard Shortcut` 선택
1. `HookyQR.beautify`를 검색(`HookyQR.beautifyFile` 아니에요!)
1. `키 바인딩` 선택
1. 원하는 단축키 등록

> "Alt + Ctrl + L"(Windows) / "Alt + Cmd + L"(macOS)을 추천합니다.

#### Live Server

하단 상태 바(Status bar)에서 `Go Live` 선택
또는,
HTML 화면에서 우클릭 > `Open with Live Server` 선택

> VS Code 버전에 따라서 이미 설치되어 있을 수 있습니다.

#### Auto Rename Tag

태그 이름을 수정할 때 열린 태그와 닫힌 태그가 쌍으로 수정됩니다.
각각 수정해야 하는 번거로움을 줄일 수 있습니다.

#### 그 외 추천

다음 확장 기능들이 당장 필요하지는 않을 겁니다.
나중에 살펴보세요.

[Terminal](https://marketplace.visualstudio.com/items?itemName=formulahendry.terminal)
[Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass)
[Turbo Console log](https://marketplace.visualstudio.com/items?itemName=ChakrounAnas.turbo-console-log)
[Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
[Highlight Matching Tag](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)

[GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
[REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)

### 알아두면 좋은 단축키

`Preferences > Keyboard Shortcut(바로 가기 키)` 에서 단축키를 확인하거나 변경할 수 있습니다.

> `"`를 사용하면 키 바인딩을 검색할 수 있습니다.
> `"`를 닫으면 정확한 검색을 요구하므로 `"cmd + p`와 같이 `"`를 닫지 않고 검색하는 것을 추천합니다.

Windows 단축키 | macOS 단축키 | 설명
--|--|--
"Ctrl + B" | "Cmd + B" | 사이드바 열기/닫기
"Ctrl + P" | "Cmd + P" | 빠른 열기(파일이나 기호 탐색)
"Ctrl + Shift + P" | "Cmd + Shift + P" | 모든 명령 표시(에디터의 모든 명령에 접근)
"Ctrl + F" | "Cmd + F" | 찾기(검색)
"Ctrl + H" | "Cmd + Opt(Alt) + F" | 찾기(검색)/바꾸기(대체)
"Alt + Up" | "Alt + Up" | 줄 위로 이동
"Alt + Down" | "Alt + Down" | 줄 아래로 이동
"Shift + Alt + UpArrow" | "Shift + Alt + UpArrow" | 위에 줄 복사
"Shift + Alt + DownArrow" | "Shift + Alt + DownArrow" | 아래 줄 복사
"Tab" | "Tab" | 들여쓰기
"Shift + Tab" | "Shift + Tab" | 내어쓰기
"Ctrl + PageUp" | "Cmd + Shift + &#91;" | 이전 편집기 열기(좌측 창으로 전환)
"Ctrl + PageDown" | "Cmd + Shift + &#93;" | 다음 편집기 열기(우측 창으로 전환)
"Ctrl + &#92;" | "Cmd + &#92;" | 편집기 분할(백슬래쉬)
"Ctrl + 숫자" | "Cmd + 숫자" | `숫자`번째 분할된 편집기 그룹에 포커스
"Ctrl + W" | "Cmd + W" | 편집기 닫기

#### 약어로 랩핑(Wrap)

1. 랩핑할 코드 선택
1. 모든 명령 표시 실행 / "Ctrl + Shift + P"(Windows), "Cmd + Shift + P"(macOs)
1. `Emmet: Wrap with Abbreviation(Emmet: 약어로 랩핑)`를 입력하거나 목록에서 선택("Enter")
1. `div`, `span` 등의 Emmet 문법(ex: `.wrapper`, `span.bold`)을 입력
1. 완료("Enter")

## 웹에서 사용하는 이미지

### 비트맵과 벡터 이미지

이미지(그래픽)는 크게 비트맵과 벡터로 구분됩니다.

비트맵(Bitmap)은 각 픽셀이 모여 만들어진 정보의 집합으로 레스터(Raster) 이미지라고도 부릅니다.
픽셀 단위로 화면에 렌더링합니다.(렌더링: 컴퓨터가 화면에 그림을 그려서 우리가 볼 수 있게 합니다)
우리가 일반적으로 사용하는 대부분의 이미지가 비트맵 형식입니다.
그림판, 포토샵과 같은 툴로 편집할 수 있습니다.

벡터(Vector)는 수학적 정보의 형태(Shape)들이 만들어내는 결과물입니다.
이미지가 가지고 있는 점, 선, 면의 위치(좌표), 색상 등의 정보를 온전히 가지고 있으며 그를 화면에 렌더링합니다.
따라서 좀 더 많은 연산을 해야 하지만, 대신 해상도(픽셀)에 영향을 비트맵 이미지와 달리 해상도로부터 자유롭게 렌더링할 수 있습니다.
쉽게 말하면 확대 및 축소를 해도 이미지가 깨지지 않죠.
또한 수학적 정보만을 가지고 있기 때문에 이미지 확대/축소에 따른 용량 변화가 없습니다.
일러스트 같은 툴로 편집할 수 있습니다.

![비트맵과 벡터의 차이](/TTEiUup/difference_bitmap_vector.jpg)

이미지 종류 | 장점 | 단점
--|--|--
비트맵 | 정교하고 다양한 색상을 자연스럽게 표현 | 확대/축소 시 계단 현상, 품질 저하
벡터 | 확대/축소에서 자유로움, 용량 변화가 없음 | 정교한 이미지(인물, 풍경 사진 같은)를 표현하기 어려움

> [Sketch 3](https://www.sketch.com/)는 이미지의 편집보단 벡터 기반의 UI 제작 툴이라고 볼 수 있습니다.

### JPG(JPEG)

JPG(Joint Photographic coding Experts Group) Full-color와 Gray-scale의 압축을 위해 만들어졌으며 압축률이 훌륭해 사진이나 예술 분야에서 많이 사용됩니다.

- 손실 압축
- 표현 색상도(24비트, 약 1600만 색상) 뛰어나 고해상도 표시장치에 적합
- 이미지의 품질과 용량을 쉽게 조절 가능
- 가장 널리 쓰이는 이미지 포맷

> 높은 압축률(적은 용량)!

### PNG

PNG(Portable Network Graphics)는 Gif의 대체 포맷으로 개발되었습니다.

- 비손실 압축
- 8비트(256 색상) / 24비트(약 1600만 색상) 컬러 이미지 처리
- Alpha Channel 지원(투명도)
- W3C 권장 포맷

> 투명도 지원!

### GIF

GIF(Graphics Interchange Format)는 이미지 파일 내에 이미지 및 문자열 같은 정보들을 저장할 수 있습니다.

- 비손실 압축
- 여러 장의 이미지를 한 개의 파일에 담을 수 있음(움짤, 애니메이션)
- 8비트 컬러만 지원(다양한 색상을 표현하는 작업에는 적합하지 않음)

> 동영상 같은 이미지!(애니메이션)

### WEBP

JPG, PNG, GIF를 모두 대체할 수 있는 구글이 개발한 이미지 포맷입니다.

- 완벽한 손실/비손실 압축 지원
- GIF 같은 애니메이션 지원
- Alpha Channel 지원(손실, 비손실 모두)

> 완벽한 포맷! 그러나 지원 브라우저가...

[Support Browser for Webp](https://caniuse.com/#feat=webp)

### SVG

SVG(Scalable Vector Graphics)는 마크업 언어(HTML/XML) 기반의 벡터 그래픽을 표현하는 포맷입니다.

- 해상도의 영향에서 자유로움
- CSS로 Styling 가능
- JavaScript로 Event Handling 가능
- 코드 혹은 파일로 사용 가능

> 벡터 이미지에 익숙하지 않다면 다루기 조금 까다로울 수 있습니다.

## 특수 문자 용어 정리

기호 | 영어(발음) | 한글
--|--|--
&#96; | Grave(그레이브) | -
~ | Tilde(틸드) | 물결표시
! | Exclamation(엑스클러메이션) mark | 느낌표
@ | At(엣) sign| 골뱅이
&#35; | Number(넘버) sign, Sharp(샵) | 샵, 우물 정
$ | Dollar(달러) sign | 달러
% | Percent(퍼센트) sign | 퍼센트
^ | Caret(캐럿) | -
& | Ampersand(엠퍼센드) | -
&#42; | Asterisk(에스터리스크) | 별표
&#45; | Hyphen(하이픈), Dash(대쉬) | 마이너스
_ | Underscore(언더스코어), Low dash(로대쉬) | 밑줄
= | Equals(이퀄) sign | 이꼬르
" | Quotation(쿼테이션) mark | 큰 따옴표
' | Apostrophe(아포스트로피) | 작은 따옴표
: | Colon(콜론) | 땡땡이
; | Semicolon(세미콜론) | 털 달린 땡땡이
, | Comma(콤마) | 쉼표
. | Period(피리어드), Dot(닷) | 점, 마침표
? | Question(퀘스천) mark | 물음표
/ | Slash(슬래쉬) | -
&#124; | Vertical bar(버티컬 바) | -
&#92; | Backslash(백슬래쉬) | -
() | Parenthesis(퍼렌서시스) | (소)괄호
{} | Brace(브레이스) | 중괄호
[] | Bracket(브래킷) | 대괄호
&#60;&#62; | Angle Bracket(앵글 브래킷) | 꺽쇠괄호

[HTML Entity List](https://www.freeformatter.com/html-entities.html)

## 오픈소스 라이선스

> 오픈소스란 어떤 제품을 개발하는 과정에 필요한 소스 코드나 설계도를 누구나 접근해서 열람할 수 있도록 공개하는 것.

오픈소스라 하면 보통 무료 저작권이고 공짜로 사용해도 문제가 없다고 생각하지만 사실 다양한 종류의 오픈소스 라이선스가 존재하며 개인적 이용은 가능하지만, 상업적 이용에 제한이 있거나 경우에 따라 비용을 지불해야 할 수도 있습니다.

현실적으론 처음부터 끝까지 모든 코드를 직접 작성할 수 없기 때문에 많은 경우 오픈소스에 의존하게 됩니다. 개인적인 사용을 목적으로는 문제가 없겠지만, 회사에서(상업적으로) 아무 생각 없이 사용하다가는 문제가 돼서 해고당하거나 피해 보상을 해줘야 할지도 모릅니다.
물론 인터넷에 떠도는 코드 몇 줄 복사해서 썼다고 그 정도 심각한 문제가 되진 않겠지만, 항상 조심하는 것이 좋습니다.
회사에서 작업 중에 괜찮은 오픈소스를 찾았다면 반사적으로 'License'부터 찾으세요!

수많은 라이선스를 다 공부할 필요는 없고, 보기만 해도 흐뭇해지는 라이선스를 몇 가지 소개합니다.

### Apache License

아파치 소프트웨어 재단에서 자체 소프트웨어에 적용하기 위해 만든 라이선스입니다.
개인적/상업적 이용, 배포, 수정, 특허 신청이 가능합니다.

### MIT License

매사추세츠공과대학(MIT)에서 소프트웨어 학생들을 위해 개발한 라이선스입니다.
개인 소스에 이 라이선스를 사용하고 있다는 표시만 지켜주면 되며, 나머지 사용에 대한 제약은 없기 때문에 인기가 많습니다.

### BSD License

BSD(Berkeley Software Distribution)는 버클리 캘리포니아대학에서 개발한 라이선스입니다.
MIT와 동일하게 라이선스 표시만 지켜주시면 됩니다.

### Beerware

오픈소스 개발자에게 맥주를 사줘야 하는 라이선스입니다.
물론 만날 수 있다면 말이죠!

그 외 더 많은 오픈소스 라이선스에 대한 정보는 [OpenSource.org](https://opensource.org/licenses)에서 확인하실 수 있습니다.

# HTML

## 정말 쉬운 HTML 문법

### 기본 형태

태그는 각자의 의미를 가지고 있으며 다음과 같은 형태를 가집니다.

```html
<TAG></TAG>
<TAG>CONTENT</TAG>
```

```html
<h1>토끼와 거북이</h1>
<p>옛날 옛적에 토끼와 거북이가 살았습니다 ...</p>

<!-- 다음과 같이 이해할 수 있습니다. -->
<주제1>토끼와 거북이</주제1>
<문단>옛날 옛적에 토끼와 거북이가 살았습니다 ...</문단>
```

또한 태그는 열리고(open) 닫히는(close) 태그 구조를 가지고 있으며 이는 한 쌍입니다.
(시작하고(start) 종료되는(end) 구조라고 부르기도 합니다)
이 구조는 태그의 범위를 만들어 줍니다.

```html
<h1>토끼와 거북이</h1>

<!-- 다음과 같이 이해할 수 있습니다. -->
<주제1여기서열림>토끼와 거북이</주제1여기서닫힘>
```

입문자가 주의할 점은 닫히는 태그는 태그 이름 앞에 `/`(슬래시)가 붙는다는 것입니다.

### 속성(Attributes)과 값(Value)

태그(요소)의 기능을 확장하기 위해 '속성'을 사용할 수 있습니다.

```html
<TAG 속성="값"></TAG>
```

```html
<img src="./my_photo.jpg" alt="내 프로필 사진" />
<div class="name">홍길동</div>

<!-- 다음과 같이 이해할 수 있습니다. -->
<이미지삽입 소스위치="./my_photo.jpg" 대체텍스트="내 프로필 사진" />
<의미없는분할 태그별명="name">홍길동</의미없는분할>
```

`<img />`는 이미지를 삽입할 때 사용하는 태그입니다.
하지만 태그만 사용하면 어떤 이미지를 삽입하는지 알 수 없기 때문에 `src`(source)라는 속성을 사용해서 삽입할 이미지의 경로를 지정합니다. 그리고 `alt`(alternative)라는 속성은 이미지를 출력하지 못하는 상황에 이미지 대신 보여질 텍스트를 지정합니다.
`<div></div>`는 의미를 가지지 않는 태그로 어떤 내용이든 묶어낼(Wrap) 수 있습니다.
위에선 `'홍길동'`이라는 텍스트를 묶었으나 그 내용이 무엇을 의미하는지 알 수 없기 때문에 `name`이라는 태그 별명(`class`)을 추가했습니다.

> `<img />`는 좀 이상하게 생겼네요. 닫히는 태그가 없으면 빈 태그(Empty Tag)라고 합니다. 다시 설명합니다.

### 부모와 자식 요소

태그A가 태그B의 콘텐츠로 사용되면, 태그B는 태그A의 부모 요소, 태그A는 태그B의 자식 요소라고 합니다.

```html
<PARENT>
  <CHILD></CHILD>
</PARENT>
```

```html
<section class="fruits">
  <h1>과일 목록</h1>
  <ul>
    <li>사과</li>
    <li>딸기</li>
    <li>바나나</li>
    <li>오렌지</li>
  </ul>
</section>

<!-- 다음과 같이 이해할 수 있습니다. -->
<섹션영역 태그별명="fruits">
  <주제1>과일 목록</주제1>
  <순서없는목록>
    <항목>사과</항목>
    <항목>딸기</항목>
    <항목>바나나</항목>
    <항목>오렌지</항목>
  </순서없는목록>
</섹션영역>
```

`<section></section>` 안에는(콘텐츠) `<h1></h1>`, `<ul></ul>`, `<li></li>`가 있고 `<ul></ul>` 안에는(콘텐츠) `<li></li>`가 있습니다.
(이하 닫히는 태그는 생략할게요)
이러한 구조에서 `<section>`는 `<h1>`과 `<ul>`의 부모 요소입니다.
또한 `<ul>`은 `<li>`의 부모 요소입니다.
반대로 `<h1>`과 `<ul>`은 `<section>`의 자식 요소입니다.
또한 `<li>`는 `<ul>`의 자식 요소입니다.

여기서 `<ul>`은 `<section>`의 자식 요소이면서 `<li>`의 부모 요소입니다.
이처럼 부모와 자식 요소는 상대적인 개념입니다.
(조금 더 나아가면 `<section>`은 `<li>`의 조상(상위) 요소, 반대로 `<li>`는 `<section>`의 후손(하위) 요소라고 합니다)

우리가 기본적인 가계도를 통해 할아버지, 엄마, 삼촌, 형제 같은 호칭을 정의하듯(혹은 반대로 호칭을 통해 가계도를 이해하듯), HTML의 구조도 위와 같은 개념으로 호칭을 정의하여 추후 선택자(Selector)를 통해 CSS와 JS로 HTML을 다룰 때 중요하게 사용됩니다.

### 빈 태그

HTML에는 닫히는 개념이 없는 태그들이 있습니다.
다음과 같은 형태를 가집니다.

```html
<!-- `/`가 없는 빈 태그 -->
<TAG>

<!-- `/`가 있는 빈 태그 -->
<TAG/>
<TAG />
```

HTML5에서는 위 2가지 형태를 다 사용할 수 있는데, XHTML 버전이나 린트(Lint) 환경 혹은 프레임워크 세팅에 따라 `/`를 사용하는 것이 필수가 될 수 있습니다.

> 어떤 형태를 써야 한다는 갑론을박이 있는데 이는 실제론 중요치 않습니다. 원하는 형태를 사용하되 혼용하지는 마세요.

## HTML 문서의 범위

`index.html` 같은 HTML 파일을 우리는 HTML 문서라고 표현할 수 있습니다.
HTML 문서의 범위를 나타내는(의미하는) 태그들을 알아봅시다.

```html
<!DOCTYPE html>
<html>
  <head>
    문서의 정보
  </head>
  <body>
    문서의 구조
  </body>
</html>
```

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="author" content="홍길동">
    <meta name="description" content="우리 사이트가 최고!">
    <title>내 사이트</title>
    <link rel="stylesheet" href="./css/main.css">
    <script src="./js/main.js"></script>
</head>
<body>
    <section>
      <h1></h1>
      <div>
        <ul>
          <li></li>
          <li></li>
        </ul>
      </div>
    </section>
</body>
</html>
```

### HTML(전체 범위)

`<html>`는 HTML 문서의 전체 범위를 지정합니다.
웹 브라우저가 해석해야 할 HTML 문서가 어디에서 시작하며, 어디에서 끝나는지 알려주는 역할을 합니다.

### HEAD(정보 범위)

웹 브라우저가 해석해야 할 HTML 문서의 정보 범위를 지정합니다.
여기서 말하는 정보에는 웹 페이지의 제목, 웹 페이지의 문자 인코딩 방식, 연결할 외부 파일의 위치, 웹 페이지를 구조화하기 위한 기본 세팅 값 같은 것들을 말합니다.
다르게는 '화면을 구성하기 위한 기본 설정'이라고 표현할 수 있습니다.

### BODY(구조 범위)

웹 브라우저가 해석해야 할 HTML 문서의 구조 범위를 지정합니다.
구조는 사용자가 화면을 통해서 볼 수 있는 내용(콘텐츠)의 형태나 레이아웃 등을 의미하며 로고, 헤더, 푸터, 내비게이션, 메뉴, 버튼, 입력창, 팝업, 광고 등 보이는 모든 것들이 구조에 해당합니다.
구조는 BODY 범위 안에서만 생성합니다.

### DOCTYPE(DTD, 버전 지정)

DOCTYPE(DTD, Document Type Definition)은 마크업 언어에서 문서 형식을 정의합니다.
이는 웹 브라우저에 우리가 제공할 HTML 문서를 어떤 HTML 버전의 해석 방식으로 구조화하면 되는지를 알려줍니다.
(HTML은 크게 1, 2, 3, 4, X-, 5 버전이 있습니다)

현재의 표준 모드는 HTML5 입니다.

```html
<!-- HTML 5 -->
<!DOCTYPE html>

<!-- XHTML 1.0 Transitional -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

[더 많은 문서형 정보 보기](https://en.wikipedia.org/wiki/Document_type_declaration)

> Windows 운영체제가 95, 98, ME, XP, Vista, 7, 8, 10 버전이 있는 것과 비슷하다고 생각하시면 쉽습니다.

## HTML 문서의 정보

`<head></head>` 안에서 사용하는 태그들은 HTML 문서의 정보를 가지고 있습니다.

### TITLE(웹 페이지의 제목)

HTML 문서의 제목을 정의합니다.
웹 브라우저의 각 사이트 탭에서 이름으로 표시됩니다.

![브라우저 탭에 표시되는 타이틀 태그](/TTEiUup/browser_tabs.jpg)

```html
<head>
  <title>네이버</title>
</head>
```

### META(웹 페이지의 정보)

HTML 문서(웹페이지)에 관한 정보(표시 방식, 제작자(소유자), 내용, 키워드 등)를 검색엔진이나 브라우저에 제공합니다.
빈(Empty) 태그입니다.

```html
<head>
  <meta charset="UTF-8">
  <meta name="author" content="홍길동">
  <meta name="description" content="우리 사이트가 최고!">
</head>

<!-- 다음과 같이 이해할 수 있습니다. -->
<문서의정보범위>
  <정보 문자인코딩방식="UTF-8">
  <정보 정보종류="사이트제작자" 정보값="홍길동">
  <정보 정보종류="사이트설명" 정보값="우리 사이트가 최고!">
</문서의정보범위>
```

`<meta>`에서 사용할 수 있는 속성은 다음과 같습니다.
각 태그는 자신이 사용할 수 있는 속성과 값이 정해져 있습니다.
어떤 속성을 사용할 수 있고, 사용할 수 없는지 구분할 수 있어야 합니다.
잘 사용하지 않는 속성도 있기 때문에 당장 모든 속성과 값을 암기할 필요는 없습니다.
('전역(Global) 속성'이라고 해서 어느 태그에서나 사용할 수 있는 속성들도 있습니다만 지금은 확인할 필요가 없습니다!)

속성 | 의미 | 값
--|--|--
`charset` | 문자인코딩 방식 | `UTF-8`, `EUC-KR` 등..
`name` | 검색엔진 등에 제공하기 위한 정보의 종류(메타 데이터) | `author`, `description`, `keywords`, `viewport` 등..
`content` | `name` 이나 `http-equiv` 속성의 값을 제공 |

### LINK(CSS 불러오기)

외부 문서를 연결할 때 사용합니다.
특히 HTML 외부에서 작성된 CSS 문서(`xxx.css` 파일)를 불러와 연결할 때 사용합니다.
빈(Empty) 태그입니다.

```html
<head>
  <link rel="stylesheet" href="./css/main.css">
  <link rel="icon" href="./favicon.png">
</head>

<!-- 다음과 같이 이해할 수 있습니다. -->
<문서의정보범위>
  <외부문서연결 관계="CSS" 문서경로="./css/main.css">
  <외부문서연결 관계="사이트대표아이콘" 문서경로="./favicon.png">
</문서의정보범위>
```

속성 | 의미 | 값
--|--|--
`rel` | (필수)현재 문서와 외부 문서와의 관계를 지정 | `stylesheet`, `icon` 등..
`href` | 외부 문서의 위치를 지정 | 경로

### STYLE(CSS 작성하기)

CSS를 외부 문서에서 작성하여 연결하는 것이 아니고 HTML 문서 내부에 작성할 때 사용합니다.

```html
<style>
  img {
    width: 100px;
    height: 200px;
  }
  p {
    font-size: 20px;
    font-weight: bold;
  }
</style>

<!-- 다음과 같이 이해할 수 있습니다. -->
<스타일정의>
  <!-- CSS 코드 -->
</스타일정의>
```

### SCRIPT(JS 불러오거나 작성하기)

HTML 문서에서 CSS는, 작성된 CSS를 `<link>`로 불러오거나 `<style></style>`안에 작성할 수 있습니다.
JS는 `<script></script>`로 이 2가지 방식을 모두 사용할 수 있습니다.

```html
<!-- 불러오기 -->
<script src="./js/main.js"></script>

<!-- 작성하기 -->
<script>
  function windowOnClickHandler(event) {
    console.log(event);
  }
  window.addEventListener('click', windowOnClickHandler);
</script>

<!-- 다음과 같이 이해할 수 있습니다. -->

<!-- 불러오기 -->
<자바스크립트 문서경로="./js/main.js"></자바스크립트>

<!-- 작성하기 -->
<자바스크립트>
  <!-- JS 코드 -->
</자바스크립트>
```

## HTML 문서의 구조

`<body></body>` 안에서 사용하는 태그들은 HTML 문서의 구조를 나타냅니다.

### DIV(막 쓰는 태그)

`<div></div>`의 'div'는 'division'으로 약자로 '분할'을 뜻하고 '문서의 부분이나 섹션을 정의'합니다.
명확한 의미를 가지지 않기 때문에 정말 많은 경우 단순히 특정 범위를 묶는(wrap) 용도로 사용합니다.
보통 이렇게 묶인 부분들에 CSS나 JS를 적용하게 됩니다.

```html
<body>
  <div>
    <p></p>
  </div>
  <div>
    <div>
      <h1></h1>
      <p></p>
    </div>
  </div>
</body>

<!-- 다음과 같이 이해할 수 있습니다. -->
<body>
  <묶음1>
    <p></p>
  </묶음1>
  <묶음2>
    <묶음2-1>
      <h1></h1>
      <p></p>
    </묶음2-1>
  </묶음2>
</body>
```

>  "DIV는 아무 의미가 없다. 왜냐하면 아무 의미가 없기 때문이다."

### IMG(이미지 넣는 태그)

`<img>`는 HTML에 이미지를 삽입할 때 사용합니다.
(웹 페이지에 이미지를 삽입하는 방식은 크게 2가지로, 'HTML에서 삽입(IMG)'과 'CSS에서 삽입(background)'이 있습니다)

```html
<body>
  <img src="./kitty.png" alt="냥이">
</body>

<!-- 다음과 같이 이해할 수 있습니다. -->
<body>
  <이미지 경로="./kitty.png" 대체텍스트="냥이">
</body>
```

속성 | 의미 | 값
--|--|--|
`src` | (필수)이미지의 URL | URL
`alt` | (필수)이미지의 대체 텍스트(alternate)를 지정 |

위 표에서 '(필수)'라고 되어 있는 속성들(`src`, `alt`)은 `<img>`를 사용할 때 반드시 포함되어야 할 속성(필수 속성, Required Attributes)입니다.
만약 `<img src="./kitty.png">`라고 작성하여 `alt` 속성이 누락되었다면 이는 웹 표준에 어긋납니다.

## 웹 표준 검사하기

우리가 작성한 HTML 문서가 표준에 부합하는지 테스트를 해볼 수 있습니다.
[W3C validator](https://validator.w3.org/#validate_by_upload)에 접속하여 작성한 HTML 문서를 업로드하고 테스트를 시작하세요!
기본적인 표준 여부를 판단할 수 있습니다.
특히 입문자라면 익숙해질 때까지는 자주 확인하는 것이 좋습니다.

![웹 표준 검사 결과 alt 누락](/TTEiUup/markup _validation_result_image_kytty.jpg)

위에서 `<img src="./kitty.png">`라고 작성했을 때 나오는 결과입니다.
HTML 문서를 작성하면서 지켜야하는 이러한 규칙들이 많이 있습니다.

> 테스트 통과가 웹 표준/웹 접근성의 준수 여부를 최종적으로 결정하진 않습니다. 이 테스트는 사실 기본 문법 검사에 가깝습니다.

또는 사이트(페이지) 주소로 검사할 수도 있습니다.
다음은 `naver.com`을 검사한 결과입니다.

![웹 표준 검사 결과 naver.com](/TTEiUup/markup _validation_result_naver_com.jpg)

## HTML 예제

다음 이미지는 [GitHub](https://github.com/) 메인 페이지의 일부입니다.(이 예제에 사용된 이미지는 예전 메인 페이지의 모습입니다)
이 페이지의 일부를 HTML로 코딩해 봅시다.

> 완성된 페이지([https://heropcode.github.io/GitHub-Responsive/](https://heropcode.github.io/GitHub-Responsive))를 공유합니다. GitHub 메인의 클론 페이지입니다.

![HTML Github 예제](/TTEiUup/guthub_clone_page.jpg)

입문 단계에서 난이도가 올라가지 않도록(코드가 너무 길어지지 않도록) 위 화면에서 다음에 표시된 부분(Header)의 내용 일부만 구조를 정리해 봅시다.

![HTML Github 예제 header](/TTEiUup/guthub_clone_page_header_structure.jpg)

바탕화면 같은 익숙한 곳에서 `example1`이라는 이름의 프로젝트 디렉터리(폴더)를 생성합니다.(이름은 원하는 대로 자유롭게 지정하세요)
이제 VS Code를 실행해 `파일/열기`를 선택해 생성한 디렉터리를 찾아 오픈합니다.
그 안에 `index.html`이라는 파일을 생성합니다.(`파일/새파일` > `저장` > 이름과 확장자 설정)
다음 코드와 위 구조를 비교하며 코딩해 보세요.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>GitHub</title>
</head>
<body>
    <div class="header">
        <div class="container">
            <div class="container-left">
                <div class="logo">
                    <img src="https://heropcode.github.io/GitHub-Responsive/img/logo.svg" alt="GitHub Logo">
                </div>
                <div class="menu">
                    <div class="menu-item">Personal</div>
                    <div class="menu-item">Open Source</div>
                    <div class="menu-item">Business</div>
                    <div class="menu-item">Explore</div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

현재는 이 구조를 브라우저에 출력하면 다음과 같이 한장의 이미지와 메뉴에 있는 4개의 TEXT만 나옵니다.(HTML 화면에서 우클릭 > 'Open with Live Server' 선택)

> 'Open with Live Server' 메뉴가 없다면 VS Code 확장 기능으로 Live Server를 설치해야 합니다.

![HTML 예제 결과](/TTEiUup/html_example_result.jpg)

미완성 같지만 HTML은 역할이 끝났습니다.
이제 예쁘게 꾸미기(스타일) 위해 CSS가 필요합니다.

# CSS

## 이보다 쉬울 수 없는 CSS 문법

CSS 문법은 HTML 보다 더 쉽습니다.
아래 예시처럼 선택자, 속성, 값이 있으며 무엇을 의미하는지 이해하는 것으로 기본 문법은 충분합니다!

```css
div {
  font-size: 20px;
  color: red;
}

/* 다음과 같이 이해할 수 있습니다. */
선택자 {
  속성: 값;
  속성: 값;
}
```

### 선택자의 역할

선택자는 HTML에 스타일(CSS)을 적용하기 위해 HTML의 특정한 요소를 선택하는 사인(sign)입니다.
"빨강 글자색(CSS, `color: red;`)을 저기 제목(HTML, `<h1></h1>`)에 적용하겠어!", "파랑 글자색(CSS, `color: blue;`)은 여기 본문(HTML, `<p></p>`)에 적용하겠어!"와 같이 적용할 스타일을 속성(`color`)과 값(`red`, `blue`)으로 나타내고 적용할 대상(H1, P)을 선택자로 나타냅니다.

위 내용을 코드로 구성하면 다음과 같습니다.

```html
<div>
  <h1>제목..</h1>
  <p>본문..</p>
</div>
```

```css
h1 {
  color: red;
}
p {
  color: blue;
}
```

### 속성(Properties)과 값(Value)

속성과 값은 글자색은 무엇, 너비는 얼마, 여백은 얼마 같은 스타일을 지정할 때 사용합니다.

```css
div {
  color: red; /* 글자색은 빨강 */
  font-size: 20px; /* 글자 크기는 20px */
  width: 300px; /* 가로 너비는 300px */
  margin: 20px; /* 바깥 여백은 20px */
  padding: 10px 20px; /* 안쪽 여백은 위아래 10px, 좌우 20px */
  position: absolute; /* 위치는 부모 요소 기준, 흠.. 이게 무슨 뜻일까? */
}
```

속성과 값은 많이 아는 것이 중요합니다.
글자 크기를 키우고 싶은데 `font-size`가 어떤 역할을 하는지 모른다면 글자 크기를 조절할 방법이 없습니다.
또한 위치(좌표)를 지정하고 싶은데 `position` 속성을 모르거나 혹은 그 속성의 값으로 사용하는 `absolute`가 어떤 의미를 갖는지 모르면 역시 방법이 없습니다.

`I like`처럼 영어가 주어와 동사로 이루진 문법이 전부라고 가정해 봅시다. 문법은 매우 쉽겠지만 주어에 들어갈 단어는 `You`, `She`, `They` 등이 많은 단어가 있을 것이고, 동사에 들어갈 단어는 `love`, `work`, `eat` 등 수많은 단어들 들어갈 수 있겠죠?!
많은 단어를 아는 만큼 풍부하고 멋진 문장을 만들 수 있듯, 많은 속성과 값을 아는 만큼 멋진 스타일을 만들어낼 수 있습니다!

## CSS 선언 방식

이제 내가 작성한 CSS 코드를 어떻게 HTML에 적용할 수 있는지 알아봅시다.

### 태그에 직접 작성하기(인라인)

이 방법은 HTML 태그에 직접 작성하기 때문에 선택자가 필요하지 않습니다.

```html
<div style="color: red;">태그에 직접 작성1</div> <!-- red -->
<div style="color: red;">태그에 직접 작성2</div> <!-- red -->
<div style="color: red;">태그에 직접 작성3</div> <!-- red -->
<div style="color: red;">태그에 직접 작성4</div> <!-- red -->
```

### HTML에 포함하기(내장)

CSS만 따로 작성하기 때문에 선택자가 필요합니다.
CSS 코드가 HTML의 `<style></style>` 안에 포함되어 있습니다.

```html
<head>
  <style>
    div {
      color: red;
    }
  </style>  
</head>
<body>
  <div>HTML에 포함1</div> <!-- red -->
  <div>HTML에 포함2</div> <!-- red -->
  <div>HTML에 포함3</div> <!-- red -->
</body>
```

### HTML 외부에서 불러오기

CSS 코드를 완전히 분리할 수 있습니다.
분리된 하나의 CSS 파일을 여러 HTML 파일이 불러와서 사용할 수 있겠네요.

```html
<!-- HTML 1 -->
<head>
  <link rel="stylesheet" href="/css/main.css">
</head>
<body>
  <div>HTML에 외부에서 불러오기1</div> <!-- red -->
</body>
```

```html
<!-- HTML 2 -->
<head>
  <link rel="stylesheet" href="/css/main.css">
</head>
<body>
  <div>HTML에 외부에서 불러오기2</div> <!-- red -->
</body>
```

```css
/* main.css */
div {
  color: red;
}
```

## 선택자

위에서 설명했듯 선택자는 HTML의 특정한 요소를 선택하는 사인(sign)입니다.
여러 종류가 있는데 우선 그중 2가지만 알아보겠습니다.

### 태그로 찾기

선택자를 입력하는 부분에 적용하려는(찾으려는) 태그의 이름을 입력합니다.

```css
/*<h1>은 글자색이 빨강이야!*/
h1 {
  color: red;
}
/*<p>는 글자색이 파랑이야!*/
p {
  color: blue;
}
```

```html
<h1>제목1</h1> <!--red-->
<h1>제목2</h1> <!--red-->
<p>본문1</p> <!--blue-->
<p>본문2</p> <!--blue-->
```

만약 '제목1'과 '본문1'에만 색상을 추가하고 싶다면 어떻게 해야 할까요?
'태그 선택자'만 가지고는 어렵겠네요..

### 클래스로 찾기

좀 더 명확하게 원하는 요소를 찾기 위해서 '클래스 선택자'라는 것이 존재합니다.
예제를 봅시다.

```css
/*class="title"은 글자색이 빨강이야!*/
.title {
  color: red;
}
/*class="main-text"는 글자색이 파랑이야!*/
.main-text {
  color: blue;
}
```

```html
<h1 class="title">제목1</h1> <!--red-->
<h1>제목2</h1>
<p class="main-text">본문1</p> <!--blue-->
<p>본문2</p>
```

`class`라는 HTML 속성에 원하는 별명을 입력합니다.
제목에는 `title`을 본문에는 `main-text`라는 별명을 지정했네요.
이제 CSS에서 이 별명을 기준으로 요소를 찾을 수 있습니다.
단, 주의할 점은 선택자에 앞에 `.`이 붙는다는 것입니다.
`.`은 클래스를 나타내며 CSS의 `.title`은 HTML의 `class="title"`와 동일합니다.
`.`이 없는 선택자 `title`은 태그 `<title>`를 의미하게 되니 전혀 다른 뜻으로 인식됩니다.
이처럼 `.`과 같은 특수한 기호들을 이용해서 HTML과 CSS를 매칭하므로 누락하기 쉽습니다. 따라서 꼼꼼한 선택자 작성이 중요합니다.

## 속성

이제 속성을 알아봅시다.
크기, 여백, 색상 같은 눈에 보이는 스타일을 지정할 수 있습니다.

### 크기

#### width(가로 너비)

요소의 가로 너비를 지정합니다.
단위는 `px`(pixels)을 사용합니다.

```css
div {
  width: 300px;
  요소가로너비: 너비값;
}
```

#### height(세로 너비)

요소의 세로 너비를 지정합니다.

```css
div {
  height: 150px;
  요소세로너비: 너비값;
}
```

#### font-size(글자 크기)

요소 내용(Text)의 글자 크기를 지정합니다.

```css
div {
  font-size: 16px;
  글자크기: 크기값;
}
```

### 여백

#### margin(요소의 바깥 여백)

요소의 바깥 여백을 지정합니다.
바깥 여백은 요소와 요소 사이의 여백(거리, 공간)을 생성할 때 사용합니다.

```css
div {
  margin: 20px;
  요소바깥여백: 여백값;
}
```

위 코드는 `margin`은 요소의 위, 아래, 좌, 우 모두 `20px`의 여백을 지정하겠다는 의미입니다.
세분화하기 위해 아래와 같이 한 방향씩 지정할 수도 있습니다.
위 코드와 아래 코드는 같은 의미입니다.

```css
div {
  margin-top: 20px;
  margin-right: 20px;
  margin-bottom: 20px;
  margin-left: 20px;
  요소바깥여백-위쪽: 여백값;
  요소바깥여백-오른쪽: 여백값;
  요소바깥여백-아래쪽: 여백값;
  요소바깥여백-왼쪽: 여백값;
}
```

#### padding(요소의 내부 여백)

요소의 내부 여백을 지정합니다.
내부 여백은 자식 요소를 감싸는 여백을 의미합니다.

```css
div {
  padding: 20px;
  요소내부여백: 여백값;
}
```

`margin`과 같이 한 방향씩 지정할 수 있습니다.

```css
div {
  padding-top: 20px;
  padding-right: 20px;
  padding-bottom: 20px;
  padding-left: 20px;
  요소내부여백-위쪽: 여백값;
  요소내부여백-오른쪽: 여백값;
  요소내부여백-아래쪽: 여백값;
  요소내부여백-왼쪽: 여백값;
}
```

### 색상

#### color(글자 색상)

요소 내용(Text)의 글자 색상을 지정합니다.
정말 많은 입문자가 `font-color`, `text-color`로 실수를 합니다만 그런 속성은 없습니다.

```css
div {
  color: red;
  글자색상: 빨강;
}
```

#### background(요소 색상)

요소의 배경 색상을 지정합니다.
`color`는 글자의 색만 지정할 수 있으며, 요소의 (배경)색을 바꾸려면 `background-color`가 필요합니다.

```css
div {
  background-color: red;
  요소배경: 빨강;
}
```

## CSS 예제

HTML 끝으로 작성했던 예제에 이어서 CSS를 적용해 봅시다.
`example1` 디렉터리 안에 `css`라는 이름의 디렉터리를 추가로 생성합니다.(Side bar 영역에서 우클릭 > 새폴더 선택)
생성한 `css` 디렉터리 안에 `main.css` 파일을 생성합니다.

다음은 이 예제의 디렉터리와 파일 구조입니다.

```bash
/example1
├─ /css
│  └─ main.css
└─ index.html
```

(아직 CSS 내용은 작성하지 않았지만) 생성한 `main.css` 파일은 기존의 `index.html` 파일과 연결해야 사용할 수 있습니다.
`<link>`를 이용해 HTML 외부에 존재하는 CSS 파일(방금 생성한 `main.css`)을 연결합니다.

```html
<head>
  <!-- 생략... -->
  <link rel="stylesheet" href="./css/main.css">
</head>
```

연결이 되었으니 CSS를 다음과 같이 작성합니다.

```css
body {
  /* 브라우저마다 기본 설정으로 BODY 요소에 margin과 padding의 값이 설정되어 있습니다. */
  /* 각각의 브라우저마다 BODY 요소가 다른 값을 가지고 있을 수 있으므로 우리가 일정하게 초기화해서 사용합니다. */
  /* 0은 단위를 사용하지 않습니다. */
  margin: 0;
  padding: 0;
}
.header {
  /* 화면에는 다음의 값으로 랜더링 되어 있는데 여러 이유로(설명이 많이 필요합니다) 생략 가능합니다. */
  /* width: 100%; */
  /* height: 75px; */
  background-color: white;
  border-bottom: 1px solid lightgray; /* 요소테두리선-아래: 1px두께 가는실선 밝은회색; - header 하단에 회색의 선이 표시됩니다. */
}
.container {
  /* height: 75px; */
  width: 980px;
  margin: auto; /* 요소바깥여백: 여백자동; - 이 속성과 값은 container를 수평 가운데 정렬하는 속성으로 쓰입니다. */
}
.container-left {
  /* width: 370px; */
  /* height: 75px; */
  /* float: left; */
  padding-top: 20px;
  padding-bottom: 20px;
}
.logo {
  margin-right: 5px;
  float: left; /* 수평정렬: 왼쪽부터차례대로; - logo와 menu를 수평 정렬하기 위해 사용되었습니다. 이 속성의 정확한 의미는 수평 정렬이 아니지만 쉽게 이해하도록 의역했습니다. */
}
.logo img { /* logo의 자식(후손) 요소인 img 태그 - 선택자에서 띄어쓰기는 자식(후손)요소를 의미합니다. */
  display: block; /* 요소특성: 형태위주; - img(이미지) 하단에 생기는 불필요한 여백을 없애기 위해서 사용되었습니다. */
}
.menu {
  float: left; /* logo와 menu를 수평 정렬하기 위해 사용되었습니다. */
}
.menu-item {
  font-size: 16px;
  padding: 8px 10px; /* padding-top: 8px; padding-bottom: 8px; padding-left: 10px; padding-right: 10px; 과 같습니다. */
  float: left; /* 각 menu-item들을 수평 정렬하기 위해 사용되었습니다. */
  line-height: 1; /* 줄 높이, 행간과 비슷한 개념으로 이해할 수 있습니다. 기본 값은 normal이며 이는 약 1.2배 정도입니다. 그대로 유지하면 .menu-item의 높이가 약 35px이 되기 때문에 1배로 수정하여 32px로 .logo의 크기와 동일하게 작업합니다. */
}

/* float: left; 를 사용하고 마무리할 때 필요한 코드입니다. */
/* float: left;를 사용한 해당 HTML 요소의 부모 요소에게 class="clearfix"를 입력하여 CSS float 속성에서 발생하는 현상을 해제합니다. */
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

큰 단위의 요소(`header`)부터 코딩하는 방법과, 작은 단위 요소(`menu-item`나 `logo`)부터 코딩하는 방법을 번갈아 가면서 하나하나 변화를 눈으로 익히며 연습을 하시면 금방 익숙해질 겁니다.

이 부분이 중요한데, `float: left`를 사용했다면 사용한 요소의 부모 요소에 꼭 `class="clearfix"`를 입력하고 변화를 확인하세요.(정확한 사용법과 의미는 상당한 분량이라서 여기서 설명하지 않겠습니다)
최종 HTML은 다음과 같습니다. 기존과 달라진 부분을 잘 살펴보세요.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>GitHub</title>
    <!-- link 요소가 추가 되었군요! -->
    <link rel="stylesheet" href="./css/main.css">
</head>
<body>
    <div class="header">
        <!-- clearfix 클래스 값이 추가 되었군요! -->
        <!-- class 속성은 띄어쓰기로 여러 클래스를 구분하여 동시에 사용할 수 있습니다. -->
        <!-- 아래 요소는 <div class="container" class="clearfix"> 와 같습니다. -->
        <div class="container clearfix">
            <!-- clearfix 클래스 값이 추가 되었군요! -->
            <div class="container-left clearfix">
                <div class="logo">
                    <img src="https://heropcode.github.io/GitHub-Responsive/img/logo.svg" alt="GitHub Logo">
                </div>
                <!-- clearfix 클래스 값이 추가 되었군요! -->
                <div class="menu clearfix">
                    <div class="menu-item">Personal</div>
                    <div class="menu-item">Open Source</div>
                    <div class="menu-item">Business</div>
                    <div class="menu-item">Explore</div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

다음과 같은 결과가 나와야 합니다.

![HTML 예제 결과 마지막](/TTEiUup/html_example_result_final.jpg)

# 앞으로..

작성하다 보니 입문자들의 이해를 돕기 위해 생략하거나 의역한 부분이 많습니다.
하지만 시작이 반이라고 여기까지 오셨다면 충분히 성공하셨다고 생각합니다.
많은 비전공 입문자가 생소한 학습 환경에 좌절하지만, HTML/CSS가 사실 그렇게 어려운 내용은 아닙니다.
자신감을 가질 필요가 있습니다!

자, 그러면 입문은 끝났고 앞으로는 어떻게 학습해야 하는지 간단히 정리하겠습니다.

원하는(학습하고자 하는) HTML, CSS, JavaScript(ECMAScript, ES)의 내용을 검색할 때는 `html div tag mdn` 혹은 `css background mdn`과 같이 'MDN'를 함께 검색하세요.
[MDN 웹 문서](https://developer.mozilla.org/ko/)는 모질라(파이어폭스 웹 브라우저)의 공식 웹사이트로 대부분 문서에서 여러 설명과 예제 그리고 한글을 지원하며 매우 신뢰할 수 있습니다.
[W3C의 웹 표준 문서](https://www.w3.org/)가 교과서라면 MDN은 해설집 정도로 이해하시면 쉽겠네요.

또는 [W3Schools 웹사이트](https://www.w3schools.com/)도 추천합니다. MDN과 다르게 영리 목적(배너 광고 등)의 사이트이지만 입문자가 접하기에 좋게 잘 구성되어 있습니다. 단, 정보의 신뢰도는 MDN보다 떨어집니다.


추가로 매우 주관적인 빠른 학습에 대해 말씀드리면,

HTML에는 태그 종류가 상당히 많습니다.
당장은 너무 자세하게 학습하지 마시고, 어떤 태그들이 있고 어떤 역할을 하는지 정도만 빠르게 훑고 넘어가세요.
그리고 필요할 때 찾아보세요!

CSS는 웹앱 디자이너, 퍼블리셔 그리고 프론트엔드 개발자에게 매우 중요합니다.
좋은 UI 프레임워크가 많이 있지만, 원하는 스타일을 만들기 위해서 CSS 학습이 꼭 필요합니다.
각 속성의 역할과 가지는 값(기본값)들을 살펴보세요.
특히 `position`, `float`, `flex` 속성은 집중적으로 공부하고, `grid`는 개념 정도만 이해하세요.

JavaScript는 학습 범위가 아주 넓습니다.
배경지식이 필요한 용어, 기술들이 많다 보니 여유를 가지고 학습하지 않으면 금방 지칠 수 있습니다.
당장 실무에서 필요하지 않은 내용도 많아 큰 그림을 그리도록 전반적으로 가볍게 훑어보고, 선택적으로 실무에 필요한 내용에 집중하는 것이 좋습니다.
발생 가능한 수많은 예외 상황들을 이론에서 모두 다룰 수 없다 보니 실무, 서브 프로젝트, 예제 등 무엇이든 직접 코드를 작성해서 만들어 보세요!

끝까지 읽어주셔서 감사드리고 이 포스트가 많은 입문자에게 도움이 되길 희망합니다.

## 패스트캠퍼스 온라인 강의[FO]

패스트캠퍼스 온라인 강의 자료들이 파편화되어 정리합니다.
온라인 강의와 별개로 [개인 강의 자료](https://github.com/HeropCode/Get-Started)도 참고하세요.
개인 강의 자료에서 확인 가능한 PPT자료들은 [ESC]를 누르면 전체 내용을 펼쳐볼 수 있습니다.

### [FO] HTML/CSS 입문

[입문자에게 추천하는 HTML, CSS 첫걸음](https://heropy.blog/2019/04/24/html-css-starter/)

### [FO] HTML

[한눈에 보는 HTML 요소(Elements & Attributes) 총정리](https://heropy.blog/2019/05/26/html-elements/)
[HTML IMG의 srcset과 sizes 속성(updated)](https://heropy.blog/2019/06/16/html-img-srcset-and-sizes/)

### [FO] CSS

[CSS 개요](https://happy-noether-c87ffa.netlify.app/presentations/level1/css/summary/)
[CSS 속성](https://happy-noether-c87ffa.netlify.app/presentations/level1/css/properties/)
[CSS3 속성](https://happy-noether-c87ffa.netlify.app/presentations/level2/css3/)
[CSS Flex(Flexible Box) 완벽 가이드](https://heropy.blog/2018/11/24/css-flexible-box/)
[CSS Grid 완벽 가이드](https://heropy.blog/2019/08/17/css-grid/)

### [FO] SCSS

[Sass(SCSS) 완전 정복!](https://heropy.blog/2018/01/31/sass/)

### [FO] 마크다운(Markdown)

[MarkDown 사용법 총정리](https://heropy.blog/2017/09/30/markdown/)

### [FO] VueJS

[Vue Todo App 예제](https://github.com/HeropCode/Vue-Todo-app)
[Vue Movie App 예제](https://github.com/HeropCode/Vue-Movie-app)
[Jest와 Vue Test Utils(VTU)로 Vue 컴포넌트 단위(Unit) 테스트](https://heropy.blog/2020/05/20/vue-test-with-jest/)

# 참고자료

https://namu.wiki/w/%EC%98%A4%ED%94%88%20%EC%86%8C%EC%8A%A4
http://www.bloter.net/archives/209318
https://opensource.org/licenses/
https://www.freeformatter.com/html-entities.html
https://wit.nts-corp.com/2013/10/16/280
