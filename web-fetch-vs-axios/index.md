---
id: QOWqjV
filename: web-fetch-vs-axios
image: https://heropy.dev/postAssets/QOWqjV/main.jpg
title: 데이터 통신을 위한, Fetch 함수와 Axios 라이브러리
createdAt: 2023-12-16
group: Web
author:
  - ParkYoungWoong
tags:
  - JS
  - Fetch
  - Axios
description:
  서버와 클라이언트 간의 데이터 통신은 웹 개발의 핵심 개념 중 하나로, 자바스크립트에서의 데이터 통신을 위한 fetch 함수와 axios 라이브러리의 사용법을 알아봅니다.
---

서버와 클라이언트 간의 데이터 통신은 웹 개발의 핵심 개념 중 하나로, 자바스크립트에서의 데이터 통신을 위한 Fetch 함수와 Axios 라이브러리를 비교하고 각 사용법을 알아봅니다.

Fetch는 웹 브라우저에서 사용할 수 있는 내장 함수로, HTTP 통신으로 서버로부터 데이터를 가져올 수 있습니다.
Axios는 `fetch` 함수와 같이 HTTP 통신을 위한 자바스크립트 라이브러리로, 여러 편리한 기능을 제공합니다.

## 데이터 통신

클라이언트-서버 모델(Client-Server Model)은 통신의 기본적인 구조입니다. 
클라이언트가 서버에 정보를 요청(Request)하면, 서버는 이러한 요청에 응답(Response)하고 이때, HTTP(HyperText Transfer Protocol)를 사용합니다.

/// message-box --icon=info
HTTP는 웹에서 데이터를 주고받기 위한 통신 규약(Protocol)입니다.
///

![클라이언트-서버 모델(Client-Server Model)](./assets/s1.jpg)

요청과 응답은 다음과 같은 정보를 기본적으로 포함합니다.

- **요청(Request)**:
  - **url**: 요청 서버 주소
  - **method**: 요청 종류(GET, POST, PUT, DELETE 등)
  - **headers**: 요청 메타 정보
  - **body**: 요청 데이터

- **응답(Response)**:
  - **status**: 응답 상태 코드(200, 400, 500 등)
  - **headers**: 응답 메타 정보
  - **body**: 응답 데이터
  - **ok**: 정상적인 처리 여부

### URL

URL은 특정 자원이 인터넷 상의 어디에 위치하는지를 나타내는 주소입니다.
다음과 같은 구조를 가지고 있습니다.

![URL 구조](./assets/s2.jpg)

### Method

`method`는 요청의 종류를 나타내며, 주로 다음과 같이 사용됩니다.

/// message-box --icon=info
각 메소드의 의미는 관례적(Convention)이며, 엄격한 표준은 아닙니다.
서버 개발 방식에 따라 의미에 차이가 있을 수 있습니다.
///

- **GET**: 데이터 조회
- **POST**: 데이터 생성
- **PUT** / **PATCH**: 데이터 수정 (전체/일부)
- **DELETE**: 데이터 삭제

같은 URL이라도 요청 종류(Method)에 따라 서버의 처리 내용과 응답 결과가 달라집니다.
또한 서버에서 지원하지 않는 메소드는 사용할 수 없습니다.

```js
// 모든 사용자 조회
fetch('https://example.dev/users', {
  method: 'GET' // 혹은 생략 가능!
})

// 새로운 사용자 생성
fetch('https://example.dev/users', {
  method: 'POST',
  headers: {
    'Content-type': 'application/json'
  },
  body: JSON.stringify({
    name: 'HEROPY',
    age: 85
  })
})

// 모든 사용자 삭제
fetch('https://example.dev/users', {
  method: 'DELETE'
})
```

### Headers

`headers`는 요청과 응답에 대한 메타 정보(Metadata)를 포함합니다.
메타 정보는 데이터 타입, 인코딩 방식, 인증 정보, 캐시 제어 등의 다양한 정보를 포함할 수 있습니다.
다음과 같이 객체 형태로 작성합니다.

```js
fetch('https://example.dev/users', {
  headers: {
    'Content-type': 'application/json',
    Apikey: 'KDnREmPe9B1',
    Username: 'ParkYoungWoong',
    Authorization: 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjlQS3I...',
    'X-Username': 'ParkYoungWoong',
    '...'
  }
})
```

