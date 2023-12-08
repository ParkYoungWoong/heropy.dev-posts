---
id: zDWwNL
filename: vue3-core-patterns-with-ts
image: https://picsum.photos/id/497/1200/800
title: Vue 핵심 패턴 (Composition API)
createdAt: 2023-11-29
group: Vue
author:
  - ParkYoungWoong
tags:
  - Vue
  - Composition API
  - TypeScript
description: 
  Vue 3버전의 기초 문법 학습이 끝났다면, Composition API와 타입스크립트를 사용한 핵심 패턴을 빠르게 탐색해 보세요!
---

# Vue 핵심 패턴 (Composition API)

이 글은 Vue 3버전의 기초 문법 학습을 전제하여, 핵심 패턴을 빠르게 탐색할 수 있도록 구성했습니다.
파편화된 핵심 정보를 모으고 [공식 문서](https://vuejs.org/guide/introduction.html)와 다른 새로운 예제를 제공하지만, 설명은 함축적입니다.
또한 이 글은 [Vite.js](https://vitejs.dev/) 'Vue > TypeScript' 템플릿을 기준으로 설명하며, Composition API와 타입스크립트를 사용합니다.

## Composition VS Options

Options API는 `data`, `methods`와 같이 강제되는 옵션을 사용해서 자바스크립트 이해도가 높지 않아도 쉽게 배우고 사용할 수 있습니다.
또한 Vue 2버전 이하의 기존 코드와 호환성을 유지하기 좋습니다.

Composition API는 새로운 스크립트 문법으로 더 유연한 구조로 코드 재사용성이 향상됩니다.
또한 타입스크립트와의 호환이 좋습니다.(Options API도 타입스크립트와 함께 사용할 수 있지만 일부 불편한 부분이 있습니다)

두 방식은 하나의 프로젝트에서 함께 사용할 수 있습니다.
만약, 타입스크립트를 사용한다면 Composition API를 사용하는 것을 추천합니다.

## 앱 생성하기

```html --path=/index.html
<div id="app"></div>
<script type="module" src="/src/main.ts"></script>
```

```js --path=/src/main.ts
import { createApp } from 'vue'
import App from './App.vue'

const app = createApp(App) // 앱 인스턴스 반환!
app.use(플러그인) // 플러그인 등록!
app.component(컴포넌트) // 전역 컴포넌트 등록!
app.directive(디렉티브) // 디렉티브 등록!
// ...
app.mount('#app') // 마지막에 호출!
```

메소드 체이닝을 사용하는 경우,

```js
createApp(App)
  .use(플러그인)
  .component(컴포넌트)
  .mount('#app')
```

### 앱 인스턴스 멤버

| 멤버 | 설명 | 비고 |
| --- | --- | --- |
| `app.mount()` | 요소에 앱 인스턴스를 연결(Mount) |  |
| `app.unmount()` | 요소에 연결된 앱 인스턴스를 해제(Unmount) |  |
| `app.use()` | Vue 외부 플러그인을 설치 |  |
| `app.component()` | 전역 컴포넌트를 등록 |  |
| `app.directive()` | 전역 커스텀 디렉티브를 등록 |  |
| `app.provide()` | 전역으로 주입(Inject)할 데이터를 제공(Provide) |  |
| `app.mixin()` | 전역 믹스인을 적용 | 하위 호환 지원을 위하며, 직접 사용은 권장하지 않음 |
| `app.runWithContext()` | `app.provide()`로 전역 제공하는 데이터를 조회할 수 있는 즉시 호출되는 콜백을 실행 | `3.3+` |
| `app.version` | Vue.js 버전 확인 |  |
| `app.config` | 환경 설정이 포함된 구성 객체 |  |
| `app.config.errorHandler` | 예외 처리되지 않은 에러 발생 시 실행할 핸들러 정의 |  |
| `app.config.warnHandler` | 경고 발생 시 실행할 핸들러 정의 |  |
| `app.config.performance` | 개발 모드일 때, 성능 추적 활성화 |  |
| `app.config.compilerOptions` | 런타임 컴파일러 옵션 설정 |  |
| `app.config.globalProperties` | 앱 내의 모든 하위 컴포넌트에서 접근할 수 있는 전역 속성을 등록 |  |
| `app.config.optionMergeStrategies` | 컴포넌트 옵션의 커스텀 병합 함수를 정의 |  |

## SFC 구조

`*.vue` 파일은 `<template>`, `<script>`, `<style>` 태그로 구성된 싱글 파일 컴포넌트(Single File Component, SFC)입니다.
`*.vue` 파일은 모듈 컴파일러를 통해 브라우저에서 사용할 수 있는 자바스크립트 파일로 변환됩니다.
`lang` 속성을 사용해, `<script>`와 `<style>` 태그에서 사용할 언어(타입스크립트, SCSS 등)를 지정할 수 있습니다.

```vue
<script setup lang="ts">
  // 스크립트(JS)
</script>

<template>
  <!-- 템플릿(HTML) -->
</template>

<style scoped lang="scss">
  /* 스타일(CSS) */
</style>
```

### 범위가 지정된 CSS

SFC 컴포넌트 `<style>` 태그에 `scoped` 속성을 추가하면, 컴포넌트 내부에서만 일치하는 CSS 선택자(Selector)를 작성할 수 있습니다.
외부 컴포넌트에 영향을 주지 않으므로, 컴포넌트 간의 선택자 이름 충돌을 방지할 수 있습니다.
대부분 `scoped` 속성 사용을 권장합니다.

```vue
<template>
  <div></div>
</template>

<style scoped>
div {
  color: red;
}
</style>
```

출력된 결과를 확인하면, 요소와 선택자에 `data-v-`로 시작하는 속성이 추가되어 있습니다.
이것을 스타일 해시(Style Hash)라고 하며, 이 고유한 속성 이름을 통해 컴포넌트 간의 선택자 이름 충돌을 방지합니다.

```html --caption=출력된 결과.
<style>
  div[data-v-7a7a37b1] {
    color: red;
  }
</style>
<div data-v-7a7a37b1></div>
```

`scoped` 속성은 이름 충돌을 방지하지만, 간혹 부모 컴포넌트에서 하위 컴포넌트에 영향을 줘야 하는 경우가 있습니다.
이때 `:deep()` 가상 클래스를 사용할 수 있습니다.

```vue --path=/src/components/Parent.vue
<script setup lang="ts">
import Child from './components/Child.vue'
</script>

<template>
  <div class="parent">
    <Child />
  </div>
</template>

<style scoped>
.parent .child {
  color: red;
}
</style>
```

```vue --path=/src/components/Child.vue
<template>
  <div class="child-wrap">
    <div class="child">CHILD</div>
  </div>
</template>

<style scoped></style>
```

/// message-box --icon=info --color=info
`scoped` 속성을 통한 부모 컴포넌트의 스타일 해시는 자식 컴포넌트의 최상위 요소에 적용됩니다.
///

```html --caption=출력된 결과.
<div data-v-7a7a37b1 class="parent">
  <div data-v-7a7a37b1 data-v-0904fc8e class="child-wrap">
    <div data-v-0904fc8e class="child">
      CHILD
    </div>
  </div>
</div>
```

하나의 컴포넌트(SFC)에서 여러 개의 `<style>` 태그를 사용할 수 있습니다.

```vue
<style scoped lang="scss"></style>
<style scoped></style>
<style></style>
```

## 반응형 데이터

데이터를 화면에 출력하고 있을 때, 기본적으로는 데이터를 변경하면 화면에 반영되지 않습니다.
Vue와 같은 모던 프론트엔드 프레임워크에서, 데이터를 변경하면 화면에 자동으로 반영되는 기능을 '반응성(Reactivity)'이라고 하고, 그 반응성을 가진 데이터를 '반응형 데이터(Reactive state)' 혹은 줄여서 '반응형'이라고 합니다.

### ref vs reactive

`ref()`와 `reactive()` 함수는 모두 반응형 데이터를 반환하지만, 두 함수는 일부 차이가 있습니다.
`ref()` 함수는 모든 데이터 타입에서 사용할 수 있고, 
`reactive()` 함수는 객체나 배열 같은 참조형 데이터 타입에서 사용해야 반응성을 가집니다.

| 함수 | 원시형 반응성 | 참조형 반응성 | `.value` 여부 | 반환 | 암시적 깊은 감시(Watch) | 
| --- | --- | --- | --- | --- | --- |
| `ref()` | O | O | O | 참조(Ref) 객체 | X |
| `reactive()` | X | O | X | 반응형 데이터 | O |

주로 `ref()` 함수를 사용하지만, 매번 `.value` 속성으로 값에 접근해야 하는 번거로움이 있습니다.
`reactive()` 함수는 `.value` 속성을 사용하지 않고도 반응성을 가질 수 있지만, 참조형 데이터 타입에서만 사용할 수 있습니다.

```vue
<script setup>
import { ref, reactive } from 'vue'

const refPrimitive = ref(123) // 반응성 O
const reactivePrimitive = reactive(123) // 반응성 X
console.log(refPrimitive.value) // 123
console.log(reactivePrimitive === 123) // true

const user = {
  name: 'HEROPY',
  age: 85
}
const refUser = ref(user)
const reactiveUser = reactive(user)

console.log(refUser.value.name) // 'HEROPY'
console.log(reactiveUser.name) // 'HEROPY'

console.log(refUser.value.age) // 85
console.log(reactiveUser.age) // 85
</script>
```

템플릿에서는 `ref()` 혹은 `reactive()` 함수 모두 `.value` 속성을 사용하지 않습니다.

```vue
<template>
  <div>{{ refPrimitive }}</div>
  <div>{{ reactivePrimitive }}</div>

  <div>{{ refUser.name }}</div>
  <div>{{ reactiveUser.name }}</div>
  
  <div>{{ refUser.age }}</div>
  <div>{{ reactiveUser.age }}</div>
</template>
```

타입스크립트를 사용하면, `reactive()` 함수에서 원시형 선언 문제를 바로 확인할 수 있습니다.

```vue --line-error=4
<script setup lang="ts">
import { reactive } from 'vue'

const reactivePrimitive = reactive(123) // 'number' 형식의 인수는 'object' 형식의 매개 변수에 할당될 수 없습니다.ts(2345)
</script>
```

## 템플릿 문법

`*.vue` 컴포넌트의 최상위 `<template>` 태그(HTML) 안에서 사용하는 문법입니다.

### 데이터 보간

`*.vue` 컴포넌트의 `<script>` 태그에서 최상위 변수는 반응성(Reactivity) 여부를 떠나 템플릿에 데이터를 보간할 수 있습니다.
`{{ data }}`와 같이, 중괄호(`{}`) 기호를 사용해 데이터를 보간하는 패턴을 '이중 중괄호 문법(Mustache)'라고 합니다.

```vue --caption=이중 중괄호 데이터 보간
<script setup lang="ts">
import { ref } from 'vue'

const data = 123 // 일반 데이터
const reactiveData = ref(123) // 반응형 데이터
</script>

<template>
  <div>{{ data }}</div>
  <div>{{ reactiveData }}</div>
</template>
```

```html --caption=출력된 결과.
<div>123</div>
<div>123</div>
```

### HTML 출력

문자에 포함된 HTML 코드를 실제 출력하려면, 이중 중괄호가 아닌 `v-html` 디렉티브를 사용해야 합니다.

/// message-box --icon=info --color=info
`v-html`, `v-bind`와 같이 `v-` 접두사로 시작하는 특수한 속성을 디렉티브(Directive)라고 합니다.
///

```vue --caption=HTML 코드를 가진 문자열
<script setup lang="ts">
  const rawHtml = '<div style="color: red;">HTML 출력</div>'
</script>
```

HTML 코드 문자를 단순히 이중 중괄호 문법으로 출력하면, `el.textContent`와 같이 문자 그대로 출력합니다.
v-html 디렉티브를 사용하면, `el.innerHTML`와 같이 출력합니다.

```vue
<template>
  <div>{{ rawHtml }}</div>
  <div v-html="rawHtml"></div>
</template>
```

```vue --caption=출력된 결과.
<div>&amp;lt;div style="color: red;"&amp;gt;HTML 출력&amp;lt;/div&amp;gt;</div>
<div style="color: red;">HTML 출력</div>
```

/// message-box --icon=warning --color=warning
외부 사용자가 작성한 HTML을 동적으로 렌더링하는 것(댓글 시스템 같은)은 [XSS 취약점](https://namu.wiki/w/XSS)이 발생할 수 있으므로 주의해야 하지만, 신뢰할 수 있는 콘텐츠일 경우 사용에 전혀 문제가 없습니다!
///

### 속성 바인딩

HTML 속성(Attributes)에 데이터를 연결할 수 있습니다.
`v-bind:속성"` 패턴보다 `:속성` 패턴(축약형)이 더 짧고 간결하기에 추천됩니다.
만약, 여러 속성을 한 번에 바인딩할 때는 `v-bind`를 속성 객체를 값으로 사용합니다.

```
<요소 v-bind:속성="데이터" />
<요소 :속성="데이터" />
<요소 v-bind="속성_객체" />
```

```vue
<script setup lang="ts">
import { ref } from 'vue'

const name = ref('hello-world')
const isValid = ref(true)
const attrs = ref({
  id: 'hello-world',
  disabled: true,
})
</script>

<template>  
  <!-- 일반 속성 바인딩 -->
  <div :id="name"></div>
  
  <!-- 불린 속성 바인딩 -->
  <input :disabled="isValid" />

  <!-- 여러 속성을 객체로 바인딩 -->
  <button v-bind="attrs">버튼!</button>
</template>
```

```html --caption=출력된 결과.
<div id="hello-world"></div>

<input disabled />

<button id="hello-world" disabled>버튼!</button>
```

`:['속성이름']` 패턴을 사용해, 동적으로 속성 이름을 결정할 수 있습니다.

```vue --caption=id와 class 속성을 동적으로 결정
<script setup lang="ts">
import { ref } from 'vue'

const attrName = ref('id')
const attrValue = ref('hello')
</script>

<template>
  <button @click="attrName = attrName === 'id' ? 'class' : 'id'">Toggle attribute name!</button>
  <h1 :[attrName]="attrValue">Hello!</h1>
</template>

<style scoped>
#hello {
  color: red;
}
.hello {
  color: blue;
}
</style>
```

### 표현식 사용

이중 중괄호와 모든 디렉티브에서는 자바스크립트 표현식(Expression)을 사용할 수 있습니다.
예를 들어, `const a = 1`, `function b() {}`과 같은 선언문(Declaration)은 사용할 수 없습니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const name = ref('HEROPY')
const age = ref(123)
const isValid = ref(true)

function add(a: number, b: number) {
  return a + b
}
</script>

<template>
  <div>{{ name.split('').reverse().join('') }}</div>
  <div>{{ age - 100 }}</div>
  <div>{{ isValid ? 'YES' : 'NO' }}</div>
  <div :id="`hello-${name}`">{{ add(age, 85) }}</div>
</template>
```

### HTML 클래스 바인딩

객체와 배열 데이터로 바인딩해 HTML 클래스 선택자를 동적으로 추가/제거할 수 있습니다.
일반적으로 객체 리터럴(Literal) 방식의 바인딩을 사용합니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const isActive = ref(true)
const error = ref(false)
const status = ref('primary')

const cssClasses = ref({
  active: true,
  error: false
})
</script>

<template>
  <!-- 객체로 바인딩 -->
  <div 
    class="btn"
    :class="{ 
      active: isActive,
      error,
      [`btn-${status}`]: true,
    }"></div>
  
  <!-- 배열로 바인딩 -->
  <div
    class="btn"
    :class="[
      isActive ? 'active' : '',
      error ? 'error' : '',
      `btn-${status}`,
    ]"></div>
  
  <!-- 객체와 배열을 함께 사용 -->
  <div
    class="btn"
    :class="[
      cssClasses,
      `btn-${status}`,
    ]"></div>
</template>
```

```html --caption=출력된 결과.
<div class="btn active btn-primary"></div>
<div class="btn active btn-primary"></div>
<div class="btn active btn-primary"></div>
```

### 인라인 스타일 바인딩

객체와 배열 데이터로 바인딩해 CSS 속성과 값을 동적으로 추가/제거할 수 있습니다.
`font-size`, `background-color`와 2개 단어 이상의 속성 이름을 카멜 케이스(Camel Case)로 작성하면 자동으로 케밥 케이스(Kebab Case)로 변환됩니다.
숫자 데이터를 입력할 때는, 단위를 함께 작성해야 합니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const color = ref('red')
const size = ref(16)

const colorStyles = {
  color: 'red',
  backgroundColor: 'blue',
}
</script>

<template>
  <!-- 객체로 바인딩 -->
  <div 
    :style="{ 
      color,
      fontSize: `${size}px`,
      backgroundColor: colorStyles.backgroundColor
    }"></div>
  
  <!-- 배열로 바인딩 -->
  <!-- 여러 스타일 객체를 사용하기 위한 패턴 -->
  <div
    :style="[
      colorStyles,
      { fontSize: `${size}px` },
    ]"></div>
</template>
```

```html --caption=출력된 결과.
<div style="color: red; font-size: 16px; background-color: blue;"></div>
<div style="color: red; font-size: 16px; background-color: blue;"></div>
```

### 요소 참조

요소에 직접 접근해야 하는 경우, Vue `ref` 속성을 사용해 반응형 데이터와 바인딩합니다.
단일 요소 참조인 경우, 반응형 데이터는 `null`로 초기화합니다.

```vue
<script setup lang="ts">
import { ref, onMounted } from 'vue'

const inputEl = ref<HTMLInputElement | null>(null)

onMounted(() => {
  inputEl.value?.focus()
})
</script>

<template>
  <input ref="inputEl" />
</template>
```

여러 요소를 참조하는 경우, 반응형 데이터는 빈 배열로 초기화합니다.

```vue
<script setup lang="ts">
import { ref, onMounted } from 'vue'

const fruits = ref(['Apple', 'Banana', 'Orange'])
const liEls = ref<HTMLLIElement[]>([])

onMounted(() => {
  liEls.value.forEach((liEl) => {
    console.log(liEl.textContent) // Apple, Banana, Orange
  })
})
</script>

<template>
  <ul>
    <li
      v-for="fruit in fruits"
      ref="liEls"
      :key="fruit">
      {{ fruit }}
    </li>
  </ul>
</template>
```

## 조건부 렌더링

`v-if`, `v-else-if`, `v-else` 디렉티브를 사용해 데이터 조건에 맞게 템플릿을 렌더링할 수 있습니다.
각 디렉티브는 연결된 형제 요소에만 사용할 수 있습니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const isShow = ref(true)
const list = ref([])
</script>

<template>
  <!-- v-if -->
  <div v-if="isShow"></div>
  <div v-if="isShow && list.length"></div>
  <div v-if="isShow || list.length"></div>
  
  <!-- v-else -->
  <div v-if="isShow"></div>
  <div v-else></div>

  <!-- v-else-if -->
  <div v-if="isShow"></div>
  <div v-else-if="list.length"></div>
  <div v-else></div>
</template>
```

`v-if`, `v-else-if`, `v-else` 디렉티브는 단일 요소에 사용해야 하지만, 다중 요소의 조건부 렌더링이 필요하면, `<template>` 태그를 사용합니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const isShow = ref(true)
</script>
```

렌더링할 요소 모두에 조건을 추가하는 방법은 권장하지 않습니다.

```vue
<template>
  <h1 v-if="isShow"></h1>
  <div v-if="isShow"></div>
  <p v-if="isShow"></p>
</template>
```

랩핑 요소를 추가하면 간단하지만, 불필요한 상위 요소(`<div>`)를 가지게 됩니다.

```vue
<template>
  <div v-if="isShow">
    <h1></h1>
    <div></div>
    <p></p>
  </div>
</template>
```

`<template>` 태그를 사용하면, 불필요한 상위 요소가 없어도 다중 요소에 한 번에 조건을 추가할 수 있습니다.
Vue에서 `<template>` 태그는 최종 렌더링에 포함되지 않습니다.

```vue
<template v-if="isShow">
  <h1></h1>
  <div></div>
  <p></p>
</template>
```

## 리스트 렌더링

기본적으로 `v-for` 디렉티브를 사용하면, 배열 데이터의 아이템 개수에 맞게 반복 렌더링을 할 수 있습니다.
`:key` 속성은 반복되는 각 아이템을 Vue.js가 구분하는 기준이므로, 고유한 문자나 숫자의 원시형 데이터가 꼭 필요합니다.
객체나 배열 등의 참조형 데이터를 `:key` 속성에 지정하지 않도록 주의해야 합니다.

'아이템 변수'의 유효범위(Scope)는 해당 요소로 제한됩니다.

```vue
<div
  v-for="아이템_변수 in 배열_데이터"
  :key="고유한_원시형">
</div>

<div
  v-for="(아이템_변수, 인덱스) in 배열_데이터"
  :key="고유한_원시형">
</div>
```

```vue
<script setup lang="ts">
import { ref } from 'vue'

const users = ref([
  { name: 'Neo', age: 85 },
  { name: 'Lewis', age: 22 },
  { name: 'Evan', age: 46 }
])
</script>

<template>
  <div
    v-for="(user, index) in users"
    :key="user.name"
    :data-user-name="user.name"
    :data-user-age="user.age">
    {{ index + 1 }}) {{ user.name }}({{ user.age }})
  </div>
