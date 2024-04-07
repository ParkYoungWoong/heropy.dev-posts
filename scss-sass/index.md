---
id: Y7OrPe
filename: scss-sass
image: https://heropy.dev/postAssets/Y7OrPe/main.jpg
title: SCSS/Sass 완벽 가이드
createdAt: 2018-01-31
group: CSS
author:
  - ParkYoungWoong
tags:
  - SCSS
  - Sass
description:
  Style(CSS) 작업 시 필수가 되어버린 CSS Preprocessor(전처리기) SCSS/Sass에 대해서 이해하고, CSS로 컴파일하는 방법부터 자세한 SCSS 문법까지 살펴봅니다.
---

## 개요

/// message-box --icon=info
이 글은 SCSS 기준으로 설명하며, 차이점이 있는 경우 별도로 Sass 설명을 추가합니다.
///

CSS는 상대적으로 배우기 쉽고 재미있습니다.
웹 개발 초심자에게는 이만큼 접근하기 좋은 게 없죠.

CSS는 분명 쉽고 재밌지만, 작업이 고도화될수록 불편함도 같이 커집니다.
불필요한 선택자(Selector)의 과용과 연산 기능의 한계, 구문(Statement)의 부재 등 프로젝트의 규모가 커질수록 아쉬움도 같이 커지죠.
하지만 웹에서는 표준 CSS만 동작할 수 있기 때문에 다른 선택권이 없습니다.

그렇다면 우리는 앞으로 계속 CSS만 사용해야 할까요?

### CSS Preprocessor 란?

HTML, CSS를 다루는 분이라면 한 번은 들어봤을 Sass, Less 등이 있습니다.
이 친구들은 CSS 전(예비)처리기 입니다.
보통 CSS Preprocessor 라고 부릅니다.

CSS가 동작하기 전에 사용하는 기능으로,
웹에서는 분명 CSS가 동작하지만 우리는 CSS의 불편함을 이런 확장 기능으로 상쇄할 수 있습니다.

> 사스는 기초 언어에 힘과 우아함을 더해주는 CSS의 확장이다.

### 어떻게 사용하나요?