`X-Frame-Options`, `X-Username`과 같이 `X-` 접두사가 포함된 헤더 정보는 사용자 정의 비표준 헤더입니다.
공식적인 HTTP 사양이 아니며, 개발자나 조직 내에서 특정한 목적이나 의미로 구분하기 위함입니다.
IETF(Internet Engineering Task Force)에서는 `X-` 접두사 없이 커스텀 헤더를 사용할 것을 권장하고 있습니다.

### Body

`body`는 요청과 응답으로 전송하고자 하는 본문(실제 데이터)입니다.
주로, 문자(JSON)나 [FormData](https://developer.mozilla.org/ko/docs/Web/API/FormData)를 전송합니다.

```js
fetch('https://example.dev/users', {
  method: 'POST',
  headers: {
    'Content-type': 'application/json'
  },
  // 생성할 사용자 정보(데이터)
  body: JSON.stringify({
    name: 'HEROPY',
    age: 85
  })
})
```

### Status

`status`는 요청에 대한 응답 상태 코드를 나타냅니다.
HTTP 상태 코드는 다음과 같이 5가지 범주로 나뉩니다.

- **1xx**: 처리 중(Processing)
- **2xx**: 성공
- **3xx**: 리다이렉션(Redirection)
- **4xx**: 클라이언트 오류
- **5xx**: 서버 오류

자주 볼 수 있는 상태 코드는 다음과 같습니다.

- **200**: 정상적으로 처리됨
- **400**: 잘못된 요청
- **401**: 인증 정보가 부족함
- **403**: 권한이 없음
- **404**: 찾을 수 없음
- **500**: 서버 오류

![404 Page Not Found 예시](./assets/s3.jpg)

## Fetch vs Axios

`fetch`는 2015년부터 웹 브라우저에서 지원하기 시작한 Web API 입니다.
`Promise` 기반으로 비동기 통신을 지원하며, 별도의 설치 없이 바로 사용할 수 있습니다.

```js
fetch(`https://jsonplaceholder.typicode.com/users`)
  .then(res => res.json())
  .then(data => console.log(data)) // User[]
```

`axios`는 2015년 경에 첫 릴리즈된 HTTP 클라이언트 라이브러리입니다. 
`fetch`와 마찬가지로 `Promise` 기반으로 비동기 통신을 지원합니다.
각 웹 브라우저의 하위호환성(Cross-Browser Compatibility)뿐만 아니라, 자동 JSON 데이터 변환이나 서버 측 지원 등의 추가 기능을 제공합니다.

CDN으로 연결하거나,

```html --caption=CDN
<script src="https://cdn.jsdelivr.net/npm/axios@1.6.2/dist/axios.min.js"></script>
```

NPM으로 설치해서 사용할 수 있습니다.

```bash --caption=NPM
$ npm i axios
```

```js
import axios from 'axios'

axios.get(`https://jsonplaceholder.typicode.com/users`)
  .then(res => console.log(res.data)) // User[]
```

`fetch`와 `axios`는 모두 현대적인 웹 개발에서 데이터 통신을 위해 널리 사용되지만, 각 장점과 사용 방식이 다릅니다.
간단하게, `fetch`는 별도의 설치 없이 바로 사용할 수 있으며, `axios`는 보다 풍부한 기능과 간결한 API를 제공합니다.

[JSONPlaceholder](https://jsonplaceholder.typicode.com/)를 사용하는 간단한 CRUD(Create / Read / Update / Delete) 예제를 통해, `fetch`와 `axios`의 사용법을 비교해보겠습니다.

### 데이터 조회

조회(Read)할 데이터를 가져올 때는, 주로 `GET` 메소드를 사용합니다.

`fetch` 함수는 `GET` 메소드를 기본값으로 사용하므로, 별도의 옵션을 지정하지 않아도 됩니다.
가져온 데이터는 `.json()`을 통해 분석(Parsing)해야 합니다.

```js --caption=fetch
;(async () => {
  // const res = await fetch('https://jsonplaceholder.typicode.com/posts', { method: 'GET' })
  const res = await fetch('https://jsonplaceholder.typicode.com/posts')
  const data = await res.json()
  console.log(data)
})()
```

`axios` 또한 `GET` 메소드를 기본값으로 사용하므로, 별도의 옵션을 지정하지 않아도 됩니다.
그리고 `.get()`, `.post()` 같이 각 HTTP 메소드에 대한 별도의 메소드(함수)를 제공하므로, 명시적으로 사용하는 것도 좋습니다.
가져온 데이터는 응답 객체의 `data` 속성을 통해 접근할 수 있습니다.

```js --caption=axios
import axios from 'axios'

;(async () => {
  // const res = await axios({ url: 'https://jsonplaceholder.typicode.com/posts', method: 'GET' })
  // const res = await axios.get('https://jsonplaceholder.typicode.com/posts')
  const res = await axios('https://jsonplaceholder.typicode.com/posts')
  console.log(res.data)
})()
```

조회(Read)는 데이터를 보내는 것이 아니므로, 보낼 데이터를 포함하지 않아야 합니다.
`fetch` 함수는 `body` 옵션을 생략하거나, 명시적으로 `null` 혹은 `undefined`를 지정해야 하며, 다른 값을 지정하면 오류가 발생합니다.

/// message-box --icon=error
Error: Failed to execute 'fetch' on 'Window': Request with GET/HEAD method cannot have body.
///

`axios` 또한 보낼 데이터를 지정하지 않아야 하지만, 데이터가 있어도 생략하고 전송합니다.

만약, 조회(Read)를 위한 세부 정보를 요청에 포함하고 싶다면, 쿼리스트링(Query String)을 사용할 수 있습니다.
대표적으로 영화 정보를 제공하는 [OMDbAPI](http://www.omdbapi.com/)를 사용할 수 있습니다.

`fetch`는 URL에 직접 쿼리스트링을 포함하거나,

```js --caption=fetch
;(async () => {
  const res = await fetch('https://omdbapi.com/?apikey=7035c60c&s=avengers', {
    method: 'GET'
  })
  const data = await res.json()
  console.log(data)
})()
```

쿼리 정보를 객체 형식으로 가진 경우, `URLSearchParams` 클래스를 사용할 수도 있습니다.

```js --caption=fetch w. URLSearchParams
const queries = new URLSearchParams({
  apikey: '7035c60c',
  s: 'avengers'
})
console.log(queries.toString()) // 'apikey=7035c60c&s=avengers'

;(async () => {
  const res = await fetch(`https://omdbapi.com/?${queries}`, {
    method: 'GET'
  })
  const data = await res.json()
  console.log(data)
})()
```

`axios` 또한 URL에 직접 쿼리스트링을 포함하거나, `params` 옵션으로 객체 형식의 쿼리 정보를 전달할 수 있습니다.

```js --caption=axios
;(async () => {
  const res = await axios.get(`https://omdbapi.com/?apikey=7035c60c&s=avengers`)
  console.log(res.data)
})()

;(async () => {
  const res = await axios({
    url: `https://omdbapi.com/`,
    method: 'GET',
    params: {
      apikey: '7035c60c',
      s: 'avengers'
    }
  })
  console.log(res.data)
})()
```

### 데이터 생성 및 수정

생성하거나 수정할 데이터를 보낼 때는 주로 `POST`나 `PUT` 메소드를 사용합니다.
`POST`는 생성(Create)을, `PUT`이나 `PATCH`는 수정(Update)을 위해 사용합니다.

`fetch` 함수는 `body` 옵션을 사용하여 데이터를 전송합니다.
전송할 데이터의 타입을 `application/json`으로 지정 후, `JSON.stringify` 메소드를 통해 문자로 변환해 `body`에 포함합니다.

```js
;(async () => {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      title: 'Hello world!',
      body: 'The quick brown fox jumps over the lazy dog.',
      userId: 1
    })
  })
  const data = await res.json()
  console.log(data)
})()
```

`axios`는 `body`가 아닌 `data` 옵션을 사용합니다.
별도의 문자화 작업이 필요하지 않고, 자동으로 JSON 문자로 변환합니다.

```js
;(async () => {
  const res = await axios({
    url: 'https://jsonplaceholder.typicode.com/posts',
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    data: {
      title: 'Hello world!',
      body: 'The quick brown fox jumps over the lazy dog.',
      userId: 1
    }
  })
  console.log(res.data)
})()
```

데이터를 수정하는 경우, `PUT`이나 `PATCH` 메소드를 사용할 수 있습니다.
이때, 어떤 데이터를 수정할 것인지 식별하기 위해 그 데이터의 ID를 제공해야 합니다.
URL이나 헤더, 바디 등 명세에 따라 다양한 방식으로 전달할 수 있습니다.

/// message-box --icon=info
`PUT`과 `PATCH`는 모두 수정이라는 의미를 가지고 있지만, `PUT`은 전체 데이터를 수정, `PATCH`는 일부 데이터만 수정한다는 의미를 가집니다.
따로 의미를 구분하지 않고 `PUT`만 사용하는 경우도 많습니다.
///

다음 예제에서는, 수정할 게시물의 ID(`2`)를 URL에 포함하고 있습니다.

```js --line-active=3
;(async () => {
  const res = await axios({
    url: 'https://jsonplaceholder.typicode.com/posts/2',
    method: 'PUT',
    headers: {
      'Content-Type': 'application/json',
    },
    data: {
      title: 'Hello World!',
      body: 'The quick brown fox jumps over the lazy dog.',
      userId: 1
    }
  })
  console.log(res.data)
})()
```

### 데이터 삭제

데이터를 삭제하는 경우, `DELETE` 메소드를 사용할 수 있습니다.
수정과 마찬가지로, 어떤 데이터를 삭제할 것인지 식별하기 위해 그 데이터의 ID를 명세에 따라 제공해야 합니다.

```js --caption=fetch
;(async () => {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts/2', {
    method: 'DELETE'
  })
  const data = await res.json()
  console.log(data)
})()
```

```js --caption=axios
;(async () => {
  const res = await axios({
    url: 'https://jsonplaceholder.typicode.com/posts/2',
    method: 'DELETE'
  })
  console.log(res.data)
})()
```

### 파일 전송

클라이언트에서 서버로 파일을 전송하는 경우, FormData를 사용하거나 파일을 Base64 문자로 변환하는 등 여러 방식을 사용할 수 있습니다.

#### FormData

Web API인 `FormData`는, HTML `<form>`을 통해 서버로 전송할 수 있는 양식 데이터를 생성합니다.
`new FormData()` 생성자 함수 호출로 반환된 인스턴스(`formData`)에서, `append` 메소드를 사용해 이름과 데이터를 명시적으로 추가할 수 있습니다.

```js --caption=FormData 생성
const formData = new FormData()
// formData.append('이름', 데이터)
formData.append('id', userId)
formData.append('pw', userPw)
formData.append('file', file)
// ...
```

```js --line-active=9
let file = null
document.querySelector('input[type="file"]')
  .addEventListener('change', event => {
    file = event.target.files[0]
  })