</template>
```

```html --caption=출력된 결과.
<div data-user-name="Neo" data-user-age="85"> 1) Neo(85) </div>
<div data-user-name="Lewis" data-user-age="22"> 2) Lewis(22) </div>
<div data-user-name="Evan" data-user-age="46"> 3) Evan(46) </div>
```

### 객체 데이터 반복

`v-for` 디렉티브를 사용해, Key-Value(속성-값) 형태의 객체 데이터도 반복적으로 렌더링할 수 있습니다.
위에서 살펴본 '아이템 변수'처럼 `값`, `속성`, `인덱스` 모두 원하는 이름을 사용할 수 있습니다.

```vue
<div
  v-for="값 in 객체_데이터"
  :key="고유한_원시형">
</div>

<div
  v-for="(값, 속성) in 객체_데이터"
  :key="고유한_원시형">
</div>

<div
  v-for="(값, 속성, 인덱스) in 객체_데이터"
  :key="고유한_원시형">
</div>
```

```vue
<script setup lang="ts">
import { ref } from 'vue'

const userInfo = ref({
  name: 'Neo',
  age: 85,
  emails: ['thesecon@gmail.com', 'neo@zillinks.com']
})
</script>

<template>
  <div
    v-for="(value, key, index) in userInfo"
    :key="key">
    <template v-if="Array.isArray(value)">
      {{ index + 1 }}) {{ key }}: {{ value.join(', ') }}
    </template>
    <template v-else>
      {{ index + 1 }}) {{ key }}: {{ value }}
    </template>
  </div>
