---
id: bCffI2
filename: db-supabase-starter
image: https://heropy.dev/postAssets/bCffI2/main.jpg
title: Supabase Database, Prisma로 빠르게 시작하기 w. Next.js
createdAt: 2024-03-24
updatedAt: 2024-03-27
group: DB
author:
  - ParkYoungWoong
tags:
  - Prisma
  - Supabase
  - Next.js
description: 
  오픈소스 백엔드 서비스인 Supabase의 PostgreSQL 데이터베이스와 Prisma를 사용해 Next.js 프로젝트를 빠르고 쉽게 구성하고 다루는 방법을 알아봅니다.
---

## Supabase 소개

[Supabase](https://supabase.com/)는 [Google Firebase](https://firebase.google.com/)와 유사한 오픈소스 백엔드 서비스로, 웹/모바일 애플리케이션을 쉽고 빠르게 개발/배포할 수 있도록 도와주며 직접적인 인프라 관리에 대한 부담을 덜어줍니다.
기본적으로 [PostgreSQL](https://www.postgresql.org/)을 기반으로 구축된 데이터베이스(Database) 등의 다음과 같은 기능을 제공합니다.

- Database: Full Postgres 데이터베이스
- Authentication: 소셜, 전화 등 다양한 방법의 사용자 인증 기능
- Storage: 이미지, 비디오, 문서 등의 AWS S3와 호환되는 파일 저장소
- Edge Functions: 사용자와 가까운 엣지에서 배포되는 서버측 TypeScript 함수
- Realtime: 전 세계적으로 분산된 Realtime 서버 클러스터
- AI & Vectors: Postgres 및 pgVector를 사용해 AI 애플리케이션을 개발하기 위한 오픈 소스 툴킷

### 요금제

무료 버전에서 제공하는 기본적인 기능 및 특징은 다음과 같습니다.
더 자세한 내용은 [Supabase Pricing](https://supabase.com/pricing) 페이지에서 확인할 수 있습니다.

- 500MB 데이터베이스
- 매월 최대 5GB 데이터 전송량(Bandwidth)
- 1주일 동안 활동하지 않으면 데이터베이스 일시 중지
- 매월 최대 5만명의 활성 사용자
- 1GB 파일 저장소(Storage)
- 파일 크기 50MB 제한
- 매월 50만 함수 호출

![](./assets/s13.JPG)

## Prisma 소개

[Prisma](https://www.prisma.io/)는 데이터베이스 스키마를 쉽게 정의하고 타입 세이프(Type-Safe)한 쿼리를 작성할 수 있도록 도와주는 차세대 Node.js 및 TypeScript ORM(Object-Relational Mapping)입니다.
Prisma를 사용해 직접 SQL을 작성하지 않고도 데이터베이스를 쉽게 다룰 수 있습니다.

```ts --caption=사용자 생성 예시
import { PrismaClient } from '@prisma/client'
const prisma = new PrismaClient()
prisma.user.create({
  data: {
    name: 'HEROPY',
    age: 85,
    email: 'thesecon@gmail.com'
  }
})
```

## Next.js 프로젝트 구성

Supabase 데이터베이스와 Prisma를 사용해 Next.js 프로젝트를 구성해 보겠습니다.
Prisma를 통해 타입 세이프한 쿼리를 작성하려면, TypeScript를 사용하는 것이 좋습니다.

다음과 같이 Next.js 프로젝트를 생성하고 패키지를 설치합니다.

- `prisma`: Prisma CLI를 사용해 데이터베이스 스키마를 가져오거나 마이그레이션을 실행하는 코어 패키지입니다.
- `@prisma/client`: 클라이언트 라이브러리로, 데이터베이스에 대한 타입 세이프한 쿼리를 요청할 수 있도록 도와줍니다.

```bash
npx create-next-app@latest supabase-test
    ✔ Would you like to use TypeScript? … Yes
    ✔ Would you like to use ESLint? … Yes
    ✔ Would you like to use Tailwind CSS? … No
    ✔ Would you like to use `src/` directory? … No
    ✔ Would you like to use App Router? (recommended) … Yes
    ✔ Would you like to customize the default import alias (@/*)? … Yes
    ✔ What import alias would you like configured? … ~/*

cd supabase-test
npm i -D prisma
npm i @prisma/client
```

### Prisma 초기화

프로젝트에서 Prisma를 사용하기 위해 초기화가 필요합니다. 
터미널에서 다음 명령을 실행하면, 프로젝트에 `/prisma/schema.prisma`, `/.env` 파일을 자동으로 생성합니다.

```bash
npx prisma init
```

### Supabase 프로젝트 생성

이제 [Supabase](https://supabase.com/)에 접속해, 회원가입 및 로그인 후 ['Dashboard > Projects'](https://supabase.com/dashboard/projects) 페이지에서 새로운 프로젝트를 생성합니다.

![](./assets/s1.JPG)

다음과 같이 조직(Organization), 프로젝트 이름, 데이터베이스 비밀번호 그리고 리전(Region)을 입력/선택합니다.
무료 버전의 경우, 하나의 조직에서 최대 2개의 활성 프로젝트를 생성할 수 있습니다.

/// message-box --icon=warning
데이터베이스 비밀번호는 클라이언트에서 연결 문제가 발생할 수 있으니, 숫자나 특수문자를 포함하지 않고 영어 대소문자로만 작성하는 것을 추천합니다.
이후에 'Project Settings > Configuration > Database Settings' 페이지에서 얼마든지 비밀번호를 변경할 수 있습니다.
///

![](./assets/s2.JPG)

'Project Settings > Configuration > Database Settings' 페이지에서 Connection String을 복사해 `/.env` 파일에 `DATABASE_URL` 변수에 붙여넣습니다.

![](./assets/s3.JPG)

다음 예시처럼, 값의 `[YOUR-PASSWORD]` 부분은 앞서 입력했던 데이터베이스 비밀번호로 대체합니다.

```plaintext --path=/.env
# DATABASE_URL="postgres://postgres.rhlkfepaasyyeqydkjkw:[YOUR-PASSWORD]@aws-0-ap-northeast-2.pooler.supabase.com:5432/postgres"
DATABASE_URL="postgres://postgres.rhlkfepaasyyeqydkjkw:abcdefghijk@aws-0-ap-northeast-2.pooler.supabase.com:5432/postgres"
```

#### 연결 문제가 발생하는 경우!

이후에 만약 다음과 같이 `Can't reach database server..` 문제가 발생하는 경우, 약간의 환경변수 수정이 필요할 수 있습니다.
이 문제는 주로 macOS나 로컬 환경에서 발생하는 것으로 보이며, 미리 해결해도 무방합니다.

```bash
Invalid `prisma.abc.xyz()` invocation:

Can't reach database server at `aws-0-ap-northeast-2.pooler.supabase.com`:`5432`

Please make sure your database server is running at `aws-0-ap-northeast-2.pooler.supabase.com`:`5432`.
```

다음과 같이 기존 `DATABASE_URL` 변수를 하나 복사해 `DIRECT_URL` 변수로 이름을 수정합니다.
그리고 `DATABASE_URL` 변수는 포트 번호를 `6543`으로 변경하고 `?pgbouncer=true` 쿼리스트링을 추가합니다.
`pgbouncer` 옵션은 자동으로 커넥션 풀링을 활성화하고, 호환성을 보장할 수 있습니다.

/// message-box --icon=info
PgBouncer는 PostgreSQL 데이터베이스 서버 앞에서 동작하는 경량의 데이터베이스 커넥션 풀러(Connection Pooler)로 여러 클라이언트 연결, 처리 시간 단축, 리소스 최적화 등의 기능을 제공합니다.
///

```bash --path=/.env
# Connect to Supabase via connection pooling with Supavisor.
DATABASE_URL="postgres://postgres.rhlkfepaasyyeqydkjkw:abcdefghijk@aws-0-ap-northeast-2.pooler.supabase.com:6543/postgres?pgbouncer=true"
# Direct connection to the database. Used for migrations.
DIRECT_URL="postgres://postgres.rhlkfepaasyyeqydkjkw:abcdefghijk@aws-0-ap-northeast-2.pooler.supabase.com:5432/postgres"
```

그리고 새로 추가한 `DIRECT_URL` 변수를 Prisma에서 사용할 수 있도록, 다음과 같이 `schema.prisma` 파일을 수정합니다.

```plaintext --path=/prisma/schema.prisma --line-active=6
// ...

datasource db {
  provider  = "postgresql"
  url       = env("DATABASE_URL")
  directUrl = env("DIRECT_URL")
}

// ...
```

### Database 테이블 생성

Supabase 프로젝트 생성이 끝났으니, 이제 'Table Editor' 페이지에서 새로운 데이터베이스 테이블을 생성합니다.

![](./assets/s4.JPG)

이 과정에서는 다음과 같이 테이블 이름(`Post`)을 입력하고 'Save' 버튼을 선택합니다.
`id`와 `created_at` 열(Column)은 자동으로 생성되며, 만약 클라이언트에서 CamelCase로만 속성 이름을 사용하려면 `created_at` 대신 `createdAt` 이름으로 미리 변경하는 것이 좋습니다.

![](./assets/s5.JPG)

![생성된 Post 테이블](./assets/s6.JPG)

### DB 스키마 가져오기

이제 Next.js 프로젝트로 돌아와 Prisma를 사용해, 생성한 Supabase 데이터베이스와 연결하겠습니다.
터미널에서 다음 명령으로 Supabase 데이터베이스의 스키마를 가져옵니다.

```bash
npx prisma db pull
```

그러면 다음과 같이 `schema.prisma` 파일에 Supabase 데이터베이스 `Post` 테이블의 스키마가 자동으로 추가됩니다.

```plaintext --path=/prisma/schema.prisma --line-active=10-13
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model Post {
  id         BigInt    @id @default(autoincrement())
  created_at DateTime  @default(now()) @db.Timestamptz(6)
}
```

그리고 추가된 스키마를 기반으로 Prisma Client를 생성하기 위해, 다음 명령을 실행합니다.
Prisma Client를 생성해야 데이터베이스에 대한 타입 세이프한 쿼리를 작성할 수 있습니다.

```bash
npx prisma generate
```

추가로 Next.js 프로젝트를 배포할 때, 서버 빌드 시에도 Prisma Client를 생성할 수 있도록 `package.json` 파일에 다음과 같이 `postinstall` 스크립트를 추가합니다.

```json --path=/package.json
{
  "scripts": {
    "postinstall": "prisma generate"
  }
}
```

### 데이터(행) 생성

Prisma Client를 사용할 준비가 끝났습니다. 
이제 데이터베이스에 접근해 새로운 데이터(행, Row)를 생성하겠습니다.

Prisma Client로 데이터베이스에 접근할 때는 다음과 같은 형식을 사용합니다.
또한 `create()` 같은 각 메소드는 'Promise 인스턴스'를 반환하므로, `await` 키워드나 `.then()`을 사용해 비동기로 처리할 수 있습니다.

```ts
// Prisma인스턴스.테이블이름.메소드()
await prisma.post.create()
```

`/app/api/post/route.ts` 파일을 생성하고 다음과 같이 코드를 작성합니다.

```ts --path=/app/api/post/route.ts
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

export async function GET() {
  const res = await prisma.post.create({
    data: {}
  })
  return Response.json('ok!')
}
```

개발 서버를 실행하고, `http://localhost:3000/api/post/`로 접속합니다.
그러면 바로 Supabase Post 테이블에서 다음과 같이 새로운 행이 생성된 것을 확인할 수 있습니다.

![](./assets/s14.JPG)

### 열 생성

새로운 열(Column)을 추가하려면, 'Table Editor' 페이지에서 머릿열 끝 '+' 버튼을 선택합니다.

![](./assets/s7.JPG)

열의 이름(Name), 간단한 설명(Description), 데이터 타입(Type), 기본 값(Default Value) 등을 입력하고 하단의 'Save' 버튼을 선택합니다.

/// message-box --icon=info
데이터 타입이 `text`인 경우, 항상 문자를 반환하도록 기본 값은 빈 문자(Empty String)로 설정하는 것을 추천합니다.
///

![](./assets/s8.JPG)

다음과 같이 추가된 `content` 열을 확인할 수 있습니다.

![](./assets/s9.JPG)

### 스키마 다시 가져오기 및 행 추가

원격 데이터베이스에서 새로운 열을 추가했으니, 터미널에서 다음 명령으로 스키마를 다시 가져와야 합니다.

```bash
npx prisma db pull
```

그러면 다음과 같이 `schema.prisma` 파일에 `content` 열이 새로 추가된 것을 확인할 수 있습니다.

```plaintext --path=/prisma/schema.prisma --line-active=6
// ...

model Post {
  id         BigInt    @id @default(autoincrement())
  created_at DateTime  @default(now()) @db.Timestamptz(6)
  content    String?   @default("")
}
```

수정된 스키마를 기반으로 Prisma Client를 다시 생성합니다.

```bash
npx prisma generate
```

다음과 같이 새롭게 추가된 `content` 열에, 정보를 추가해 행를 생성해 봅시다.

```ts --path=/app/api/post/route.ts --line-active=6
// ...

export async function GET() {
  const res = await prisma.post.create({
    data: {
      content: '포스트 내용 입력!'
    }
  })
  return Response.json('ok!')
}
```

위와 같이 수정한 내용으로 `http://localhost:3000/api/post/`로 접속한 후 바로 Supabase 테이블을 확인하면, 다음과 같이 새로운 행이 생성된 것을 확인할 수 있습니다.

![](./assets/s10.JPG)

Prisma Clients는 스키마(`schema.prisma`)를 기반으로 타입 세이프한 쿼리를 작성할 수 있기 때문에, `contents`와 `hello` 같이 존재하지 않는 열을 사용하려고 하면 다음과 같이 타입 에러가 발생합니다.

```ts --path=/app/api/post/route.ts --line-error=6,7
// ...

export async function GET() {
  const res = await prisma.post.create({
    data: {
      contents: '포스트 내용 입력!', // Error - ... 형식에 'contents'이(가) 없습니다. 'content'을(를) 쓰려고 했습니까? ts(2561)
      hello: new Date() // Error - ... 형식에 'hello'이(가) 없습니다. ts(2353)
    }
  })
  return Response.json('ok!')
}
```

### 스키마 내보내기

원격의 'Table Editor'를 대신해, 로컬에서 수정한 스키마를 반영할 수도 있습니다.
'Table Editor'가 편하긴 하지만, 지원하지 않는 기능이나 복잡한 작업을 할 때는 로컬에서 직접 스키마를 수정해 내보내는 과정이 필요할 수 있습니다.

여기에서는 행을 수정할 때의 시간을 저장하도록 `updated_at` 열을 추가해 보겠습니다.
`/prisma/schema.prisma` 파일을 다음과 같이 직접 수정합니다.

타입은 선택적(Optional) `DateTime?`이고 `@updatedAt`와 `@db.Timestamptz(6)` 데코레이터를 사용해 Timezone으로 업데이트 시간을 자동으로 저장하도록 설정합니다.

/// message-box --icon=warning
`DateTime?`의 `?` 기호가 있는 것을 주의하세요!
지금까지의 과정을 통해서 기존에 추가한 2개의 행이 있기 때문에, 새로운 `updated_at` 열을 필수적(Required)으로 설정하고 스키마를 내보내면, 기존 테이블 구조와의 충돌로 테이블 데이터를 모두 잃을 수 있습니다.
이런 경우, 필요하다면 선택적(Optional) 타입으로 열을 추가하고 이후 다른 행의 해당 열에 데이터를 모두 채운 후 필수적 타입으로 변경해야 합니다.
///

```plaintext --path=/prisma/schema.prisma --line-active=6
// ...

model Post {
  id         BigInt    @id @default(autoincrement())
  created_at DateTime  @default(now()) @db.Timestamptz(6)
  updated_at DateTime? @updatedAt @db.Timestamptz(6)
  content    String?   @default("")
}
```

로컬에서 스키마를 수정했으니, 원격 데이터베이스에 적용(내보내기)하기 위해 터미널에서 다음 명령을 실행합니다.
이렇게 내보내는 경우, Prisma Client는 자동으로 생성됩니다.

```bash
npx prisma db push

  🚀  Your database is now in sync with your Prisma schema. Done in 341ms
  ✔ Generated Prisma Client (v5.11.0) to ./node_modules/@prisma/client in 75ms
```

완료되면, 다음과 같이 `updated_at` 열이 추가된 것을 확인할 수 있습니다.

![](./assets/s11.JPG)

그리고 이번에는 새롭게 추가된 열에 데이터가 잘 저장되는지 확인하기 위해 기존의 행을 수정해 봅시다.
다음과 같이 `update` 메소드의 `where` 속성으로 특정 `id`의 행을 찾아 수정할 수 있습니다.

/// message-box --icon=warning
`update` 메소드는 단일 행을 수정하기 때문에 고유 열(Unique)의 제약 조건이 필요하고, 따라서 `id`와 같은 고유 열의 정보를 조건으로 제공해야 합니다.
반대로 고유 열 없이, 제공된 조건으로 찾은 모든 행을 수정하려면 `updateMany` 메소드를 사용하면 됩니다.
///

```ts --path=/app/api/post/route.ts --line-active=4-7,9
// ...

export async function GET() {
  const res = await prisma.post.update({
    where: {
      id: 2
    },
    data: {
      content: '포스트 내용 수정~'
    }
  })
  return Response.json('ok!')
}
```

`http://localhost:3000/api/post/`로 접속한 후 바로 Supabase 테이블을 확인하면, 다음과 같이 기존 행이 수정되면서 `updated_at` 열에 시간이 자동으로 추가된 것을 확인할 수 있습니다.

![](./assets/s12.JPG)

## Prisma Studio

Prisma Studio는 데이터베이스를 시각적으로 확인하고 수정할 수 있는 GUI(Graphical User Interface) 도구입니다.
우리는 Supabase의 'Table Editor'를 사용하고 있기 때문에, Prisma Studio를 사용하지 않아도 무방합니다.
단지, 원격이 아닌 로컬에서 데이터베이스를 시각적으로 관리하고 싶다면 Prisma Studio를 사용할 수 있습니다.

터미널에서 다음 명령을 실행하면, 브라우저에서 `http://localhost:5555`로 접속할 수 있습니다.

```bash
npx prisma studio

  Environment variables loaded from .env
  Prisma schema loaded from prisma/schema.prisma
  Prisma Studio is up on http://localhost:5555
```

![](./assets/s15.JPG)

Prisma Studio에서 수정한 내용은 별도 저장해야 원격의 Supabase 데이터베이스에 반영됩니다.

![](./assets/s16.JPG)

## Prisma Client API

Prisma Client에서 제공하는 API 중 기본적인 모델 쿼리(Model queries) 및 옵션은 다음과 같습니다.
더 자세한 내용은 [Prisma Client API](https://www.prisma.io/docs/orm/reference/prisma-client-reference) 문서를 참고하세요.

```ts
prisma.post.update({
  where: {
    id: 2
  },
  data: {
    content: '포스트 내용 수정~'
  }
})
```

| 메소드 | 설명 |
| --- | --- |
| `findUnique` | 고유(Unique) 열을 기반으로 단일 행을 찾습니다. |
| `findFirst` | 조건의 첫 번째 행을 찾습니다. |
| `findMany` | 조건의 여러 행을 찾습니다. |
| `create` | 새로운 행을 생성합니다. |
| `createMany` | 여러 행을 생성합니다. |
| `upsert` | 행을 찾아 수정하거나, 없으면 새로 생성합니다. |
| `update` | 조건의 행을 수정합니다. |
| `updateMany` | 조건의 여러 행을 수정합니다. |
| `delete` | 조건의 행을 삭제합니다. |
| `deleteMany` | 조건의 여러 행을 삭제합니다. |
| `count` | 조건의 행 개수를 반환합니다. |
| `aggregate` | 조건의 행 집계 정보를 반환합니다. |
| `groupBy` | 열을 기준으로 그룹화된 정보를 반환합니다. |

| 옵션 | 설명 |
| --- | --- |
| `select` | 열을 선택합니다. |
| `include` | 관계(Relation) 열을 선택합니다. |
| `where` | 조건 행을 찾습니다. |
| `orderBy` | 열을 기준으로 정렬합니다. |
| `distinct` | 중복 행을 제거합니다. |


