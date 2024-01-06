---
id: 5PlGxB
filename: api-v0-users
image: https://heropy.dev/postAssets/5PlGxB/main.jpg
title: 사용자 정보 API
createdAt: 2023-12-21
updatedAt: 2024-01-06
group: HEROPY API
author:
  - ParkYoungWoong
tags:
  - API
  - Users
  - JSON
description:
  가짜 사용자 정보(Mock Data)가 필요할 때 사용할 수 있는 REST API를 제공합니다. JSON 형식으로 사용자 정보를 조회, 생성, 수정, 삭제(CRUD / Create, Read, Update, Delete)할 수 있습니다.
---

학습 및 테스트를 위해 가짜 사용자 정보(Mock Data)를 REST API로 제공합니다.
JSON 형식으로 사용자 정보를 조회, 생성, 수정, 삭제(CRUD / Create, Read, Update, Delete)할 수 있으며, 이미지를 Base64 형식으로 전송해 사용자 프로필 사진을 등록하거나 삭제하는 기능을 테스트할 수 있습니다.
(요청하는 모든 데이터는 실제로 저장되지 않습니다)

## 사용자 목록 조회

기본 사용자 목록만 반환하며, 생성, 수정, 삭제한 사용자가 포함되지는 않습니다.

```curl
curl https://api.heropy.dev/v0/users
  \ -X 'GET'
```

```js --caption=요청 코드 예시
;(async () => {
  const res = await fetch('https://api.heropy.dev/v0/users', {
    method: 'GET'
  })
  const data = await res.json()
  console.log(data)
})()
```

__요청 데이터 타입 및 예시:__

- 없음

__응답 데이터 타입 및 예시:__

```ts --caption=응답 데이터 타입
interface ResponseValue {
  total: number
  users: {
    id: string
    name: string
    age: number
    isValid: boolean
    emails: string[]
    photo?: {
      name: string
      size: number
      mimeType: string
      url: string
    }
  }[]
}
```

```json --caption=응답 데이터 예시
{
  "total": 7,
  "users": [
    {
      "id": "ywTTX",
      "name": "Neo",
      "age": 85,
      "isValid": true,
      "emails": [
        "neo1@heropy.dev",
        "neo2@heropy.dev"
      ],
      "photo": {
        "name": "neo.jpg",
        "size": 517122,
        "mimeType": "image/jpeg",
        "url": "https://picsum.photos/id/406/400"
      }
    },
    {
      "id": "bhxd4",
      "name": "Trinity",
      "age": 22,
      "isValid": false,
      "emails": [
        "trinity1@heropy.dev"
      ],
      "photo": {
        "name": "trinity.jpg",
        "size": 102392,
        "mimeType": "image/jpeg",
        "url": "https://picsum.photos/id/201/400"
      }
    },
    {
      "id": "MO3Tq",
      "name": "Emily",
      "age": 45,
      "isValid": false,
      "emails": [
        "emily1@heropy.dev"
      ]
    },
    // ...
  ]
}
```

## 사용자 생성

새로운 사용자를 생성합니다.
생성한 사용자가 목록을 조회할 때 포함되지는 않습니다.
응답으로 반환한 데이터는 생성한 사용자의 정보입니다.
`photo` 속성은 업로드한 이미지의 정보를 반환하지만, 접근 가능한 주소(`url`)는 샘플 주소입니다.

```curl
curl https://api.heropy.dev/v0/users
  \ -X 'POST'
```