위에서 언급한 것처럼 웹에서는 CSS만 동작합니다.
[Sass](https://sass-lang.com/), [Less](http://lesscss.org/), [Stylus](http://stylus-lang.com/) 같은 전처리기(이하 '전처리기'로 표기)는 직접 동작시킬 수 없습니다.
그렇다면 어떻게 사용할 수 있을까요?

CSS는 불편하니 일단 배제하고 우선 전처리기로 작성(코딩)합니다.
전처리기는 CSS 문법과 굉장히 유사하지만 선택자의 중첩(Nesting)이나 조건문, 반복문, 다양한 단위(Unit)의 연산 등... 표준 CSS 보다 훨씬 많은 기능을 사용해서 편리하게 작성할 수 있습니다.
단, 웹에서는 직접 동작하지 않으니 이렇게 작성한 전처리기를 웹에서 동작 가능한 표준의 CSS로 컴파일(Compile)합니다.
전처리기로 작성하고 CSS로 컴파일해서 동작시키는 거죠.

### Sass와 SCSS는 차이점은 뭔가요?

Sass(Syntactically Awesome Style Sheets)의 3버전에서 새롭게 등장한 SCSS는 CSS 구문과 완전히 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능을 지원하는 CSS의 상위집합(Superset) 입니다.
즉, SCSS는 CSS와 거의 같은 문법으로 Sass 기능을 지원한다는 말입니다.

더 쉽고 간단한 차이는 `{}`(중괄호)와 `;`(세미콜론)의 유무입니다.
아래의 예제를 비교해 보세요.

Sass:

```sass
.list
  width: 100px
  float: left
  li
    color: red
    background: url("./image.jpg")
    &:last-child
      margin-right: -10px
```

SCSS:

```scss
.list {
  width: 100px;
  float: left;
  li {
    color: red;
    background: url("./image.jpg");
    &:last-child {
      margin-right: -10px;
    }
  }
}
```

Sass는 선택자의 유효범위를 '들여쓰기'로 구분하고, SCSS는 `{}`로 범위를 구분합니다.
Sass 방식과 SCSS 방식 중 어떤 방식이 마음에 드세요?

거의 유일합니다만, 다른 차이도 있습니다.
아래는 Mixins('믹스인'은 재사용 가능한 기능을 만드는 방식의 의미합니다) 예제입니다.
Sass는 단축 구문으로 사용합니다.

:Sass

```sass
=border-radius($radius)
  -webkit-border-radius: $radius
  -moz-border-radius:    $radius
  -ms-border-radius:     $radius
  border-radius:         $radius

.box
  +border-radius(10px)
```

:SCSS

```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```

Sass는 `=`와 `+` 기호로 Mixins 기능을 사용했고,
SCSS는 `@mixin`과 `@include`로 기능을 사용했습니다.

단순한 몇 가지를 제외하면 거의 차이가 없지만 복잡한 문장이 될 경우 여러 환경에 따른 장단점이 있을 수 있습니다.
Sass는 좀 더 간결하고 작성하기 편리하며, `{}`나 `;`를 사용하지 않아도 되니 코드가 훨씬 깔끔해집니다.
SCSS는 인라인 코드(한 줄 작성)를 작성할 수 있고, CSS와 유사한 문법을 가지기 때문에 코드 통합이 훨씬 쉽습니다.

이렇게 몇몇 장단점이 있기 때문에 회사나 팀에서 원하는 방식을 사용해야 하거나, 개인 취향에 따라서 선택할 수 있습니다.
단지 상황에 맞는, 원하는 방식으로 골라서 사용하면 됩니다.

보통의 경우 SCSS를 추천합니다.

## 컴파일 방법

Sass(SCSS)는 웹에서 직접 동작할 수 없습니다.
어디까지나 최종에는 표준 CSS로 동작해야 하며, 우리는 전처리기로 작성 후 CSS로 컴파일해야 합니다.
다양한 방법으로 컴파일이 가능하지만 자바스크립트 개발 환경([Node.js](https://nodejs.org/ko/))에서 추천하는 몇가지 방법을 소개합니다.

### SassMeister

간단한 Sass 코드는 컴파일러를 설치하는게 부담될 수 있습니다.
그럴 경우 [SassMeister](https://www.sassmeister.com/)를 사용할 수 있습니다.

페이지 접속 후 바로 Sass나 SCSS 문법으로 코딩하면 CSS로 실시간 변환됩니다.
HTML를 작성하여 적용된 결과를 보거나 Sass 버전 설정 등 여러 환경 설정들을 지원하니 학습에 도움이 될 것입니다.

### Webpack

```bash
npm i -D style-loader css-loader
npm i -D sass-loader sass
```

```js --path=webpack.config.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.s?[ac]ss$/i,
        use: [
          'style-loader',
          'css-loader',
          'sass-loader',
        ]
      }
    ]
  }
}
```

### Parcel

```bash
npm i parcel
npm i -D sass
```

HTML에 `<link>`로 SCSS/Sass 파일만 연결하면 됩니다.
다른 설정은 필요하지 않습니다.

```html
<link rel="stylesheet" href="./src/main.scss">
```

```bash
npx parcel index.html
```

### Vite

[Vue.js](https://vuejs.org/) 개발환경을 위한 빠른 웹 개발 빌드 도구 [Vite](https://vitejs.dev/)는 Sass(SCSS)를 지원합니다.
간단하게 설치 후 별도의 구성 없이 사용할 수 있습니다.

```bash
npm i -D sass
```

## 주석

CSS 주석(Comment)은 `/* ... */` 입니다.
Sass(SCSS)는 JavaScript처럼 두 가지 스타일의 주석을 사용합니다.

```scss
// 컴파일되지 않는 주석
/* 컴파일되는 주석 */
```

Sass의 경우 컴파일되는 여러 줄 주석을 사용할 때 각 줄 앞에 `*`을 붙여야 하고, 중요한 것은 `*`의 라인을 맞춰줘야 합니다.

Sass:

```sass
/* 컴파일되는
 * 여러 줄
 * 주석 */

// Error
/* 컴파일되는
* 여러 줄
    * 주석 */
```

SCSS는 각 줄에 `*`이 없어도 문제되지 않습니다. 따라서 기존 CSS와 호환이 쉽습니다.

SCSS:

```scss
/*
컴파일되는
여러 줄
주석
*/
```

## 데이터 종류

데이터 | 설명 | 예시
---|---|---
Numbers | 숫자 | `1`, `.82`, `20px`, `2em`...
Strings | 문자 | `bold`, `relative`, `"/images/a.png"`, `"dotum"`
Colors | 색상 표현 | `red`, `blue`, `#FFFF00`, `rgba(255,0,0,.5)`
Booleans | 논리 | `true`, `false`
Nulls | 아무것도 없음 | `null`
Lists | 공백이나 `,`로 구분된 값의 목록 | `(apple, orange, banana)`, `apple orange`
Maps | Lists와 유사하나 값이 `Key: Value` 형태 | `(apple: a, orange: o, banana: b)`

### 특이사항

Sass에서 사용하는 데이터 종류들의 몇 가지 특이사항을 소개합니다.

- Numbers: 숫자에 단위가 있거나 없습니다.
- Strings: 문자에 따옴표가 있거나 없습니다.
- Nulls: 속성값으로 `null`이 사용되면 컴파일하지 않습니다.
- Lists: `()`를 붙이거나 붙이지 않습니다.
- Maps: `()`를 꼭 붙여야 합니다.

## 중첩

Sass는 중첩(Nesting) 기능을 사용할 수 있습니다.
상위 선택자의 반복을 피하고 좀 더 편리하게 복잡한 구조를 작성할 수 있습니다.

SCSS:

```scss
.section {
  width: 100%;
  .list {
    padding: 20px;
    li {
      float: left;
    }
  }
}
```

Compiled to:

```css
.section {
  width: 100%;
}
.section .list {
  padding: 20px;
}
.section .list li {
  float: left;
}
```

### Ampersand(&)

중첩 안에서 `&` 키워드는 상위(부모) 선택자를 참조하여 치환합니다.

SCSS:

```scss
.btn {
  position: absolute;
  &.active {
    color: red;
  }
}

.list {
  li {
    &:last-child {
      margin-right: 0;
    }
  }
}
```

Compiled to:

```css
.btn {
  position: absolute;
}
.btn.active {
  color: red;
}
.list li:last-child {
  margin-right: 0;
}
```

`&` 키워드가 참조한 상위 선택자로 치환되는 것이기 때문에 다음과 같이 응용할 수도 있습니다.

SCSS:

```scss
.fs {
  &-small { font-size: 12px; }
  &-medium { font-size: 14px; }
  &-large { font-size: 16px; }
}
```

Compiled to:

```css
.fs-small {
  font-size: 12px;
}
.fs-medium {
  font-size: 14px;
}
.fs-large {
  font-size: 16px;
}
```

### @at-root

중첩에서 벗어나고 싶을 때 `@at-root` 키워드를 사용합니다.
중첩 안에서 생성하되 중첩 밖에서 사용해야 경우에 유용합니다.

SCSS:

```scss
.list {
  $w: 100px;
  $h: 50px;
  li {
    width: $w;
    height: $h;
  }
  @at-root .box {
    width: $w;
    height: $h;
  }
}
```

Compiled to:

```css
.list li {
  width: 100px;
  height: 50px;
}
.box {
  width: 100px;
  height: 50px;
}
```

아래 예제 처럼 `.list` 안에 있는 특정 변수를 범위 밖에서 사용할 수 없기 때문에, 위 예제 처럼 `@at-root` 키워드를 사용해야 합니다.(변수는 아래에서 설명합니다)

```scss
.list {
  $w: 100px;
  $h: 50px;
  li {
    width: $w;
    height: $h;
  }
}

// Error
.box {
  width: $w;
  height: $h;
}
```

### 중첩된 속성

`font-`, `margin-` 등과 같이 동일한 네임 스페이스를 가지는 속성들을 다음과 같이 사용할 수 있습니다.

SCSS:

```scss
.box {
  font: {
    weight: bold;
    size: 10px;
    family: sans-serif;
  };
  margin: {
    top: 10px;
    left: 20px;
  };
  padding: {
    bottom: 40px;
    right: 30px;
  };
}
```
Compiled to:

```css
.box {
  font-weight: bold;
  font-size: 10px;
  font-family: sans-serif;
  margin-top: 10px;
  margin-left: 20px;
  padding-bottom: 40px;
  padding-right: 30px;
}
```

## 변수

반복적으로 사용되는 값을 변수로 지정할 수 있습니다.
변수 이름 앞에는 항상 `$`를 붙입니다.

```scss
$변수이름: 속성값;
```

SCSS:

```scss
$color-primary: #e96900;
$url-images: "/assets/images/";
$w: 200px;

.box {
  width: $w;
  margin-left: $w;
  background: $color-primary url($url-images + "bg.jpg");
}
```

Compiled to:

```css
.box {
  width: 200px;
  margin-left: 200px;
  background: #e96900 url("/assets/images/bg.jpg");
}
```

### 변수 유효범위

변수는 사용 가능한 유효범위(Scope)가 있습니다.
선언된 블록(`{}`) 내에서만 유효범위를 가집니다.

변수 `$color`는 `.box1`의 블록 안에서 설정되었기 때문에, 블록 밖의 `.box2`에서는 사용할 수 없습니다.

```scss
.box1 {
  $color: #111;
  background: $color;
}
// Error
.box2 {
  background: $color;
}
```

### 변수 재 할당

다음과 같이 변수에 변수를 다시 할당(Reassignment)할 수 있습니다.

SCSS:

```scss
$red: #FF0000;
$blue: #0000FF;

$color-primary: $blue;
$color-danger: $red;

.box {
  color: $color-primary;
  background: $color-danger;
}
```

Compiled to:

```css
.box {
  color: #0000FF;
  background: #FF0000;
}
```

### !global

`!global` 플래그를 사용하면 변수의 유효범위를 전역(Global)로 설정할 수 있습니다.

SCSS:

```scss
.box1 {
  $color: #111 !global;
  background: $color;
}
.box2 {
  background: $color;
}
```

Compiled to:

```css
.box1 {
  background: #111;
}
.box2 {
  background: #111;
}
```

대신 기존에 사용하던 같은 이름의 변수가 있을 경우 값이 덮어져 사용될 수 있습니다.

SCSS:

```scss
$color: #000;
.box1 {
  $color: #111 !global;
  background: $color;
}
.box2 {
  background: $color;
}
.box3 {
  $color: #222;
  background: $color;
}
```

Compiled to:

```css
.box1 {
  background: #111;
}
.box2 {
  background: #111;
}
.box3 {
  background: #222;
}
```

### !default

`!default` 플래그는 할당되지 않은 변수의 초깃값을 설정합니다.
즉, 할당되어있는 변수가 있다면 변수가 기존 할당 값을 사용합니다.

SCSS:

```scss
$color-primary: red;

.box {
  $color-primary: blue !default;
  background: $color-primary;
}
```

Compiled to:

```css
.box {
  background: red;
}
```

좀 더 유용하게, '변수와 값을 설정하겠지만, 혹시 기존 변수가 있을 경우는 현재 설정하는 변수의 값은 사용하지 않겠다'는 의미로 쓸 수 있습니다.
예를 들어, [Bootstrap](https://github.com/twbs/bootstrap/tree/v4-dev/scss) 같은 외부 Sass(SCSS) 라이브러리를 연결했더니 변수 이름이 같아 내가 작성한 코드의 변수들이 Overwrite(덮어쓰기) 된다면 문제가 있겠죠.
반대로 내가 만든 Sass(SCSS) 라이브러리가 다른 사용자 코드의 변수들을 Overwrite 한다면, 사용자들은 그 라이브러리를 더 이상 사용하지 않을 것입니다.
이럴 때 Sass(SCSS) 라이브러리(혹은 새롭게 만든 모듈)에서 사용하는 변수에 `!default` 플래그가 있다면 기존 코드(원본)를 Overwrite 하지 않고도 사용할 수 있습니다.

```scss
// _config.scss
$color-active: red;
```

```scss
// main.scss
@import 'config';

$color-active: blue !default;

.box {
  background: $color-active;  // red
}
```

다음은 Bootstrap 코드([_variables.scss](https://github.com/twbs/bootstrap/blob/v4-dev/scss/_variables.scss))의 일부입니다.

<script src="https://gist.github.com/ParkYoungWoong/3c1c1c326a38753161e06e78c8264b3d.js"></script>

### #{}

`#{}`를 이용해서 코드의 어디든지 변수 값을 넣을 수 있습니다.
이를 문자 보간(Interpolation)이라고 합니다.

```scss
$family: unquote("Droid+Sans");
@import url("http://fonts.googleapis.com/css?family=#{$family}");
```

```css
@import url("http://fonts.googleapis.com/css?family=Droid+Sans");
```

Sass의 내장 함수 `unquote()`는 문자에서 따옴표를 제거합니다.

## 가져오기

`@import`로 외부에서 가져온 Sass 파일은 모두 단일 CSS 출력 파일로 병합됩니다.
또한, 가져온 파일에 정의된 모든 변수 또는 Mixins 등을 주 파일에서 사용할 수 있습니다.

Sass `@import`는 기본적으로 Sass 파일을 가져오는데, CSS `@import` 규칙으로 컴파일되는 몇 가지 상황이 있습니다.

- 파일 확장자가 `.css`일 때
- 파일 이름이 `http://`로 시작하는 경우
- `url()`이 붙었을 경우
- 미디어쿼리가 있는 경우

위의 경우 CSS `@import` 규칙대로 컴파일 됩니다.

```scss
@import "hello.css";
@import "http://hello.com/hello";
@import url(hello);
@import "hello" screen;
```

### 여러 파일 가져오기

하나의 `@import`로 여러 파일을 가져올 수도 있습니다.
파일 이름은 `,`로 구분합니다.

```scss
@import "header", "footer";
```

### 파일 분할

프로젝트 규모가 커지면 파일들을 `header`나 `side-menu` 같이 각 기능과 부분으로 나눠 유지보수가 쉽도록 관리하게 됩니다.
이 경우 파일이 점점 많아지는데, 모든 파일이 컴파일 시 각각의 `~.css` 파일로 나눠서 저장된다면 관리나 성능 차원에서 문제가 될 수 있겠죠.
그래서 Sass는 파일 분할(Partials) 기능을 지원합니다.
파일 이름 앞에 `_`를 붙여(`_header.scss`와 같이) `@import`로 가져오면 컴파일 시 `~.css` 파일로 컴파일하지 않습니다.

예를 들어보겠습니다.
다음과 같이 `scss/` 안에 3개의 Sass 파일이 있습니다.

```bash
Sass-App
  # ...
  ├─scss
  │  ├─header.scss
  │  ├─side-menu.scss
  │  └─main.scss
  # ...
```

`main.scss`로 나머지 `~.scss` 파일을 가져옵니다.

```scss
// main.scss
@import "header", "side-menu";
```

그리고 이 파일들을 `css/`디렉토리로 컴파일합니다.
(컴파일은 위에서 설명한 `node-sass`로 진행합니다.)

```bash
# `scss`디렉토리에 있는 파일들을 `css`디렉토리로 컴파일
node-sass scss --output css
```

컴파일 후 확인하면 아래와 같이 `scss/`에 있던 파일들이 `css/` 안에 각 하나씩의 파일로 컴파일됩니다.

```bash
Sass-App
  # ...
  ├─css
  │  ├─header.css
  │  ├─side-menu.css
  │  └─main.css
  ├─scss
  │  ├─header.scss
  │  ├─side-menu.scss
  │  └─main.scss
  # ...
```

자, 이번에는 가져올 파일 이름에 `_`를 붙이겠습니다.
메인 파일인 `main.scss`에서는 `_`를 사용하지 않습니다.

```bash
Sass-App
  # ...
  ├─scss
  │  ├─_header.scss
  │  ├─_side-menu.scss
  │  └─main.scss
  # ...
```

```scss
// main.scss
@import "header", "side-menu";
```

같은 방법으로 컴파일하면...

```bash
node-sass scss --output css
```

아래처럼 별도의 파일로 컴파일되지 않고 사용됩니다.

```bash
Sass-App
  # ...
  ├─css
  │  └─main.css  # main + header + side-menu
  ├─scss
  │  ├─header.scss
  │  ├─side-menu.scss
  │  └─main.scss
  # ...
```

`Webpack`이나 `Parcel`, `Gulp` 같은 일반적인 빌드툴에서는 Partials 기능을 사용할 필요 없이, 설정된 값에 따라 빌드됩니다. 하지만 되도록 `_`를 사용할 것을 권장합니다.

## 연산

Sass는 기본적인 연산(Operations) 기능을 지원합니다.
레이아웃 작업시 상황에 맞게 크기를 계산을 하거나 정해진 값을 나눠서 작성할 경우 유용합니다.
다음은 Sass에서 사용 가능한 연산자 종류 입니다.

산술 연산자:

종류 | 설명 | 주의사항
:---:|:---:|:---:
`+` | 더하기 |
`-` | 빼기 |
`*` | 곱하기 | 하나 이상의 값이 반드시 숫자(Number)
`/` | 나누기 | 오른쪽 값이 반드시 숫자(Number)
`%` | 나머지 |

비교 연산자:

종류 | 설명
:---:|:---:
`==` | 동등
`!=` | 부등
`<` | 대소 / 보다 작은
`>` | 대소 / 보다 큰
`<=` | 대소 및 동등 / 보다 작거나 같은
`>=` | 대소 및 동등 / 보다 크거나 같은

논리(불린, Boolean) 연산자:

종류 | 설명
:---:|:---:
`and` | 그리고
`or` | 또는
`not` | 부정

### 숫자

#### 상대적 단위 연산

일반적으론 절댓값을 나타내는 `px` 단위로 연산을 합니다만, 상대적 단위(`%`, `em`, `vw` 등)의 연산의 경우 [CSS calc()](https://developer.mozilla.org/ko/docs/Web/CSS/calc)로 연산해야 합니다.

```scss
width: 50% - 20px;  // 단위 모순 에러(Incompatible units error)
width: calc(50% - 20px);  // 연산 가능
```

#### 나누기 연산의 주의사항

CSS는 속성 값의 숫자를 분리하는 방법으로 `/`를 허용하기 때문에 `/`가 나누기 연산으로 사용되지 않을 수 있습니다.
예를 들어, `font: 16px / 22px serif;` 같은 경우 `font-size: 16px`와 `line-height: 22px`의 속성값 분리를 위해서 `/`를 사용합니다.
아래 예제를 보면 나누기 연산자만 연산 되지 않고 그대로 컴파일됩니다.

SCSS:

```scss
div {
  width: 20px + 20px;  // 더하기
  height: 40px - 10px;  // 빼기
  font-size: 10px * 2;  // 곱하기
  margin: 30px / 2;  // 나누기
}
```

Compiled to:

```css
div {
  width: 40px;  /* OK */
  height: 30px;  /* OK */
  font-size: 20px;  /* OK */
  margin: 30px / 2;  /* ?? */
}
```

따라서 `/`를 나누기 연산 기능으로 사용하려면 다음과 같은 조건을 충족해야 합니다.

- 값 또는 그 일부가 변수에 저장되거나 함수에 의해 반환되는 경우
- 값이 `()`로 묶여있는 경우
- 값이 다른 산술 표현식의 일부로 사용되는 경우

SCSS:

```scss
div {
  $x: 100px;
  width: $x / 2;  // 변수에 저장된 값을 나누기
  height: (100px / 2);  // 괄호로 묶어서 나누기
  font-size: 10px + 12px / 3;  // 더하기 연산과 같이 사용
}
```

Compiled to:

```css
div {
  width: 50px;
  height: 50px;
  font-size: 14px;
}
```

### 문자

문자 연산에는 `+`가 사용됩니다.
문자 연산의 결과는 첫 번째 피연산자를 기준으로 합니다.
첫 번째 피연산자에 따옴표가 붙어있다면 연산 결과를 따옴표로 묶습니다.
반대로 첫 번째 피연산자에 따옴표가 붙어있지 않다면 연산 결과도 따옴표를 처리하지 않습니다.

SCSS:

```scss
div::after {
  content: "Hello " + World;
  flex-flow: row + "-reverse" + " " + wrap
}
```

Compiled to:

```css
div::after {
  content: "Hello World";
  flex-flow: row-reverse wrap;
}
```

### 색상

색상도 연산할 수 있습니다.

SCSS:

```scss
div {
  color: #123456 + #345678;
  // R: 12 + 34 = 46
  // G: 34 + 56 = 8a
  // B: 56 + 78 = ce
  background: rgba(50, 100, 150, .5) + rgba(10, 20, 30, .5);
  // R: 50 + 10 = 60
  // G: 100 + 20 = 120
  // B: 150 + 30 = 180
  // A: Alpha channels must be equal
}
```

Compiled to:

```css
div {
  color: #468ace;
  background: rgba(60, 120, 180, 0.5);
}
```

RGBA에서 Alpha 값은 연산되지 않으며 서로 동일해야 다른 값의 연산이 가능합니다.
Alpha 값을 연산하기 위한 다음과 같은 색상 함수(Color Functions)를 사용할 수 있습니다.

[opacify()](http://sass-lang.com/documentation/Sass/Script/Functions.html#opacify-instance_method), [transparentize()](http://sass-lang.com/documentation/Sass/Script/Functions.html#transparentize-instance_method)

SCSS:

```scss
$color: rgba(10, 20, 30, .5);
div {
  color: opacify($color, .3);  // 30% 더 불투명하게 / 0.5 + 0.3
  background-color: transparentize($color, .2);  // 20% 더 투명하게 / 0.5 - 0.2
}
```

Compiled to:

```css
div {
  color: rgba(10, 20, 30, 0.8);
  background-color: rgba(10, 20, 30, 0.3);
}
```

### 논리

Sass의 `@if` 조건문에서 사용되는 논리(Boolean) 연산에는 '그리고',' 또는', '부정'이 있습니다.
자바스크립트 문법에 익숙하다면 `&&`, `||`, `!`와 같은 기능으로 생각하면 됩니다.

종류 | 설명
:---:|:---:
`and` | 그리고
`or` | 또는
`not` | 부정(반대)

간단한 예제를 확인하고, 더 자세한 내용은 조건문에서 살펴보겠습니다.

SCSS:

```scss
$width: 90px;
div {
  @if not ($width > 100px) {
    height: 300px;
  }
}
```

Compiled to:

```css
div {
  height: 300px;
}
```

## 재활용

Sass Mixins는 스타일 시트 전체에서 **재사용 할 CSS 선언 그룹** 을 정의하는 아주 훌륭한 기능입니다.
약간의 Mixin(믹스인)으로 다양한 스타일을 만들어낼 수 있습니다.

우선, Mixin은 두 가지만 기억하면 됩니다.
선언하기(`@mixin`)와 포함하기(`@include`) 입니다.
만들어서(선언), 사용(포함)하는 거죠!

### @mixin

기본적인 Mixin 선언은 아주 간단합니다.
`@mixin` 지시어를 이용하여 스타일을 정의합니다.

```scss
// SCSS
@mixin 믹스인이름 {
  스타일;
}

// Sass
=믹스인이름
  스타일
```

```scss
// SCSS
@mixin large-text {
  font-size: 22px;
  font-weight: bold;
  font-family: sans-serif;
  color: orange;
}

// Sass
=large-text
  font-size: 22px
  font-weight: bold
  font-family: sans-serif
  color: orange
```

Mixin은 선택자를 포함 가능하고 상위(부모) 요소 참조(`&` 같은)도 할 수 있습니다.

```scss
@mixin large-text {
  font: {
    size: 22px;
    weight: bold;
    family: sans-serif;
  }
  color: orange;

  &::after {
    content: "!!";
  }

  span.icon {
    background: url("/images/icon.png");
  }
}
```

### @include

선언된 Mixin을 사용(포함)하기 위해서는 `@include`가 필요합니다.
위에서 선언한 Mixin을 사용해 보겠습니다.

```scss
// SCSS
@include 믹스인이름;

// Sass
+믹스인이름
```

SCSS:

```scss
// SCSS
h1 {
  @include large-text;
}
div {
  @include large-text;
}

// Sass
h1
  +large-text
div
  +large-text
```

Compiled to:

```css
h1 {
  font-size: 22px;
  font-weight: bold;
  font-family: sans-serif;
  color: orange;
}
h1::after {
  content: "!!";
}
h1 span.icon {
  background: url("/images/icon.png");
}

div {
  font-size: 22px;
  font-weight: bold;
  font-family: sans-serif;
  color: orange;
}
div::after {
  content: "!!";
}
div span.icon {
  background: url("/images/icon.png");
}
```

### 인수

Mixin은 함수(Functions)처럼 인수(Arguments)를 가질 수 있습니다.
하나의 Mixin으로 다양한 결과를 만들 수 있습니다.

```scss
// SCSS
@mixin 믹스인이름($매개변수) {
  스타일;
}
@include 믹스인이름(인수);

// Sass
=믹스인이름($매개변수)
  스타일

+믹스인이름(인수)
```

> 매개변수(Parameters)란 변수의 한 종류로, 제공되는 여러 데이터 중 하나를 가리키기 위해 사용된다.
제공되는 여러 데이터들을 전달인수(Arguments) 라고 부른다.

SCSS:

```scss
@mixin dash-line($width, $color) {
  border: $width dashed $color;
}

.box1 { @include dash-line(1px, red); }
.box2 { @include dash-line(4px, blue); }
```

Compiled to:

```css
.box1 {
  border: 1px dashed red;
}
.box2 {
  border: 4px dashed blue;
}
```

#### 인수의 기본값 설정

인수(argument)는 기본값(default value)을 가질 수 있습니다.
`@include` 포함 단계에서 별도의 인수가 전달되지 않으면 기본값이 사용됩니다.

```scss
@mixin 믹스인이름($매개변수: 기본값) {
  스타일;
}
```

SCSS:

```scss
@mixin dash-line($width: 1px, $color: black) {
  border: $width dashed $color;
}

.box1 { @include dash-line; }
.box2 { @include dash-line(4px); }
```

Compiled to:

```css
.box1 {
  border: 1px dashed black;
}
.box2 {
  border: 4px dashed black;
}
```

#### 키워드 인수

```scss
@mixin 믹스인이름($매개변수A: 기본값, $매개변수B: 기본값) {
  스타일;
}

@include 믹스인이름($매개변수B: 인수);
```

Mixin에 전달할 인수를 입력할 때 명시적으로 키워드(변수)를 입력하여 작성할 수 있고, 이를 키워드 인수(Keyword Arguments)라고 합니다.
별도의 인수 입력 순서를 필요로 하지 않아 편리하게 작성할 수 있습니다.
단, 작성하지 않은 인수가 적용될 수 있도록 기본값을 설정해 주는 것이 좋습니다.

```scss
@mixin position(
  $p: absolute,
  $t: null,
  $b: null,
  $l: null,
  $r: null
) {
  position: $p;
  top: $t;
  bottom: $b;
  left: $l;
  right: $r;
}

.absolute {
  // 키워드 인수로 설정할 값만 전달
  @include position($b: 10px, $r: 20px);
}
.fixed {
  // 인수가 많아짐에 따라 가독성을 확보하기 위해 줄바꿈
  @include position(
    fixed,
    $t: 30px,
    $r: 40px
  );
}
```

```css
.absolute {
  position: absolute;
  bottom: 10px;
  right: 20px;
}
.fixed {
  position: fixed;
  top: 30px;
  right: 40px;
}
```

#### 가변 인수

때때로 입력할 인수의 개수가 불확실한 경우가 있습니다.
그럴 경우 가변 인수(Variable Arguments)를 사용할 수 있습니다.
가변 인수는 매개변수 뒤에 `...`을 붙여줍니다.

```scss
@mixin 믹스인이름($매개변수...) {
  스타일;
}

@include 믹스인이름(인수A, 인수B, 인수C);
```

```scss
// 인수를 순서대로 하나씩 전달 받다가, 3번째 매개변수($bg-values)는 인수의 개수에 상관없이 받음
@mixin bg($width, $height, $bg-values...) {
  width: $width;
  height: $height;
  background: $bg-values;
}

div {
  // 위의 Mixin(bg) 설정에 맞게 인수를 순서대로 전달하다가 3번째 이후부터는 개수에 상관없이 전달
  @include bg(
    100px,
    200px,
    url("/images/a.png") no-repeat 10px 20px,
    url("/images/b.png") no-repeat,
    url("/images/c.png")
  );
}
```

```css
div {
  width: 100px;
  height: 200px;
  background: url("/images/a.png") no-repeat 10px 20px,
              url("/images/b.png") no-repeat,
              url("/images/c.png");
}
```

위에선 인수를 받는 매개변수에 `...`을 사용하여 가변 인수를 활용했습니다.
이번엔 반대로 가변 인수를 전달할 값으로 사용해 보겠습니다.

```scss
@mixin font(
  $style: normal,
  $weight: normal,
  $size: 16px,
  $family: sans-serif
) {
  font: {
    style: $style;
    weight: $weight;
    size: $size;
    family: $family;
  }
}
div {
  // 매개변수 순서와 개수에 맞게 전달
  $font-values: italic, bold, 16px, sans-serif;
  @include font($font-values...);
}
span {
  // 필요한 값만 키워드 인수로 변수에 담아 전달
  $font-values: (style: italic, size: 22px);
  @include font($font-values...);
}
a {
  // 필요한 값만 키워드 인수로 전달
  @include font((weight: 900, family: monospace)...);
}
```

```css
div {
  font-style: italic;
  font-weight: bold;
  font-size: 16px;
  font-family: sans-serif;
}
span {
  font-style: italic;
  font-weight: normal;
  font-size: 22px;
  font-family: sans-serif;
}
a {
  font-style: normal;
  font-weight: 900;
  font-size: 16px;
  font-family: monospace;
}
```

### @content

선언된 Mixin에 `@content`이 포함되어 있다면 해당 부분에 원하는 **스타일 블록** 을 전달할 수 있습니다.
이 방식을 사용하여 기존 Mixin이 가지고 있는 기능에 선택자나 속성 등을 추가할 수 있습니다.

```scss
@mixin 믹스인이름() {
  스타일;
  @content;
}

@include 믹스인이름() {
  // 스타일 블록
  스타일;
}
```

SCSS:

```scss
@mixin icon($url) {
  &::after {
    content: $url;
    @content;
  }
}
.icon1 {
  // icon Mixin의 기존 기능만 사용
  @include icon("/images/icon.png");
}
.icon2 {
  // icon Mixin에 스타일 블록을 추가하여 사용
  @include icon("/images/icon.png") {
    position: absolute;
  };
}
```

Compiled to:

```css
.icon1::after {
  content: "/images/icon.png";
}
.icon2::after {
  content: "/images/icon.png";
  position: absolute;
}
```

Mixin에게 전달된 스타일 블록은 Mixin의 범위가 아니라 스타일 블록이 정의된 범위에서 평가됩니다.
즉, Mixin의 매개변수는 전달된 스타일 블록 안에서 사용되지 않고 전역 값으로 해석됩니다.
전역 변수(Global variables)와 지역 변수(Local variables)를 생각하면 좀 더 쉽습니다.

SCSS:

```scss
$color: red;

@mixin colors($color: blue) {
  // Mixin의 범위
  @content;
  background-color: $color;
  border-color: $color;
}

div {
  @include colors() {
    // 스타일 블록이 정의된 범위
    color: $color;
  }
}
```

Compiled to:

```css
div {
  color: red;
  background-color: blue;
  border-color: blue;
}
```

## 확장

특정 선택자가 다른 선택자의 모든 스타일을 가져야하는 경우가 종종 있습니다.
이럴 경우 선택자의 확장(Extend) 기능을 사용할 수 있습니다.
다음 예제를 봅시다.

```scss
@extend 선택자;
```

SCSS:

```scss
.btn {
  padding: 10px;
  margin: 10px;
  background: blue;
}
.btn-danger {
  @extend .btn;
  background: red;
}
```

Compiled to:

```css
.btn, .btn-danger {
  padding: 10px;
  margin: 10px;
  background: blue;
}
.btn-danger {
  background: red;
}
```

컴파일된 결과가 마음에 드시나요?
결과를 보면 `,`로 구분하는 다중 선택자(Multiple Selector)가 만들어졌습니다.

사실 `@extend`는 다음과 같은 문제를 고려해야 합니다.

- 내 현재 선택자(위 예제의 `.btn-danger`)가 어디에 첨부될 것인가?
- 원치 않는 부작용이 초래될 수도 있는가?
- 이 한 번의 확장으로 얼마나 큰 CSS가 생성되는가?

결과적으로 확장(Extend) 기능은 무해하거나 혹은 유익할 수도 있지만 그만큼 <strong>부작용</strong>을 가지고 있을 수 있습니다.
따라서 확장은 사용을 권장하지 않으며, 위에서 살펴본 <strong>Mixin을 대체 기능으로 사용</strong>하세요.

사용을 권장하지 않는 이유에 대해서 좀 더 자세한 정보를 원하면 [Sass Guidelines Extend](https://sass-guidelin.es/ko/#extend)를 참고하세요.

## 함수

자신의 함수(Functions)를 정의하여 사용할 수 있습니다.
함수와 Mixins은 거의 유사하지만 반환되는 내용이 다릅니다.

Mixin은 위에서 살펴본 대로 지정한 스타일(Style)을 반환하는 반면,
함수는 보통 연산된(Computed) 특정 <strong>값</strong>을 `@return` 지시어를 통해 반환합니다.

```scss
// Mixins
@mixin 믹스인이름($매개변수) {
  스타일;
}

// Functions
@function 함수이름($매개변수) {
  @return 값
}
```

사용하는 방법에도 차이가 있습니다.
Mixin은 `@include` 지시어를 사용하는 반면,
함수는 함수이름으로 바로 사용합니다.

```scss
// Mixin
@include 믹스인이름(인수);

// Functions
함수이름(인수)
```

SCSS:

```scss
$max-width: 980px;

@function columns($number: 1, $columns: 12) {
  @return $max-width * ($number / $columns)
}

.box_group {
  width: $max-width;

  .box1 {
    width: columns();  // 1
  }
  .box2 {
    width: columns(8);
  }
  .box3 {
    width: columns(3);
  }
}
```

Compiled to:

```css
.box_group {
  /* 총 너비 */
  width: 980px;
}
.box_group .box1 {
  /* 총 너비의 약 8.3% */
  width: 81.66667px;
}
.box_group .box2 {
  /* 총 너비의 약 66.7% */
  width: 653.33333px;
}
.box_group .box3 {
  /* 총 너비의 25% */
  width: 245px;
}
```

위와 같이 함수는 `@include` 같은 별도의 지시어 없이 사용하기 때문에 내가 지정한 함수와 내장 함수(Built-in Functions)의 이름이 충돌할 수 있습니다.
따라서 내가 지정한 함수에는 별도의 접두어를 붙여주는 것이 좋습니다.

> 내장 함수란, 응용 프로그램에 내장되어 있으며 최종 사용자가 액세스 할 수 있는 기능입니다.
예를 들어, 대부분의 스프레드 시트 응용 프로그램은 행이나 열의 모든 셀을 추가하는 내장 SUM 함수를 지원합니다.

예를 들어, 색의 빨강 성분을 가져오는 내장 함수로 이미 `red()`가 있습니다.
같은 이름을 사용하여 함수를 정의하면 이름이 충돌하기 때문에 별도의 접두어를 붙여 `extract-red()` 같은 이름을 만들 수 있습니다.

```scss
// 내가 정의한 함수
@function extract-red($color) {
  // 내장 함수
  @return rgb(red($color), 0, 0);
}

div {
  color: extract-red(#D55A93);
}
```

혹은 모든 내장 함수의 이름을 다 알고 있을 수 없기 때문에 특별한 이름을 접두어로 사용할 수도 있습니다.
`my-custom-func-red()`

## 조건과 반복

### if 함수

조건의 값(`true`, `false`)에 따라 두 개의 표현식 중 하나만 반환합니다.
[조건부 삼항 연산자(conditional ternary operator)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)와 비슷합니다.

조건의 값이 `true`이면 `표현식1`을,
조건의 값이 `false`이면 `표현식2`를 실행합니다.

```scss
if(조건, 표현식1, 표현식2)
```

SCSS:

```scss
$width: 555px;
div {
  width: if($width > 300px, $width, null);
}
```

Compiled to:

```css
div {
  width: 555px;
}
```

### @if

`@if` 지시어는 조건에 따른 분기 처리가 가능하며, [if 문(if statements)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/if...else)과 유사합니다.
같이 사용할 수 있는 지시어는 `@else`, `if`가 있습니다.
추가 지시어를 사용하면 좀 더 복잡한 조건문을 작성할 수 있습니다.

```scss
// @if
@if (조건) {
  /* 조건이 참일 때 구문 */
}

// @if @else
@if (조건) {
  /* 조건이 참일 때 구문 */
} @else {
  /* 조건이 거짓일 때 구문 */
}

// @if @else if
@if (조건1) {
  /* 조건1이 참일 때 구문 */
} @else if (조건2) {
  /* 조건2가 참일 때 구문 */
} @else {
  /* 모두 거짓일 때 구문 */
}
```

조건에 `()`는 생략이 가능하기 때문에, `()` 없이 작성하는 방법이 좀 더 편리할 수 있습니다.

```scss
$bg: true;
div {
  @if $bg {
    background: url("/images/a.jpg");
  }
}
```

SCSS:

```scss
$color: orange;
div {
  @if $color == strawberry {
    color: #FE2E2E;
  } @else if $color == orange {
    color: #FE9A2E;
  } @else if $color == banana {
    color: #FFFF00;
  } @else {
    color: #2A1B0A;
  }
}
```

Compiled to:

```css
div {
  color: #FE9A2E;
}
```

조건에는 논리 연산자 `and`, `or`, `not`을 사용할 수 있습니다.

SCSS:

```scss
@function limitSize($size) {
  @if $size >= 0 and $size <= 200px {
    @return 200px;
  } @else {
    @return 800px;
  }
}

div {
  width: limitSize(180px);
  height: limitSize(340px);
}
```

Compiled to:

```css
div {
  width: 200px;
  height: 800px;
}
```

다른 예제도 살펴봅시다!
Sass의 내장 함수 `unitless()`는 숫자에 단위가 있는지 여부를 반환합니다.

SCSS:

```scss
@mixin pCenter($w, $h, $p: absolute) {
  @if
    $p == absolute
    or $p == fixed
    // or not $p == relative
    // or not $p == static
  {
    width: if(unitless($w), #{$w}px, $w);
    height: if(unitless($h), #{$h}px, $h);
    position: $p;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
  }
}

.box1 {
  @include pCenter(10px, 20px);
}
.box2 {
  @include pCenter(50, 50, fixed);
}
.box3 {
  @include pCenter(100, 200, relative);
}
```

Compiled to:

```css
.box1 {
  width: 10px;
  height: 20px;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
}

.box2 {
  width: 50px;
  height: 50px;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
}
```

### @for

`@for`는 스타일을 반복적으로 출력합니다.
[for 문](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for)과 유사합니다.

`@for`는 `through`를 사용하는 형식과 `to`를 사용하는 형식으로 나뉩니다.
두 형식은 종료 조건이 해석되는 방식이 다릅니다.

```scss
// through
// 종료 만큼 반복
@for $변수 from 시작 through 종료 {
  // 반복 내용
}

// to
// 종료 직전까지 반복
@for $변수 from 시작 to 종료 {
  // 반복 내용
}
```

차이점을 이해하기 위해 다음 예제를 살펴봅시다.
변수는 관례상 `$i`를 사용합니다.

SCSS:

```scss
// 1부터 3번 반복
@for $i from 1 through 3 {
  .through:nth-child(#{$i}) {
    width : 20px * $i
  }
}

// 1부터 3 직전까지만 반복(2번 반복)
@for $i from 1 to 3 {
  .to:nth-child(#{$i}) {
    width : 20px * $i
  }
}
```

Compiled to:

```css
.through:nth-child(1) { width: 20px; }
.through:nth-child(2) { width: 40px; }
.through:nth-child(3) { width: 60px; }

.to:nth-child(1) { width: 20px; }
.to:nth-child(2) { width: 40px; }
```

`to`는 주어진 값 직전까지만 반복해야할 경우 유용할 수 있습니다.
그러나 `:nth-child()`에서 특히 유용하게 사용되는 `@for`는 일반적으로 `through`를 사용하길 권장합니다.

### @each

`@each`는 List와 Map 데이터를 반복할 때 사용합니다.
[for in 문](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...in)과 유사합니다.

```scss
@each $변수 in 데이터 {
  // 반복 내용
}
```

List 데이터를 반복해 보겠습니다.

SCSS:

```scss
// List Data
$fruits: (apple, orange, banana, mango);

.fruits {
  @each $fruit in $fruits {
    li.#{$fruit} {
      background: url("/images/#{$fruit}.png");
    }
  }
}
```

Compiled to:

```css
.fruits li.apple {
  background: url("/images/apple.png");
}
.fruits li.orange {
  background: url("/images/orange.png");
}
.fruits li.banana {
  background: url("/images/banana.png");
}
.fruits li.mango {
  background: url("/images/mango.png");
}
```

혹시 매번 반복마다 Index 값이 필요하다면 다음과 같이 `index()` 내장 함수를 사용할 수 있습니다.

SCSS:

```scss
$fruits: (apple, orange, banana, mango);

.fruits {
  @each $fruit in $fruits {
    $i: index($fruits, $fruit);
    li:nth-child(#{$i}) {
      left: 50px * $i;
    }
  }
}
```

Compiled to:

```css
.fruits li:nth-child(1) {
  left: 50px;
}
.fruits li:nth-child(2) {
  left: 100px;
}
.fruits li:nth-child(3) {
  left: 150px;
}
.fruits li:nth-child(4) {
  left: 200px;
}
```

동시에 여러 개의 List 데이터를 반복 처리할 수도 있습니다.
단, 각 데이터의 Length가 같아야 합니다.

SCSS:

```scss
$apple: (apple, korea);
$orange: (orange, china);
$banana: (banana, japan);

@each $fruit, $country in $apple, $orange, $banana {
  .box-#{$fruit} {
    background: url("/images/#{$country}.png");
  }
}
```

Compiled to:

```css
.box-apple {
  background: url("/images/korea.png");
}
.box-orange {
  background: url("/images/china.png");
}
.box-banana {
  background: url("/images/japan.png");
}
```

Map 데이터를 반복할 경우 하나의 데이터에 두 개의 변수가 필요합니다.

```scss
@each $key변수, $value변수 in 데이터 {
  // 반복 내용
}
```

```scss
$fruits-data: (
  apple: korea,
  orange: china,
  banana: japan
);

@each $fruit, $country in $fruits-data {
  .box-#{$fruit} {
    background: url("/images/#{$country}.png");
  }
}
```

```css
.box-apple {
  background: url("/images/korea.png");
}
.box-orange {
  background: url("/images/china.png");
}
.box-banana {
  background: url("/images/japan.png");
}
```

### @while

`@while`은 조건이 `false`로 평가될 때까지 내용을 반복합니다.
[while 문](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/while)과 유사하게 잘못된 조건으로 인해 컴파일 중 무한 루프에 빠질 수 있습니다.
사용을 권장하지 않습니다.

```scss
@while 조건 {
  // 반복 내용
}
```

```scss
$i: 6;

@while $i > 0 {
  .item-#{$i} {
    width: 2px * $i;
  }
  $i: $i - 2;
}
```

```css
.item-6 { width: 12px; }
.item-4 { width: 8px; }
.item-2 { width: 4px; }
```

## 내장 함수

Sass에서 기본적으로 제공하는 내장 함수(Built-in Functions)에는 많은 종류가 있습니다.
모두 소개하지 않고, 주관적 경험에 의거해 필요하거나 필요할 수 있는 함수만 정리했습니다.

[Sass Built-in Functions](http://sass-lang.com/documentation/Sass/Script/Functions.html)에서 모든 내장 함수를 확인할 수 있습니다.

- `[]`는 선택 가능한 인수(argument)입니다.
- [Zero-based numbering](https://en.wikipedia.org/wiki/Zero-based_numbering)을 사용하지 않습니다.

### 색상 함수

[mix($color1, $color2)](http://sass-lang.com/documentation/Sass/Script/Functions.html#mix-instance_method) : 두 개의 색을 섞습니다.

[lighten($color, $amount)](http://sass-lang.com/documentation/Sass/Script/Functions.html#lighten-instance_method) : 더 밝은색을 만듭니다.

[darken($color, $amount)](http://sass-lang.com/documentation/Sass/Script/Functions.html#darken-instance_method) : 더 어두운색을 만듭니다.

[saturate($color, $amount)](http://sass-lang.com/documentation/Sass/Script/Functions.html#saturate-instance_method) : 색상의 채도를 올립니다.

[desaturate($color, $amount)](http://sass-lang.com/documentation/Sass/Script/Functions.html#desaturate-instance_method) : 색상의 채도를 낮춥니다.

[grayscale($color)](http://sass-lang.com/documentation/Sass/Script/Functions.html#grayscale-instance_method) : 색상을 회색으로 변환합니다.

[invert($color)](http://sass-lang.com/documentation/Sass/Script/Functions.html#invert-instance_method) : 색상을 반전시킵니다.

[rgba($color, $alpha)](http://sass-lang.com/documentation/Sass/Script/Functions.html#rgba-instance_method) : 색상의 투명도를 변경합니다.

[opacify($color, $amount) / fade-in($color, $amount)](http://sass-lang.com/documentation/Sass/Script/Functions.html#opacify-instance_method) : 색상을 더 불투명하게 만듭니다.

[transparentize($color, $amount) / fade-out($color, $amount)](http://sass-lang.com/documentation/Sass/Script/Functions.html#transparentize-instance_method) : 색상을 더 투명하게 만듭니다.

### 문자 함수

[unquote($string)](http://sass-lang.com/documentation/Sass/Script/Functions.html#unquote-instance_method) : 문자에서 따옴표를 제거합니다.

[quote($string)](http://sass-lang.com/documentation/Sass/Script/Functions.html#quote-instance_method) : 문자에 따옴표를 추가합니다.

[str-insert($string, $insert, $index)](http://sass-lang.com/documentation/Sass/Script/Functions.html#str_insert-instance_method) : 문자의 index번째에 특정 문자를 삽입합니다.

[str-index($string, $substring)](http://sass-lang.com/documentation/Sass/Script/Functions.html#str_index-instance_method) : 문자에서 특정 문자의 첫 index를 반환합니다.

[str-slice($string, $start-at, [$end-at])](http://sass-lang.com/documentation/Sass/Script/Functions.html#str_slice-instance_method) : 문자에서 특정 문자(몇 번째 글자부터 몇 번째 글자까지)를 추출합니다.

[to-upper-case($string)](http://sass-lang.com/documentation/Sass/Script/Functions.html#to_upper_case-instance_method) : 문자를 대문자를 변환합니다.

[to-lower-case($string)](http://sass-lang.com/documentation/Sass/Script/Functions.html#to_lower_case-instance_method) : 문자를 소문자로 변환합니다.

### 숫자 함수

[percentage($number)](http://sass-lang.com/documentation/Sass/Script/Functions.html#percentage-instance_method) : 숫자(단위 무시)를 백분율로 변환합니다.

[round($number)](http://sass-lang.com/documentation/Sass/Script/Functions.html#round-instance_method) : 정수로 반올림합니다.

[ceil($number)](http://sass-lang.com/documentation/Sass/Script/Functions.html#ceil-instance_method) : 정수로 올림합니다.

[floor($number)](http://sass-lang.com/documentation/Sass/Script/Functions.html#floor-instance_method) : 정수로 내림(버림)합니다.

[abs($number)](http://sass-lang.com/documentation/Sass/Script/Functions.html#abs-instance_method) : 숫자의 절대 값을 반환합니다.

[min($numbers...)](http://sass-lang.com/documentation/Sass/Script/Functions.html#min-instance_method) : 숫자 중 최소 값을 찾습니다.

[max($numbers...)](http://sass-lang.com/documentation/Sass/Script/Functions.html#max-instance_method) : 숫자 중 최대 값을 찾습니다.

[random()](http://sass-lang.com/documentation/Sass/Script/Functions.html#random-instance_method) : `0` 부터 `1` 사이의 난수를 반환합니다.

### List 함수

모든 List 내장 함수는 기존 List 데이터를 갱신하지 않고 새 List 데이터를 반환합니다.
모든 List 내장 함수는 Map 데이터에서도 사용할 수 있습니다.

[length($list)](http://sass-lang.com/documentation/Sass/Script/Functions.html#length-instance_method) : List의 개수를 반환합니다.

[nth($list, $n)](http://sass-lang.com/documentation/Sass/Script/Functions.html#nth-instance_method) : List에서 n번째 값을 반환합니다.

[set-nth($list, $n, $value)](http://sass-lang.com/documentation/Sass/Script/Functions.html#set_nth-instance_method) : List에서 n번째 값을 다른 값으로 변경합니다.

[join($list1, $list2, [$separator])](http://sass-lang.com/documentation/Sass/Script/Functions.html#join-instance_method) : 두 개의 List를 하나로 결합합니다.

[zip($lists...)](http://sass-lang.com/documentation/Sass/Script/Functions.html#zip-instance_method) : 여러 List들을 하나의 다차원 List로 결합합니다.

[index($list, $value)](http://sass-lang.com/documentation/Sass/Script/Functions.html#index-instance_method) : List에서 특정 값의 index를 반환합니다.

### Map 함수

모든 Map 내장 함수는 기존 Map 데이터를 갱신하지 않고 새 Map 데이터를 반환합니다.

[map-get($map, $key)](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_get-instance_method) : Map에서 특정 key의 value를 반환합니다.

[map-merge($map1, $map2)](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_merge-instance_method) : 두 개의 Map을 병합하여 새로운 Map를 만듭니다.

[map-keys($map)](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_keys-instance_method) : Map에서 모든 key를 List로 반환합니다.

[map-values($map)](http://sass-lang.com/documentation/Sass/Script/Functions.html#map_values-instance_method) : Map에서 모든 value를 List로 반환합니다.

### 관리(Introspection) 함수

[variable-exists(name)](http://sass-lang.com/documentation/Sass/Script/Functions.html#variable_exists-instance_method) : 변수가 현재 범위에 존재하는지 여부를 반환합니다.(인수는 `$`없이 변수의 이름만 사용합니다.)

[unit($number)](http://sass-lang.com/documentation/Sass/Script/Functions.html#unit-instance_method) : 숫자의 단위를 반환합니다.

[unitless($number)](http://sass-lang.com/documentation/Sass/Script/Functions.html#unitless-instance_method) : 숫자에 단위가 있는지 여부를 반환합니다.

[comparable($number1, $number2)](http://sass-lang.com/documentation/Sass/Script/Functions.html#comparable-instance_method) : 두 개의 숫자가 연산 가능한지 여부를 반환합니다.
