---
id: 2FdUKju
filename: svelte
title: Svelte.js 완벽 가이드(Renew)
date: 2019-09-29 18:00:01
group: Svelte
tags:
  - svelte.js
  - sapper
  - routify
description:
  Svelte는 Rich Harris가 제작한 새로운 접근 방식을 가지는 프론트엔드 프레임워크입니다.
  Svelte는 자신을 '프레임워크가 없는 프레임워크' 혹은 '컴파일러'라고 소개합니다.
  이는 Virtual(가상) DOM이 없고, Runtime(런타임)에 로드할 프레임워크가 없음을 의미합니다.
---

> 이하 내용은 [Svelte@3.31.0](https://github.com/sveltejs/svelte/blob/master/CHANGELOG.md)을 기준으로 작성했습니다.

# 변경사항

## 2020년 12월

- &lt;컴포넌트 / Slot&gt; 파트를 &lt;슬롯(Slot)&gt;으로 변경하고 하위 파트를 추가했습니다.
- 다음의 파트들을 추가했습니다.
  - 키 블록
  - 슬롯 포워딩 &lt;슬롯(Slot)&gt;
  - $$slots &lt;슬롯(Slot)&gt;
- 일부 내용과 오타 등을 수정했습니다.

## 2020년 11월

- 별도 구성 없이 바로 프로젝트를 시작할 수 있는 [Snowpack 기반의 Svelte 템플릿](https://github.com/ParkYoungWoong/svelte-snowpack-template)을 추가했습니다.
- '시작하기' 파트를 '개발환경 구성'으로 수정했습니다.
- 다음의 파트들을 추가했습니다.
  - Snowpack template
  - Web Test Runner &lt;Unit Test&gt;
  
## 2020년 10월

- 문서 제목을 'SvelteJS(스벨트) - 새로운 개념의 프론트엔드 프레임워크'에서 'Svelte.js 완벽 가이드'로 변경했습니다.
- 문서 전체를 Svelte 최신 버전에 맞게 재단장했습니다.
- 다음의 대주제(파트)들을 추가했습니다.
  - Svelte 시작하기
  - Svelte Core API
  - Svelte Animation API
  - Router
  - 기능
  - Unit Test
  - Tools

<!-- toc -->

# Svelte 온라인 강의

## Svelte Core API 완벽 가이드

<strong>인프런 강의</strong> - https://www.inflearn.com/course/스벨트-완벽-가이드?inst=c1552804
<strong>유튜브 공개 목록</strong> - https://www.youtube.com/watch?v=QjaHjFlPa-g&list=PL5v0w59YqSue9aPueJ15phdPv6lcvWzVy

이 강의는,
- 21시간 분량의 강의로, 이론 및 기본 예제와 클론 프로젝트까지 한 번에 진행할 수 있어요!
- 최신 Svelte.js의 Core API를 기초부터 탄탄하게 학습해요!
- 자바스크립트 데이터의 불변성(Immutable)과 가변성(Mutable)에 대해서 이해할 수 있어요!
- 자바스크립트의 비동기에 대해서 이해하고 여러 비동기 패턴을 학습해요!
- Rollup.js의 기본 구성을 이해하고 추가 구성으로 실제 프로젝트를 만들어요!
- Snowpack의 기본 구성을 이해하고 프로젝트를 이전(Migration)하는 작업도 진행해요!
- Sortable.js를 핵심 모듈로 '트렐로(Trello) 클론 앱'을 만들고, Netlify 서비스에 가입하고 프로젝트를 지속적으로 배포(CD)할 수 있어요!

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/QjaHjFlPa-g?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

### Trello clone app

Svelte Core API 완벽 가이드에 포함된 Rollup 기반의 Trello 클론 프로젝트입니다.
프로젝트 내 각 파일에 주석으로 자세한 설명을 명시했으니, 학습에 도움이 되실 거예요!

GitHub Repo - https://github.com/HeropCode/Svelte-Trello-app
DEMO - https://boring-agnesi-165a0d.netlify.app

![Trello clone app](/images/screenshot/svelte/svelte-trello-example.gif)

## Svelte SPA 영화 검색 프로젝트

<strong>인프런 강의</strong> - https://www.inflearn.com/course/스벨트-실습-프로젝트?inst=0bd6a806
<strong>유튜브 공개 목록</strong> - https://www.youtube.com/watch?v=yMOSlm667To&list=PL5v0w59YqSueBr4Nwu2xHb_a32RRkDqH4

이 강의는,
- Svelte.js의 SPA(Single Page Application)을 구성할 수 있어요!
- SPA의 장점을 활용하고 단점을 보완할 수 있어요!
- Netlify Serverless Functions를 사용해 손쉽게 백엔드 API를 구성할 수 있어요!

GitHub Repo - https://github.com/HeropCode/Svelte-Movie-app
DEMO - https://competent-cori-258206.netlify.app

![Movie app](/images/screenshot/svelte/svelte-movie-app.gif)

## Svelte 입문 가이드(무료)

<strong>인프런 강의</strong> - https://www.inflearn.com/course/스벨트-입문-가이드?inst=e4eed96c

이 강의는,
- Svelte.js 기본 사용법에 대해서 학습해요!
- Store를 사용하는 간단한 Todo 예제를 만들어요!

# Svelte?

[Svelte(스벨트)](https://svelte.dev/)는 [Rich Harris](https://twitter.com/rich_harris)가 제작한 새로운 접근 방식을 가지는 프론트엔드 프레임워크입니다.
Svelte는 자신을 '프레임워크가 없는 프레임워크' 혹은 <strong>'컴파일러'</strong>라고 소개합니다.
이는 Virtual(가상) DOM이 없고, Runtime(런타임)에 로드할 프레임워크가 없음을 의미합니다.
기본적으로 빌드 단계에서 구성 요소를 컴파일하는 도구이므로 페이지에 단일 번들(bundle.js)을 로드하여 앱을 렌더링할 수 있습니다.

최근까지 'The magical disappearing UI framework'라는 [태그라인](https://veriide.com/info/motto-slogan-catch-phrase-tagline/)을 사용했습니다.

> 'Cybernetically enhanced web apps'라는 태그라인으로 변경되었습니다.

다른 프레임워크와 Svelte의 주요 차이점을 알아봅시다.

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/nV-cpUd5R7Y?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## 간결한 코드

Svelte는 높은 가독성을 유지하며 더 적은 코드를 작성할 수 있습니다.
다음의 Svelte 코드를 살펴보세요.

```svelte
<!-- Svelte -->

<script>
  let a = 1;
  let b = 2;
</script>

<input type="number" bind:value={a}>
<input type="number" bind:value={b}>

<p>{a} + {b} = {a + b}</p>
```

위 코드는 [React](https://ko.reactjs.org/)와 [Vue](https://kr.vuejs.org/v2/guide/index.html)에서 다음과 같이 작성할 수 있습니다.

```react
// React

import React, { useState } from 'react';

export default () => {
  const [a, setA] = useState(1);
  const [b, setB] = useState(2);

  function handleChangeA(event) {
    setA(+event.target.value);
  }

  function handleChangeB(event) {
    setB(+event.target.value);
  }

  return (
    <div>
      <input type="number" value={a} onChange={handleChangeA}/>
      <input type="number" value={b} onChange={handleChangeB}/>

      <p>{a} + {b} = {a + b}</p>
    </div>
  );
};
```

```vue
<!-- Vue -->

<template>
  <div>
    <input type="number" v-model.number="a">
    <input type="number" v-model.number="b">

    <p>{{a}} + {{b}} = {{a + b}}</p>
  </div>
</template>

<script>
  export default {
    data: function() {
      return {
        a: 1,
        b: 2
      };
    }
  };
</script>
```

## No virtual DOM

Svelte는 [Virtual(가상) DOM](https://velopert.com/3236)을 사용하지 않습니다.
Virtual DOM은 **충분히 빠르고 유용하지만** 이는 기능이 아닌 수단일 뿐이며, 이를 사용하지 않고도 유사한 프로그래밍 모델을 얻을 수 있다고 Svelte는 설명합니다.
새로운 Virtual DOM을 이전 Snapshot과 비교하거나([Diffing](https://meetup.toast.com/posts/110)), 상태 변화에 따른 새로운 가상 요소 생성 등에 많은 [오버헤드](https://ko.wikipedia.org/wiki/%EC%98%A4%EB%B2%84%ED%97%A4%EB%93%9C)가 있을 수 있으며 최종적으론 실제 DOM을 업데이트해야 하므로 그 과정을 생략하는 것이 더욱 빠를 수 있다고 합니다.

이에 대한 더 자세한 내용은 [Virtual DOM is pure overhead](https://svelte.dev/blog/virtual-dom-is-pure-overhead#Where_does_the_overhead_come_from)에서 더 자세하게 확인할 수 있습니다.

> 기존 UI 프레임워크와 달리, Svelte는 런타임에 작업을 기다리지 않고 빌드 시간에 앱에서 변경 사항이 어떻게 발생하는지 알고 있는 컴파일러입니다.

## 반응성

반응성은 변경된 값이 DOM에 자동으로 반영됨을 의미합니다.
Svelte는 별도의 Setter 없이 값의 할당(assignments)만으로 업데이트를 트리거(Trigger)할 수 있습니다.
실제로 상당히 편리합니다!

```svelte
<script>
  let count = 0;
</script>

<button on:click={() => count += 1}>
  {count}
</button>
```

컴파일 결과가 할당을 계측하고 DOM을 갱신합니다.

```js
// JS output

$$invalidate('count', count += 1);
```

이는 다음과 같이 Store 사용에도 굉장한 이점을 부여합니다.

```js
// store.js

import { writable } from 'svelte/store';

export const count = writable(0); // similar to `count = 0`
```

`count`는 `writable()`에서 반환된 쓰기용 객체 데이터이기 때문에,
`$` 접두사(`$count`)를 사용해 Store를 참조하겠다는 의미로 사용할 수 있습니다.

```svelte
<script>
  import { count } from './store.js';
</script>

<button on:click={() => $count += 1}>
  {$count}
</button>
```

![Svelte Twitter with Evan you](/images/screenshot/svelte/svelte-twitter-with-evan-you.jpg)
<div class="image-caption">Svelte2는 Vue와 상당히 비슷했었죠!</div>

## 퍼포먼스

W3C HTML5 Conf 2019에서 [변규현](https://novemberde.github.io/) 님의 Svelte와 React 퍼포먼스 비교 시연은 생각보다 놀라웠습니다.
메모리 사용량의 비교 결과를 보시면 차이가 확실히 느껴지는데, 컴파일 Output이 워낙 작기도 하고 가상 DOM Diffing이 없어서인지 훨씬 안정적으로 동작하고 있었습니다.

발표 자료는 [변규현 님의 블로그(Let's start SVELTE, goodbye React & Vue)](https://novemberde.github.io/javascript/2019/10/11/Svelte-revealjs.html)에서 확인하실 수 있습니다.

![W3C 2019 Conf Svlete](/images/screenshot/svelte/w3c-conf-svelte-session.jpg)
<div class="image-caption">W3C HTML5 Conf 2019, 변규현 님의 Svelte 세션</div>

# Svelte 시작하기

이 파트에서는 Svelte의 전반적인 내용을 비교적 가볍게 다룹니다.
Svelte의 특징에 대해서 빠르게 이해할 수 있습니다.

> 영상 다음에 첨부된 REPL은 최종 결과로, 강의 진행과는 일부 코드가 다를 수 있습니다.

## 개발환경 구성

Svelte는 런타임 프레임워크가 아니기 때문에, CDN을 제공하지 않습니다!

### Svelte REPL

[Svelte REPL(레플)](https://svelte.dev/repl/)이 준비되어 있습니다.
'+' 버튼을 눌러 파일을 추가하고 상대경로(확장자를 작성해야 합니다)로 접근할 수 있습니다.

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/qH4JwW9LIFc?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<iframe style="width: 100%; height: 600px;" src="https://svelte.dev/repl/hello-world?version=3.29.4" frameborder="0" allow="allowfullscreen"></iframe>

### Svelte/template

[Degit](https://github.com/Rich-Harris/degit)을 이용해 [Rollup.js](https://rollupjs.org/guide/en/) 기반의 새로운 프로젝트를 생성합니다.
[sveltejs/template](https://github.com/sveltejs/template)에서 템플릿 구조를 확인할 수 있습니다.

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/ugZTg1_BvBo?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div><div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/XhNpjuG4s0w?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div><div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/Kyex5XlGzYM?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

```bash
$ npx degit sveltejs/template PROJECT_NAME
$ cd PROJECT_NAME
$ npm install
$ npm run dev
```

설치 후 Svelte는 다음과 같은 구조를 가집니다.

![Svelte template directory structure](/images/screenshot/svelte/svelte-template-directory-structure.jpg)

- `/public/build`에는 Svelte가 수행한 컴파일 결과가 들어갑니다.
- `/src`는 모든 사용자 정의 Svelte 코드를 저장합니다.
- `rollup.config.js`은 [Rollup](https://github.com/rollup/rollup)이라는 [Webpack](https://webpack.js.org/)에 대응하는 자바스크립트용 모듈 번들러의 설정 파일입니다. 각 번들러의 차이점을 이해하고 싶다면 [Comparing bundlers: Webpack, Rollup & Parcel](https://medium.com/js-imaginea/comparing-bundlers-webpack-rollup-parcel-f8f5dc609cfd)를 확인해 보세요.
- [sirv-cli](https://github.com/lukeed/sirv/tree/master/packages/sirv-cli) 모듈은 `sirv public`을 이용해 [SPA](https://poiemaweb.com/js-spa) 서버를 실행합니다.

#### main.js

`main.js`는 Svelte의 시작점입니다.
기본 구성을 `App.svelte`컴포넌트에서 가져오고 다음 2개 속성을 포함하는 생성자로 `App` 인스턴스를 생성합니다.

- `target`은 `App.svelte`컴포넌트에서 생성된 HTML Output(출력)을 문서에 삽입하도록 지정합니다.

<div class="filename">src/main.js</div>

```js
import App from './App.svelte';

const app = new App({
  target: document.body
});

export default app;
```

그리고 `main.js`를 `rollup.config.js`에서 진입점(Entry point)으로 설정합니다.

<div class="filename">rollup.config.js</div>

```js
export default {
  input: 'src/main.js',
  // ...
};
```

Svelte에는 [Rollup을 위한 플러그인](https://github.com/rollup/rollup-plugin-svelte)뿐만 아니라 [Webpack을 위한 Loader](https://github.com/sveltejs/svelte-loader) 그리고 [Parcel을 위한 플러그인](https://github.com/DeMoorJasper/parcel-plugin-svelte)도 준비되어 있습니다.

### Snowpack template

[Snowpack 기반의 Svelte 템플릿](https://github.com/ParkYoungWoong/svelte-snowpack-template)을 만들었습니다.
별도의 구성 없이 바로 프로젝트를 시작할 수 있습니다.
템플릿에서 지원하는 내용은 크게 다음과 같습니다.

- Svelte
- TypeScript
- SCSS
- Autoprefixer/PostCSS
- Web test runner
- Chai
- Reset.css

다음과 같이 설치합니다.

```bash
## Install template
$ npx degit ParkYoungWoong/svelte-snowpack-template DIR_NAME
## Change directory
$ cd DIR_NAME
## Install dependencies
$ npm i
## Start dev server
$ npm run dev
```

타입스크립트를 사용하는 경우 다음과 같이 작성할 수 있습니다.

```svelte
<script lang="ts">
  let count: number = 0
</script>
```

SCSS를 사용하는 경우 다음과 같이 작성할 수 있습니다.

```svelte
<style lang="scss">
  $color--primary: royalblue;
  h1 {
    color: $color--primary;
  }
</style>
```

## 선언적 렌더링

- 보간법: 내용/속성/표현식 보간
- 반응성: 할당
- 클래스와 스타일: 클래스와 스타일 속성 바인딩
- 요소 바인딩: 입력 요소 바인딩(Properties, group) 패턴 정리
- 사용자 입력 핸들링: 인라인 이벤트 핸들러

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/3a5BHWBHFGA?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

[REPL에서 예제 보기 >](https://svelte.dev/repl/a7baafe9e79347abb4f96e185c034cc5?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let name = 'world'
  let age = 85
  function assign() {
    name = 'Heropy'
    age = 36
  }
</script>

<h1>Hello {name}!</h1>

<h2 class={age < 85 ? 'active': ''}>
  {age}
</h2>

<img 
  src="" 
  alt={name} />

<input 
  type="text" 
  bind:value={name} />

<button on:click={assign}>
  Assign
</button>

<style>
  h1 {
    color: red;
  }
  .active {
    color: blue;
  }
</style>
```

## 조건문과 반복문

- 조건과 반복: 조건 블록 패턴 정리, 반복 블록 패턴 정리

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/INI1x-mMDK0?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

[REPL에서 예제 보기 >](https://svelte.dev/repl/18a4858a86f64f779f65bb4e52a03ad4?version=3.29.4)

<div class="filename">If.svelte</div>

```svelte
<script>
  let name = 'world'
  let toggle = false
</script>

<button on:click={() => {toggle = !toggle}}>
  Toggle
</button>

{#if toggle}
  <h1>Hello {name}!</h1>
{:else}
  <div>No name!</div>
{/if}
```

<div class="filename">Each.svelte</div>

```svelte
<script>
  let name = 'Fruits'
  let fruits = ['Apple', 'Banana', 'Cherry', 'Orange', 'Mango']
  function deleteFruit() {
    fruits = fruits.slice(1)
  }
</script>

<h1>Hello {name}!</h1>
<ul>
  {#each fruits as fruit}
    <li>{fruit}</li>
  {/each}
</ul>
<button on:click={deleteFruit}>
  Eat it!
</button>
```

## 이벤트 핸들링

- 사용자 입력 핸들링: 인라인 이벤트 핸들러, 다중 이벤트 핸들러

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/7RK_Wri4qRI?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

[REPL에서 예제 보기 >](https://svelte.dev/repl/a452ad7129a640189023590680934e13?version=3.29.4)

<div class="filename">EventHandling.svelte</div>

```svelte
<script>
  let name = 'world'
  let isRed = false
  
  function enter() {
    name = 'enter'
  }
  function leave() {
    name = 'leave'
  }
</script>

<h1>Hello {name}!</h1>
<div
  class="box"
  style="background-color: {isRed ? 'red' : 'orange'};"
  on:click={() => { isRed = !isRed }}
  on:mouseenter={enter}
  on:mouseleave={leave}>
  Box!
</div>

<style>
  .box {
    width: 300px;
    height: 150px;
    background-color: orange;
  }
</style>
```

<div class="filename">BindingInput.svelte</div>

```svelte
<script>
  let text = ''
</script>

<h1>
  {text}
</h1>
<input 
  type="text" 
  value={text}
  on:input={e => {text = e.target.value}} />
<input 
  type="text"
  bind:value={text} />
<button on:click={() => {text = 'Heropy'}}>
  Click
</button>
```

## 컴포넌트

- 반응성: 데이터의 불변성과 가변성
- 컴포넌트: 컴포넌트 개요(with 컴포넌트 바인딩), 부모에서 자식으로(Props)

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/FRztfUuEvcM?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

[REPL에서 예제 보기 >](https://svelte.dev/repl/a6bd6b5f01534d478df444f80b40ceb3?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Fruits from './Fruits.svelte'
  
  let fruits = ['Apple', 'Banana', 'Cherry', 'Orange', 'Mango']
</script>

<Fruits {fruits} />
<Fruits {fruits} reverse />
<Fruits {fruits} slice="-2" />
<Fruits {fruits} slice="0, 3" />
```

<div class="filename">Fruits.svelte</div>

```svelte
<script>
  // Props
  export let fruits
  export let reverse
  export let slice
  
  let computedFruits = []
  let name = ''
  
  if (reverse) {
    computedFruits = [...fruits].reverse()
    name = 'reverse'
  } else if (slice) {
    computedFruits = fruits.slice(...slice.split(','))
    name = `slice ${slice}`
  } else {
    computedFruits = fruits  
  }
</script>

<h2>
  Fruits {name}
</h2>
<ul>
  {#each computedFruits as fruit}
    <li>{fruit}</li>
  {/each}
</ul>
```

## 스토어

- 스토어: 쓰기 가능 스토어(writable) & 수동 구독과 자동 구독

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/MIxp5RHEPSI?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

[REPL에서 예제 보기 >](https://svelte.dev/repl/61d85b0d98924e31a68e304fc17982f8?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { storeName } from './store.js'
  import Parent from './Parent.svelte'
  
  let name = 'world'
  // let $hello = '' // Error!
  $storeName = name
  // console.log(storeName) // 스토어 객체
  // console.log($storeName) // 스토어 값(데이터)
</script>

<h1>Hello {name}!</h1>
<Parent />
```

<div class="filename">Parent.svelte</div>

```svelte
<script>
  import Child from './Child.svelte'
</script>

<div>
  Parent
</div>
<Child />
```

<div class="filename">Child.svelte</div>

```svelte
<script>
  import { storeName } from './store.js'
</script>

<div>
  Child {$storeName}
</div>
```

<div class="filename">store.js</div>

```js
import { writable } from 'svelte/store'

export let storeName = writable('Heropy')
```

## Todo 예제 만들기

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/dFTu4-I0cdU?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

[REPL에서 예제 보기 >](https://svelte.dev/repl/ef3dc9c2559847c0a8575712d25accc6?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { writable } from 'svelte/store'
  import Todo from './Todo.svelte'

  let title = ''
  let todos = writable([])
  let id = 0
  
  function createTodo() {
    if (!title.trim()) {
      title = ''
      return
    }
    $todos.push({
      id,
      title
    })
    $todos = $todos
    title = ''
    id += 1
  }
</script>

<input 
  bind:value={title}
  on:keydown={(e) => {e.key === 'Enter' && createTodo()}} />
<button on:click={createTodo}>
  Create Todo
</button>

{#each $todos as todo}
  <Todo {todos} {todo} />
{/each}
```

<div class="filename">Todo.svelte</div>

```svelte
<script>
  export let todos // Store!
  export let todo
  
  let isEdit = false
  let title = ''
  
  function onEdit() {
    isEdit = true
    title = todo.title
  }
  function offEdit() {
    isEdit = false
  }
  function updateTodo() {
    todo.title = title
    $todos = $todos
    offEdit()
  }
  function deleteTodo() {
    $todos = $todos.filter(t => t.id !== todo.id)
  }
</script>

{#if isEdit}
  <div>
    <input 
       type="text" 
       bind:value={title}
       on:keydown={(e) => {e.key === 'Enter' && updateTodo()}} />  
    <button on:click={updateTodo}>OK</button>
    <button on:click={offEdit}>cancel</button>
  </div>
{:else}
  <div>
    <span>{todo.title}</span>
    <button on:click={onEdit}>Edit</button>
    <button on:click={deleteTodo}>Delete</button>
  </div>
{/if}
```

# Svelte Core API

앞선 'Svelte 시작하기' 파트를 통해 기본적인 내용을 모두 학습하시고 다음으로 넘어가시는 것을 추천합니다.

## 라이프 사이클

Svelte에서는 다음과 같은 라이프 사이클을 제공합니다. 

라이프 사이클 | 설명
--|--
onMount | 컴포넌트가 연결된 직후 콜백을 실행
onDestroy | 컴포넌트가 연결 해제되기 직전 콜백을 실행
beforeUpdate | 컴포넌트의 데이터가 업데이트되기 직전 콜백을 실행
afterUpdate | 컴포넌트의 데이터가 업데이트된 직후 콜백을 실행
tick | 변경된 데이터가 화면에 반영될 때까지 기다림

### onMount, onDestroy, beforeUpdate, afterUpdate

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/ZIdQ4lqKOp8?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/I5CZIdlmjoU?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<div style="position: relative; padding-bottom: 56.25%; height: 0; margin-bottom: 50px;">
<iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/jUiSTCPzGDU?rel=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

[REPL에서 예제 보기 >](https://svelte.dev/repl/28721203605a4ed7a398ef1955a8584d?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { beforeUpdate, afterUpdate, onMount, onDestroy } from 'svelte'
  import Something from './Something.svelte'
  
  let toggle = false
  
  beforeUpdate(() => console.log('Before update!'))
  afterUpdate(() => console.log('After update!'))
  onMount(() => console.log('Mounted!'))
  onDestroy(() => console.log('Before Destroy!'))
</script>

<button on:click={() => {toggle = !toggle}}>
  Toggle
</button>

{#if toggle}
  <Something />
{/if}
```

<div class="filename">Something.svelte</div>

```svelte
<h1>
  Something
</h1>
```

> 공개 가능한 영상은 여기까지입니다.
> 더 많은 영상은 [인프런 강의 커리큘럼](https://inf.run/6CVP)을 확인하세요.

### tick

반응성 데이터의 변경이 곧 화면의 갱신을 의미하지는 않습니다.
`tick`을 사용하면 데이터 변경 후 화면의 갱신까지 기다릴 수 있습니다.
단, 비동기로 처리해야 합니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/2a085acd47f547308fafbf463427e593?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { tick } from 'svelte'
  
  let name = 'world'
  
  async function handler() {
    name = 'Heropy'
    await tick()
    const h1 = document.querySelector('h1')
    console.log(h1.innerText) // Hello Heropy!
  }
</script>

<h1 on:click={handler}>Hello {name}!</h1>
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/acb036fc91794a15bb5cc70b4d3d1067?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { tick } from 'svelte'

  let isShow = false
  let input

  async function showInput() {
    isShow = true
    await tick() // Wait..
    input && input.focus()
  }
</script>

<button on:click={showInput}>Show input..</button>

{#if isShow}
  <input 
    bind:this={input}
    type="text" />
{/if}
```

### 라이프 사이클 모듈화

Svelte의 라이프 사이클은 컴포넌트 외부에서도 정의할 수 있기 때문에, 모듈로 만들 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/1d3a95f322544ad6a9e2214d3b08743d?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { lifecycle, delayRender } from './lifecycle.js'
  import Something from './Something.svelte'
  
  let done = delayRender()
  lifecycle()
</script>

{#if $done}
  <h1>Hello Lifecycle!</h1>
{/if}

<Something />
```

<div class="filename">Something.svelte</div>

```svelte
<script>
  import { delayRender } from './lifecycle.js'
  
  let done = delayRender(1000)
</script>

{#if $done}
  <h1>Something...</h1>
{/if}
```

<div class="filename">lifecycle.js</div>

```js
import { onMount, onDestroy, beforeUpdate, afterUpdate } from 'svelte'
import { writable } from 'svelte/store'

export function lifecycle() {
  onMount(() => {
    console.log('Mounted!')
  })
  onDestroy(() => {
    console.log('Before destroy!')
  })
  beforeUpdate(() => {
    console.log('Before update!')
  })
  afterUpdate(() => {
    console.log('After update!')
  })
}

export function delayRender(delay = 3000) { // ms
  let render = writable(false)
  onMount(() => {
    setTimeout(() => {
      // $render = true
      console.log(render) // set, update, subscribe
      render.set(true)
    }, delay)
  })
  return render
}
```

## 기본 보간

`{ }`(중괄호)를 사용해 데이터를 속성/내용 등에 보간할 수 있습니다. 

[REPL에서 예제 보기 >](https://svelte.dev/repl/9517da43874346719d77658c1d5d9f32?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let href = 'https://heropy.blog'
  let name = 'Heropy'
  let value = 'New input value!'
  let isUpperCase = false
</script>

<!-- 속성과 내용의 단방향 연결 -->
<a {href}>{name}</a>

<!-- 입력 요소 양방향 연결 -->
<input 
  {value} 
  on:input={e => value = e.target.value} />

<!-- bind 지시어로 양방향 연결 -->
<input bind:value />

<!-- 표현식 -->
<div>{isUpperCase ? 'DIV' : 'div'}</div>
```

### 원시 HTML

기본 보간법은 데이터를 HTML이 아닌 일반 텍스트로 해석합니다.
실제 HTML을 출력하려면 `{@html}`를 사용해야 합니다.
단, 이는 [XSS 취약점](https://en.wikipedia.org/wiki/Cross-site_scripting)으로 이어질 수 있기 때문에, 신뢰할 수 있는 콘텐츠에서만 사용하세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/64013cecb696408bbf3d1c3b42274d4a?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let h1 = '<h1>Hello Heropy</h1>'
  let xss = '<iframe onload="alert(123)"></iframe>'
</script>

{@html h1}
{@html xss}
```

### 디버그

데이터가 변경되면 이를 감지해 로그를 작성합니다.
개발자 도구가 열려있는 경우엔 프로세스를 일시정시합니다.
HTML 구조에서 데이터 변경 감지를 작성할 때 유용하겠지만, 
개인적으로 자주 사용하고 있진 않습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/9b819dbcaf0e4f21b48f49a0b05c939a?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let name = 'Heropy'
  let index = 0
</script>

{@debug index, name}
<h1 on:click={() => {index += 1}}>
  Hello {name}!
</h1>
```

## 반응성

### 할당

Svelte에서 반응성 갱신하려면 할당 연산자(`=`)를 사용해야 합니다!
`.push`나 `.splice` 같은 메소드 사용은 반응성을 갱신할 수 없습니다.

다음 예제에서 `user.numbers.push(3)`은 반응성이 갱신됩니다.
그러나 `assign` 함수에서 `user.name = 'Neo'`과 `user.depth.a = 'c'`를 제거하면 반응성은 갱신되지 않습니다.
이는 `user.name = 'Neo'`과 `user.depth.a = 'c'`가 동작하면서 각자 `user` 객체를 재할당하기 때문입니다.

> 주석 처리된 `$$invalidate` 함수 실행을 확인하세요!
> 실제 `$$invalidate` 함수는 컴파일 결과에서 확인할 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/a19796ee05bc43a7b2aeb284ad01e00e?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let name = 'Heropy'
  let fruits = ['Apple', 'Banana', 'Cherry']
  let user = { 
    name: 'Heropy', 
    age: 85, 
    depth: { 
      a: 'b' 
    }, 
    numbers: [1, 2] 
  }
  let numbers = user.numbers
  let hello = 'world'
  
  function assign() {
    name = 'Neo'
  
    fruits.push('Orange') // ['Apple', 'Banana', 'Cherry', 'Orange']
    fruits = fruits
  
    user.name = 'Neo' // $$invalidate(2, user.name = "Neo", user);
    user.depth.a = 'c' // $$invalidate(2, user.depth.a = "c", user);
    user.numbers.push(3)
  
    numbers = numbers
  }
</script>

<button on:click={assign}>Assign!</button>

<h1>name: {name}</h1>
<h2>fruits: {fruits}</h2>
<h2>user name: {user.name} / {user.age}</h2>
<h2>user depth: {user.depth.a}</h2>
<h2>user numbers: {user.numbers}</h2>
<h2>numbers: {numbers}</h2>
<h2>{hello}</h2>
```

### 반응성 구문

`$:`은 Label 식별자(Identifier)가 `$`인 순수한 [자바스크립트 Label 구문](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label)이며, 
Svelte는 이 구문에 <strong>특별한 의미를 부여하고 반응성을 자동으로 계측</strong>합니다.
`let` 선언을 사용하지 않는 것에 주의합시다.

데이터 변경이 아닌 반응성을 계측하는 것이기 때문에, 데이터의 변경이 즉각 반영되지 않습니다!
따라서 다음 예제와 같이 `tick` 라이프 사이클을 사용해 반응성을 기다릴 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/2218611e49744987acec52df4ef3303f?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { tick } from 'svelte'
  
  let count = 0
  $: double = count * 2
  
  async function assign() { 
    count += 1
    console.time('timer')
    await tick() // Wait for reactivity..
    console.timeEnd('timer') // 0.1~0.5ms
    console.log(double)
  }
</script>

<button on:click={assign}>Assign!</button>
<h2>{count}</h2>
<h2>{double}</h2>
```

#### 사용 패턴

다음 예제는 REPL에서 개발자 도구 콘솔을 꼭 확인해 보세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/f56ebc00bd2a49fbaae4943d036ed511?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<!-- 콘솔을 확인해 보세요! -->

<script>
  let count = 0
  
  // 선언
  $: double = count * 2
  
  // 블록
  $: {
    console.log(count)
    console.log(double)
  }
  
  // 함수 실행
  $: count, log()  
  
  // 즉시 실행 함수(IIFE)
  $: count, (() => { 
    console.log('iife: Heropy') 
  })();
  
  // 조건문(If)
  $: if (count > 0) {
    console.log('if:', double)
  }
  
  // 반복문(For)
  $: for (let i = 0; i < 3; i += 1) {
    count
    console.log('for:', i)
  }
  
  // 조건문(Switch)
  $: switch (count) {
    case 1:
      console.log('switch: 1')
      break
    default:
      console.log('switch: default')
  }
  
  // 유효범위
  $: {
    function scope1() {
      console.log('scope1')
      function scope2() {
        console.log('scope2')
        function scope3() {
          console.log('scope3', count)
        }
        scope3()
      }
      scope2()
    }
    scope1()
  }
  
  function log() {
    console.log('fn: Heropy!')
  }
  function assign() {
    count += 1
  }
</script>

<button on:click={assign}>Assign!</button>
```

## 클래스와 스타일 

### 속성 바인딩

클래스와 스타일은 모두 기본 보간을 통해 데이터를 연결할 수 있습니다.
추가로 클래스는 `class` 지시어(Directive)를 제공하는데,
이를 통해 좀 더 단순한 문법으로 작성할 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/90ae426e584a44069d9519ed7ac67ac4?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let active = false
  let color = 'tomato'
  let white = 'white'
  let letterSpacing = 'letter-spacing: 5px;'
</script>

<button on:click={() => {active = !active}}>
  Toggle!
</button>

<!-- <div class={active ? 'active' : ''}> -->
<div class:active={active}>
  Hello
</div>

<h2 style="
  background-color: {color}; 
  color: {white};
  {letterSpacing}">
  Heropy!
</h2>

<style>
  div {
    width: 120px;
    height: 200px;
    background: royalblue;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 20px;
    transition: .4s;
  }
  .active {
    width: 250px;
    background: tomato;  
  }
</style>
```

#### 사용 패턴

[REPL에서 예제 보기 >](https://svelte.dev/repl/9769c0776d6945b38eb45ac8abfb715f?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let active = true
  let valid = false
  let camelCase = true
  let color = {
    white: '#FFF',
    red: '#FF0000'
  }
  let bold = 'font-weight: bold;'
  
  function multiClass() {
    return 'active valid camel-case'
  }
</script>
 
<div class={active ? 'active' : ''}>
  3항 연산자 보간
</div>

<div class:active={active}>
  Class 지시어(Directive) 바인딩
</div>

<div class:active>
  Class 지시어 바인딩 단축 형태
</div>

<div 
  class:active
  class:valid
  class:camelCase
  class:camel-case={camelCase}>
  다중 Class 지시어 바인딩
</div>

<div class={multiClass()}>
  함수 실행
</div>

<div 
  class="style-binding"
  style="
    color: {color.white}; 
    background-color: {color.red}; 
    {bold}">
  스타일 바인딩
</div>
```

### 스타일 유효범위와 전역화 

Svelte 컴포넌트에서 작성하는 스타일을 더 쉽고 안전하게 관리할 수 있는 편리한 방법을 제공합니다.
`<style>`에 선언된 CSS는 기본적으로 해당 컴포넌트의 유효범위(Scoped)를 가집니다.
요소의 `class`속성에 Svelte-Hash가 추가됩니다.

> 입문자 시각에선 스타일 유효범위가 더 복잡한 관리 방식으로 보일 수 있지만,
> 애플리케이션 규모가 늘어나는 경우, 전역 스타일로 인해 심각하고 복잡한 스타일 충돌이 일어날 수 있습니다!

![Svelte style hash](/images/screenshot/svelte/svelte-style-class-hash-for-element.jpg)
<div class="image-caption">Class 속성에 추가된 Svelte-Hash</div>

![Svelte style hash](/images/screenshot/svelte/svelte-style-class-hash-for-style.jpg)
<div class="image-caption">Svelte-Hash가 적용된 선택자</div>

```svelte
<style>
  ul.container li.item {
    width: 100px;
  }
</style>
```

![Svelte scoped](/images/screenshot/svelte/svelte-style-scoped.jpg)
<div class="image-caption">일반 선택자 사용</div>

만약 유효범위 없이 선언하려면 `:global(선택자)` 수정자(Modifier)를 사용할 수 있습니다.

```svelte
<style>
  :global(ul.container li.item) {
    width: 100px;
  }
</style>
```

![Svelte no scoped](/images/screenshot/svelte/svelte-style-no-scoped.jpg)
<div class="image-caption">:global() 사용</div>

### @keyframes 전역화

컴포넌트에서 정의한 Keyframes 규칙 또한 Svelte-Hash가 적용됩니다.
규칙 이름 앞에 `-global-` 수식어를 작성해 Keyframes 규칙을 전역화할 수 있습니다. 

[REPL에서 예제 보기 >](https://svelte.dev/repl/88c30c43aa49483199748090dc662f31?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<div class="box"></div>

<style>
  :global(body) {
    padding: 50px;  
  }
  .box {
    width: 100px;Class & Style Binding: Pattern
    height: 100px;
    background: tomato;
    animation: zoom .4s infinite alternate;
  }
  /* -global- */
  @keyframes -global-zoom {
    0% {
      transform: scale(1);
    }
    100% {
      transform: scale(1.5);
    }
  }
</style>
```

## 요소 바인딩

### 일반 요소

DOM에서 검색하지 않아도 `bind:this`를 통해 바로 요소를 참조할 수 있습니다.

화면에 없던 요소를 데이터를 통해 출력하고 참조하기 위해, 
데이터가 변경되고 화면이 갱신될 때까지 기다리도록 `tick` 라이플 사이클을 사용할 수 있습니다. 

[REPL에서 예제 보기 >](https://svelte.dev/repl/76a65cdbd14f40a5818ab327c7b3105b?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { tick, onMount } from 'svelte'
  
  let isShow = false
  let inputEl
  
  async function toggle() {
    isShow = !isShow
    await tick()
    // const inputEl = document.querySelector('input')
    console.log(inputEl)
    inputEl && inputEl.focus()
  }
</script>

<button on:click={toggle}>Edit!</button>
{#if isShow}
  <input bind:this={inputEl} />
{/if}
```

### 입력 요소

입력 요소는 기본적으로 `value` 속성을 통해 데이터를 연결(바인딩)하며, 많은 경우 양방향 데이터 연결을 위해 `bind` 지시어를 사용합니다.(`bind:value`)
Svelte에서는 'checkbox' 타입을 위해 `bind:checked`를, 
'radio' 타입 등의 여러 입력 요소를 위해 `bind:group`을 제공합니다.
아래 예제를 통해 다양한 사용 패턴을 확인하세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/3aca814fe08e49f08a42a7db3baed19a?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let text = ''
  let number = 3
  let checked = false
  let fruits = ['Apple', 'Banana', 'Cherry']
  let selectedFruits = []
  let group = 'Banana'
  let textarea = ''
  let select = 'Banana'
  let multipleSelect = ['Banana', 'Cherry']
</script>

<!-- let text = '' -->
<section>
  <h2>Text</h2>
  <input type="text" bind:value={text} />
</section>

<!-- let number = 3 -->
<section>
  <h2>Number/Range</h2>
  <div>
    <input type="number" bind:value={number} min="0" max="10" />
  </div>
  <div>
    <input type="range" bind:value={number} min="0" max="10" />
  </div>
</section>

<!-- let checked = false -->
<section>
  <h2>Checkbox</h2>
  <input type="checkbox" bind:checked={checked} /> Agree?
  <label>
    <input type="checkbox" bind:checked={checked} /> Agree?(label wrapping)
  </label>
</section>

<!-- let fruits = ['Apple', 'Banana', 'Cherry'] -->
<!-- let selectedFruits = [] -->
<section>
  <h2>Checkbox 다중 선택</h2>
  <strong>Selected: {selectedFruits}</strong>
  {#each fruits as fruit}
    <label>
      <input type="checkbox" value={fruit} bind:group={selectedFruits} />
      {fruit}
    </label>
  {/each}
</section>

<!-- let group = 'Banana' -->
<section>
  <h2>Radio</h2>
  <!--
  <input type="radio" value="Apple" name="my radio" />
  <input type="radio" value="Banana" name="my radio" />
  <input type="radio" value="Cherry" name="my radio" />
  -->
  <strong>Selected: {group}</strong>
  <label>
    <input type="radio" value="Apple" bind:group={group} /> Apple
  </label>
  <label>
    <input type="radio" value="Banana" bind:group={group} /> Banana
  </label>
  <label>
    <input type="radio" value="Cherry" bind:group={group} /> Cherry
  </label>
</section>

<!-- let textarea = '' -->
<section>
  <h2>Textarea</h2>
  <pre>{textarea}</pre>
  <textarea bind:value={textarea} />
</section>

<!-- let select = 'Banana' -->
<section>
  <h2>Select 단일 선택</h2>
  <strong>Seleced: {select}</strong>
  <div>
    <select bind:value={select}>
      <option disabled value="">Please select one!</option>
      <option>Apple</option>
      <option>Banana</option>
      <option>Cherry</option>
    </select>
  </div>
</section>

<!-- let multipleSelect = ['Banana', 'Cherry'] -->
<section>
  <h2>Select 다중 선택(Multiple)</h2>
  <strong>Seleced: {multipleSelect}</strong>
  <div>
    <select multiple bind:value={multipleSelect}>
      <option disabled value="">Please select one!</option>
      <option>Apple</option>
      <option>Banana</option>
      <option>Cherry</option>
    </select>
  </div>
</section>
```

### 편집 가능 요소

Svelte는 [Contenteditable(내용 수정이 가능한)](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/contenteditable) 요소에 연결할 수 있는, `innerHTML`과 `textContent` 속성을 제공합니다.
Contenteditable 요소도 하나의 입력 요소이기 때문에 `bind` 지시어를 통해서 양방향으로 데이터를 연결합니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/6a5a459c443844a3a15d16b33076396b?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let innerHTML = ''
  let textContent = 'Hello world!'
</script>

<div 
  contenteditable 
  bind:innerHTML
  bind:textContent>
  Hello world!
</div>
  
<div>{innerHTML}</div>
<div>{textContent}</div>
<div>{@html innerHTML}</div>

<style>
  div {
    border: 1px solid red;
    margin-bottom: 10px;
  }
</style>
```

## 조건 블록

If 조건에 따라 블록을 렌더링합니다.
조건이 true를 반환할 때만 렌더링 됩니다.

기본 형태는 다음과 같습니다.

```svelte
<script>
  let age = 90
</script>

{#if age > 70}
  <div>The old man!</div>
{/if}
```

### 사용 패턴

시작 블록은 `#`을,
중간 블록은 `:`을,
종료 블록은 `/`를 사용합니다. 

[REPL에서 예제 보기 >](https://svelte.dev/repl/7d2cffd5f49a4b279cfe720c96f51798?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let count = 0
</script>

<button on:click={() => { count += 1}}>증가!</button>
<button on:click={() => { count -= 1}}>감소!</button>

<h2>{count}</h2>

<section>
  <h2>if</h2>
  {#if count > 3}
    <div>count &gt; 3</div>
  {/if}
</section>

<section>
  <h2>if else</h2>
  {#if count > 3} 
    <div>count &gt; 3</div>
  {:else}
    <div>count &lt;= 3</div>
  {/if}
</section>

<section>
  <h2>if else if</h2>
  {#if count > 3}
    <div>count &gt; 3</div>
  {:else if count === 3}
    <div>count === 3</div>
  {:else}
    <div>count &lt; 3</div>
  {/if}
</section>

<section>
  <h2>다중 블록</h2>
  {#if count > 3}
    {#if count === 5}
      count === 5
    {:else}
      count &gt; 3
    {/if}
  {/if}
</section>

<style>
  section {
    border: 1px solid orange;
    margin-bottom: 10px;
    padding: 10px;
  }
  h2 {
    margin: 0;
    margin-bottom: 10px;
  }
</style>
```

## 반복 블록

Each 반복 블록은 배열 데이터를 기반으로 렌더링합니다.

기본 형태는 다음과 같습니다.

```svelte
<script>
  let fruits = ['Apple', 'Banana', 'Cherry']
</script>

{#each fruits as fruit}
  <div>{fruit}</div>
{/each}
``` 

### key

Svelte는 할당을 통해 반응성을 갱신하므로 반복 데이터 자체가 갱신되면 목록 전체가 다시 렌더링 됩니다.
이떄 Svelte가 변경되지 않은 데이터의 항목을 다시 렌더링하지 않도록 식별 가능한 고유 Key를 제공하는 것이 중요합니다. 
Key는 고유해야 합니다!

> 많은 경우 반복 데이터 각 항목의 `id` 속성을 사용합니다.

사용할 데이터 구조가 Key로 사용할 고유한 값을 가지도록 설계하는 것이 좋습니다. 
다음 예제의 출력 이름에 `Apple`이 중복되고 있지만, 
`id` 속성으로 식별 가능한 고유 Key를 제공했기 때문에 문제없이 동작합니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/552c012ffff549c3ba4a136f5dcc08db?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let fruits = [
    { id: '1', name: 'Apple' },
    { id: '2', name: 'Banana' },
    { id: '3', name: 'Cherry' },
    { id: '4', name: 'Apple' }
  ]

  function deleteFirst() {
    fruits = fruits.slice(1) // ['Banana', 'Cherry', 'Orange']
  }
</script>

<button on:click={deleteFirst}>
  Delete first fruit!
</button>

<ul>
  {#each fruits as fruit (fruit.id)}
    <li>{fruit.name}</li>
  {/each}
</ul>
```

### 사용 패턴

시작 블록은 `#`을,
중간 블록은 `:`을,
종료 블록은 `/`를 사용합니다. 

[REPL에서 예제 보기 >](https://svelte.dev/repl/b1f53749f8014e9c82fb8ea7d5d26825?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let fruits = [
    { id: 1, name: 'Apple' },
    { id: 2, name: 'Banana' },
    { id: 3, name: 'Cherry' },
    { id: 4, name: 'Apple' },
    { id: 5, name: 'Orange' }
  ]
  let todos = []
  let fruits2D = [
    [1, 'Apple'], 
    [2, 'Banana'], 
    [3, 'Cherry'], 
    [4, 'Orange']
  ]
  let user = {
    name: 'Heropy',
    age: 85,
    email: 'thesecon@gmail.com'
  }
</script>

<section>
  <h2>기본</h2>
  <!-- {#each 배열 as 속성} {/each} -->
  {#each fruits as fruit}
    <div>{fruit.name}</div>
  {/each}
</section>

<section>
  <h2>순서(index)</h2>
  <!-- {#each 배열 as 속성, 순서} {/each} -->
  {#each fruits as fruit, index}
    <div>{index} / {fruit.name}</div>
  {/each}
</section>

<section>
  <h2>아이템 고유화(key)</h2>
  <!-- {#each 배열 as 속성, 순서 (키)} {/each} -->
  {#each fruits as fruit, index (fruit.id)}
    <div>{index} / {fruit.name}</div>
  {/each}
</section>

<section>
  <h2>빈 배열 처리(else)</h2>
  <!-- {#each} {:else} {/each} -->
  {#each todos as todo (todo.id)}
    <div>{todo.name}</div>
  {:else}
    <div>아이템이 없어요!</div>
  {/each}
</section>

<section>
  <h2>구조 분해(destructuring)</h2>
  <!-- {#each 배열 as {id, name}} {/each} -->
  {#each fruits as {id, name} (id)}
    <div>{name}</div>
  {/each}
</section>

<section>
  <h2>2차원 배열</h2>
  <!-- {#each 배열 as [id, name]} {/each} -->
  {#each fruits2D as [id, name] (id)}
    <div>{name}</div>
  {/each}
</section>

<section>
  <h2>나머지 연산자(rest)</h2>
  <!-- {#each 배열 as {id, ...rest}} {/each} -->
  {#each fruits as {id, ...rest} (id)}
    <div>{rest.name}</div>
  {/each}
</section>

<section>
  <h2>객체 데이터</h2>
  {#each Object.entries(user) as [key, value] (key)}
    <div>{key}: {value}</div>
  {/each}
</section>

<style>
  section {
    border: 1px solid orange;
    margin-bottom: 10px;
    padding: 10px;
  }
  h2 {
    margin: 0;
  }
</style>
```

## 키 블록

키 블록은 연결된 데이터가 변경되면 블록 안의 내용을 화면에 다시 렌더링합니다.
블록 안에서 Svelte 컴포넌트를 사용하는 경우,
컴포넌트가 다시 초기화되고 연결(Mount)됩니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/454f0523049045e39dd647bac3c5fe05?version=3.31.0)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Count from './Count.svelte'
  let reset = false
</script>

{#key reset}
  <Count />
{/key}

<button on:click={() => reset = !reset}>
  Reset!
</button>
```

<div class="filename">Count.svelte</div>

```svelte
<script>
  let count = 0
  setInterval(() => {
    count += 1
  }, 1000)
</script>

<h1>
  {count}
</h1>
```

## 비동기 블록

Await 비동기 블록은 [Promise 객체](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)를 사용해서 비동기 코드를 다음 상태로 분기할 수 있습니다.

- 대기(pending): '이행'하거나 '거부'되지 않은 초기 상태.
- 이행(fulfilled): 연산이 성공적으로 완료됨.
- 거부(rejected): 연산이 실패함.

다음의 간단한 영화 검색 예제를 테스트하기 위해 [OMDb API](http://www.omdbapi.com/)에서 API키를 무료로 발급받으세요.

[REPL에서 예제 보기 >](https://svelte.dev/repl/6f025fe7d28441c9a8267a6be38ea8f9?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>  
  // Svelte REPL에서는 npm install을 사용할 수 없어요...
  // 자바스크립트 fetch 함수를 사용해도 되지만, 사용법이 일부 다릅니다.
  // VS Code에서는 Axios 모듈을 다음과 같이 설치하세요!!
  // npm i -D axios
  // import axios from 'axios'
  import axios from 'https://unpkg.com/axios/dist/axios.min.js'

  // http://www.omdbapi.com/apikey.aspx에서 API키를 무료로 발급 받을 수 있습니다.
  // 발급 받은 API키를 입력하고 테스트해 보세요!
  // 무료 API는 하루 1000개 데이터 제한이 있어요.
  let apikey = 'ENTER_YOUR_API_KEY'
  
  let title = ''
  // let promise = new Promise(resolve => resolve([]))
  let promise = Promise.resolve([])

  function searchMovies() {
    return new Promise(async (resolve, reject) => {
      try {
        const res = await axios(`https://www.omdbapi.com/?apikey=${apikey}&s=${title}`)
        console.log(res)
        resolve(res.data.Search)
      } catch (err) {
        console.log(err)
        reject(err)
      } finally {
        console.log('Done!')
      }
    })
  }
</script>

<input bind:value={title} />
<button on:click={() => promise = searchMovies()}>검색!</button>

{#await promise}
  <!-- pending(대기) -->
  <p style="color: royalblue;">loading...</p>
{:then movies}
  <!-- fulfilled(이행) -->
  <ul>
    {#each movies as movie}
      <li>{movie.Title}</li>
    {:else}
      <li>검색된 결과가 없어요...</li>
    {/each}
  </ul>
{:catch err}
  <!-- rejected(거부) -->
  <p style="color: red;">{err.message}</p>
{/await}
```

## 사용자 입력 핸들링

`on` 지시어를 사용해 DOM 이벤트를 작성합니다.

기본 형태는 다음과 같습니다.

```svelte
<script>
  let count = 0
</script>

<button on:click={() => count += 1}>
  Click me!
</button>

<h1>{count}</h1>
```

### 다중 이벤트 핸들러

한 요소에 같은 이벤트를 여러 개 연결할 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/91a053c1a3ed4aa3ac73b0b0518bf20e?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let count = 0
  
  function increase() {
    count += 1
  }
  function current(e) {
    console.log(e.currentTarget)
  }
</script>

<button
  on:click={increase}
  on:click={current}
  on:click={() => console.log('click!')}>
  Click me!
</button>

<h1>{count}</h1>
```

### 이벤트 수식어

Svelte에서는 DOM 이벤트를 위한 여러 수식어를 제공합니다.
`|`(Vertical bar) 기호를 이용해 작성할 수 있으며, 체이닝이 가능합니다.

```svelte
<a 
  href="#" 
  on:click|preventDefault={() => console.log('link!')}>
  Internal link..
</a>

<div on:click|preventDefault|capture|self|once={() => console.log('!')}>
  Chaining..
</div>
```

다음과 같은 수식어를 사용할 수 있습니다.

수식어 | 설명
--|--
preventDefault | 기본 동작 방지
stopPropagation | 이벤트 버블링 방지
passive | 이벤트 처리를 완료하지 않고도 기본 속도로 화면을 스크롤
nonpassive | 명시적인 `passive: false`(보통 필요하지 않음)
capture | 캡쳐링에서 핸들러 실행
once | 최초 실행 후 핸들러 삭제
self | 이벤트의 `target`과 `currentTarget`이 일치하는 경우 핸들러 실행

[REPL에서 예제 보기 >](https://svelte.dev/repl/1ff9d07bc2fc45349874b1b1b2c013e4?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  function clickHandler(event) {
    // console.log(event.target)
    console.log(event.currentTarget)
  }
  function wheelHandler(event) {
    console.log(event)
  }
</script>

<section>
  <!-- 기본 동작 방지 -->
  <!-- el.addEventListener('click', e => e.preventDefault()) -->
  <h2>preventDefault</h2>
  <a 
    href="https://naver.com"
    target="_blank"
    on:click|preventDefault={clickHandler}>
    Naver
  </a>
</section>

<section>
  <!-- 최초 실행 후 핸들러 삭제 -->
  <h2>Once</h2>
  <a 
    href="https://naver.com"
    target="_blank"
    on:click|preventDefault|once={clickHandler}>
    Naver
  </a>
</section>

<section>
  <!-- 이벤트 버블링 방지 -->
  <!-- el.addEventListener('click', e => e.stopPropagation()) -->
  <h2>stopPropagation</h2>
  <div 
    class="parent"
    on:click={clickHandler}>
    <div 
      class="child"
      on:click|stopPropagation={clickHandler}></div> 
  </div>
</section>

<section>
  <!-- 캡쳐링에서 핸들러 실행 -->
  <!-- el.addEventListener('click', e => {}, true) -->
  <!-- el.addEventListener('click', e => {}, {capture: true}) -->
  <h2>capture</h2>
  <div 
    class="parent"
    on:click|capture={clickHandler}>
    <div 
      class="child" 
      on:click={clickHandler}></div> 
  </div>
</section>

<section>
  <!-- event의 target과 currentTarget이 일치하는 경우 핸들러 실행 -->
  <h2>self</h2>
  <div 
    class="parent"
    on:click|self={clickHandler}>
    <div class="child"></div> 
  </div>
</section>

<section>
  <!-- 이벤트 처리를 완료하지 않고도 기본 속도로 화면을 스크롤 -->
  <!-- el.addEventListener('wheel', e => {}, {passive: true}) -->
  <h2>passive</h2>
  <div 
    class="parent wheel"
    on:wheel|passive={wheelHandler}>
    <div class="child"></div>   
  </div>
</section>

<style>
  section {
    border: 1px solid orange;
    padding: 10px;
    margin-bottom: 10px;
  }
  h2 {
    margin: 0;
    margin-bottom: 10px;
  }
  .parent {
    width: 160px;
    height: 120px;
    background: royalblue;
    padding: 20px;
  }
  .child {
    width: 100px;
    height: 100px;
    background: tomato;
  }
  .wheel.parent {
    overflow: auto;  
  }
  .wheel .child {
    height: 1000px;
  }
</style>
```

## 컴포넌트

[REPL에서 예제 보기 >](https://svelte.dev/repl/49dba27ecdcc47e5a259b2246b939759?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { onMount } from 'svelte'
  import Heropy from './Heropy.svelte'
  
  let heropy
  
  onMount(() => {
    // Error in REPL, Try in VS Code.
    // console.log(heropy)
    // console.log(heropy.title)
  })
</script>

<Heropy />
<Heropy title="Hello Heropy" />
<Heropy 
  title="Hello Neo"
  bind:this={heropy} />
```

<div class="filename">Heropy.svelte</div>

```svelte
<script>
  export let title = 'Default value!!'
  
  let name = 'Heropy'
  let age = 85
  let email = 'thesecon@gmail.com'
</script>

<h2>{title}</h2>
<div>{name}</div>
<div>{age}</div>
<div>{email}</div>
```

### Props

컴포넌트의 Props를 사용해 부모에서 자식 컴포넌트로 데이터를 전달할 수 있습니다.
기본적으로 단반향 연결입니다.
관련한 몇 가지 사용 패턴을 살펴보세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/0fdb93c27de942f5bdb88958247ec9f0?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import User from './User.svelte'

  let users = [
    {
      name: 'Neo',
      age: 85,
      email: 'neo@abc.com'
    },
    {
      name: 'Lewis',
      age: 30,
      email: 'lewis@abc.com'
    },
    {
      name: 'Evan',
      age: 52
    }
  ]
</script>

<section>
  {#each users as user}
    <User 
      name={user.name} 
      age={user.age}
      email={user.email} />
  {/each}
</section>

<section>
  {#each users as {name, age, email}}
    <User {name} {age} {email} />
  {/each}
</section>

<section>
  {#each users as user}
    <User {...user} />
  {/each}
</section>

<style>
  section {
    border: 1px solid orange;
    margin-bottom: 10px;
    padding: 10px;
  }
</style>
```

<div class="filename">User.svelte</div>

```svelte
<script>
  export let name
  export let age
  export let email = 'None...'
</script>

<ul>
  <li>{name}</li>
  <li>{age}</li>
  <li>{email}</li>
</ul>
```

#### 양방향 바인딩

자식 컴포넌트가 부모로부터 전달받은 Props를 내부에서 수정(할당)하는 경우, 부모 컴포넌트에선 반응성을 가지지 않습니다.
만약 자식에서 수정한 Props가 부모 컴포넌트에서도 반응성을 유지하려면 `bind` 지시어를 사용해 양방향으로 연결해야 합니다.

> 편리한 방법이지만, 데이터의 유효범위 관리를 위해 이 방법을 남발하지 않는 것이 좋습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/5352578a0fc646929ca45a2f7f3365eb?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Todo from './Todo.svelte'

  let todos = [
    { id: 1, title: 'Breakfast', done: false },
    { id: 2, title: 'Lunch', done: false },
    { id: 3, title: 'Dinner', done: false }
  ]
</script>

{#each todos as todo, index (todo.id)}
  <Todo 
    bind:todos 
    {todo} 
    {index} />
{/each}
```

<div class="filename">Todo.svelte</div>

```svelte
<script>
  export let todos
  export let todo
  export let index

  function deleteTodo() {
    todos.splice(index, 1)
    todos = todos
    console.log(todos)
  }
</script>

<div>
  <input type="checkbox" bind:value={todo.done} />
  {todo.title}
  <button on:click={deleteTodo}>X</button>
</div>
```

### Event Dispatcher

Props가 부모에서 자식으로 데이터를 전달하는 방법이라면,
Event Dispatcher는 자식에서 부모로 데이터(이벤트)를 전달하는 방법입니다.

자식 컴포넌트에서 데이터를 포함하는 이벤트를 발생시키고,
부모 컴포넌트에선 그 이벤트를 수신한 핸들러에서 데이터를 꺼내는 방식입니다. 

자식 컴포넌트(`Child.svelte`)에서 사용하는 기본 구조는 다음과 같습니다.

```svelte
<script>
  import { createEventDispatcher } from 'svelte'
  const dispatch = createEventDispatcher()
  
  const 전달할_데이터 = '나는 데이터!'
  dispatch('이벤트_이름', 전달할_데이터)
</script>
```

부모 컴포넌트에서 사용하는 기본 구조는 다음과 같습니다.

```svelte
<script>
  import Child from './Child.svelte'
</script>

<Child on:이벤트_이름={event => {
  console.log(event.detail) // '나는 데이터!' 
}} />
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/43bfe9802c88462aac11b87025b9534d?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Todo from './Todo.svelte'

  let todos = [
    { id: 1, title: 'Breakfast', done: false },
    { id: 2, title: 'Lunch', done: false },
    { id: 3, title: 'Dinner', done: false }
  ]

  function deleteTodo(event) {
    // event.detail => `new CustomEvent()`를 통해 이벤트를 초기화 할 때 전달 된 모든 데이터를 반환
    const todo = event.detail.todo
    const index = todos.findIndex(t => t.id === todo.id)
    console.log(todo)
    todos.splice(index, 1)
    todos = todos
  }
</script>

{#each todos as todo (todo.id)}
  <Todo 
    {todo} 
    on:deleteMe={deleteTodo} />
{/each}
```

<div class="filename">Todo.svelte</div>

```svelte
<script>
  import { createEventDispatcher } from 'svelte'

  export let todo

  const dispatch = createEventDispatcher()

  function deleteTodo() {
    // dispatch('deleteMe', todo)
    dispatch('deleteMe', {
      todo
    })
  }
</script>

<div>
  <input 
    type="checkbox" 
    bind:value={todo.done} />
  {todo.title}
  <button on:click={deleteTodo}>X</button>
</div>
```

#### Event Forwarding

이벤트 포워딩은 자식에서 부모 컴포넌트로 이벤트를 던져 올리는 방법으로,
이벤트 핸들러를 부모 컴포넌트에서 작성할 수 있습니다.

사용법은 아주 간단합니다.
단순히 이벤트의 핸들러를 명시하지 않으면 됩니다.

```svelte
<div on:click>
  Forwarding!
</div>
```

다음은 Child 컴포넌트에서 Parent 컴포넌트를 거쳐 App 컴포넌트로 `myEvent`라는 이벤트를 전달하는 예제입니다.
Parent 컴포넌트의 `click` 이벤트도 잘 확인해 보세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/053c93e397ab4ccd8921d2beca238ffe?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Parent from './Parent.svelte'

  function handler(e) {
    console.log(e.currentTarget)
  }
  function myEventHandler(e) {
    console.log(e.detail.myName)
  }
</script>

<Parent
  on:click={handler} 
  on:myEvent={myEventHandler} />
```

<div class="filename">Parent.svelte</div>

```svelte
<script>
  import Child from './Child.svelte'
</script>

<h2>Parent!</h2>
<button on:click>
  Parent click!
</button>

<Child on:myEvent />
```

<div class="filename">Child.svelte</div>

```svelte
<script>
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()
</script>

<h2>Child!</h2>
<button on:click={() => {
  dispatch('myEvent', {
    myName: 'Heropy!!'
  })
}}>
  Child click!
</button>
```

### Context API

컴포넌트에서 `setContext`로 데이터를 지정하면,
그 컴포넌트를 포함한 모든 하위 컴포넌트에서 `getContext`로 그 정의된 데이터를 가져와 사용할 수 있습니다.

> Props와 Store의 중간 개념 정도로 이해하면 쉽습니다.

Context API는 다음과 같이 Getter와 Setter로 구성되어 있습니다. 

API | 설명
--|--
getContext | 정의된 데이터를 가져옵니다.
setContext | 자신을 포함한 하위 컴포넌트에서 사용할 데이터를 정의합니다.

다음 예제를 통해 Context API가 동작하는 범위를 이해하세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/5f9b24be6cfa4faebe3bc549d2e0a132?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { getContext } from 'svelte'
  import Heropy from './Heropy.svelte'
  import Lewis from './Lewis.svelte'
  import Evan from './Evan.svelte'

  const pocketMoney = getContext('heropy') // undefined
</script>

<h1>App({pocketMoney})</h1>
<div>
  <Heropy />
  <Lewis />
  <Evan />
</div>

<style>
  h1 {
    font-size: 50px;
  }
  div {
    padding-left: 50px;
  }
</style>
```

<div class="filename">Heropy.svelte</div>

```svelte
<script>
  import { getContext, setContext } from 'svelte'
  import Anderson from './Anderson.svelte'

  setContext('heropy', 10000)
  const pocketMoney = getContext('heropy') // 10000
</script>

<h1 style="color: red">
  Heropy({pocketMoney})
</h1>
<ul>
  <li>
    <Anderson />
  </li>
</ul>
```

<div class="filename">Lewis.svelte</div>

```svelte
<script>
  import { getContext } from 'svelte'

  const pocketMoney = getContext('heropy') // undefined
</script>

<h1>Lewis({pocketMoney})</h1>
```

<div class="filename">Evan.svelte</div>

```svelte
<script>
  import { getContext } from 'svelte'

  const pocketMoney = getContext('heropy') // undefined
</script>

<h1>Evan({pocketMoney})</h1>
```

<div class="filename">Anderson.svelte</div>

```svelte
<script>
  import { getContext } from 'svelte'
  import Neo from './Neo.svelte'
  import Emily from './Emily.svelte'

  const pocketMoney = getContext('heropy') // 10000
</script>

<h2>Anderson({pocketMoney})</h2>
<ul>
  <li>
    <Neo />
  </li>
  <li>
    <Emily />
  </li>
</ul>
```

<div class="filename">Neo.svelte</div>

```svelte
<script>
  import { getContext } from 'svelte'

  const pocketMoney = getContext('heropy') // 10000
</script>

<h3>Neo({pocketMoney})</h3>
```

<div class="filename">Emily.svelte</div>

```svelte
<script>
  import { getContext } from 'svelte'

  const pocketMoney = getContext('heropy') // 10000
</script>

<h3>Emily({pocketMoney})</h3>
```

### Module Context

다음과 같이 `context="module"` 속성/값을 가지는 SCRIPT 태그에 정의된 내용은,
컴포넌트를 사용하기 위해 **모듈로 처음 가져오는 상황에 전역으로 한 번 실행**됩니다.

이 블록 안에서 선언된 값은 해당 컴포넌트 내에서 접근 가능하지만, 
반대로 `<script context="module">`가 해당 컴포넌트의 다른 값에는 접근할 수 없습니다.

흥미로운 기능이지만 `<script context="module">` 내에서 선언된 변수는 값을 재할당해도 반응성(DOM 업데이트)이 없다는 점에 주의해야 합니다.

> 반응성이 없기 때문에 화면 갱신용이 아닌, 단순 전역 데이터처럼 사용하면 됩니다.

```svelte
<script context="module">
  let count = 0
</script>
```

컴포넌트 외부에서도 변수/함수 등을 참조할 수 있도록 `export`를 사용할 수 있습니다.

```svelte
<script context="module">
  export let count = 0
</script> 
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/c414c6308f6e4cb2a3e6aba330a51e41?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Fruit, { count } from './Fruit.svelte'

  let fruits = [
    'Apple', 
    'Banana', 
    'Cherry',
    'Mango',
    'Orange'
  ]
</script>

<button on:click={() => console.log(count)}>
  Total count log!
</button>

{#each fruits as fruit}
  <Fruit {fruit} />
{/each}
```

<div class="filename">Fruit.svelte</div>

```svelte
<script context="module">
  export let count = 0
  console.log('Module context!')
</script>

<script>
  export let fruit
  console.log('Each component init!')
</script>

<div on:click={() => {
  count += 1
  // console.log(count)
}}>
  {fruit}
</div>
```

다음은 공식 홈페이지의 예제를 이해하기 쉽도록 간소화한 예제입니다.
[Set 생성자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Set)에 대한 이해만 있으면 충분한데,
`new Set()`으로 만들어진 인스턴스는 `.add()`, `.forEach()` 같은 메소드를 사용할 수 있는 일종의 유사 배열입니다.
`.add()`는 `.push()`를 생각하면 쉽습니다.

`stopAll` 함수가 어떤 역할을 하는지 이해하는 것이 포인트입니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/316363bd1ea047639c9ffecfde84f741?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import AudioPlayer, { stopAll } from './AudioPlayer.svelte'

  let audioTracks = [
    'https://sveltejs.github.io/assets/music/strauss.mp3',
    'https://sveltejs.github.io/assets/music/holst.mp3',
    'https://sveltejs.github.io/assets/music/satie.mp3'
  ]
</script>

<button on:click={stopAll}>
  Stop all!
</button>

{#each audioTracks as src}
  <AudioPlayer {src} />
{/each}
```

<div class="filename">AudioPlayer.svelte</div>

```svelte
<script context="module">
  const players = new Set()

  export function stopAll() {
    players.forEach(p => p.pause())
  }
</script>

<script>
  import { onMount } from 'svelte'

  export let src
  
  let player

  onMount(() => {
    // Like players.push(player)
    players.add(player)
  })
</script>

<div>
  <audio
    bind:this={player}
    {src}
    controls>
    <track kind="captions" />
  </audio>
</div>
```

다음은 `<script context="module">`를 사용하는 [Sapper 동적 라우팅](https://sapper.svelte.dev/docs#Routing) 설정 코드의 예시입니다.

```svelte
<!-- src/routes/blog/[slug].svelte -->

<script context="module">
  // the (optional) preload function takes a
  // `{ path, params, query }` object and turns it into
  // the data we need to render the page
  export async function preload(page, session) {
    // the `slug` parameter is available because this file
    // is called [slug].svelte
    const { slug } = page.params;

    // `this.fetch` is a wrapper around `fetch` that allows
    // you to make credentialled requests on both
    // server and client
    const res = await this.fetch(`blog/${slug}.json`);
    const article = await res.json();

    return { article };
  }
</script>

<script>
  export let article;
</script>
```

### $$props, $$restProps

Svelte는 컴포넌트가 전달받는 모든 Props의 정보를 가진 객체(`$$props`)를 제공합니다.
따라서 전달받을 Props를 모두 명시하지 않아도 사용할 수 있는 장점이 있습니다.
혹은 명시한 Props를 제외한 나머지만 다룰 수 있는 객체(`$$restProps`)도 제공합니다.

이름 | 설명
--|--
$$props | 컴포넌트에 전달된 모든 Props 정보를 가진 객체입니다.
$$restProps | 컴포넌트에 명시된 Props를 제외한, 나머지 Props 정보를 가진 객체입니다.

다음 예제에서 TextField 컴포넌트에 명시된 Props는 `value`와 `color`입니다.

`value`와 `color`를 포함한,
컴포넌트에 연결된 `type`, `placeholder` 같은 모든 Props 정보가 들어있는 객체는 `$$props`이고,

`value`와 `color`를 제외한,
컴포넌트에 연결된 `type`, `placeholder` 같은 Props 정보만 들어있는 객체가 `$$restProps`입니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/ac157035d0374176887a9e84e09fc13d?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import TextField from './TextField.svelte'

  let id = ''
  let pw = ''

  function submit() {
    // 
  }
</script>

<TextField 
  bind:value={id}
  color="yellowgreen"
  type="email"
  placeholder="ID!"
  maxlength="10"
  required />

<TextField
  bind:value={pw}
  color="tomato"
  type="password"
  placeholder="Password!"
  required />

<button on:click={submit}>
  Submit!
</button>

<!-- <div>{id} / {pw}</div> -->
```

<div class="filename">TextField.svelte</div>

```svelte
<script>
  export let value
  export let color
</script>

<div class="my-custom-input">
  <input 
    bind:value 
    style="color: {color};"
    {...$$restProps} />
    <!-- {...$$props} /> -->
</div>

<style>
  .my-custom-input input {
    border-radius: 100px;
    padding: 10px 20px;
  }
</style>
```

## 슬롯(Slot)

슬롯(Slot)은 컴포넌트의 내용(Content)입니다.
요소(Element)의 내용(Content)과 개념이 같습니다.

```svelte
<script>
  import Hello from './Hello.svelte'
</script>

<!--요소의 내용-->
<h1>Hello world!</h1>

<!--컴포넌트의 내용-->
<Hello>Hello world!</Hello>
```

단지 컴포넌트의 내용이 어디에 삽입(출력)될 것인지만 `<slot>`로 지정하면 됩니다.
다음은 위 예제에서 사용한 Hello 컴포넌트입니다.

```svelte
<h2>
  <!--내용은 <slot>에 삽됩니다!-->
  <slot></slot>
</h2>
<p>I'm 'Hello' Component.</p>
```

### 단일 슬롯과 Fallback Content

슬롯으로 들어오는 내용이 없는 경우 기본 내용을 지정할 수 있습니다.
이를 'Fallback Content'라고 합니다.
Fallback Content는 글자(문장)만 아니라 여러 요소 및 컴포넌트를 포함할 수 있습니다.

```svelte
<slot>Fallback content, 들어오는 내용이 없으면 이 문장을 출력합니다!</slot>
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/d59c20f90ebd4985856f3fe168855674?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Btn from './Btn.svelte'
</script>

<Btn></Btn>
<Btn>Submit!</Btn>
<Btn block>Submit!</Btn>
<Btn color="royalblue">Submit!</Btn>
<Btn 
  block 
  color="red">
  Danger!
</Btn>
```

<div class="filename">Btn.svelte</div>

```svelte
<script>
  export let block
  export let color
</script>

<button 
  class:block
  style="
    background-color: {color};
    color: {color ? 'white' : '' };">
    <slot>
      Default Button!
    </slot>
</button>

<style>
  button {
    background: lightgray;
    padding: 10px 20px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: .2s;
  }
  button:hover {
    text-decoration: underline;  
  }
  button:active {
    transform: scale(1.05);
  }
  button.block {
    width: 100%;
    display: block;
  }
</style>
```

### 이름을 가지는 슬롯 

다음과 같이 내용에 슬롯 이름을 지정해 원하는 슬롯에 삽입할 수 있습니다.

```svelte
<div slot="슬롯_이름"></div>
```

슬롯에 지정된 이름으로 해당 내용이 삽입됩니다.

```svelte
<slot name="슬롯_이름"></slot>
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/b0cde9c785db4dbf8f1e00203aec94ec?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Card from './Card.svelte'
</script>

<Card>
  <div slot="age">85</div>
  <h2 slot="name">Heropy</h2>
  <div slot="email">thesecon@gmail.com</div>
</Card>

<Card>
  <span slot="email">neo@abc.com</span>
  <h3 slot="name">Neo</h3>
</Card>

<style>
  h2 {
    font-weight: 400;
  }
  h3 {
    color: red;
  }
</style>
```

<div class="filename">Card.svelte</div>

```svelte
<div class="card">
  <slot name="name"></slot>
  <slot name="age">??</slot>
  <slot name="email"></slot>
</div>

<style>
  .card {
    margin: 20px;
    padding: 12px;
    border: 1px solid gray;
    border-radius: 10px;
    box-shadow: 4px 4px 0 rgba(0,0,0,.1);
  } 
</style>
```

### 범위를 가지는 슬롯

범위를 가지는 슬롯으로 컴포넌트 내부에서 특정한 값을 꺼내서 사용할 수 있습니다.
다음과 같이 슬롯에 **속성과 값**을 포함합니다.

```svelte트
<script>
  let message = 'Hello world!'
</script>

<slot myMsg={message}></slot>
```

그리고 컴포넌트에서 `let` 지시어를 통해 그 속성을 정의하고 범위 내에서 변수(데이터)처럼 사용할 수 있습니다. 

```svelte
<script>
  import Heropy from '~/components/Heropy.svelte'
</script>

<Heropy let:myMsg>
  <h2>{myMsg}</h2>
</Heropy>
``` 

[REPL에서 예제 보기 >](https://svelte.dev/repl/9078478b56b44e25af91275a6712173d?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Wrap from './Wrap.svelte'
  
  let fruits = {
    apple: {
      value: '',
      options: {
        readonly: false,
        disabled: false,
        placeholder: 'placeholder A'
      }
    },
    banana: {
      value: 'BANANA',
      options: {
        disabled: false,
        placeholder: 'placeholder A'
      }
    }
  }
  function add(name) {
    console.log(name)
  }
  function update(name) {
    console.log(name)
  }
  function remove(name) {
    console.log(name)
  }
</script>

<Wrap 
  scopeName="apple"
  let:_name>
  <label
    class="fruits__{_name}"
    name="{_name}">
    <input
      bind:value={fruits[_name].value}
      readonly={fruits[_name].options.readonly}
      disabled={fruits[_name].options.disabled}
      placeholder={fruits[_name].options.placeholder}
      on:change={() => add(_name)} />
  </label>
</Wrap>

<Wrap 
  scopeName="banana"
  let:_name>
  <input
    bind:value={fruits[_name].value}
    disabled={fruits[_name].options.disabled}
    placeholder={fruits[_name].options.placeholder}
    on:click={() => update(_name)} />
</Wrap>

<Wrap
  scopeName="cherry"
  let:_name>
  <div
    class="hello-{_name}"
    name="{_name}"
    on:click={() => remove(_name)}>
    {_name}
  </div>
</Wrap>
```

<div class="filename">Wrap.svelte</div>

```svelte
<script>
  export let scopeName
</script>

<div>
  <slot _name={scopeName}></slot>
</div>
```

### 슬롯 포워딩

슬롯 포워딩은 부모 컴포넌트로부터 전달(Forwarding)받은 내용(Content)을 자식 컴포넌트의 내용으로 슬롯(Slot)을 이용해 전달하는 것을 의미합니다.
앞서 살펴본 단일 슬롯, 이름을 가지는 슬롯, 범위를 가지는 슬롯 모두 자식 컴포넌트로 전달할 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/df846b646a364ce689f3dabda34e54be?version=3.31.0)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Parent from './Parent.svelte'
</script>

<Parent let:scoped>
  <h2>Default slot..</h2>
  <h3 slot="named">Named slot..</h3>
  <h1 slot="scoped">Scoped slot.. {scoped}</h1>
</Parent>
```

<div class="filename">Parent.svelte</div>

```svelte
<script>
  import Child from './Child.svelte'
</script>

<Child let:scoped>
  <slot></slot>
  <slot 
    name="named" 
    slot="named"></slot>
  <slot
    name="scoped" 
    slot="scoped" 
    scoped={scoped}></slot>
</Child>
```

<div class="filename">Child.svelte</div>

```svelte
<script>
  let scoped = 'Scoped!!'
</script>

<slot 
  name="scoped" 
  scoped={scoped}></slot>
<slot name="named"></slot>
<slot></slot>
```

### $$slots

Svelte는 컴포넌트가 전달받은 내용(Content)의 정보를 가진 객체(`$$slots`)를 제공합니다.
슬롯으로 받을 내용이 존재하는지를 확인하는 데 유용합니다!

<div class="filename">App.svelte</div>

```svelte
<script>
  import UserCard from './UserCard.svelte'
</script>

<UserCard>
  <h2 slot="name">HEROPY</h2>
  <div slot="age">85</div>
  <div slot="email">thesecon@gmail.com</div>
</UserCard>

<UserCard>
  <h2 slot="name">Neo</h2>
  <div slot="email">neo@zillinks.com</div>
</UserCard>

<UserCard>
  <h2 slot="name">Evan</h2>
</UserCard>
```

<div class="filename">UserCard.svelte</div>

```svelte
<script>
  console.log($$slots)
</script>

<div class="user-card">
  <slot name="name"></slot>
  {#if $$slots.age}
    <hr />
    <slot name="age"></slot>
  {/if}
  {#if $$slots.email}
    <hr />
    <slot name="email"></slot>
  {/if}
</div>

<style>
  .user-card {
    width: 300px;
    margin: 20px 10px;
    padding: 0 10px 20px;
    border: 4px solid lightgray;
    border-radius: 10px;
    box-shadow: 8px 8px rgba(0,0,0,.03);
    position: relative;
  }
</style>
```

위 예제의 각 `UserCard.svelte` 컴포넌트에서 출력한 콘솔을 확인하면 다음과 같습니다.

![Svelte $$slots object](/images/screenshot/svelte/svelte-slots-object.jpg)

이름을 가지는 슬롯으로 받는 내용이 2개 이상이면 `default` 속성(단일 슬롯)이 자동으로 추가되는 것을 확인할 수 있는데,
이는 줄 바꿈으로 인한 공백 문자(띄어쓰기)가 내용으로 전달되면서 해석되는 것으로 확인했습니다.
따라서 다음과 같이 인라인으로 내용을 전달하면 `default` 속성(단일 슬롯)이 사라지게 됩니다.

![Svelte $$slots object](/images/2FdUKju/svelte-slots-object-inline-contents.jpg)
![Svelte $$slots object](/2FdUKju/svelte-slots-object-inline-contents-console.jpg)

## 스토어

> 'Svelte 시작하기 > 스토어' 파트를 먼저 학습하시면 좋습니다.

Svelte는 자체적으로 스토어(Store)를 지원합니다.
내장된 `svelte/store` 모듈을 사용하면 됩니다.

<div class="filename">store.js</div>

```js
import { readable, writable, derived, get } from 'svelte/store';

export const r = readable(1);
export const w = writable(7);
export const d = derived(w, $w => $w + 1);

get(r) // 1
get(w) // 7
get(d) // 8
```

`readable`, `writable`, `derived`로 정의된 스토어 객체는 기본적으로 `subscribe` 메소드를 포함하며,
`writable`로 정의된 객체는 추가로 `set`과 `update` 메소드를 사용할 수 있습니다.

![Svelte store object](/2FdUKju/svelte-store-objects.jpg)

`subscribe` 메소드를 직접 사용해서 수동 구독을 만들 수 있습니다.

```svelte
<script>
  import { w } from './store.js';

  const data = w.subscribe(d => data = d)

  console.log(data) // 7
</script>
```

Svelte 컴포넌트에서는 각 메소드를 사용할 필요 없이 `$` 접두사로 스토어를 참조할 수 있습니다.
이를 자동 구독(Auto-subscription)이라고 합니다.
자동 구독을 통해 `set`과 `update` 메소드를 대신할 수 있어 편리합니다.

> Svelte 컴포넌트에선 자동 구독(`$` 접두사) 사용을 권장합니다! 

```svelte
<script>
  import { w } from './store.js';

  console.log($w) // 7

  $w = 1;  // w.set(1)
  $w += 1;  // w.update(v => v + 1) // .update()의 콜백에서 반환하는 값이 지정됩니다. 

  console.log($w) // 2
</script>
```

Svelte 컴포넌트가 아니면(`.js`, `.ts` 파일 같은) 자동 구독을 사용할 수 없기 때문에,
`set`, `update`, `subscribe` 메소드를 직접 사용해야 합니다.

### 쓰기 가능 스토어

값을 읽거나 쓸 수 있는 스토어를 생성합니다.

```plaintext
writable(값)
writable(값, 콜백)
```

첫 번째 인수는 스토어의 값(초깃값)입니다.

두 번째 인수는 스토어 구독(자동, 수동)이 발생하면 실행될 콜백입니다.
콜백에서 반환하는 함수는 구독이 모두 취소되면(구독자가 모두 없어지면) 실행됩니다.

```js
import { writable } from 'svelte/store'

export let store = writable('값', () => {
  // 구독자가 1명 이상이 되면 실행!

  return () => {
    // 구독자가 0명이 되면 실행!
  }
})
```

#### 사용 패턴

[REPL에서 예제 보기 >](https://svelte.dev/repl/e47d56b83bea437b841a88186f8f61a5?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import WritableMethods from './WritableMethods.svelte'
  
  let toggle = true
</script>

<button on:click={() => toggle = !toggle}>
  Toggle
</button>

{#if toggle}
  <WritableMethods />
{/if}
```

<div class="filename">WritableMethods.svelte</div>

```svelte
<script>
  import { onDestroy } from 'svelte'
  import { get } from 'svelte/store'
  import { name, count } from './store.js'

  let number
  let userName

  // Store 객체
  // 사용 가능 메소드: set, update, subscribe
  console.log(name, count)
  
  // 구독하지 않고 Store 객체의 값만 얻기
  console.log(get(name), get(count))

  // count 구독자 추가!
  const unsubscribeCount = count.subscribe(c => {
    number = c
  })
  // count 구독자 추가!
  const unsubscribeCount2 = count.subscribe(() => {})
  // name 구독자 추가!
  const unsubscribeName = name.subscribe(n => {
    userName = n
  })

  function increase() {
    count.update(c => c + 1)
    try {
      unsubscribeCount() // Only once!
      unsubscribeCount2()
    } catch (e) {}
  }
  function changeName() {
    // name.update(() => 'Neo')
    name.set('Neo')
  }
  
  onDestroy(() => {
    unsubscribeCount()
    unsubscribeCount2()
    unsubscribeName()
  })
</script>

<button 
  on:click={increase}
  on:click={changeName}>
  Click me!
</button>

<h2>{number}</h2>
<h2>{userName}</h2>
```

<div class="filename">store.js</div>

```js
import { writable } from 'svelte/store'

export let name = writable('Heropy', () => {
  console.log('name 구독자가 1명 이상일 때!')
  return () => {
    console.log('name 구독자가 0명일 때...')
  }
})
export let count = writable(0, () => {
  console.log('count 구독자가 1명 이상일 때!')
  return () => {
    console.log('count 구독자가 0명일 때...')
  }
})
```

스토어 자동 구독을 통해 훨씬 간단하게 작성할 수 있습니다.

<div class="filename">WritableMethods.svelte</div>

```svelte
<script>
  import { name, count } from './store.js'
</script>

<button on:click={() => {
  $count += 1 // Increase
  $name = 'Neo' // Change name
}}>
  Click me!
</button>

<h2>{$count}</h2>
<h2>{$name}</h2>
```

### 읽기 전용 스토어

값을 읽을 수만 있는 스토어를 생성합니다.

```plaintext
readable(값)
readable(값, 콜백)
```

첫 번째 인수는 스토어의 값(초깃값)입니다.

두 번째 인수는 스토어 구독(자동, 수동)이 발생하면 실행될 콜백입니다.
콜백에서 반환하는 함수는 구독이 모두 취소되면(구독자가 모두 없어지면) 실행됩니다.
읽을 수만 있는 스토어기 때문에 초깃값을 최초 한 번 수정할 수 있도록 콜백에서 `set` 함수(매개변수)를 사용할 수 있습니다.

```js
import { readable } from 'svelte/store'

export let store = writable('값', set => {
  // 구독자가 1명 이상이 되면 실행!

  set('값')
  return () => {
    // 구독자가 0명이 되면 실행!
  }
})
```

#### 사용 패턴

[REPL에서 예제 보기 >](https://svelte.dev/repl/e4840e62287f4b44b35388276b33cea7?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Readable from './Readable.svelte'
  
  let toggle = true
</script>

<button on:click={() => toggle = !toggle}>
  Toggle
</button>

{#if toggle}
  <Readable />
{/if}
```

<div class="filename">Readable.svelte</div>

```svelte
<script>
  import { user } from './store.js'
  
  // 어떤 메소드를 가지는지 Readable 스토어 출력하기!
  console.log(user)
  console.log($user)
</script>

<button on:click={() => {$user.name = 'Neo'}}>
  Click!
</button>
<h1>{$user.name}</h1>
```

<div class="filename">store.js</div>

```js
import { readable } from 'svelte/store'

const userData = {
  name: 'Heropy',
  age: 85,
  email: 'thesecon@gmail.com',
  token: 'Ag1oy1hsdSDe'
}

export let user = readable(userData, (set) => {
  console.log('user 구독자가 1명 이상일 때!')
  delete userData.token
  set(userData)
  return () => {
    console.log('user 구독자가 0명일 때...')
  }
})
```

### 계산된 스토어

쓰기 가능(`writable`)하거나 읽기 전용(`readable`) 스토어를 통해 새롭게 계산한 값을 가지는 스토어를 생성합니다.

> 유독 사용 패턴이 많지만 앞선 '쓰기 가능', '읽기 전용' 스토어 파트를 이해했다면 특별히 어려운 건 없습니다.

첫 번째 인수는 계산에 사용할 스토어이고,
계산할 스토어가 2개 이상인 경우 첫 번째 인수를 배열로 처리해야 합니다.

두 번째 인수는 스토어 구독(자동, 수동)이 발생하면 실행될 콜백입니다.
콜백에서 반환하는 함수는 구독이 모두 취소되면(구독자가 모두 없어지면) 실행됩니다.

세 번째 인수는 계산이 완료되기 전에(비동기 요청 등) 최초 한 번 출력할 초깃값입니다.

```plaintext
derived(스토어, 콜백)
derived(스토어, 콜백, 초깃값)
derived([스토어1, 스토어2], 콜백)
derived([스토어1, 스토어2], 콜백, 초깃값)
```

콜백에서 스토어를 사용해 계산할 수 있습니다.

첫 번째 인수는 앞서 명시된 스토어의 값을 매개변수로 받습니다.
앞서 명시된 스토어가 배열로 처리되었다면, 값도 순서대로 배열로 받아야 합니다.

> 따로 기능이 있는 것은 아니고 통상적으로 매개변수 앞에 `$`를 붙여서 '스토어의 값'이라는 의미를 부여합니다.
> 컴포넌트에서 사용하는 '스토어 자동 구독(Auto-subscription)'과는 관계가 없습니다.

두 번째 인수는 `set` 매개변수입니다.
콜백에서 '계산된 값'을 반환하면 스토어(`derived`)에 반영되는데,
`set` 매겨변수가 명시되어 있으면, 반환되는 값은 '구독이 모두 취소되면 실행할 함수'가 됩니다.

> '구독이 모두 취소되면 실행할 함수'가 필요하지 않은 일반적으로는 `set` 매개변수를 명시하지 마세요.

다음 패턴에선 이해하기 쉽게 일반 함수을 사용했지만, 보통은 화살표 함수 사용을 권장합니다.

```plaintext
function ($스토어) {
  // 계산..
  return 계산된_값
}
function ([$스토어1, $스토어2]) {
  // 계산..
  return 계산된_값
}
function ($스토어, set) {
  // 계산..
  set(계산된_값)
  return 구독이_모두_취소되면_실행할_함수
}
```

#### 사용 패턴

[REPL에서 예제 보기 >](https://svelte.dev/repl/dac9457f4e2a4ad082347ccf32d860b5?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Derived from './Derived.svelte'
  
  let toggle = true
</script>

<button on:click={() => toggle = !toggle}>
  Toggle
</button>

{#if toggle}
  <Derived />
{/if}
```

<div class="filename">Derived.svelte</div>

```svelte
<script>
  import { count, double, total, initialValue } from './store.js'

  console.log(initialValue)
  console.log($count, $double)
  total.subscribe($total => {
    console.log($total)
  })
</script>

<button on:click={() => $count += 1}>
  Click!
</button>

<h1>total: {$total}</h1>
<h2>count: {$count}</h2>
<h2>double: {$double}</h2>
<h2>count+1(after 1s): {$initialValue}</h2>
```

<div class="filename">store.js</div>

```js
import { writable, derived } from 'svelte/store'

export let count = writable(1)
export let double = derived(count, $count => $count * 2)
export let total = derived(
  [count, double],
  ([$count, $double], set) => {
    console.log('total 구독자가 1명 이상일 때!')
    set($count + $double)
    return () => {
      console.log('total 구독자가 0명일 때...')
    }
  }
)
export let initialValue = derived(
  count,
  ($count, set) => {
    setTimeout(() => set($count + 1), 1000)
  }, 
  '최초 계산 중...'
)
```

### 스토어 값 얻기

구독하지 않고도 스토어의 값을 얻을 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/6e05a5d1d33642ff8ccc2d9b7af20379?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { get } from 'svelte/store'
  import { count, double, user } from './store.js'
  
  console.log(get(count))
  console.log(get(double))
  console.log(get(user))
</script>
```

<div class="filename">store.js</div>

```js
import { writable, readable, derived } from 'svelte/store'

export let count = writable(1)
export let double = derived(count, $count => $count * 2)
export let user = readable({
  name: 'Heropy',
  age: 85,
  email: 'thesecon@gmail.com'
})
```

### 커스텀 스토어

스토어 객체의 메소드(`set`, `update`, `subscribe`)가 포함된 객체를 '커스텀 스토어'라고 합니다.
다른 속성이나 메소드를 사용할 수 있는 장점이 있습니다.
스토어의 수동/자동 구독을 위해서 `subscribe` 메소드는 필수로 포함해야 합니다!

```js
import { writable } from 'svelte/store'

const store = writable(7)

export let customStore = {
  subscribe: store.subscribe,
  a: () => {},
  b: () => {},
  x: 'abc',
  y: 123
}
```

```svelte
<script>
  import { customStore } from './store.js'
  
  // Auto-subscription
  console.log($customStore) // 7
</script>
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/e2ac8a29dfdd4b7bb6cc782c8b91df1b?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { fruits } from './fruits.js'
  
  let value
</script>

<input bind:value />
<button on:click={() => fruits.setItem(value)}>
  Add fruit!  
</button>
<button on:click={() => console.log(fruits.getList())}>
  Log fruit list!
</button>

<ul>
  {#each $fruits as {id, name} (id)}
    <li>{name}</li>
  {/each}
</ul>
```

<div class="filename">fruits.js</div>

```js
import { writable, get } from 'svelte/store'

const _fruits = writable([
  { id: 1, name: 'Apple' },
  { id: 2, name: 'Banana' },
  { id: 3, name: 'Cherry' }
])

export let fruits = {
  ..._fruits,
  getList: () => get(_fruits).map(f => f.name),
  setItem: (name) => _fruits.update(f => {
    f.push({
      id: f.length + 1,
      name
    })
    console.log(f)
    return f
  })
}
```

## 액션

`use` 지시어를 사용해 연결된 요소가 생성될 때 호출할 함수를 지정할 수 있습니다. 
이 함수를 '액션(Action)'이라고 합니다.
요소를 사용하는 플러그인(모듈)을 제작할 때 유용합니다.

```plaintext
<요소 use:함수이름></요소>
<요소 use:함수이름={인수}></요소>
```

연결된 함수는 다음과 같은 구조를 가집니다.

```plaintext
function 함수이름(요소, 인수) {
  // Logic..
  return {
    update(인수) {}, // '인수'가 변경되면 실행됩니다.
    destroy() {} // '요소'가 제거되면 실행됩니다.
  }
}
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/11d88c715641499c92ec70cd4813e1c2?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let toggle = true
  let width = 200
  
  function hello(node, options = {}) {
    console.log('Init hello function!')
    const { 
      width = '100px', 
      height = '100px', 
      color = 'tomato' 
    } = options
    node.style.width = width
    node.style.height = height
    node.style.backgroundColor = color
  
    return {
      update: (opts) => {
        console.log('update!', opts)
      },
      destroy: () => {
        console.log('destroy!')
      }
    }
  }
</script>

<button on:click={() => toggle = !toggle}>
  Toggle!
</button>
<button on:click={() => width += 20}>
  Size up!
</button>

<div use:hello></div>
{#if toggle}
  <div use:hello={{
    width: `${width}px`,
    color: 'royalblue'
  }}></div>
{/if}
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/2cf17ac3b4ea47a0ade11361c242e068?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import { zoom } from './zoom.js'
</script>

<div use:zoom></div>
<div use:zoom={0.7}></div>

<style>
  div {
    width: 100px;
    height: 100px;
    background-color: tomato;
  }
</style>
```

<div class="filename">zoom.js</div>

```js
export function zoom(node, scale = 1.5) {
  node.style.transition = '1s'

  function zoomIn() {
    node.style.transform = `scale(${scale})`
  }
  function zoomOut() {
    node.style.transform = 'scale(1)'
  }
  node.addEventListener('mouseenter', zoomIn)
  node.addEventListener('mouseleave', zoomOut)

  return {
    destroy() {
      node.removeEventListener('mouseenter', zoomIn)
      node.removeEventListener('mouseleave', zoomOut)
    }
  }
}
```

## 특별한 요소

### self

컴포넌트 자신을 재귀적으로 포함합니다.
A 컴포넌트 내부에서 다시 A 컴포넌트를 사용하는 방법입니다.

```svelte
<svelte:self />
```

다음의 재귀 함수와 같은 개념입니다.
무한루프에 빠지지 않도록 재귀 호출이 멈출 수 있는 조건이 붙어야 합니다.

```js
function self() {
  self()
}
self()
```

다음 예제의 `address` 데이터를 활용할 때와 같이,
같은 컴포넌트가 반복적으로 사용될 수 있는 구조에서 유용합니다.
어떤 조건으로 재귀 호출이 멈추는지 확인해 보세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/7114e7233bfd48e0b47b88f59e0b40de?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Address from './Address.svelte'
  
  let address = {
    label: '대한민국',
    children: [
      {
        label: '경기도',
        children: [
          { label: '수원' },
          { label: '성남' }
        ]
      },
      {
        label: '강원도',
        children: [
          { label: '강릉' },
          { label: '속초' }
        ]
      }
    ]
  }
</script>

<Address {address} />
```

<div class="filename">Address.svelte</div>

```svelte
<script>
  export let address
</script>

<ul>
  <li>
    {address.label}
    {#if address.children}
      {#each address.children as address}
        <svelte:self {address} />  
      {/each}
    {/if}
  </li>
</ul>
```

### component

컴포넌트를 동적으로 렌더링할 때 사용합니다.
`this` 속성에 컴포넌트 객체를 연결해야 합니다.

```svelte
<script>
  import MyComp from './MyComp.svelte'
</script>

<svelte:component this={MyComp} />
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/08f86ae2d1c54ab2bf5f9d1818695450?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Heropy from './Heropy.svelte'
  import Neo from './Neo.svelte'
  import Anderson from './Anderson.svelte'
  
  let components = [
    { name: 'Heropy', comp: Heropy },
    { name: 'Neo', comp: Neo },
    { name: 'Anderson', comp: Anderson }
  ]
  let index = 2
  let selected = components[index - 1].comp
</script>

{#each components as {name, comp}, i (name)}
  <label>
    <input 
      type="radio" 
      value={comp} 
      bind:group={selected}
      on:change={() => index = i + 1} />
    {name}
  </label>
{/each}

<svelte:component 
  this={selected} 
  {index} />

<!-- <div>{selected}</div> -->
```

<div class="filename">Heropy.svelte</div>

```svelte
<script>
  export let index
</script>

<h2>{index}. Heropy!</h2>
```

<div class="filename">Neo.svelte</div>

```svelte
<script>
  export let index
</script>

<h2>{index}. Neo?</h2>
```

<div class="filename">Anderson.svelte</div>

```svelte
<h2>
  Anderson~
</h2>
```

### window

컴포넌트가 파괴(제거)될 때 같이 제거할 Window 이벤트를 추가하거나,
SSR에서 window 객체의 존재를 확인하지 않고도 이벤트를 추가할 때 사용합니다.
`bind` 지시어를 사용해 아래 명시된 속성들과 연결할 수 있습니다.

```svelte
<svelte:window 
  on:이벤트={핸들러}
  bind:속성={데이터} />
```

속성 | 특성 | 설명
--|--|--
innerWidth | 읽기 전용 | 뷰포트의 가로 너비
innerHeight | 읽기 전용 | 뷰포트의 가로 너비
outerWidth | 읽기 전용 | 브라우저 가로 너비
outerHeight | 읽기 전용 | 브라우저 가로 너비
online | 읽기 전용 | 네트워크 상태
scrollX | 쓰기 가능 | 스크롤 X좌표
scrollY | 쓰기 가능 | 스크롤 Y좌표

[REPL에서 예제 보기 >](https://svelte.dev/repl/aa24e0b95bad4d06a5c8d0d051b521b4?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  let key = ''
  let innerWidth
  let innerHeight
  let outerWidth
  let outerHeight
  let online
  let scrollX
  let scrollY
  // window.addEventListener('keydown', event => {
  //   key += event.key
  // })
</script>

<svelte:window 
  on:keydown={e => key = e.key}
  bind:innerWidth={innerWidth}
  bind:innerHeight
  bind:outerWidth
  bind:outerHeight
  bind:online
  bind:scrollX
  bind:scrollY />

<h1>{key}</h1>
<div>innerWidth: {innerWidth}</div>
<div>innerHeight: {innerHeight}</div>
<div>outerWidth: {outerWidth}</div>
<div>outerHeight: {outerHeight}</div>
<div>online: {online}</div>
<div class="fixed">
  <input type="number" bind:value={scrollX} />
  <input type="number" bind:value={scrollY} />  
</div>
<div class="for-scroll"></div>

<style>
  .fixed {
    position: fixed;
    top: 10px;
    right: 10px;
  }
  .for-scroll {
    width: 2000px;
    height: 2000px;
  }
</style>
```

### head, body

`document.head`를 통해 정보 요소(META, LINK..)를 삽입하거나,
`document.body`에 이벤트를 추가할 수 있습니다.
해당 컴포넌트가 파괴(제거)될 때 같이 제거됩니다.

```svelte
<svelte:head></svelte:head>
<svelte:body />
```

[REPL에서 예제 보기 >](https://svelte.dev/repl/e02ef1d7e75d4657aa2bd62f9481f775?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Heropy from './Heropy.svelte'

  let toggle = false
</script>

<button on:click={() => toggle = !toggle}>
  Toggle!
</button>

{#if toggle}
  <Heropy />
{/if}
```

<div class="filename">Heropy.svelte</div>

```svelte
<svelte:head>
  <link rel="stylesheet" href="./main.css" />
  <style>
    body {
      background-color: orange;
    }
  </style>
</svelte:head>

<svelte:body on:mousemove={e => console.log(e.clientX, e.clientY)} />
  
<h1>Heropy!</h1>
```

### options

```svelte
<svelte:options 속성={값} />
```

#### 불변성 선언(immutable)

가변성(같은 메모리 주소를 참조)을 가지는 객체 타입(object, array, function..)의 특성으로 인해,
Svelte의 할당은 불필요한 반응성(Reactive, DOM 업데이트)을 가질 수 있습니다.
컴포넌트가 전달받은 Props의 데이터 불변성(Immutable)을 선언합니다.

```svelte
<svelte:options immutable={true} />
<svelte:options immutable />
```

해당 Props의 불변성이 확인되면 Svelte는 기존 Props와 새로운 Props를 동등 연산자로 비교하고,
그 결과가 `false`가 되면 반응성을 갱신합니다.

```plaintext
기존_Props === 새로운_Props
```

Fruit 컴포넌트의 옵션을 활성화하고 테스트해보세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/6392d60f17c44329b0d8087a651e4b0b?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Fruit from './Fruit.svelte'
  
  let fruits = [
    { id: 1, name: 'Apple' },
    { id: 2, name: 'Banana' },
    { id: 3, name: 'Cherry' },
    { id: 5, name: 'Mango' },
    { id: 4, name: 'Orange' }
  ]
</script>

<button on:click={() => {
  fruits[0] = { id: 1, name: 'Apple' }
  fruits = fruits
}}>
  Update!
</button>

{#each fruits as fruit (fruit.id)}
  <Fruit {fruit} />
{/each}
```

<div class="filename">Fruit.svelte</div>

```svelte
<script>
  import { afterUpdate } from 'svelte'

  export let fruit
  // 기존 fruit === 새로운 fruit
  let updateCount = 0

  afterUpdate(() => {
    updateCount += 1
  })
</script>

<!-- <svelte:options immutable /> -->

<div>{fruit.name}({updateCount})</div>
```

#### 접근 허용(accessors)

외부에서 컴포넌트의 데이터 혹은 함수에 접근을 허용할 때 사용합니다.
단, 허용할 데이터나 함수에 `export`를 사용해야 합니다.

```svelte
<svelte:options accessors={true} />
<svelte:options accessors />
```

Heropy 컴포넌트의 옵션을 비활성화하고 테스트해보세요!

[REPL에서 예제 보기 >](https://svelte.dev/repl/811a7e65d9524b3ea20d5c5fe4d48649?version=3.29.4)

<div class="filename">App.svelte</div>

```svelte
<script>
  import Heropy from './Heropy.svelte'

  let heropy

  function handler() {
    console.log(heropy)
    console.log(heropy.name)
    console.log(heropy.getAge())
  }
</script>

<button on:click={handler}>
  Toggle!
</button>
<Heropy bind:this={heropy} />
```

<div class="filename">Heropy.svelte</div>

```svelte
<svelte:options accessors />

<script>
  let age = 85
  export let name = 'Heropy'
  export function getAge() {
    console.log(age)
  }
</script>

<h1 on:click={getAge}>{name}!</h1>
```

# Svelte Animation API

## 모션

### tweened

`tweened`는 지정된 값을 정해진 시간 동안 업데이트하는 재미있는 기능으로 스토어 객체를 반환하는 것에 주의해야 합니다.
다음과 같이 작성할 수 있습니다.

```js
import { tweened } from 'svelte/motion'

const store = tweened(1, { // 첫 번째 인수로 기본값 설정
  delay: 0, // 값을 업데이트 하기 전에 대기 시간
  duration: 400, // 값을 업데이트 하는 시간
  easing: t => t, // Same as `linear`, 타이밍 함수
  interpolate: (a, b) => t => value // 보간 함수
})
```

`tweened`가 스토어 객체를 반환하기 때문에 `number`을 업데이트하기 위해 `$`(`$number += 1`)를 사용합니다.
`number.update(n => n + 1)`과 같이 `update` 메소드를 사용할 수도 있습니다.

```svelte
<script>
  import { tweened } from 'svelte/motion'
  import { linear } from 'svelte/easing'

  const number = tweened(1, {
    duration: 1000,
    // easing: linear  // Default value!
  })

  $: fixedNumber = $number.toFixed(2)
</script>

<h1>
  {fixedNumber}
</h1>
<button on:click={() => $number += 1}>
  Increase!
</button>
```

![Svelte tweened store example](/2FdUKju/svelte-tweened-example.gif)
<div class="image-caption">Tweened Store 예제 결과</div>

# Router

## svelte-spa-router

[svelte-spa-router](https://github.com/ItalyPaleAle/svelte-spa-router)는 **SPA(Single Page Application)**을 위한 라우터 모듈입니다.
Svelte REPL에서도 사용할 수 있습니다.

[REPL에서 예제 보기 >](https://svelte.dev/repl/c35ccfc5a3914983b386929b0e3c82fd?version=3.29.4)

```bash
$ npm i -D svelte-spa-router
```

`routes.js`를 생성해 다음과 같이 Route로 정의할 컴포넌트를 연결합니다.
이 컴포넌트들은 `/routes` 디렉터리에 생성합니다.

<div class="filename">src/routes.js</div>

```js
import Home from './routes/Home.svelte'
import About from './routes/About.svelte'
import Blog from './routes/Blog.svelte'

const routes = {
  '/': Home,
  '/about': About,
  '/blog': Blog
}

export default routes
```

위 설정 파일을 `App.svelte`에서 가져와 다음과 같이 연결합니다.
각 경로로 이동할 수 있게 `Header.svelte` 컴포넌트도 같이 추가합니다.

![Svelte SPA Router default directory structure](/2FdUKju/svelte-spa-router-default-directory-structure.jpg)

<div class="filename">src/App.svelte</div>

```svelte
<script>
  import Router from 'svelte-spa-router'
  import routes from './routes'
  import Header from './components/Header.svelte'
</script>

<Header />
<Router {routes} />
```

<div class="filename">src/components/Header.svelte</div>

```svelte
<script>
  import { link } from 'svelte-spa-router'
  import active from 'svelte-spa-router/active'
</script>

<header>
  <a 
    href="/"
    use:link
    use:active>
    Home
  </a>
  <a 
    href="/about"
    use:link
    use:active>
    About
  </a>
  <a 
    href="/blog"
    use:link
    use:active>
    Blog
  </a>
</header>

<style>
  :global(header a.active) {
    font-weight: bold;
    text-decoration: underline;
  }
</style>
```

![Svelte SPA Router Example](/2FdUKju/svelte-spa-router-default-example.gif)

# 기능

## 전/후 처리기(svelte-preprocess)

[svelte-preprocess](https://github.com/kaisermann/svelte-preprocess)는 다음과 같은 전/후 처리기들을 지원합니다.
[Svelte Preprocess Documentation](https://github.com/sveltejs/svelte-preprocess/tree/master/docs)

- Babel
- TypeScript
- CoffeeScript
- Pug
- PostCSS / SugarSS
- Sass(SCSS)
- Less
- Stylus
- globalStyle
- replace

### 자동 전처리 모드(Auto Preprocessing mode)

svelte-preprocess는 요소의 `src`, `lang`, `type` 속성을 기반으로 각각의 전처리기를 자동으로 사용합니다.

```svelte
<template lang="pug"></template>

<script lang="ts"></script>
<script lang="coffee"></script>
  
<style type="text/less"></style>
<style lang="scss"></style>
<style src="./my-style.styl"></style>
```

### 구성

#### Rollup

```bash
$ npm i -D rollup-plugin-svelte svelte-preprocess
```

<div class="filename">rollup.config.js</div>

```js
import svelte from 'rollup-plugin-svelte';
import sveltePreprocess from 'svelte-preprocess';

export default {
  plugins: [
    svelte({
      preprocess: sveltePreprocess({
        // 옵션..
      })
    })
  ]
};
```

#### Snowpack

**@snowpack/plugin-svelte**를 설치하면 **svelte-preprocess**이 같이 설치됩니다.

```bash
$ npm i -D @snowpack/plugin-svelte
```

<div class="filename">snowpack.config.js</div>

```js
import sveltePreprocess from 'svelte-preprocess';

module.exports = {
  plugins: [
    ['@snowpack/plugin-svelte', {
      preprocess: sveltePreprocess({
        // 옵션..
      })
    }]
  ]
};
```

## 경로 별칭

```svelte
<script>
  // 상대 경로인 경우..
  import MyComponent from '../../../components/MyComponent'
</script>
```

이하 각 빌드 구성을 마치면,
경로에서 다음과 같이 `~` 혹은 `@`를 별칭으로 사용할 수 있습니다.

```svelte
<script>
  import MyComponent from '~/components/MyComponent';
</script>
```

### Rollup

다음과 같이 [@rollup/plugin-alias](https://github.com/rollup/plugins/tree/master/packages/alias)를 설치하고 `rollup.config.js`를 설정합니다.

```bash
$ npm i -D @rollup/plugin-alias
```

<div class="filename">rollup.config.js</div>

```js
import path from 'path';
import alias from '@rollup/plugin-alias';

export default {
  plugins: [
    alias({
      entries: [
        { find: '~', replacement: path.resolve(__dirname, 'src/') },
        { find: '@', replacement: path.resolve(__dirname, 'src/') }
      ]
    })
  ]
};
```

### Snowpack

Snowpack에는 경로 별칭 기능이 내장되어 있습니다.
다음과 같이 구성합니다.

<div class="filename">snowpack.config.js</div>

```js
module.exports = {
  alias: {
    '~': './src',
    '@': './src'
  }
};
```

# Unit Test

## Jest 

[Jest](https://jestjs.io/docs/en/getting-started)를 사용해 Test 환경을 구성합니다.

> Jest 24버전부터 Babel 6버전의 지원이 중단되었습니다. Jest 23버전의 설치와는 방법이 조금 다릅니다.

```bash
$ npm i -D jest @babel/core @babel/preset-env babel-core@7.0.0-bridge.0 babel-jest @testing-library/svelte jest-transform-svelte
```

- `babel-jest`: Jest를 위한 Babel을 구성.
- `babel-core@7.0.0-bridge.0`: `babel-jest`를 `@babel/*`패키지에서 정상적으로 동작시키기 위해 사용.
- `jest-transform-svelte`: Jest를 사용해 Svelte 컴포넌트를 정상적으로 동작시키기 위해 사용.

Jest의 설정을 위해 `jest.config.js`을 생성합니다.
혹은 `package.json`에 `"jest"`블록을 선언할 수도 있습니다.

<div class="filename">jest.config.js</div>

```js
const sveltePreprocess = require('svelte-preprocess'); // If you use Svelte preprocess like SCSS or Autoprefixer

module.exports = {
  transform: {
    '^.+\\.js$': 'babel-jest',
    '^.+\\.svelte$': [
      'jest-transform-svelte',
      {
        preprocess: sveltePreprocess(),
        debug: false,
        noStyles: true,
        compilerOptions: {}
      }
    ]
  },
  moduleFileExtensions: ['js', 'svelte'],
  moduleNameMapper: {
    '~(.*)$': '<rootDir>/src/$1', // If you use Import path alias `~`
  },
  coverageReporters: ['html'],
  bail: false,
  verbose: false
};
```

> 우리는 Babel 7버전을 설치했습니다.

<div class="filename">babel.config.js</div>

```js
module.exports = {
  'env': {
    'test': {
      'presets': [['@babel/preset-env', { 'targets': { 'node': 'current' } }]]
    }
  }
};
```

간단한 설정이 끝났습니다.
빠른 테스트 실행을 위해 Watch 모드로 스크립트를 등록합니다.

<div class="filename">package.json</div>

```json
{
  "_comment": "package.json",
  "scripts": {
    "test": "jest --watchAll"
  }
}
```

이제 다음과 같이 실행할 수 있습니다.

```bash
$ npm test
$ npm t # Alias
```

정상적으로 동작하는지 테스트하기 위해,
`__tests__` 디텍터리를 생성하고 테스트를 진행할 파일과 동일한 이름으로 `App.test.js`을 생성합니다.

```bash
├─ /src
│   ├─ /__tests__
│   │   └─ App.test.js
│   └─ App.svelte
```

설정한 테스트 환경이 정상적으로 동작하는지 확인하기 위해 최소한의 코드만 작성합니다.

<div class="filename">&lowbar;&lowbar;tests&lowbar;&lowbar;/App.test.js</div>

```js
import App from '../App.svelte'
import { render, cleanup } from '@testing-library/svelte'

beforeEach(cleanup) // Required!

describe('App', () => {
  test('정상적으로 동작해야 합니다', () => {
    const { container } = render(App)

    expect(container.nodeName).toBe('BODY')
  })
})
```

![Svelte test with Jest](/2FdUKju/svelte-with-jest-success.jpg)

다음은 [svelte-testing-library](https://github.com/testing-library/svelte-testing-library/blob/master/src/index.js)의 일부분으로 `render`의 반환 값을 확인할 수 있습니다.
`getQueriesForElement`는 [DOM Testing library Queries](https://testing-library.com/docs/dom-testing-library/api-queries)에서 확인할 수 있습니다.

<script src="https://gist.github.com/ParkYoungWoong/c6d1a152faa665df824f20ef0b5d23ca.js"></script>

## Web Test Runner

[@web/test-runner](https://modern-web.dev/docs/test-runner/overview/)는 __Snowpack 프로젝트에 권장되는 테스트 러너__ 입니다.
Jest보다 더 빠르고 실제 브라우저와 더 근접하게 일치하는 테스트 환경을 제공합니다.

[Svelte & Snowpack 템플릿](https://github.com/ParkYoungWoong/svelte-snowpack-template)로 쉽게 시작하고 테스트하세요!

<div class="filename">web-test-runner.config.js</div>

```js
// NODE_ENV=test - Needed by "@snowpack/web-test-runner-plugin"
process.env.NODE_ENV = 'test';

module.exports = {
  plugins: [require('@snowpack/web-test-runner-plugin')()],
};
```

# Tools

## WebStorm plugin

https://plugins.jetbrains.com/plugin/12375-svelte/

WebStorm을 위한 Svelte 플러그인이 있네요.
WebStorm 버전에 따라 플러그인 버전도 차이가 있을 수 있습니다.

![Svelte for Webstorm](/2FdUKju/svelte-plugin-for-webstorm.jpg)

## VS Code plugin

https://marketplace.visualstudio.com/items?itemName=JamesBirtles.svelte-vscode

VS Code를 위한 플러그인도 있으니 확인해 보세요.

> 'Svelte for VS Code' 확장 프로그램은, 기존 'Svelte' 확장 프로그램(by James Birtles)과 통합된 버전입니다.

![Svelte for VS Code](/2FdUKju/svelte-plugin-for-vscode.jpg)

### Sass(SCSS) 에러 해결

Svelte `<style>`에서 SCSS를 사용할 때,<br />
`node-sass`를 설치해도 VS Code에서 다음과 같은 에러가 발생할 수 있습니다.

```error
Cannot find any of modules: sass,node-sass ...
```

![Cannot find node-sass module](/2FdUKju/issue1-cannot-find-module-node-sass.jpg)

확장 프로그램 **Svelte for VS Code**의 환경설정에서,<br />
`Svelte > Language-server: Runtime` 옵션에 NodeJS 설치 경로를 입력하세요.<br />
NodeJS 설치 경로는 터미널에서 다음과 같이 입력해 확인할 수 있습니다.

```bash
# for Mac
$ which node

# for Windows
$ where node
``` 

![Svelte for VS Code extension settings](/2FdUKju/issue1-svelte-for-vs-code-extension-settings.jpg)

![Svelte language server: runtime](/2FdUKju/issue1-language-server-runtime.jpg)

설정 완료 후 VS Code를 재부팅하세요!

## Svelte Devtools

For Chrome
https://chrome.google.com/webstore/detail/svelte-devtools/ckolcbmkjpjmangdbmnkpjigpkddpogn

For FireFox
https://addons.mozilla.org/en-US/firefox/addon/svelte-devtools/

Svelte 애플리케이션 디버깅을 위한 브라우저용 확장 프로그램입니다.
크롬과 파이어폭스 브라우저를 지원합니다.

![Svelte Devtools](/2FdUKju/svelte-dev-tool.jpg)
<div class="image-caption">구성이 단순하네요</div>

# 참고 자료(References)

https://svelte.dev