```js --caption=요청 코드 예시
;(async () => {
  const res = await fetch('https://api.heropy.dev/v0/users', {
    method: 'POST',
    body: JSON.stringify({
      name: 'HEROPY',
      age: 85,
      isValid: true,
      emails: ['thesecon@gmail.com'],
      photo: {
        name: 'heropy.png',
        data: 'data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEASABIAAD/2wBDABQODxIPDRQSEBIXFRQYHjIhHhwcHj0sLiQySUBMS0dARkVQWnNiUFVtVkVGZIhlbXd7gYKBTmCNl4x9lnN+gXz/2wBDARUXFx4aHjshITt8U0ZTfHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHx8fHz/wAARCAAkACQDASIAAhEBAxEB/8QAGQAAAgMBAAAAAAAAAAAAAAAAAAUDBAYB/8QAKRAAAgICAAUDAwUAAAAAAAAAAQIAAwQRBRITITFBUXEVgaEiJEJSYf/EABgBAAMBAQAAAAAAAAAAAAAAAAACAwEE/8QAHBEAAwEBAAMBAAAAAAAAAAAAAAECERIDITFB/9oADAMBAAIRAxEAPwBCBs6kngak60BcDqEfqZtj4jrF4Tj0Gprh1WcbVWbWzrfYev3iKlW4V55+i7D4PkZmO1yEL/UH+UX3VtWxVxysp0RN1bYuPWNBVXxsnQERcapH1Kiwpy867cfHbv8AiDeLQ514Z2ElyqujkOnoD2+IRk01qJtOXjGeKVOHW3LzKFZWA8jtNPUf2tbBeYhAQPtMXg5fQJRhtG/Bmg4Znpagxb1Ycg2jbPcfb2kvHNS2s9HRVTST32Nls6jcvTbXklhqK+LneQEA2zV637Dm8/iXLbsWpDabC4Qb0HLRBl8TL2Pc9ZVmGlXfgCbfXL5RkOel0xfxFg2W2vQAQlZmLMWPck7MI8TzKRG66p0ck1OTdQ6vU5VlOwfaEI6FLWVxjLy6xXYyhfJCrrfzKDMWO2JJ/wBhCZ+A/pyEIQA//9k='
      }
    })
  })
  const data = await res.json()
  console.log(data)
})()
```

__요청 데이터 타입 및 예시:__

```ts --caption=요청 데이터 타입
interface RequestBody {
  name: string
  age: number
  isValid?: boolean
  emails?: string[]
  photo?: {
    name: string
    data: string // Base64
  }
}
```

```json --caption=요청 데이터 예시
{
  "name": "ParkYoungWoong",
  "age": 25,
  "isValid": true,
  "emails": [
    "thesecon@gmail.com"
  ],
  "photo": {
    "name": "profile.jpg",
    "data": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBD..."
  }
}
```

__응답 데이터 타입 및 예시:__

```ts --caption=응답 데이터 타입
interface RequestBody {
  id: string
  name: string
  age: number
  isValid: boolean
  emails: string[]
  photo?: {
    name: string
    size: number
    mimeType: string
    url: string // 샘플 이미지 주소
  }
}
```

```json --caption=응답 데이터 예시
{
  "id": "ywTTX",
  "name": "ParkYoungWoong",
  "age": 25,
  "isValid": true,
  "emails": [
    "thesecon@gmail.com"
  ],
  "photo": {
    "name": "profile.jpg",
    "size": 236172,
    "mimeType": "image/jpeg",
    "url": "https://picsum.photos/id/21/400"
  }
}
```

## 사용자 확인

기본 사용자 목록에 포함된 사용자 ID를 통해 해당 사용자 정보를 조회합니다.

```curl
curl https://api.heropy.dev/v0/users/:userId
  \ -X 'GET'
```

```js --caption=요청 코드 예시
;(async () => {
  const res = await fetch('https://api.heropy.dev/v0/users/ywTTX', {
    method: 'GET'
  })
  const data = await res.json()
  console.log(data)
})()
```

__요청 데이터 타입 및 예시:__

- 없음

__응답 데이터 타입 및 예시:__

```ts --caption=응답 데이터 타입
interface ResponseValue {
  id: string
  name: string
  age: number
  isValid: boolean
  emails: string[]
  photo?: {
    name: string
    size: number
    mimeType: string
    url: string // 샘플 이미지 주소
  }
}
```

```json --caption=응답 데이터 예시
{
  "id": "ywTTX",
  "name": "Neo",
  "age": 85,
  "isValid": true,
  "emails": [
    "neo1@heropy.dev",
    "neo2@heropy.dev"
  ],
  "photo": {
    "name": "neo.jpg",
    "size": 517122,
    "mimeType": "image/jpeg",
    "url": "https://picsum.photos/id/406/400"
  }
}
```

## 사용자 수정