document.querySelector('button')
  .addEventListener('click', async () => {
    if (!file) return
    sendFile(file)
  })
```

```js --caption=fetch
async function sendFile(file) {
  const formData = new FormData()
  formData.append('file', file)

  const res = await fetch('URL주소', {
    method: '메소드',
    // headers: { 'Content-Type': 'multipart/form-data' }, // 생략 가능!
    body: formData
  })
  return await res.json()
}
```

```js --caption=axios
async function sendFile(file) {
  const formData = new FormData()
  formData.append('file', file)

  const res = await axios({
    url: 'URL주소',
    method: '메소드',
    // headers: { 'Content-Type': 'multipart/form-data' }, // 생략 가능!
    data: formData
  })
  return res.data
}
```

`<form>`을 활용하는 경우, `append` 메소드 없이 데이터를 추가할 수 있습니다.
단, `<input>`의 `name` 속성을 추가해서 데이터의 이름을 명시해야 합니다.

```html
<form>
  <input type="text" autocomplete="username" name="id" />
  <input type="password" autocomplete="current-password" name="pw" />
  <input type="file" name="file" />
  <button type="submit">전송</button>
</form>
```

```js --line-active=3,5
document.querySelector('form')
  .addEventListener('submit', async event => {
    event.preventDefault() // 페이지가 새로고침되지 않도록 기본 동작 방지!

    const formData = new FormData(event.target) // `<form>` 요소 참조를 전달!
    const res = await axios({
      url: 'URL주소',
      method: '메소드',
      data: formData
    })
    return res.data
  })
