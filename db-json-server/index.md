---
id: zZdlXx
filename: db-json-server
image: https://heropy.dev/postAssets/zZdlXx/main.jpg
title: JSON Server 핵심 정리
createdAt: 2024-09-07
group: DB
author: 
  - ParkYoungWoong
tags:
  - JSON
  - Server
  - DB
description:
  JSON Server는 JSON 파일을 이용해 모의용 REST API 서버 및 DB를 구축할 수 있는 도구입니다. 이를 통해 백엔드 API 서버나 DB가 준비되지 않은 상황에서도 프로토타입을 개발하거나 테스트할 수 있습니다.
---

/// message-box --icon=info
이 글은 JSON Server `1.0.0-beta.2` 버전을 기준으로 작성되었습니다.
///

## JSON Server란?

JSON Server는 JSON 파일을 이용해 모의용 RESTful API 서버 및 DB를 구축할 수 있는 도구입니다. 
이를 통해 백엔드 API 서버나 DB가 준비되지 않은 상황에서도 프로토타입을 개발하거나 테스트할 수 있습니다.

## 설치 및 실행

[`json-server`](https://github.com/typicode/json-server?tab=readme-ov-file) 패키지를 설치합니다.
그리고 모의 API 서버는 프론트엔드 개발 서버와 따로 실행해야 하므로, 동시에 스크립트 실행이 가능한 [`concurrently`](https://github.com/open-cli-tools/concurrently) 패키지도 함께 설치해 사용하면 좋습니다.
```bash
npm i -D json-server concurrently
```

패키지 설치가 끝나면, `package.json`에 다음과 같이 스크립트를 추가합니다.
`npm run` 명령으로 실행하는, `watch:` 접두사로 시작하는 모든 스크립트를 동시에 실행할 수 있습니다.

/// message-box --icon=info
Vite 프로젝트의 기본 포트는 5173번이고 JSON Server의 기본 포트는 3000번입니다.
`--port` 플래그를 사용해 JSON Server의 포트를 변경할 수 있습니다.
///

```json --path=/package.json
{
  "scripts": {
    "watch:json-server": "json-server db.json --port 3000",
    "watch:vite": "vite",
    "dev": "concurrently npm:watch:*"
  }
}
```

이제 `npm run dev` 명령으로 프론트엔드 개발 서버와 모의 API 서버를 동시에 실행할 수 있습니다.

```bash
npm run dev
```

## JSON 파일 생성

패키지 설치가 완료되면, 데이터베이스 역할을 하는 `db.json` 파일을 생성합니다.
그리고 다음과 같이 관리할 컬렉션은 수동으로 추가해야 합니다.

```json --path=/db.json
{
  "users": [],
  "posts": [],
  "comments": []
}
```

JSON 파일을 대표적인 NoSQL 데이터베이스인 MongoDB의 구조로 생각하면, 기본 배열은 컬렉션(Collection), 배열의 객체 아이템은 도큐먼트(Document), 객체 아이템의 각 속성은 필드(Field)로 이해할 수 있습니다.

```json
{
  "컬렉션": [
    도큐먼트 {
      "필드": "값",
      "필드": "값"
    },
    도큐먼트,
    도큐먼트
  ]
}
```

우선, 연습용으로 다음과 같이 JSON 데이터(`db.json`)를 작성할 수 있습니다.
사용자 5명, 게시글 2개, 댓글 3개의 데이터로, 각 게시글과 댓글은 어떤 사용자가 작성했는지 `userId`로 참조합니다.
그리고 각 댓글은 어떤 게시글의 댓글인지 `postId`로 참조합니다.

```json --path=/db.json --caption=연습용 데이터
{
  "users": [
    {
      "id": "58f2",
      "name": "Neo",
      "age": 22
    },
    {
      "id": "7a8b",
      "name": "Lewis",
      "age": 57
    },
    {
      "id": "9c3d",
      "name": "Evan",
      "age": 35
    },
    {
      "id": "2b1c",
      "name": "Alex",
      "age": 22
    },
    {
      "id": "4e6a",
      "name": "Mike",
      "age": 41
    }
  ],
  "posts": [
    {
      "id": "47g2",
      "createdAt": "2025-12-16",
      "title": "CSS Grid와 Flexbox 비교",
      "content": "레이아웃을 구성할 때 CSS Grid와 Flex 중 무엇을 사용할지 결정하는 방법. 장단점을 비교합니다.",
      "userId": "7a8b"
    },
    {
      "id": "59h3",
      "createdAt": "2024-09-29",
      "title": "자바스크립트 성능 향상 팁",
      "content": "웹 애플리케이션의 성능을 향상시키는 자바스크립트 최적화 기술을 소개합니다.",
      "userId": "58f2"
    }
  ],
  "comments": [
    {
      "id": "91bg",
      "createdAt": "2026-02-07",
      "comment": "Grid와 Flex는 항상 어려웠는데, 명확하게 설명해 주셔서 감사합니다!",
      "userId": "2b1c",
      "postId": "47g2"
    },
    {
      "id": "92ch",
      "createdAt": "2024-10-01",
      "comment": "이 성능 향상 팁은 정말 유용하네요. 제 앱이 훨씬 빨라졌어요!",
      "userId": "2b1c",
      "postId": "59h3"
    },
    {
      "id": "93di",
      "createdAt": "2025-03-14",
      "comment": "이 설명 덕분에 잘 관리할 수 있을 것 같아요.",
      "userId": "4e6a",
      "postId": "59h3"
    }
  ]
}
```

위 데이터의 스키마(Schema)를 타입스크립트로 정의하면 다음과 같습니다.
`user`나 `post` 속성은, `_embed` 쿼리 파라미터를 사용할 때 채워집니다.
관련 내용은 '[데이터 가져오기 / 참조](#h3_참조)' 부분에서 확인할 수 있습니다.

```ts --path=/server.ts
export interface User {
  id: string
  name: string
  age: number
}
export interface Post {
  id: string
  createdAt: string
  title: string
  content: string
  userId: string
  user?: User
}
export interface Comment {
  id: string
  createdAt: string
  comment: string
  userId: string
  postId: string
  user?: User
  post?: Post
}
```

## 요청 방법

JSON Server는 RESTful 원칙에 맞게 컬렉션 단위로 요청을 처리할 수 있습니다.
요청 주소에 컬렉션 이름을 작성하고, 요청 메소드를 지정해 처리 방식을 결정합니다.

```curl
curl http://localhost:3000/컬렉션 \
  -X 메소드
```

```curl --caption=사용자 목록 데이터를 가져오는 예시
curl http://localhost:3000/users \
  -X GET \
```

```curl --caption=사용자 ID로 정보를 수정하는 예시
curl http://localhost:3000/users/9c3d \
  -X PATCH \
  -d '{ "age": 99 }'
```

다음과 같은 요청 메소드를 사용할 수 있습니다.

- `GET`: 데이터 가져오기
- `POST`: 데이터 생성하기
- `PUT`: 데이터 전체 수정하기
- `PATCH`: 데이터 일부 수정하기
- `DELETE`: 데이터 삭제하기

## 데이터 가져오기

DB에서 사용자 목록 데이터를 가져오기 위해, 다음과 같이 함수를 작성할 수 있습니다.

쿼리스트링으로 조건을 추가하면, 조건에 맞는 데이터만 필터링해 가져올 수 있습니다.
쿼리스트링을 사용하지 않으면, 해당 컬렉션의 모든 데이터를 가져옵니다.

```ts --caption=사용자 목록을 가져오는 함수
export async function fetchUsers(query = ''): Promise<User[]> {
  const res = await fetch(`http://localhost:3000/users/?${query}`) // GET
  const users = await res.json()
  return users
}
```

```ts --caption=함수 호출
fetchUsers()
```

```json --caption=응답 결과
[
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "7a8b",
    "name": "Lewis",
    "age": 57
  },
  {
    "id": "9c3d",
    "name": "Evan",
    "age": 35
  },
  {
    "id": "2b1c",
    "name": "Alex",
    "age": 22
  },
  {
    "id": "4e6a",
    "name": "Mike",
    "age": 41
  }
]
```

### 조건

쿼리스트링으로 조건을 추가해, 데이터를 필터링할 수 있습니다.
`_` 기호로 시작하면, 일반 필드가 아닌 쿼리 파라미터로 인식합니다.

```
필드_조건=값
```

- `_lt`: Less Than, 미만(`<`)
- `_lte`: Less Than or Equal, 이하(`<=`)
- `_gt`: Greater Than, 초과(`>`)
- `_gte`: Greater Than or Equal, 이상(`>=`)
- `_ne`: Not Equal, 같지 않음(`!=`)

다음 예시는 나이 필드(`age`)의 값이 `22`인, 즉 나이가 22세인 사용자들을 조회합니다.

```ts --caption=함수 호출
fetchUsers('age=22')
```

```json --caption=응답 결과
[
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "2b1c",
    "name": "Alex",
    "age": 22
  }
]
```

다음 예시는 41세 미만 사용자들을 조회합니다.

```ts --caption=함수 호출
fetchUsers('age_lt=41')
```

```json --caption=응답 결과
[
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "9c3d",
    "name": "Evan",
    "age": 35
  },
  {
    "id": "2b1c",
    "name": "Alex",
    "age": 22
  }
]
```

다음 예시는 41세 이하 사용자들을 조회합니다.

```ts
fetchUsers('age_lte=41')
```

```json --caption=응답 결과
[
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "9c3d",
    "name": "Evan",
    "age": 35
  },
  {
    "id": "2b1c",
    "name": "Alex",
    "age": 22
  },
  {
    "id": "4e6a",
    "name": "Mike",
    "age": 41
  }
]
```

기타 다음과 같이 조건을 추가할 수 있습니다.

```ts --caption=함수 호출
fetchUsers('age_gt=41') // 35세 초과 사용자
fetchUsers('age_gte=41') // 35세 이상 사용자
fetchUsers('age_ne=41') // 35세가 아닌 사용자
```

### 범위

쿼리스트링으로 범위를 지정해 데이터를 가져올 수 있습니다.
몇 번째부터 몇 번째까지 혹은 몇 개를 가져올지 지정할 수 있습니다.

- `_start`: 가져올 시작 인덱스를 지정합니다.
- `_end`: 가져올 종료 인덱스를 지정합니다.
- `_limit`: 가져올 개수를 지정합니다.

다음 예제는 모두 같은 결과를 반환합니다.
`_end` 파라미터에는 배열 데이터에서 사용하는 `.slice()`와 같이 종료 인덱스 직전까지를 지정합니다.

```ts --caption=함수 호출
fetchUsers('_start=0&_end=2') // 0번째부터 2번째 직전까지
fetchUsers('_start=0&_limit=2') // 0번째부터 2개
fetchUsers('_limit=2') // 0번째부터 2개
```

```json --caption=응답 결과
[
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "7a8b",
    "name": "Lewis",
    "age": 57
  }
]
```

### 페이지

가져올 데이터를 페이지로 구분하고 페이지 단위로 가져올 수 있습니다.

- `_page`: 가져올 페이지를 지정합니다.
- `_per_page`: 페이지 당 데이터 개수를 지정합니다. 기본값은 `10`입니다.

```ts --caption=함수 호출
fetchUsers('_page=2&_per_page=2')
```

응답 결과를 확인하면, 다음과 같은 페이지 정보가 포함되어 있습니다.
실제 데이터는 `data` 속성에 포함되어 있습니다.

- `first`: 첫 페이지 번호
- `prev`: 이전 페이지 번호
- `next`: 다음 페이지 번호
- `last`: 마지막 페이지 번호
- `pages`: 전체 페이지 수
- `items`: 전체 아이템 수
- `data`: 응답 데이터

```json --caption=응답 결과
{
  "first": 1,
  "prev": 1,
  "next": 3,
  "last": 3,
  "pages": 3,
  "items": 5,
  "data": [
    {
      "id": "9c3d",
      "name": "Evan",
      "age": 35
    },
    {
      "id": "2b1c",
      "name": "Alex",
      "age": 22
    }
  ]
}
```

### 정렬

어떤 필드를 기준으로 정렬할지 지정할 수 있습니다.
기본적으로 오름차순(`asc`)으로 정렬됩니다.

- `_sort`: 정렬할 필드를 지정합니다.

```ts --caption=함수 호출
fetchUsers('_sort=age')
```

```json --caption=응답 결과
[
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "2b1c",
    "name": "Alex",
    "age": 22
  },
  {
    "id": "9c3d",
    "name": "Evan",
    "age": 35
  },
  {
    "id": "4e6a",
    "name": "Mike",
    "age": 41
  },
  {
    "id": "7a8b",
    "name": "Lewis",
    "age": 57
  }
]
```

만약 가져오는 데이터를 내림차순(`desc`)으로 정렬하고 싶다면, 필드 앞에 `-` 기호를 붙이면 됩니다.

```ts --caption=함수 호출
fetchUsers('_sort=-age')
```

```json --caption=응답 결과
[
  {
    "id": "7a8b",
    "name": "Lewis",
    "age": 57
  },
  {
    "id": "4e6a",
    "name": "Mike",
    "age": 41
  },
  {
    "id": "9c3d",
    "name": "Evan",
    "age": 35
  },
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "2b1c",
    "name": "Alex",
    "age": 22
  }
]
```

여러 필드를 기준으로 정렬할 수도 있습니다.
다음은 나이를 기준으로 내림차순으로 정렬하고, 나이가 같으면 이름을 기준으로 오름차순으로 정렬합니다.

```ts
fetchUsers('_sort=-age,name')
```

```json --line-active=19,24 --caption=응답 결과
[
  {
    "id": "7a8b",
    "name": "Lewis",
    "age": 57
  },
  {
    "id": "4e6a",
    "name": "Mike",
    "age": 41
  },
  {
    "id": "9c3d",
    "name": "Evan",
    "age": 35
  },
  {
    "id": "2b1c",
    "name": "Alex",
    "age": 22
  },
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  }
]
```

### 참조

이번에는 게시물 목록을 가져오는 함수를 작성합니다.
마찬가지로 쿼리스트링을 통해 데이터를 필터링할 수 있도록 합니다.

```ts --caption=댓글 목록을 가져오는 함수
export async function fetchComments(query = ''): Promise<User[]> {
  const res = await fetch(`http://localhost:3000/comments/?${query}`) // GET
  const comments = await res.json()
  return comments
}
```

쿼리스트링을 전달하지 않으면 모든 댓글을 가져옵니다.

```ts --caption=함수 호출
fetchComments()
```

```json --caption=응답 결과
[
  {
    "id": "91bg",
    "createdAt": "2026-02-07",
    "comment": "Grid와 Flex는 항상 어려웠는데, 명확하게 설명해 주셔서 감사합니다!",
    "userId": "2b1c",
    "postId": "47g2"
  },
  {
    "id": "92ch",
    "createdAt": "2024-10-01",
    "comment": "이 성능 향상 팁은 정말 유용하네요. 제 앱이 훨씬 빨라졌어요!",
    "userId": "2b1c",
    "postId": "59h3"
  },
  {
    "id": "93di",
    "createdAt": "2025-03-14",
    "comment": "이 설명 덕분에 잘 관리할 수 있을 것 같아요.",
    "userId": "4e6a",
    "postId": "59h3"
  }
]
```

`_embed` 쿼리 파라미터를 사용해 댓글 목록을 가져오면서 게시글의 ID(`postId`)로 해당 게시글을 함께 가져올 수 있습니다.

/// message-box --icon=warning
`_embed` 쿼리 파라미터의 값이 `posts`가 아닌 `post`임에 주의하세요!
///

```ts --caption=함수 호출
fetchComments('_embed=post')
```

```json --caption=응답 결과
[
  {
    "id": "91bg",
    "createdAt": "2026-02-07",
    "comment": "Grid와 Flex는 항상 어려웠는데, 명확하게 설명해 주셔서 감사합니다!",
    "userId": "2b1c",
    "postId": "47g2",
    "post": {
      "id": "47g2",
      "createdAt": "2025-12-16",
      "title": "CSS Grid와 Flexbox 비교",
      "content": "레이아웃을 구성할 때 CSS Grid와 Flex 중 무엇을 사용할지 결정하는 방법. 장단점을 비교합니다.",
      "userId": "7a8b"
    }
  },
  {
    "id": "92ch",
    "createdAt": "2024-10-01",
    "comment": "이 성능 향상 팁은 정말 유용하네요. 제 앱이 훨씬 빨라졌어요!",
    "userId": "2b1c",
    "postId": "59h3",
    "post": {
      "id": "59h3",
      "createdAt": "2024-09-29",
      "title": "자바스크립트 성능 향상 팁",
      "content": "웹 애플리케이션의 성능을 향상시키는 자바스크립트 최적화 기술을 소개합니다.",
      "userId": "58f2"
    }
  },
  {
    "id": "93di",
    "createdAt": "2025-03-14",
    "comment": "이 설명 덕분에 잘 관리할 수 있을 것 같아요.",
    "userId": "4e6a",
    "postId": "59h3",
    "post": {
      "id": "59h3",
      "createdAt": "2024-09-29",
      "title": "자바스크립트 성능 향상 팁",
      "content": "웹 애플리케이션의 성능을 향상시키는 자바스크립트 최적화 기술을 소개합니다.",
      "userId": "58f2"
    }
  }
]
```

`_embed` 쿼리 파라미터를 여러 번 작성하여 참조하는 데이터를 동시에 여러 개 가져올 수도 있습니다.

```ts --caption=함수 호출
fetchComments('_embed=post&_embed=user')
```

```json --caption=응답 결과
[
  {
    "id": "91bg",
    "createdAt": "2026-02-07",
    "comment": "Grid와 Flex는 항상 어려웠는데, 명확하게 설명해 주셔서 감사합니다!",
    "userId": "2b1c",
    "postId": "47g2",
    "post": {
      "id": "47g2",
      "createdAt": "2025-12-16",
      "title": "CSS Grid와 Flexbox 비교",
      "content": "레이아웃을 구성할 때 CSS Grid와 Flex 중 무엇을 사용할지 결정하는 방법. 장단점을 비교합니다.",
      "userId": "7a8b"
    },
    "user": {
      "id": "2b1c",
      "name": "Alex",
      "age": 22
    }
  },
  {
    "id": "92ch",
    "createdAt": "2024-10-01",
    "comment": "이 성능 향상 팁은 정말 유용하네요. 제 앱이 훨씬 빨라졌어요!",
    "userId": "2b1c",
    "postId": "59h3",
    "post": {
      "id": "59h3",
      "createdAt": "2024-09-29",
      "title": "자바스크립트 성능 향상 팁",
      "content": "웹 애플리케이션의 성능을 향상시키는 자바스크립트 최적화 기술을 소개합니다.",
      "userId": "58f2"
    },
    "user": {
      "id": "2b1c",
      "name": "Alex",
      "age": 22
    }
  },
  {
    "id": "93di",
    "createdAt": "2025-03-14",
    "comment": "이 설명 덕분에 잘 관리할 수 있을 것 같아요.",
    "userId": "4e6a",
    "postId": "59h3",
    "post": {
      "id": "59h3",
      "createdAt": "2024-09-29",
      "title": "자바스크립트 성능 향상 팁",
      "content": "웹 애플리케이션의 성능을 향상시키는 자바스크립트 최적화 기술을 소개합니다.",
      "userId": "58f2"
    },
    "user": {
      "id": "4e6a",
      "name": "Mike",
      "age": 41
    }
  }
]
```

## 데이터 추가하기

`POST` 요청으로 데이터를 추가할 수 있습니다.
`POST` 요청으로 생성되는 데이터에서 `id` 필드는 JSON Server를 통해 자동으로 생성되므로, `id` 필드를 제외합니다.

/// message-box --icon=info
타입스크립트의 `Omit` 유틸리티 타입은 특정 속성을 제외한 새로운 타입을 반환합니다.
///

```ts --caption=사용자 데이터를 생성하는 함수
export async function createUser(user: Omit<User, 'id'>): Promise<User> {
  const res = await fetch('http://localhost:3000/users', {
    method: 'POST',
    body: JSON.stringify(user)
  })
  const createdUser = await res.json()
  return createdUser
}
```

```ts --caption=함수 호출
createUser({
  name: 'John',
  age: 30
})
```

응답으로 생성된 문서를 반환합니다.
`id` 필드가 포함된 것을 확인할 수 있습니다.

```json --caption=응답 결과
{
  "id": "1a2b",
  "name": "John",
  "age": 30
}
```

## 데이터 수정하기

`PUT` 혹은 `PATCH` 요청으로 데이터를 수정할 수 있습니다.

### 전체 수정

`PUT` 요청은 데이터 전체를 수정하도록 요청합니다.
따라서 수정하지 않는 필드도 함께 전달해야 합니다.
어떤 데이터를 수정할 것인지 요청 주소에 ID를 포함하고 수정할 데이터를 요청 본문에 담아 호출할 수 있는 함수를 다음과 같이 작성할 수 있습니다.

/// message-box --icon=warning
`PUT` 요청으로 데이터 전체를 수정할 수 있지만, `id` 필드는 수정할 수 없습니다.
///

```ts --caption=사용자 데이터 전체를 수정하는 함수
export async function updateUser(user: User): Promise<User> {
  const res = await fetch(`http://localhost:3000/users/${user.id}`, {
    method: 'PUT',
    body: JSON.stringify(user)
  })
  const updatedUser = await res.json()
  return updatedUser
}
```

```ts --caption=함수 호출
updateUser({
  id: '58f2',
  name: 'Neo',
  age: 123 // 수정
})
```

수정된 그 데이터를 반환합니다.

```json --caption=응답 결과
{
  "id": "58f2",
  "name": "Neo",
  "age": 123
}
```

### 일부 수정

`PATCH` 요청은 데이터 일부를 수정하도록 요청합니다.
따라서 수정하지 않는 필드는 전달하지 않아도 됩니다.

/// message-box --icon=info
`Partial<User> & Pick<User, 'id'>`는 `User` 타입에서 `id` 속성은 필수로 하고 나머지 속성은 모두 선택적으로 만든 타입입니다.
///
///

```ts --caption=사용자 데이터 일부를 수정하는 함수
export async function updateUser(user: Partial<User> & Pick<User, 'id'>): Promise<User> {
  const res = await fetch(`http://localhost:3000/users/${user.id}`, {
    method: 'PATCH',
    body: JSON.stringify(user)
  })
  const updatedUser = await res.json()
  return updatedUser
}
```

```ts --caption=함수 호출
updateUser({
  id: '58f2',
  age: 123 // 수정
})
```

```json --caption=응답 결과
{
  "id": "58f2",
  "name": "Neo",
  "age": 123
}
```

## 데이터 삭제하기

`DELETE` 요청으로 특정 데이터를 삭제할 수 있습니다.
어떤 데이터를 삭제할 것인지 요청 주소에 ID를 포함해야 합니다.

```ts --caption=사용자 데이터를 삭제하는 함수
export async function deleteUser(userId: string): Promise<User> {
  const res = await fetch(`http://localhost:3000/users/${userId}`, {
    method: 'DELETE'
  })
  const user = await res.json()
  return user
}
```

```ts
deleteUser('4e6a')
```

삭제된 데이터를 반환합니다.

```json --caption=응답 결과
{
  "id": "4e6a",
  "name": "Mike",
  "age": 41
}
```

### 일괄 삭제

한 번의 요청으로 여러 데이터를 삭제하기 위해 다음과 같이 함수를 작성할 수 있습니다.

```ts --caption=사용자 데이터를 일괄 삭제하는 함수
export async function deleteUsers(userIds: string[] = []): Promise<User[]> {
  return Promise.all(userIds.map(async userId => {
    const res = await fetch(`http://localhost:3000/users/${userId}`, {
      method: 'DELETE'
    })
    const deletedUser = await res.json()
    return deletedUser
  }))
}
```

삭제할 데이터의 ID를 배열로 전달합니다.

```ts
deleteUsers(['58f2', '7a8b', '9c3d'])
```

삭제된 데이터 목록을 반환합니다.

```json --caption=응답 결과
[
  {
    "id": "58f2",
    "name": "Neo",
    "age": 22
  },
  {
    "id": "7a8b",
    "name": "Lewis",
    "age": 57
  },
  {
    "id": "9c3d",
    "name": "Evan",
    "age": 35
  }
]
```

### 참조 삭제

`DELETE` 요청으로 데이터를 삭제할 때, 해당 데이터를 참조하는 다른 데이터가 있다면 함께 삭제할 수 있습니다.
`_dependent` 쿼리 파라미터를 사용하면 됩니다.

다음 함수는 게시글을 삭제할 때, 연관 댓글도 함께 삭제할 수 있습니다.
댓글(Comments) 컬렉션에서 `postId` 필드가 해당(삭제) 게시글의 ID와 일치하는 모든 댓글을 같이 삭제할 수 있습니다.

```ts --line-active=2 --caption=게시글 데이터를 삭제하는 함수
export async function deletePost(postId: string, isDeleteRefs = true): Promise<Post> {
  const query = isDeleteRefs ? '_dependent=comments' : ''
  const res = await fetch(`http://localhost:3000/posts/${postId}?${query}`, {
    method: 'DELETE'
  })
  const deletedPost = await res.json()
  return deletedPost
}
```

`isDeleteRefs` 인자의 기본값은 `true`이므로 호출 시 생략할 수 있습니다.
그러면 게시글과 연관 댓글이 모두 삭제됩니다.

```ts --caption=함수 호출
// 게시글을 삭제하며, 연관 댓글도 삭제합니다.
deletePost('59h3')
deletePost('59h3', true)
```

만약 게시글을 삭제하지만 연관 댓글은 삭제하지 않고 싶다면, 다음과 같이 두 번째 인자로 `false`를 전달합니다.

```ts
// 게시글을 삭제하지만, 연관 댓글은 삭제하지 않습니다.
deletePost('59h3', false)
```

그러면 참조할 게시글(Post) 도큐먼트가 없어지면서, `postId` 필드에는 `null`이 할당됩니다.

```json --caption=comments 컬렉션 결과
{
  "comments": [
    {
      "id": "91bg",
      "createdAt": "2026-02-07",
      "comment": "Grid와 Flex는 항상 어려웠는데, 명확하게 설명해 주셔서 감사합니다!",
      "userId": "2b1c",
      "postId": "47g2"
    },
    {
      "id": "92ch",
      "createdAt": "2024-10-01",
      "comment": "이 성능 향상 팁은 정말 유용하네요. 제 앱이 훨씬 빨라졌어요!",
      "userId": "2b1c",
      "postId": null
    },
    {
      "id": "93di",
      "createdAt": "2025-03-14",
      "comment": "이 설명 덕분에 잘 관리할 수 있을 것 같아요.",
      "userId": "4e6a",
      "postId": null
    }
  ]
}
```