기본 사용자 목록에 포함된 사용자 ID를 통해 해당 사용자 정보를 수정합니다.
사용자 정보를 수정해도 조회한 기본 사용자 목록에는 반영되지는 않습니다.
사용자 프로필 사진(`photo`)에서 `null` 값을 전송하면, 프로필 사진을 삭제합니다.

```curl
curl https://api.heropy.dev/v0/users/:userId
  \ -X 'PUT'
```

```js --caption=요청 코드 예시
;(async () => {
  const res = await fetch('https://api.heropy.dev/v0/users/ywTTX', {
    method: 'PUT',
    body: JSON.stringify({
      name: "HEROPY",
      emails: ['thesecon@gmail.com']
    })
  })
  const data = await res.json()
  console.log(data)
})()
```

__요청 데이터 타입 및 예시:__

```ts --caption=요청 데이터 타입
interface RequestBody {
  name?: string
  age?: number
  isValid?: boolean
  emails?: string[]
  photo?: {
    name: string
    data: string // Base64
  } | null // 삭제할 경우!
}
```

```json --caption=요청 데이터 예시
{
  "name": "ParkYoungWoong",
  "age": 25,
  "isValid": true,
  "emails": [
    "thesecon@gmail.com"
  ],
  "photo": {
    "name": "profile.jpg",
    "data": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBD..."
  }
}
```

__응답 데이터 타입 및 예시:__

```ts --caption=응답 데이터 타입
interface ResponseValue {
  id: string
  name: string
  age: number
  isValid: boolean
  emails: string[]
  photo?: {
    name: string
    size: number
    mimeType: string
    url: string // 샘플 이미지 주소
  }
}
```

```json --caption=응답 데이터 예시
{
  "id": "ywTTX",
  "name": "ParkYoungWoong",
  "age": 25,
  "isValid": true,
  "emails": [
    "thesecon@gmail.com"
  ],
  "photo": {
    "name": "neo.jpg",
    "size": 517122,
    "mimeType": "image/jpeg",
    "url": "https://picsum.photos/id/406/400" // 샘플 이미지
  }
}
```

## 사용자 삭제

기본 사용자 목록에 포함된 사용자 ID를 통해 해당 사용자 정보를 삭제합니다.
사용자 정보를 삭제해도 조회한 기본 사용자 목록에는 반영되지는 않습니다.

```curl
curl https://api.heropy.dev/v0/users/:userId
  \ -X 'DELETE'
```

```js --caption=요청 코드 예시
;(async () => {
  const res = await fetch('https://api.heropy.dev/v0/users/ywTTX', {
    method: 'DELETE'
  })
  const data = await res.json()
  console.log(data)
})()
```

__요청 데이터 타입 및 예시:__

- 없음

__응답 데이터 타입 및 예시:__

```ts --caption=응답 데이터 타입
interface ResponseValue {
  id: string
  name: string
  age: number
  isValid: boolean
  emails: string[]
  photo?: {
    name: string
    size: number
    mimeType: string
    url: string // 샘플 이미지 주소
  }
}
```

```json --caption=응답 데이터 예시
{
  "id": "ywTTX",
  "name": "Neo",
  "age": 85,
  "isValid": true,
  "emails": [
    "neo1@heropy.dev",
    "neo2@heropy.dev"
  ],
  "photo": {
    "name": "neo.jpg",
    "size": 517122,
    "mimeType": "image/jpeg",
    "url": "https://picsum.photos/id/406/400" // 샘플 이미지
  }
}
```

## 사용자 정의 HTTP 상태 코드

모든 요청은 `200`부터 `599` 사이의 HTTP 상태 코드를 임의로 지정할 수 있으며, 그에 맞는 응답(Response)을 받을 수 있습니다.
`Request-Status` 요청 헤더에 원하는 상태 코드를 지정합니다.

```js
;(async () => {
  try {
    await fetch('https://api.heropy.dev/v0/users', {
      method: 'GET',
      headers: {
        'Request-Status': 444
      }
    })
  } catch (err) {
    console.error(err.response.status) // 444
    console.error(err.response.data.message) // '444: 잘못된 요청입니다.'
  }
})()
```