```

`formData`에 포함된 데이터는 다음과 같이 확인할 수 있습니다.

```js
formData.get('이름') // '이름'과 일치하는, 단일 데이터 확인!
formData.getAll('이름') // '이름'과 일치하는, 모든 데이터를 배열로 확인!
// ...

// 모든 데이터 확인!
for (const [key, value] of formData) {
  console.log(key, value)
}
```

#### JSON 문자

Base64를 활용해, 파일을 문자로 전송할 수도 있습니다.

/// message-box --icon=info
Base64는 바이너리 데이터를 텍스트 형식으로 인코딩하는 방법입니다.
이메일이나 URL 등 텍스트로만 정보를 전송하는 경우 유용하지만, 변환된 데이터의 크기가 원본보다 더 커지는 단점이 있습니다.
///

앞서 살펴본 FormData 예제에서, 파일을 Base64 문자로 변환하는 비동기 함수(`toBase64`)를 추가로 작성합니다.

```js
function toBase64(file) {
  return new Promise((resolve, reject) => {
    const reader = new FileReader()
    reader.readAsDataURL(file)
    reader.onload = () => resolve(reader.result)
    reader.onerror = error => reject(error)
  })
}
```

그리고 `sendFile` 함수에서 파일을 받아 Base64로 변환 후 전송합니다.

```js --line-active=2,9 --caption=fetch
async function sendFile(file) {
  const base64 = await toBase64(file)
  const res = await fetch('URL주소', {
    method: '메소드',
    headers: {
      'Content-Type': 'application/json' 
    },
    body: JSON.stringify({ 
      file: base64 
    })
  })
  return await res.json()
}
```

```js --line-active=2,10 --caption=axios
async function sendFile(file) {
  const base64 = await toBase64(file)
  const res = await axios({
    url: 'URL주소',
    method: '메소드',
    headers: { 
      'Content-Type': 'application/json' 
    },
    data: {
      file: base64
    }
  })
  return res.data
}
```

### 에러 처리

`fetch` 함수는 응답 상태에 대해 약속(Promise)을 거부(Reject)하지 않습니다.
오직 네트워크 실패나 요청이 완전히 불가능한 경우에만 거부합니다.

예를 들어, 다음과 같이 [OMDbAPI](http://www.omdbapi.com/)에서 API Key를 제공하지 않고 요청하는 경우, `401 Unauthorized` 오류가 발생합니다.
하지만 `fetch` 함수는 상태 코드(401)에 대해 약속을 거부하지 않으므로, `catch` 구문은 실행되지 않습니다.

```js --line-active=3 --line-error=6-8
;(async () => {
  try {
    const res = await fetch('https://omdbapi.com/?apikey=&s=avengers') // Error: 401 Unauthorized!
    const data = await res.json()
    console.log(data) // { Response: 'False', Error: 'No API key provided.' }
  } catch (err) {
    console.error('Error:', err)
  }
})()
```

따라서 다음과 같이 응답 객체의 속성을 명세에 맞게 확인한 후, 에러를 수동으로 처리해야 합니다.

```js --line-active=3,5-7
;(async () => {
  try {
    const res = await fetch('https://omdbapi.com/?apikey=&s=avengers') // Error: 401 Unauthorized!
    const data = await res.json() // { Response: 'False', Error: 'No API key provided.' }
    if (data.Response === 'False') {
      return console.error(data.Error) // 'No API key provided.'
    }
    console.log(data)
  } catch (err) {
    console.error('Error:', err)
  }
})()
```


`axios`는 정상 처리(2xx)가 아닌 응답 상태 코드에 대해 자동으로 약속(Promise)을 거부(Reject)하기 때문에 사용이 편리합니다.

```js --line-active=3,5-7
;(async () => {
  try {
    const res = await axios('https://omdbapi.com/?apikey=&s=avengers') // Error: 401 Unauthorized!
    console.log(res.data)
  } catch (err) {
    console.error('Error:', err) // { name: 'AxiosError', message: 'Request failed with status code 401', ... }
  }
})()
```

### 시간 초과

네트워크 요청에서 특정 시간 이내에 응답이 오지 않으면, 요청을 중단할 수 있습니다.
이를 통해, 무한 대기 현상을 방지하고, 불필요한 네트워크 트래픽을 줄이는 효과를 얻을 수 있습니다.

/// message-box --icon=info
웹 브라우저는 기본적으로 특정 시간 이상(1~5분)의 시간 초과(Timeouts)를 허용하지 않습니다.
///

`fetch` 함수는 기본적으로 시간 초과 설정이 없으므로, 별도의 작업이 필요합니다.
다음과 같이 `Promise.race` 정적 메소드를 통해, 먼저 처리되는 약속을 반환하도록 함수를 작성하고 사용할 수 있습니다.

```js --line-active=1,16 --caption=fetch
function fetchWithTimeout(url, options, timeout = 1000) {
  return Promise.race([
    fetch(url, options),
    new Promise((_, reject) =>
      setTimeout(() => reject(new Error('Request timed out!')), timeout)
    )
  ])
}