</template>
```

```html --caption=출력된 결과.
<div>1) name: Neo</div>
<div>2) age: 85</div>
<div>3) emails: thesecon@gmail.com, neo@zillinks.com</div>
```

### 숫자 범위로 반복

`v-for` 디렉티브에서는 정수를 사용해 요소를 반복 출력할 수 있습니다.
다음 예제에서 아이템 변수 `n`은 0이 아닌 `1`부터 시작합니다.

```vue
<template>
  <div 
    v-for="n in 4" 
    :key="n">
    {{ n }}
  </div>
</template>
```

```html --caption=출력된 결과.
<div>1</div>
<div>2</div>
<div>3</div>
<div>4</div>
```

### v-if 와 v-for

요소에 `v-if`와 `v-for`(리스트 렌더링) 디렉티브를 함께 사용하면, `v-if`가 먼저 평가됩니다.
단일 요소에서 사용하는 두 디렉티브는 기능적으로 충돌하니, 처음부터 단일 요소에서 같이 사용하지 않도록 주의하세요!

```vue
<script setup lang="ts">
import { ref } from 'vue'

const isShow = ref(true)
const list = ref([1, 2, 3])
</script>
```

다음의 두 방식 모두 출력된 결과는 같습니다.

```vue
<!-- 권장하지 않는 방법 -->
<template>
  <div
    v-if="isShow"
    v-for="item in list" 
    :key="item">
    {{ item }}  
  </div>
</template>
```

```vue
<!-- 권장하는 방법 -->
<template v-if="isShow">
  <div
    v-for="item in list" 
    :key="item">
    {{ item }}  
  </div>
</template>
```

조건에 따라 일부 요소만 반복 출력(필터링)하는 경우, 두 디렉티브를 단일 요소에서 사용하지 않기 위해 `v-for` 디렉티브를 `<template>` 태그에서 사용할 수도 있습니다.
이 때는 `key` 속성도 `<template>` 태그에 같이 작성합니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const list = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
</script>

<template>
  <ul>
    <template
      v-for="item in list"
      :key="item">
      <li v-if="item > 3 && item < 8">
        {{ item }}
      </li>
    </template>
  </ul>
</template>
```

