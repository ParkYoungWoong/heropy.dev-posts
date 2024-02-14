---
image: https://heropy.dev/postAssets/71PGfA/main.jpg
filename: api-v0-delay
id: 71PGfA
title: 지연 응답 API
createdAt: 2024-01-28
updatedAt: 2024-02-14
group: HEROPY API
author:
  - ParkYoungWoong
tags:
  - API
  - Delay
description:
  지연 응답이 필요할 때 사용할 수 있는 API를 제공합니다. 최대 5초까지 지연 응답이 가능합니다.
---

학습 및 테스트를 위해 지연 응답 API를 제공합니다.
원하는 시간을 지정하고 그 시간 후에 응답을 받을 수 있습니다.

## 지연 응답(GET)

원하는 시간을 ms(밀리초) 단위로 `t` 파라미터에 작성해 요청하면, 그 시간 후 응답을 받을 수 있습니다.
지연 시간은 최대 5초(5000ms)까지 지정할 수 있습니다.

```curl
curl https://api.heropy.dev/v0/delay?t=DELEY_TIME
  \ -X 'GET'
```

```js --caption=요청 코드 예시
;(async () => {
  console.time('시간')
  const res = await fetch('https://api.heropy.dev/v0/delay?t=3000')
  console.timeEnd('시간') // 시간: 3021.283935546875 ms
  const data = await res.json()
  console.log(data) // 3초 지연된 응답입니다.
})()
```

__요청 데이터 타입 및 예시:__

- 없음

__응답 데이터 타입 및 예시:__

```ts --caption=응답 데이터 타입
type ResponseValue = string
```

```json --caption=응답 데이터 예시
"3초 지연된 응답입니다."
```

## 지연 응답(POST)

원하는 시간을 ms(밀리초) 단위로 `t` 파라미터에 작성해 요청하면, 그 시간 후 응답을 받을 수 있습니다.
또한 POST 메소드 요청 본문(body)에 작성한 정보를 그대로 응답합니다.
지연 시간은 최대 5초(5000ms)까지 지정할 수 있습니다.

```curl
curl https://api.heropy.dev/v0/delay?t=DELEY_TIME
  \ -X 'POST'
```

```js --caption=요청 코드 예시
;(async () => {
  console.time('시간')
  const res = await fetch('https://api.heropy.dev/v0/delay?t=3000', {
    method: 'POST',
    body: JSON.stringify({ 
      name: 'HEROPY',
      age: 85
    })
  })
  console.timeEnd('시간') // 시간: 3021.283935546875 ms
  const { _message, data } = await res.json()
  console.log(_message, data)
})()
```

__요청 데이터 타입 및 예시:__

```ts --caption=요청 데이터 타입
type RequestBody = any
```

```json
{
  "name": "HEROPY",
  "age": 85
}
```

__응답 데이터 타입 및 예시:__

```ts --caption=응답 데이터 타입
type ResponseValue = {
  _message: string
  data: any
}
```

```json --caption=응답 데이터 예시
{
  "_message": "3초 지연된 응답입니다.",
  "data": {
    "name": "HEROPY",
    "age": 85
  }
}
```