;(async () => {
  try {
    await fetchWithTimeout('URL주소', {
      method: '메소드',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ name: 'HEROPY' })
    }, 3000)
  } catch (err) {
    console.error('Error:', err)
  }
})()
```

`axios`는 `timeout` 옵션을 통해 시간 초과 설정을 쉽게 추가할 수 있습니다.

```js --line-active=8 --caption=axios
;(async () => {
  try {
    await axios({
      url: 'URL주소',
      method: '메소드',
      headers: { 'Content-Type': 'application/json' },
      data: { name: 'HEROPY' },
      timeout: 3000 // 3초
    })
  } catch (err) {
    console.error('Error:', err)
  }
})()
```

### 요청 취소

필요한 경우, 언제든지 네트워크 요청을 취소할 수 있습니다.
이를 통해, 불필요한 네트워크 트래픽을 줄이고 불필요한 응답을 처리하지 않아도 됩니다.

`fetch` 함수는 요청 취소를 위해 `AbortController`를 사용해야 합니다.
`new AbortController()` 생성자 함수 호출로 반환된 인스턴스(`controller`)에서, `signal` 속성을 사용해 `fetch` 함수의 옵션으로 전달합니다
필요할 때, `controller.abort()` 메소드를 호출해 요청을 취소할 수 있습니다.

```js --line-active=1,9,14-16,23
const controller = new AbortController()