```html --caption=출력된 결과.
<ul>
  <li>4</li>
  <li>5</li>
  <li>6</li>
  <li>7</li>
</ul>
```

## 이벤트 핸들링

요소에 `v-on:이벤트` 패턴을 이용해 이벤트 핸들러를 등록할 수 있습니다.
`v-on:이벤트` 패턴보다 `@이벤트` 패턴(축약형)이 더 짧고 간결하기에 추천됩니다.
간단한 표현식은 인라인 핸들러 방식으로 작성할 수 있습니다.
혹은 이미 정의된 함수를 연결하는 방식(메소드 핸들러)으로도 작성할 수 있습니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)

function handler() {
  count.value += 1
}
</script>

<template>
  <h1>{{ count }}</h1>
  <button @click="count += 1">증가!</button> <!-- 인라인 핸들러 -->
  <button @click="handler">증가!</button> <!-- 메소드 핸들러 -->
</template>
```

인라인 핸들러에서 메소드를 호출할 때, 인수로 이벤트 객체(`$event`)를 전달할 수 있습니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const urls = ref([
  'heropy.dev',
  'github.com',
  'google.com',
])

function handler(name: string, event: MouseEvent) {
  event.preventDefault()
  location.href = `https://${name}`
}
</script>

<template>
  <a 
    v-for="url in urls" 
    :key="url" 
    :href="url" 
    @click="handler(url, $event)">
    {{ url }}
  </a>
</template>
```

`,` 혹은 `;` 기호로 구분해 하나의 이벤트에 여러 개의 핸들러를 등록할 수 있습니다.

```vue
<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)

function increase() {
  count.value += 1
}
function log(event: MouseEvent) {
  console.log(event)
}
</script>

<template>
  <h1>{{ count }}</h1>
  <button @click="increase(), log($event)">증가!</button>
  <button @click="increase(); log($event)">증가!</button>
</template>
```

### 수식어

이벤트 핸들러에 수식어(Modifier)를 사용하면, 추가적인 동작을 부여할 수 있습니다.
각 수식어는 체이닝(Chaining) 형태로 사용할 수 있습니다.

```vue
<template>
  <a @click.stop="handler">클릭!</a>
  <input @keydown.stop="handler" />
  
  <!-- 핸들러 없이 수식어만 사용 -->
  <a @click.stop>클릭!</a>
  <input @keydown.stop />

  <!-- 수식어 체이닝 -->
  <a @click.stop.prevent="handler">클릭!</a>
  <input @keydown.stop.enter="handler" />
  
  <!-- 정확한 키 조합 -->
  <a @click.ctrl.exact="handler">클릭!</a>
  <input @keydown.alt.enter.exact="handler" />
</template>
```

#### 이벤트 수식어

| 수식어 | 설명 | 비고 |
| --- | --- | --- |
| `.prevent` | 기본 동작 중지 | `event.preventDefault()` |
| `.stop` | 이벤트 전파 중지 | `event.stopPropagation()` |
| `.capture` | 캡처링 모드로 이벤트 핸들러 등록 | `{ capture: true }` |
| `.once` | 한 번만 실행되는 핸들러 등록 | `{ once: true }` |
| `.passive` | 화면 동작와 로직의 분리를 통한 체감 성능 향상 | `{ passive: true }` |
| `.self` | 이벤트가 등록된 요소와 발생한 요소가 일치하는 경우만 핸들러 호출 | `if (target === currentTarget)` |

#### 키 수식어

| 수식어 | 설명 | 비고 |
| --- | --- | --- |
| `.KEY-NAME` | 키보드의 kebab-case 키 이름 |  | 
| `.exact` | 정확한 키 조합 |  |
| `.enter` | `Enter` 키 |  |
| `.tab` | `Tab` 키 |  |
| `.delete` | `Backspace`, `Delete` 키 |  |
| `.esc` | `Escape` 키 |  |
| `.space` | `[공백]` 키 |  |
| `.up` | `ArrowUp` 키 |  |
| `.down` | `ArrowDown` 키 |  |
| `.left` | `ArrowLeft` 키 |  |
| `.right` | `ArrowRight` 키 |  |
| `.ctrl` | `Control` 키 |  |
| `.alt` | `Alt` 키 |  |
| `.shift` | `Shift` 키 |  |
| `.meta` | `Meta` 키 | Cmd 혹은 Win |

#### 마우스 수식어

| 수식어 | 설명 | 비고 |
| --- | --- | --- |
| `.left` | 마우스 좌측 버튼 클릭 | `click` | 
| `.right` | 마우스 우측 버튼 클릭 | `contextmenu` | 
| `.middle` | 마우스 휠 버튼 클릭 | `auxclick` |

## 양식 입력 바인딩

`<input>`, `<textarea>`, `<select>`와 같은 HTML 양식 요소에서는 속성 바인딩과 이벤트 핸들링을 통해 양방향 데이터 바인딩을 할 수 있습니다.
그리고 `v-model` 디렉티브를 사용하면, 더욱 간결하게 양방향 데이터 바인딩을 할 수 있습니다.

/// message-box --icon=warning --color=warning
`v-model` 디렉티브를 사용하면, 한글(CJK)을 입력이 지연되는 문제가 있습니다. (IME 구성 중 `v-model` 업데이트 실패)
만약 한글 입력이 필요한 경우, 축약형의 `v-model` 디렉티브 대신 속성과 이벤트 핸들링을 통한 바인딩을 사용해야 합니다.
///

```vue
<script setup lang="ts">
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <!-- 양방향 데이터 바인딩 -->
  <input
    :value="text"
    @input="text = ($event.target as HTMLInputElement).value" />

  <!-- v-model 디렉티브를 통한 양방향 데이터 바인딩 -->
  <input v-model="text" />
</template>
```

축약형의 `v-model` 디렉티브를 사용하지 않는 경우, 각 요소는 다음과 같은 속성과 이벤트를 사용합니다.

| 요소 | 사용 속성 | 사용 이벤트 | 비고 |
| --- | --- | --- | --- |
| `<input type="text" />` | `:value` | `@input` |  |
| `<textarea>` | `:value` | `@input` |  |
| `<input type="checkbox" />` | `:checked` | `@change` |  |
| `<input type="radio" />` | `:checked` | `@change` |  |
| `<select>` | `:value` | `@change` |  |

### 요소별 바인딩 패턴

#### 텍스트

```vue
<script setup lang="ts">
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <!-- 일반적인 경우, -->
  <input v-model="text" />
  <!-- 한글이 필요한 경우, -->
  <input
    :value="text"
    @input="text = ($event.target as HTMLInputElement)?.value" />
  <h1>{{ text }}</h1>
</template>
```

#### 여러 줄 텍스트

```vue
<script setup lang="ts">
import { ref } from 'vue'

const text = ref('')
</script>

<template>
  <!-- 일반적인 경우, -->
  <textarea v-model="text"></textarea>
  <!-- 한글이 필요한 경우, -->
  <textarea
    :value="text"
    @input="text = ($event.target as HTMLInputElement)?.value"></textarea>
  <pre>{{ text }}</pre>
</template>
```

#### 단일 체크박스

```vue
<script setup lang="ts">
import { ref } from 'vue'

const checked = ref(false)
</script>

<template>
  <label>
    <input
      v-model="checked"
      type="checkbox" />
    동의합니다.
  </label>
  <h2>동의 여부: {{ checked ? '예' : '아니오' }}</h2>
</template>
```

#### 다중 체크박스

```vue
<script setup lang="ts">
import { ref } from 'vue'

interface Fruit {
  text: string
  value: string
}
const fruits = ref<Fruit[]>([
  { text: '사과', value: 'apple' },
  { text: '바나나', value: 'banana' },
  { text: '체리', value: 'cherry' }
])
const checked = ref<string[]>([])

function setChecked(event: Event, fruit: Fruit) {
  checked.value = (event.target as HTMLInputElement)?.checked
    ? checked.value.concat([fruit.value])
    : checked.value.filter(v => v !== fruit.value)
}
</script>

<template>
  <label
    v-for="fruit in fruits"
    :key="fruit.value">
    <input
      :value="fruit.value"
      type="checkbox"
      @change="setChecked($event, fruit)" />
    {{ fruit.text }}
  </label>
  <h2>선택된 과일: {{ checked.join(', ') }}</h2>
