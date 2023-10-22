---
id: Na8BvZi
filename: js-resize-observer
title: Resize Observer - 요소의 크기 변화 관찰
date: 2019-11-30 00:00:00
group: JavaScript
tags:
  - javascript
description:
  Resize Observer는 요소(Element)의 크기를 관찰하며, 요소의 크기가 변화할 때 실행할 최적화 콜백(callback)을 제공할 수 있습니다. 활용도를 높이기 위한 폴리필(polyfill) 사용법도 같이 알아봅니다.
---

<!-- toc -->

[Resize Observer](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver)는 설정한 요소의 크기 변화를 관찰하며,
크기 변화를 제어할 경우 발생할 수 있는 무한 콜백 루프나 [순환 종속성(Circular dependency)](https://en.wikipedia.org/wiki/Circular_dependency) 등의 다양한 문제 없이 사용할 수 있습니다.

<iframe height="488" style="width: 100%;" scrolling="no" title="ResizeObserver example(textarea)" src="https://codepen.io/heropark/embed/ExaYWBa?height=488&theme-id=default&default-tab=js,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/heropark/pen/ExaYWBa'>ResizeObserver example(textarea)</a> by park young woong
  (<a href='https://codepen.io/heropark'>@heropark</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

# Polyfill

ResizeObserver는 [표준화 초안 단계(ED, Editor's Draft)](https://drafts.csswg.org/resize-observer-1/)이므로 브라우저 버전에 따라 네이티브 ResizeObserver의 사용법이 다를 수 있으니 폴리필(Polyfill) 사용을 <strong>적극 추천</strong>합니다.

이 포스트에서는 [@juggle/resize-observer](https://github.com/juggle/resize-observer)를 사용합니다.

> ResizeObserver의 사양은 권고 단계(REC)가 아니기 때문에 변경될 수 있습니다.<br>표준 사양이 크게 변경되면 이 라이브러리(@juggle/resize-observer)에 변경 사항이 있을 수 있음으로 주 버전(Major) 충돌에 주의합시다.

## Installation and Basic usage

```bash
$ npm i @juggle/resize-observer
```

```js
import ResizeObserver from '@juggle/resize-observer'

const ro = new ResizeObserver(callback)
ro.observe(element)
```

## Tested Browsers

[chrome]: https://github.com/alrra/browser-logos/raw/master/src/chrome/chrome_64x64.png
[safari]: https://github.com/alrra/browser-logos/raw/master/src/safari/safari_64x64.png
[safari-ios]: https://github.com/alrra/browser-logos/raw/master/src/safari-ios/safari-ios_64x64.png
[ff]: https://github.com/alrra/browser-logos/raw/master/src/firefox/firefox_64x64.png
[opera]: https://github.com/alrra/browser-logos/raw/master/src/opera/opera_64x64.png
[opera-mini]: https://github.com/alrra/browser-logos/raw/master/src/opera-mini/opera-mini_64x64.png
[edge_12-18]: https://github.com/alrra/browser-logos/raw/master/src/archive/edge_12-18/edge_12-18_64x64.png
[edge]: https://github.com/alrra/browser-logos/raw/master/src/edge/edge_64x64.png
[samsung]: https://github.com/alrra/browser-logos/raw/master/src/samsung-internet/samsung-internet_64x64.png
[ie]: https://github.com/alrra/browser-logos/raw/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_64x64.png

### Desktop
| ![chrome][chrome] | ![safari][safari] | ![ff][ff] | ![opera][opera] | ![edge][edge] | ![edge][edge_12-18] | ![IE][ie] |
|--------|--------|---------|-------|------|------------|---------------------------------------|
| Chrome | Safari | Firefox | Opera | Edge | Edge 12-18 | IE11<br/>IE 9-10 (with polyfills)\*\* |

### Mobile
| ![chrome][chrome] | ![safari][safari] | ![ff][ff] | ![opera][opera] | ![opera mini][opera-mini] | ![edge][edge_12-18] | ![samsung internet][samsung] |
|--------|--------|---------|-------|------------|------|------------------|
| Chrome | Safari | Firefox | Opera | Opera Mini | Edge | Samsung Internet |

# ResizeObserver

`new ResizeObserver`를 통해 생성한 인스턴스(`ro`)로 관찰자(Observer)를 초기화하고 관찰할 대상([Element](https://developer.mozilla.org/ko/docs/Web/API/Element))을 지정합니다.
생성자는 1개의 인수(`callback`)를 가집니다.

```js
// 관찰자 초기화
const ro = new ResizeObserver(callback)

// 관찰할 대상(요소) 등록
ro.observe(element)
```

## callback

관찰할 대상이 등록되거나 크기에 변화가 생기면 관찰자는 콜백을 실행합니다.
콜백은 2개의 인수(`entries`, `observer`)를 가집니다.

```js
const ro = new ResizeObserver((entries, observer) => {})

ro.observe(element)
```

### entries

`entries`는 ResizeObserverEntry 인스턴스의 <strong>배열</strong>입니다.
ResizeObserverEntry는 다음 속성들을 포함합니다.

- `contentRect`(legacy): 관찰 대상의 사각형 정보([DOMRectReadOnly](https://developer.mozilla.org/en-US/docs/Web/API/DOMRectReadOnly))
- `target`(legacy): 관찰 대상 요소([Element](https://developer.mozilla.org/en-US/docs/Web/API/Element))
- `contentBoxSize`: 관찰 대상의 `content-box`(content) 크기
- `borderBoxSize`: 관찰 대상의 `border-box`(content + padding + border) 크기

```js
const ro = new ResizeObserver((entries, observer) => {
  entries.forEach(entry => {
    console.log(entry)
  })
})

ro.observe(element)
```

![resize observer entry object](/Na8BvZi/resize-observer-entry-object.jpg)
<div class="image-caption">ResizeObserverEntry 구조(after polyfill)</div>

### observer

콜백이 실행되는 해당 인스턴스를 참조합니다.

![resize observer entry object](/Na8BvZi/resize-observer-object.jpg)
<div class="image-caption">ResizeObserver 구조</div>

## Methods

### observe()

대상 요소의 관찰을 시작합니다.

```js
const ro1 = new ResizeObserver(callback1)
const ro2 = new ResizeObserver(callback2)

const div = document.querySelector('div')
const button = document.querySelector('button')
const textarea = document.querySelector('textarea')

ro1.observe(div) // DIV 요소 관찰
ro2.observe(button) // BUTTON 요소 관찰
ro2.observe(textarea) // TEXTAREA 요소 관찰
```

### unobserve()

대상 요소의 관찰을 중지합니다.

```js
const ro1 = new ResizeObserver(callback1)
const ro2 = new ResizeObserver(callback2)

// ...

ro1.observe(div)
ro2.observe(button)
ro2.observe(textarea)

ro1.unobserve(button) // Nothing..
ro2.unobserve(button) // BUTTON 요소 관찰 중지
```

### disconnect()

ResizeObserver 인스턴스가 관찰하는 모든 요소의 관찰을 중지합니다.

```js
const ro1 = new ResizeObserver(callback1)
const ro2 = new ResizeObserver(callback2)

// ...

ro1.observe(div)
ro2.observe(button)
ro2.observe(textarea)

ro2.disconnect() // `ro2`가 관찰하는 모든 요소(BUTTON, TEXTAREA) 관찰 중지
```

# 예제

<iframe height="516" style="width: 100%;" scrolling="no" title="Resize Observer example - Text overflow" src="https://codepen.io/heropark/embed/MWYgoVv?height=516&theme-id=default&default-tab=result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/heropark/pen/MWYgoVv'>Resize Observer example - Text overflow</a> by park young woong
  (<a href='https://codepen.io/heropark'>@heropark</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

# 참고 자료(References)

https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver
https://github.com/juggle/resize-observer