;(async () => {
  try {
    const res = await fetch('URL주소', { 
      method: '메소드',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ name: 'HEROPY' }),
      signal: controller.signal
    })
    const data = await res.json()
    console.log(data)
  } catch (err) {
    if (err.name === 'AbortError') {
      console.log('요청이 취소되었습니다!')
    }
    console.error(err)
  }
})()

document.querySelector('button.cancel')
  .addEventListener('click', () => {
    controller.abort() // 요청 취소!
  })
```

`axios`도 사용 방법이 같습니다.

/// message-box --icon=info
`axios.CancelToken`을 사용하는 방식이 내장되어 있었지만, `0.22.0` 버전부터 더 이상 사용되지 않습니다.
///

```js --line-active=1,10,14-16,23
const controller = new AbortController()

;(async () => {
  try {
    const res = await axios({ 
      url: 'URL주소',
      method: '메소드',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ name: 'HEROPY' }),
      signal: controller.signal
    })
    console.log(res.data)
  } catch (err) {
    if (err.name === 'AbortError') {
      console.log('요청이 취소되었습니다!')
    }
    console.error(err)
  }
})()

document.querySelector('button.cancel')
  .addEventListener('click', () => {
    controller.abort()
  })
```

### 자격 증명

서버에 요청을 보낼 때, 사용자의 인증 정보를 포함해 전송하는 것을 '자격 증명(Credentials)'이라고 합니다.
API 명세에 따라, 쿠키(Cookies)와 기본 인증 헤더(Basic Authorization Header) 등을 자동으로 포함해 전송할 수도 있습니다.

/// message-box --icon=warning
자격 증명을 포함하는 경우, 중간자 공격에 노출되지 않도록, 반드시 HTTPS를 사용해야 합니다.
///

`fetch` 함수는 `credentials` 옵션을 통해 자격 증명의 자동 전송 여부를 지정할 수 있습니다.
기본값(Default Value)은 자격 증명을 전송하지 않는 `omit`이며, `include`로 지정하면 자격 증명을 포함해 전송합니다.
(동일 출처일 때만 전송하려면, `same-origin`)

```js --line-active=6 --caption=fetch
;(async () => {
  const res = await fetch('URL주소', {
    method: '메소드',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ name: 'HEROPY' }),
    credentials: 'include'
  })
  const data = await res.json()
  console.log(data)
})()
```

`axios`는 `withCredentials` 옵션을 통해 자격 증명의 자동 전송 여부를 지정합니다.
기본값은 `false`입니다.

```js --line-active=7 --caption=axios
;(async () => {
  const res = await axios({
    url: 'URL주소',
    method: '메소드',
    headers: { 'Content-Type': 'application/json' },
    data: { name: 'HEROPY' },
    withCredentials: true
  })
  console.log(res.data)
})()
```

수동으로 포함하고 싶은 경우, 다음과 같이 헤더 정보를 직접 추가할 수도 있습니다.
역시 API 명세에 따라 다릅니다.

/// message-box --icon=info
`Authorization: 'Bearer ...'`는 JWT(JSON Web Tokens) 등과 같은 현대적인 인증 메커니즘에서 널리 사용되는 방식입니다.
`Bearer`(지위를 가진 사람)는 토큰을 소유한 사용자가 자원에 접근할 수 있음을 의미합니다.
///

```js --line-active=7
;(async () => {
  const res = await axios({
    url: 'URL주소',
    method: '메소드',
    headers: {
      'Content-Type': 'application/json',
      Authorization: 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjlQS3I...',
    },
    data: { name: 'HEROPY' }
  })
  console.log(res.data)
})()
```

### 사용자 정의 구성

사용자 정의 구성을 사용해, 요청과 관련된 코드를 간결하고 관리하기 쉽게 만들 수 있습니다.

`fetch` 함수는 다음과 같이 원하는대로 구성을 만들고 재사용할 수 있습니다.

```js --caption=fetch
function api(method, endpoint, data) {
  const url = 'https://api.heropy.dev' + endpoint
  const timeout = 2000
  const options = {
    method,
    headers: {
      Apikey: 'KDnREmPe9B1',
      Username: 'ParkYoungWoong'
    },
    body: data ? JSON.stringify(data) : null
  }
  return Promise.race([
    fetch(url, options),
    new Promise((_, reject) =>
      setTimeout(() => reject(new Error('Request timed out!')), timeout)
    )
  ])
}