</template>
```

#### 라디오 버튼

```vue
<script setup lang="ts">
import { ref } from 'vue'

interface Fruit {
  text: string
  value: string
}
const fruits = ref<Fruit[]>([
  { text: '사과', value: 'apple' },
  { text: '바나나', value: 'banana' },
  { text: '체리', value: 'cherry' }
])
const picked = ref('')
</script>

<template>
  <label
    v-for="fruit in fruits"
    :key="fruit.value">
    <input
      v-model="picked"
      type="radio"
      :value="fruit.value" />
    {{ fruit.text }}
  </label>
  <h2>선택된 과일: {{ picked }}</h2>
</template>
```

#### 단일 선택

```vue
<script setup lang="ts">
import { ref } from 'vue'

interface Fruit {
  text: string
  value: string
}
const fruits = ref<Fruit[]>([
  { text: '사과', value: 'apple' },
  { text: '바나나', value: 'banana' },
  { text: '체리', value: 'cherry' }
])
const selected = ref('')
</script>

<template>
  <select v-model="selected">
    <option
      value=""
      disabled>
      가장 좋아하는 과일을 선택하세요.
    </option>
    <option
      v-for="fruit in fruits"
      :key="fruit.value"
      :value="fruit.value">
      {{ fruit.text }}
    </option>
  </select>
  <h2>선택된 과일: {{ selected }}</h2>
</template>
```

#### 다중 선택

```vue
<script setup lang="ts">
import { ref } from 'vue'

const fruits = ref([
  { text: '사과', value: 'apple' },
  { text: '바나나', value: 'banana' },
  { text: '체리', value: 'cherry' }
])
const selected = ref([])
</script>

<template>
  <select
    v-model="selected"
    multiple>
    <option
      value=""
      disabled>
      가장 좋아하는 과일을 선택하세요.
    </option>
    <option
      v-for="fruit in fruits"
      :key="fruit.value"
      :value="fruit.value">
      {{ fruit.text }}
    </option>
  </select>
  <h2>선택된 과일: {{ selected }}</h2>
</template>
```

#### 편집 가능 요소

다음은 HTML `contenteditable` 속성을 사용하는 요소의 예제입니다.

```vue
<script setup lang="ts">
import { ref, watch } from 'vue'

const text = ref('')
const inputEl = ref<HTMLElement | null>(null)

// text 갱신과 inputEl 내용을 동기화
watch(text, newValue => {
  if (inputEl.value && inputEl.value.innerText !== newValue) {
    inputEl.value.innerText = newValue
  }
})
</script>

<template>
  <div
    ref="inputEl"
    contenteditable
    @input="text = (inputEl as HTMLElement)?.innerText"></div>
  <pre>{{ text }}</pre>
</template>
```

### 수식어

입력 요소의 `v-model` 디렉티브에 수식어(Modifier)를 사용하면, 추가적인 동작을 부여할 수 있습니다.

| 수식어 | 설명 | 비고 |
| --- | --- | --- |
| `.lazy` | 입력이 완료된 후(Enter, Tab 등) 데이터를 업데이트 | `@change` |
| `.number` | 숫자 데이터 타입으로 변환 | `type="number"` |
| `.trim` | 입력된 텍스트의 앞뒤 공백을 제거 | `text.trim()` |

```vue
<script setup lang="ts">
import { ref } from 'vue'

const text = ref('')
const count = ref(0)
</script>

<template>
  <input v-model.lazy="text" />
  <input v-model.number="count" />
  <input v-model.trim="text" />
</template>
```

## 계산된 데이터

Getter를 사용해 반응형 데이터를 기준으로 새롭게 계산된 데이터(Computed)를 만들 수 있습니다.

/// message-box --icon=info --color=info
Getter(게터)는 데이터를 읽을 때(Get), 호출되는 함수를 말합니다.
Setter(세터)는 데이터를 지정할 때(Set), 호출되는 함수를 말합니다.
///

/// message-box --icon=error --color=error
비동기 요청이나 DOM 변경은 계산된 데이터(Getter)를 사용하지 않아야 합니다.
필요한 경우, 감시자(Watcher)를 사용해야 합니다!
///

```ts
const 계산된_데이터 = computed(게터)
```

```vue
<script setup lang="ts">
import { ref, computed } from 'vue'

const count = ref(0)
const double = computed(() => count.value * 2)

function increase() {
  count.value += 1
}
</script>

<template>
  <div>{{ count }}</div>
  <div>{{ double }}</div>
  <button @click="increase">증가!</button>
</template>
```

Getter는 읽기 전용이므로, 데이터를 지정할 때 호출할 Setter를 추가할 수 있습니다.
`computed()`의 인수로 Getter 대신, `get`과 `set` 속성을 포함한 객체를 전달합니다.

```ts
const 계산된_데이터 = computed({
  get: 게터,
  set: 세터
})
```

```vue
<script setup lang="ts">
import { ref, computed } from 'vue'

const count = ref(0)
const double = computed({
  get: () => count.value * 2,
  set: val => {
    count.value = val / 2
  }
})

function increase() {
  double.value += 1
}
</script>

<template>
  <div>{{ count }}</div>
  <div>{{ double }}</div>
  <button @click="increase">증가!</button>
</template>
```

## 데이터 감시

| 함수 | 설명 | 즉시 실행 | 이전값 확인 | 깊은 감시 | 옵션 |
| --- | --- | --- | --- | --- | --- |
| `watch()` | 명시적 반응형 데이터 감시 | X | O | 명시적, 암시적 모두 가능 | `immediate`, `deep`, `flush` |
| `watchEffect()` | 콜백 모든 반응형 데이터 감시 | O | X | 명시적만 가능 | `flush` |

`immediate`와 `deep` 옵션의 기본값은 `false`입니다.
`flush` 옵션의 기본값은 `pre`이며, 다음과 같은 값을 가질 수 있습니다.

| 값 | 설명 | 기본값 |
| --- | --- | --- |
| `pre` | 상태 변경 시, 화면 갱신 전 콜백 호출 | O |
| `post` | 상태 변경 시, 화면 갱신 후 콜백 호출 |  |
| `sync` | 여러 번 상태 변경 시에도 버퍼링 없이 동일 Tick에서 같은 횟수로 콜백 호출 |  |

### 감시 패턴

#### 단일 데이터 감시

`watch()` 함수는 이전값(`oldVal`)을 확인할 수 있지만, `watchEffect()` 함수는 이전값을 확인할 수 없습니다.
`watchEffect()` 함수는 별도 옵션이 없이도 즉시 실행되기 때문에 처음부터 이전값(`1`)이 콘솔에 출력되고 버튼을 클릭하면 새로운 값(`7`)이 출력됩니다.

```vue
<script setup lang="ts">
import { ref, watch, watchEffect } from 'vue'

const count = ref(1)

watch(count, (newVal, oldVal) => {
  console.log(newVal, oldVal) // 7, 1
})

watchEffect(() => {
  console.log(count.value) // 1 // 7
})
</script>

<template>
  <!-- 버튼 클릭! -->
  <button @click="count = 7">새로운 값 할당!</button>
</template>
```

#### 다중 데이터 감시

```vue
<script setup lang="ts">
import { ref, watch, watchEffect } from 'vue'

const count = ref(1)
const double = ref(2)

watch([count, double], ([newCount, newDouble], [oldCount, oldDouble]) => {
  console.log(newCount, oldCount) // 7, 1
  console.log(newDouble, oldDouble) // 14, 2
})

watchEffect(() => {
  console.log(count.value) // 1 // 7
  console.log(double.value) // 2 // 14
})

function assignValue() {
  count.value = 7
  double.value = 14
}
</script>
```

#### 깊은 감시

`ref()` 함수로 생성한 반응형 데이터는 암시적으로 깊은 감시를 하지 않기 때문에, 필요한 경우 `watch()` 함수의 `deep` 옵션을 사용해야 합니다.
`reactive()` 함수로 생성한 반응형 데이터는 암시적으로 깊은 감시를 하므로, `watch()` 함수로 감시할 때 `deep` 옵션을 사용하지 않아도 됩니다.

/// message-box --icon=warning --color=warning
암시적 깊은 감시는 대상의 모든 중첩 속성을 탐색하므로, 성능에 좋지 않은 영향을 줄 수 있습니다.
///

```vue
<script setup lang="ts">
import { ref, watch, watchEffect } from 'vue'

