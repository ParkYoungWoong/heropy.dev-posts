---
id: 5PlGxB
filename: api-v0-users
image: https://heropy.dev/postAssets/5PlGxB/main.jpg
title: 사용자 정보(JSON)
createdAt: 2023-12-21
group: Open API
author:
  - ParkYoungWoong
tags:
  - Open API
  - Users
  - JSON
description:
  가짜 사용자 정보(Mock Data)가 필요할 때 사용할 수 있는 REST API를 제공합니다. JSON 형식으로 사용자 정보를 조회, 생성, 수정, 삭제(CRUD / Create, Read, Update, Delete)할 수 있습니다.
---

[HEROPY.DEV](https://heropy.dev)는 가짜 사용자 정보(Mock Data)가 필요할 때 사용할 수 있는 REST API를 제공합니다.
JSON 형식으로 사용자 정보를 조회, 생성, 수정, 삭제(CRUD / Create, Read, Update, Delete)할 수 있습니다.
또한 Base64 이미지 데이터를 전송해, 사용자 프로필 사진을 등록하거나 삭제할 수 있습니다.

## 사용자 목록 조회

기본 사용자 목록만 반환하며, 생성, 수정, 삭제한 사용자가 포함되지는 않습니다.

```curl
curl https://api.heropy.dev/v0/users
  \ -X 'GET'
```

요청 데이터 타입 및 예시:

- 없음

응답 데이터 타입 및 예시:

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

```curl
curl https://api.heropy.dev/v0/users
  \ -X 'POST'
```

요청 데이터 타입 및 예시:

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

응답 데이터 타입 및 예시:

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
    "url": "https://picsum.photos/400" // 샘플 이미지
  }
}
```

## 사용자 확인

사용자 ID를 통해 기본 사용자 목록에서 특정 사용자를 조회합니다.
별도 생성한 사용자는 조회할 수 없습니다.

```curl
curl https://api.heropy.dev/v0/users/:userId
  \ -X 'GET'
```

요청 데이터 타입 및 예시:

- 없음

응답 데이터 타입 및 예시:

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
    url: string
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

## 사용자 수정

사용자 ID를 통해 기본 사용자 목록에서 특정 사용자 정보를 수정합니다.
수정한 사용자 정보가 목록을 조회할 때 반영되지는 않습니다.

```curl
curl https://api.heropy.dev/v0/users/:userId
  \ -X 'PUT'
```

요청 데이터 타입 및 예시:

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

응답 데이터 타입 및 예시:

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
    url: string
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

사용자 ID를 통해 기본 사용자 목록에서 특정 사용자 정보를 삭제합니다.
삭제한 사용자가 목록을 조회할 때 반영되지는 않습니다.

```curl
curl https://api.heropy.dev/v0/users/:userId
  \ -X 'DELETE'
```

요청 데이터 타입 및 예시:

- 없음

응답 데이터 타입 및 예시:

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
    url: string
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

모든 요청은 `200`~`599` 사이의 HTTP 상태 코드를 임의로 지정할 수 있으며, 그에 맞는 응답을 받을 수 있습니다.
다양한 상태 코드를 테스트해보고 싶다면, [HTTP Status Dogs](https://httpstatusdogs.com/)를 참고하세요.

요청 헤더에 `Request-Status` 정보를 추가합니다.

```js
import axios from 'axios'

try {
  const { data } = await axios({
    url: 'https://api.heropy.dev/v0/users',
    method: 'GET',
    headers: {
      'Request-Status': 444
    }
  })
} catch (err) {
  console.error(err.response.status) // 444
  console.error(err.response.data.message) // '444: 잘못된 요청입니다.'
}
```