api('GET', '/users')
api('POST', '/users', {
  name: 'HEROPY',
  age: 85
})
api('PUT', `/users/${userId}`, {
  age: 127
})
api('DELETE', `/users/${userId}`)
```

`axios`는 `axios.create` 함수를 통해 보다 쉽게 사용자 정의 구성을 만들 수 있습니다.

```js --caption=axios
const api = axios.create({
  baseURL: 'https://api.heropy.dev',
  timeout: 2000,
  headers: {
    Apikey: 'KDnREmPe9B1',
    Username: 'ParkYoungWoong'
  }
})

api.get('/users')
api.post('/users', {
  name: 'HEROPY',
  age: 85
})
api.put(`/users/${userId}`, {
  age: 127
})
api.delete(`/users/${userId}`)
```

### Node.js 지원

Node.js 환경에서도 데이터 통신을 위한 도구로 `fetch`와 `axios`를 사용할 수 있습니다.
단, `fetch` 함수는 Web API이기 때문에 별도 구현이 필요하고, `node-fetch` 패키지를 설치해 Node.js 환경에서도 `fetch` 함수를 사용할 수 있습니다.

```bash
$ npm i node-fetch
```

```js --caption=fetch
import fetch from 'node-fetch'

fetch(`https://jsonplaceholder.typicode.com/users`)
  .then(res => res.json())
  .then(data => console.log(data)) // User[]
```

`axios`는 Node.js 환경도 지원하므로, 동일하게 설치해서 사용할 수 있습니다.

```bash
$ npm i axios
```

```js --caption=axios
import axios from 'axios'

axios.get(`https://jsonplaceholder.typicode.com/users`)
  .then(res => console.log(res.data)) // User[]
```