const user = ref({
  name: 'HEROPY',
  address: {
    city: 'Busan'
  }
})

watch(user, newVal => {
  console.log(newVal) // 반응 없음!
})

watch(
  user,
  newVal => {
    console.log(newVal) // user 객체
  },
  {
    deep: true // 암시적 깊은 감시
  }
)

watch(
  () => user.value.address.city, // 명시적 깊은 감시
  newVal => {
    console.log(newVal) // 'Seoul'
  }
)

watchEffect(() => {
  console.log(user.value.address.city) // 'Busan' // 'Seoul'
})
</script>

<template>
  <!-- 버튼 클릭! -->
  <button @click="user.address.city = 'Seoul'">새로운 값 할당!</button>
</template>
```

#### 감시 종료

각 감시 함수의 반환된 값(함수)을 호출하면, 감시를 종료할 수 있습니다.

```vue
<script setup lang="ts">
import { ref, watch, watchEffect } from 'vue'

const count = ref(0)

const unwatch = watch(count, (newVal, oldVal) => {
  console.log('watch:', newVal, oldVal)
})

const unwatchEffect = watchEffect(() => {
  console.log('watchEffect:', count.value)
})
</script>

<template>
  <button @click="count += 1">새로운 값 할당!</button>
  <button @click="unwatch">watch() 감시 종료</button>
  <button @click="unwatchEffect">watchEffect() 감시 종료</button>
</template>
```

## 생명주기 훅

생명주기 훅(Lifecycle Hook)은 [컴포넌트의 각 생명주기](https://vuejs.org/assets/lifecycle.16e4c08e.png)에서 호출되는 함수를 말합니다.
Options API에서는 대부분 `created`와 `mounted` 훅을 사용하지만, Composition API에는 `created`(`beforeCreate`) 훅이 없습니다.

| 훅 | 설명 | 비고 |
| --- | --- | --- |
| `onMounted()` | 컴포넌트가 연결된 후 |  |
| `onUpdated()` | 컴포넌트가 화면을 갱신한 후 |  |
| `onUnmounted()` | 컴포넌트가 해제된 후 |  |
| `onBeforeMount()` | 컴포넌트가 연결되기 전 |  |
| `onBeforeUpdate()` | 컴포넌트가 화면을 갱신하기 전 |  |
| `onBeforeUnmount()` | 컴포넌트가 해제되기 전 |  |
| `onErrorCaptured()` | 에러가 캡쳐된 후 |  |
| `onActivated()` | `<KeepAlive>`로 캐싱된 컴포넌트가 출력된 후 | No SSR |
| `onDeactivated()` | `<KeepAlive>`로 캐싱된 컴포넌트가 제거된 후 | No SSR |
| `onServerPrefetch()` | 컴포넌트가 서버 측에서 렌더링되기 전에 해결할 비동기 함수를 등록 | SSR only |

```vue --caption=생명주기 훅 사용 예제.
<script setup lang="ts">
import { ref, onMounted } from 'vue'

const inputEl = ref<HTMLInputElement | null>(null)

onMounted(() => {
  inputEl.value?.focus()
})
</script>

<template>
  <input ref="inputEl" />
</template>
```

## 컴포넌트

### 등록

`*.vue` 컴포넌트는 필요한 경우, 다음과 같이 전역으로 등록해 어디서나 사용할 수 있습니다.

/// message-box --icon=warning --color=warning
전역 등록된 컴포넌트는 트리쉐이킹(Tree Shaking)을 방지하므로, 등록 후 전혀 사용하지 않아도 최종 번들에는 포함됩니다.
자주 사용하는 등, 필요한 경우에만 전역으로 등록하는 것이 좋습니다.
///

```vue --path=/src/components/TheButton.vue
<script setup lang="ts">
defineProps<{
  color: string
}>()
</script>

<template>
  <button
    :style="{ backgroundColor: color }"
    class="btn">
    <slot></slot>
  </button>
</template>
```

```ts --path=/src/main.ts
import { createApp } from 'vue'
import App from './App.vue'
import TheButton from './components/TheButton.vue'

createApp(App)
  .component('TheButton', TheButton) // 전역 컴포넌트 등록!
  .mount('#app')
```

```vue --path=/src/App.vue --caption=별도의 가져오기 없이 바로 컴포넌트를 사용할 수 있습니다.
<template>
  <TheButton color="red">버튼!</TheButton>
</template>
```

컴포넌트를 지역적으로 사용하면, 효율적으로 번들(Bundle)되기에 권장됩니다.
Composition API에서는 (부모) 컴포넌트에서 가져오기(Import) 후 별도 등록 없이 바로 템플릿에서 사용할 수 있습니다.

```vue --path=/src/App.vue
<script setup lang="ts">
import TheButton from './components/TheButton.vue'
</script>

<template>
  <TheButton color="red">버튼!</TheButton>
</template>
```

### Props

부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달할 때, Props 방식을 사용합니다.
`defineProps()`와 `withDefaults()` 함수는 별도 가져오기 없이 바로 사용할 수 있습니다.

스크립트에서는, `defineProps()`와 `withDefaults()` 함수에서 반환된 `props` 객체로 각 Prop에 접근할 수 있습니다.
템플릿에서는, `props` 객체 없이 바로 각 Prop에 접근할 수 있습니다.(혹은 `$props` 객체로 접근할 수 있습니다)
따라서 반응형 데이터의 이름을 각 Prop과 중복하지 않아야 합니다.

/// message-box --icon=info --color=info
$props와 같이 템플릿에서 사용할 수 있는 $ 접두사를 가진 객체는 컴포넌트의 내장 속성(Built-in Property)입니다.
///

```ts
interface Props {
  // Prop 타입..
}
let props = defineProps<Props>()
props = withDefaults(props, { // Props에 기본값이 필요한 경우에만 사용!
  // 기본값..
})
```

```vue --path=/src/components/TextField.vue --line-active=19-21 --line-error=16-18
<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    myValue: string
    backgroundColor?: string // 선택적 Prop
  }>(),
  {
    backgroundColor: 'yellow'
  }
)

console.log(props)
</script>

<template>
  <input
    :style="{ backgroundColor: $props.backgroundColor }"
    :value="$props.myValue" />
  <input
    :style="{ backgroundColor }"
    :value="myValue" />
</template>
```

부모 컴포넌트에서 Props를 사용할 때는, camelCase 대신 kebab-case를 사용해야 합니다.

```vue --path=/src/App.vue
<script setup lang="ts">
import { ref } from 'vue'
import TextField from './components/TextField.vue'

const text = ref('Hello World!')
</script>

<template>
  <TextField
    :my-value="text"
    background-color="royalblue" />
</template>
```

### Emits

부모 컴포넌트에서 Props로 전달한 데이터는 자식 컴포넌트에서 읽을 수 있지만, 변경할 수는 없습니다.
만약 변경이 필요하면, 자식 컴포넌트에서 부모 컴포넌트로 Emits을 사용해 (커스텀) 이벤트 발생과 함께 데이터를 전달할 수 있습니다.
혹은 데이터를 포함하지 않고 이벤트만 발생시킬 수도 있습니다.

`defineEmits()` 함수도 별도 가져오기 없이 바로 사용할 수 있습니다.

스크립트에서는, `defineEmits()` 함수에서 반환된 `emit` 함수를 사용하고, 템플릿에서는, `$emit` 함수를 사용합니다.

```ts
const emit = defineEmits(['커스텀이벤트', ...], 데이터)
```

```vue --path=/src/components/TextField.vue
<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    myValue: string
    backgroundColor?: string
  }>(),
  {
    backgroundColor: 'yellow'
  }
)
const emit = defineEmits(['abc', 'xyz'])

console.log(props, emit)

function handler(event: Event) {
  emit('abc', (event.target as HTMLInputElement)?.value)
}
</script>

<template>
  <input
    :style="{ backgroundColor }"
    :value="myValue"
    @input="handler" />
  <button @click="$emit('xyz', 'XYZ?!')"></button>
</template>
```

Emits로 발생시킨 이벤트는 부모 컴포넌트에서 `v-on`(`@`) 디렉티브를 사용해 감지할 수 있습니다.
그리고 첨부한 데이터는 핸들러의 첫 번째 인수(템플릿에서는 `$event`)로 전달됩니다.

```vue --path=/src/App.vue
<script setup lang="ts">
import { ref } from 'vue'
import TextField from './components/TextField.vue'

const text = ref('')

function handler(event: string) {
  console.log(event) // 'XYZ?!'
}
</script>

<template>
  <TextField
    my-value="email"
    @abc="text = $event"
    @xyz="handler" />
</template>
```

### Slots

HTML 요소처럼 열리고 닫히는 컴포넌트 태그 사이에 작성한 모든 내용(Contents)은 자식 컴포넌트의 슬롯(Slot)으로 전달됩니다.

```vue --line-active=3-5
<template>
  <MyComponent>
    <h2></h2>
    <div></div>
    <p></p>
  </MyComponent>
</template>
```

#### 기본 슬롯과 대체 콘텐츠

`name` 속성이 없는(이름이 없는) `<slot>` 요소를 기본 슬롯(Default Slot) 혹은 슬롯 아울렛(Slot Outlet)이라고 합니다. 
그리고 컴포넌트 슬롯으로 전달되는 내용이 없을 때, 출력될 대체 내용(Fallback Content)은 열리고 닫히는 <slot> 태그 사이에 작성할 수 있습니다.

```vue --path=/src/components/TheButton.vue
<template>
  <button class="btn">
    <slot>버튼 이름이 없습니다..</slot>
  </button>
</template>
```

```vue --path=/src/App.vue
<script setup lang="ts">
import TheButton from './components/TheButton.vue'
</script>

<template>
  <TheButton />
  <TheButton>클릭하세요!</TheButton>
</template>
```

```html --caption=출력된 결과.
<button class="btn">버튼 이름이 없습니다..</button>
<button class="btn">클릭하세요!</button>
```

#### 이름 슬롯

`<slot>` 요소에 `name` 속성을 추가해 이름을 지정할 수 있으며, 이를 이름이 있는 슬롯(Named Slots)이라고 합니다.
`name` 속성이 없는 `<slot>` 요소의 이름은 `default` 이고 생략 가능합니다.

각 슬롯에 추가할 내용에 `#슬롯이름`으로 이름을 일치시킬 수 있습니다.

```vue --path=/src/components/TheButton.vue
<template>
  <button class="btn">
    <slot name="abc"></slot>
    <slot></slot>
    <slot name="xyz"></slot>
  </button>
</template>

<style scoped>
span {
  display: block;
}
</style>
```

```vue --path=/src/App.vue
<script setup lang="ts">
import TheButton from './components/TheButton.vue'
</script>

<template>
  <TheButton>
    <template #abc>ABC</template>
    <template #default>DEFAULT</template>
    <template #xyz>XYZ</template>
  </TheButton>
</template>
```

혹은, 기본 슬롯은 다음과 같이 이름을 생략할 수 있습니다.

```vue --path=/src/App.vue
<template>
  <TheButton>
    <template #abc>ABC</template>
    DEFAULT
    <template #xyz>XYZ</template>
  </TheButton>
</template>
```

```html --caption=출력된 결과.
<button class="btn">
  ABC
  DEFAULT
  XYZ
</button>
```

#### 범위 슬롯

범위가 지정된 슬롯(Scoped Slots)은 `<slot>` 요소를 통해 데이터를 전달할 수 있는 패턴을 제공합니다.
자식 컴포넌트의 슬롯으로 부모 컴포넌트로 (반응형) 데이터를 전달할 수 있습니다.
단, 그 데이터의 유효 범위(Scoped)는 슬롯 내용(Slot Content)으로 제한됩니다.

```vue --path=/src/components/TheMenu.vue
<script setup lang="ts">
import { ref } from 'vue'

const isShow = ref(false)

function showMenu() {
  isShow.value = true
  window.addEventListener('click', hideMenu)
}
function hideMenu() {
  isShow.value = false
  window.removeEventListener('click', hideMenu)
}
function toggleMenu(event: MouseEvent) {
  event.stopPropagation()
  isShow.value ? hideMenu() : showMenu()
}
</script>

<template>
  <slot
    name="activator"
    :status="isShow"
    :attrs="{ onClick: toggleMenu }"></slot>
  <div
    v-if="isShow"
    class="the-menu"
    @click.stop>
    <slot></slot>
  </div>
</template>
```

```vue --path=/src/App.vue
<script setup lang="ts">
import TheMenu from './components/TheMenu.vue'
</script>

<template>
  <TheMenu>
    <template #activator="{ attrs, status }">
      <button v-bind="attrs">
        메뉴! ({{ status }})
      </button>
    </template>
    <!-- attrs, status 변수는 이곳에서 사용할 수 없습니다! -->
    <ul>
      <li>사과</li>
      <li>바나나</li>
      <li>체리</li>
    </ul>
  </TheMenu>
</template>
```

```html --caption=출력된 결과.
<button>메뉴! (false)</button>
<!-- v-if -->
```

### 폴스루 속성

Props에 정의한 속성은 직접 요소에 연결하지 않으면, 출력되지 않습니다.
반대로 Props에 정의하지 않았지만, 컴포넌트를 사용할 때 작성하는 속성을 폴스루 속성(Fallthrough Attributes)이라고 합니다.

```vue --path=/src/App.vue --caption=부모 컴포넌트에서 자식 컴포넌트로 c와 d 속성을 통해 문자 전달
<script setup lang="ts">
import MyComponent from './components/MyComponent.vue'
</script>

<template>
  <MyComponent
    c="C"
    d="D" />
</template>
```

모든 폴스루 속성은 자동으로 컴포넌트 최상위 요소에 연결(상속, Inheritance)됩니다.

```vue --path=/src/components/MyComponent.vue --caption=단일 최상위 요소만 가지는 컴포넌트
<script setup lang="ts">
// 사용하지 않은, Props로 정의한 속성 a와 b
defineProps<{
  a?: string
  b?: number
}>()
</script>

<template>
  <div>
    <span>Hello!</span>
  </div>
</template>
```

```html --caption=출력된 결과, 단일 최상위 요소에 자동으로 연결된 c와 d 속성.
<div c="C" d="D">
  <span>Hello!</span>
</div>
```

반대로 최상위 요소가 2개 이상 경우, 폴스루 속성은 어떤 요소에도 연결되지 않습니다.

```vue --path=/src/components/MyComponent.vue --caption=다중 최상위 요소를 가지는 컴포넌트
<script setup lang="ts">
defineProps<{
  a?: string
  b?: number
}>()
</script>

<template>
  <div>
    <span>Hello!</span>
  </div>
  <h2>Hi?</h2>
  <p>Greetings~</p>
</template>
```

```html --caption=출력된 결과, 어떤 요소에도 연결되지 않은 c와 d 속성.
<div>
  <span>Hello!</span>
</div>
<h2>Hi?</h2>
<p>Greetings~</p>
```

최상위 요소가 2개 이상일 때, 폴스루 속성을 원하는 요소로 전달하려면 `$attrs` 내장 객체를 `v-bind` 속성으로 연결합니다.

```vue --line-active=10
<script setup lang="ts">
defineProps<{
  a?: string
  b?: number
}>()
</script>

<template>
  <div>
    <span v-bind="$attrs">Hello!</span>
  </div>
  <h2>Hi?</h2>
  <p>Greetings~</p>
</template>
```

```html --caption=출력된 결과, 원하는 요소에 연결된 c와 d 속성.
<div>
  <span c="C" d="D">Hello!</span>
</div>
<h2>Hi?</h2>
<p>Greetings~</p>
```

필요한 경우, 최상위 요소가 하나라도 폴스루 속성이 자동으로 연결되지 않도록 처리할 수 있습니다.

```vue --path=/src/components/MyComponent.vue --line-active=6-8
<script setup lang="ts">
defineProps<{
  a?: string
  b?: number
}>()
defineOptions({
  inheritAttrs: false // 폴스루 속성의 상속 옵션 OFF
})
</script>

<template>
  <div>
    <span>Hello!</span>
  </div>
</template>
```

폴스루 속성은 스크립트에서도 접근할 수 있습니다.
그리고 `attrs`(`$attrs`) 객체는 `onClick`과 같이 이벤트를 포함합니다.(Props는 포함하지 않습니다)

```vue --path=/src/App.vue --line-active=13-15
<script setup lang="ts">
import MyComponent from './components/MyComponent.vue'

function handler() {
  console.log('Clicked!!')
}
</script>

<template>
  <MyComponent
    a="A"
    :b="2"
    c="C"
    d="D"
    @click="handler" />
</template>
```

```vue --path=/src/components/MyComponent.vue
<script setup lang="ts">
import { useAttrs } from 'vue'

defineProps<{
  a?: string
  b?: number
}>()

const attrs = useAttrs()
console.log(attrs) // 출력!
</script>

<template>
  <div>
    <span>Hello!</span>
  </div>
</template>
```

```js --caption=출력된 결과.
{
  c: "C",
  d: "D",
  onClick: f handler()
}
```

### 양방향 데이터 바인딩(v-model)

부모 컴포넌트에서 정의된 반응형 데이터를 Props로 전달하면, 자식 컴포넌트에서는 읽기 전용으로만 사용할 수 있습니다.
만약, 반응형 데이터를 수정하려면, 쓰기 권한을 가진 부모 컴포넌트로 Emits을 사용해 (커스텀) 이벤트 발생과 데이터를 전달하는 패턴이 필요합니다.
이 패턴에서 사용하는 Props와 Emits 이름은 무엇이든 가능합니다.

```vue --path=/src/components/TextField.vue --line-error=3,6,14,15 --caption='abc' Prop의 수정을 위해 'xyz' 커스텀 이벤트 발생
<script setup lang="ts">
defineProps<{
  abc: string
  label?: string
}>()
defineEmits(['xyz'])
</script>

<template>
  <label>
    {{ label }}
    <input
      v-bind="$attrs"
      :value="abc"
      @input="$emit('xyz', ($event.target as HTMLInputElement)?.value)" />
  </label>
</template>

<style scoped>
label {
  display: block;
}
</style>
```

```vue --path=/src/App.vue --line-error=16,19,21,25
<script setup lang="ts">
import { ref } from 'vue'
import TextField from './components/TextField.vue'

const email = ref('')
const password = ref('')

function signIn() {
  console.log('로그인 정보:', email.value, password.value)
}
</script>

<template>
  <form @submit.prevent="signIn">
    <TextField
      :abc="email"
      label="이메일"
      autocomplete="username"
      @xyz="email = $event" />
    <TextField
      :abc="password"
      label="비밀번호"
      type="password"
      autocomplete="current-password"
      @xyz="password = $event" />
    <button type="submit">로그인</button>
  </form>
</template>
```

만약 Props와 Emits 이름을 (Vue에서 약속된) `modelValue`와 `update:modelValue`로 지정하면, 축약형으로 `v-model` 디렉티브를 사용할 수 있습니다.

```vue --path=/src/components/TextField.vue --line-active=3,6,14,15
<script setup lang="ts">
defineProps<{
  modelValue: string
  label?: string
}>()
defineEmits(['update:modelValue'])
</script>

<template>
  <label>
    {{ label }}
    <input
      v-bind="$attrs"
      :value="modelValue"
      @input="$emit('update:modelValue', ($event.target as HTMLInputElement)?.value)" />
  </label>
</template>

<style scoped>
label {
  display: block;
}
</style>
```

```vue --path=/src/App.vue --line-active=8,12
<script setup lang="ts">
// 생략..
</script>

<template>
  <form @submit.prevent="signIn">
    <TextField
      v-model="email"
      label="이메일"
      autocomplete="username" />
    <TextField
      v-model="password"
      label="비밀번호"
      type="password"
      autocomplete="current-password" />
    <button type="submit">로그인</button>
  </form>
</template>
```

### 동적 컴포넌트

`<component :is="컴포넌트" />` 방식의 특수 요소(Special Element)를 활용해 동적으로 컴포넌트를 출력할 수 있습니다.

/// message-box --icon=info --color=info
`<component>`, `<slot>`, `<template>`는 Vue에서 사용하는 특수한 기능의 내장 요소들입니다.
///

```vue --path=/src/App.vue --caption=버튼을 선택할 때마다 동적으로 변경(출력)되는 컴포넌트
<script setup lang="ts">
import { ref } from 'vue'
import type { Component } from 'vue'
import Home from './components/Home.vue'
import About from './components/About.vue'
import Posts from './components/Posts.vue'

interface Tabs {
  [key: string]: Component // 인덱스 시그니처!
}

const currentTab = ref('Home')
const tabs: Tabs = {
  Home,
  About,
  Posts
}
function changeTab(tab: string | number) {
  if (typeof tab === 'string') {
    currentTab.value = tab
  }
}
</script>

<template>
  <button
    v-for="(_, tab) in tabs"
    :key="tab"
    @click="changeTab(tab)">
    {{ tab }}
  </button>
  <component :is="tabs[currentTab]" />
</template>
```

### Provide / Inject

앞서 살펴본 것처럼, 부모에서 자식 컴포넌트로 데이터를 전달할 때는 Props 방식을 사용합니다.
그런데 만약 부모와 자식 관계 이상으로 상위에서 하위 컴포넌트로 데이터를 한 번에 전달하려면, 부모-자식 단계를 거쳐 데이터를 전달해야 하는 Props 대신, Provide / Inject 방식을 사용할 수 있습니다.

```ts
// 상위 컴포넌트
provide(이름, 데이터)

// 하위 컴포넌트
const 데이터 = inject(이름)
```

다음은 자식 컴포넌트를 거치지 않고, 바로 하위 컴포넌트로 데이터를 전달하는 예제입니다.
주의할 점은, 반응성을 유지하기 위해 `count.value`와 같이 단순히 값을 전달하는 것이 아닌 `count`와 같이 반응형 데이터를 전달해야 합니다.

/// message-box --icon=info --color=info
`ref()`, `reactive()`, `computed()` 등의 모든 반응형 데이터는 반응성을 유지할 수 있습니다.
///

```vue --path=/src/App.vue
<script setup lang="ts">
import { ref, provide } from 'vue'
import Parent from './components/Parent.vue'

const count = ref(0)
provide('count', count)
</script>

<template>
  <button @click="count += 1">
    증가!
  </button>
  <Parent />
</template>
```

```vue --path=/src/components/Parent.vue
<script setup lang="ts">
import Child from './Child.vue'
</script>

<template>
  <Child />
</template>
```

```vue --path=/src/components/Child.vue
<script setup lang="ts">
import { inject } from 'vue'

const count = inject('count')
</script>

<template>
  <h2>{{ count }}</h2>
</template>
```

`inject()` 함수로 주입하는 데이터는 기본적으로 `unknown` 타입입니다.
물론 제네릭을 사용해 타입을 지정할 수 있지만, 런타임에 이 값이 제공된다는 보장이 없으므로 주입된 값은 여전히 `undefined`가 될 수 있습니다.

```vue --path=/src/components/Child.vue --line-error=8
<script setup lang="ts">
import { inject } from 'vue'
import type { Ref } from 'vue'

const count = inject<Ref<number>>('count')
// const count: Ref<number> | undefined

console.log(count.value) // Error! - 'count'은(는) 'undefined'일 수 있습니다.ts(18048)
</script>

<template>
  <h2>{{ count }}</h2>
</template>
```

따라서 타입 가드를 추가하거나,
만약 값이 항상 제공된다고 확신한다면, 타입을 단언(Assertion)할 수도 있습니다.

```ts --path=/src/components/Child.vue --caption=타입 가드를 추가한 경우.
const count = inject<Ref<number>>('count')

if (count && typeof count.value === 'number') {
  console.log(count.value)
}
```

```ts --path=/src/components/Child.vue --caption=타입을 단언한 경우.
const count = inject('count') as Ref<number>

console.log(count.value)
```

`provide()` 함수로 제공할 데이터를 객체 형태로 전달하면, 여러 데이터를 한 번에 전달할 수 있습니다.
다음과 같이 반응형 데이터를 변경하는 함수를 같이 제공해, 하위 요소에서 사용할 수도 있습니다.

```vue --path=/src/App.vue
<script setup lang="ts">
import { ref, provide } from 'vue'
import Parent from './components/Parent.vue'

const count = ref(0)

provide('App.vue', {
  count,
  increase
})
// 제공 데이터의 타이핑!
export interface Provide {
  count: typeof count
  increase: typeof increase
}

function increase() {
  count.value += 1
}
</script>

<template>
  <button @click="increase">증가!(App)</button>
  <Parent />
</template>
```

```vue --path=/src/components/Child.vue --caption=Child 컴포넌트의 '증가!'' 버튼은 잘 동작합니다.
<script setup lang="ts">
import { inject } from 'vue'
import type { Provide } from '../App.vue'

const { count, increase } = inject('App.vue') as Provide
</script>

<template>
  <button @click="increase">증가!(Child)</button>
  <h2>{{ count }}</h2>
</template>
```