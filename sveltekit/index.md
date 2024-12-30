---
id: QWrwz3
filename: sveltekit
image: https://heropy.dev/postAssets/QWrwz3/main.jpg
title: (초안) SvelteKit
createdAt: 2024-06-27
updatedAt: 2024-12-30
group: Svelte
author:
  - ParkYoungWoong
tags:
  - Svelte
  - SvelteKit
description:
  SvelteKit은 Svelte 프레임워크로, 서버 사이드 렌더링(SSR) 기반의 빠른 빌드 속도와 간편한 라우팅 시스템을 제공하며, SEO 최적화 등 성능 향상을 위한 여러 기능을 제공합니다.
---

/// message-box --icon=error
이 글은 초안으로, 아직 작성 중인 문서입니다.
현재 블로그는 SvelteKit으로 제작했고, 관리 중에 파편화된 관련 내용을 꾸준히 정리하려고 합니다.
///

[SvelteKit](https://kit.svelte.dev/)은 [Svelte](https://svelte.dev/) 프레임워크로, 서버 사이드 렌더링(SSR) 기반의 빠른 빌드 속도와 간편한 라우팅 시스템을 제공하며, SEO 최적화 등 성능 향상을 위한 여러 기능을 제공합니다.
2021년, Svelte의 창시자인 [Rich Harris](https://github.com/Rich-Harris)가 [Vercel](https://vercel.com/) 팀에 합류하면서 더욱 Vercel 친화적으로 쉬운 사용성을 갖추게 되었습니다.

## 설치 및 구성

다음 명령으로 SvelteKit 프로젝트를 설치합니다.
TypeScript와 ESLint 그리고 Prettier를 사용합니다.

```bash
# npm create svelte@latest sveltekit-project
# npm create svelte@latest .
npm create svelte@latest <경로|프로젝트이름>
    ✔ Which Svelte app template? - SvelteKit demo app
    ✔ Add type checking with TypeScript? - Yes, using TypeScript syntax
    ✔ Select additional options (use arrow keys/space bar) - Select all
```

### SCSS

SCSS를 사용하기 위해 다음 패키지를 설치합니다.
설치 후 바로 `*.scss` 파일을 사용할 수 있습니다.

```bash
npm i -D sass
```

```scss --path=/src/app.scss
html {
  --color-font: #333;
  body {
    color: var(--color-font);
  }
}
```

```svelte --path/src/routes/+layout.svelte --caption=SCSS 사용 예시
<script lang="ts">
  // ...
  import '../app.scss'
</script>
```

## 경로 별칭

새로운 경로 별칭이 필요하면, 다음과 같이 `alias` 옵션을 사용할 수 있습니다.

/// message-box --icon=warning
내장된 `$lib` 경로 별칭과 중복되지 않도록 주의하세요!
`$lib` 경로 별칭은 `config.kit.files.lib` 옵션에서 제어할 수 있습니다.
///

```js --path=/svelte.config.js --line-active=6-7,10 --line-error=5
// ...
const config = {
  kit: {
    alias: {
      // $lib: './src/lib',
      $components: './src/components',
      $store: './src/store'
    },
    files: {
      lib: './src/lib'
    }
  }
}
export default config
```

```svelte
<script lang="ts">
  import TextField from '$components/TextField.svelte'
  import { scrollPaddingTop } from '$store/page'
</script>
```

## 환경변수

```plaintext --path=/.env --caption=환경변수 예시
CREDENTIALS=1234
API_KEY=5678
PUBLIC_CLIENT_URL=https://heropy.dev
PUBLIC_DATABASE_ANON_KEY=abcd
```

환경변수는 기본적으로 서버 측에서만 사용할 수 있습니다.
`$env/static/private` 모듈에서 가져옵니다.

```ts
import { CREDENTIALS, API_KEY } from '$env/static/private'
```

클라이언트에서 사용할 환경변수는, `PUBLIC_` 접두사를 붙여야 합니다.
이는 해당 환경변수가 클라이언트에서 노출되어도 문제가 없다는 것을 명시적으로 표현하기 위함입니다.
`$env/static/public` 모듈에서 가져옵니다.

```ts
import { PUBLIC_CLIENT_URL, PUBLIC_DATABASE_ANON_KEY } from '$env/static/public'
```

필요하면, 원하는 접두사를 추가하거나 수정할 수 있습니다.

```js --path=/svelte.config.js --line-active=8 --line-error=7
// ...
const config = {
  kit: {
    env: {
      publicPrefix: 'PUBLIC_', // 기본값!
      privatePrefix: 'SECRET_'
    }
  }
}
export default config
```

```plaintext --path=/.env --caption=접두사를 추가한 환경변수 예시
SECRET_CREDENTIALS=1234
SECRET_API_KEY=5678
PUBLIC_CLIENT_URL=https://heropy.dev
PUBLIC_DATABASE_ANON_KEY=abcd
```

```ts
import { SECRET_CREDENTIALS, SECRET_API_KEY } from '$env/static/private'
import { PUBLIC_CLIENT_URL, PUBLIC_DATABASE_ANON_KEY } from '$env/static/public'
```

## 폰트 미리로드

`font-display: swap`을 사용해 폰트를 출력하지 못하는 상황(FOIT, Flash Of Invisible Text)을 방지할 수 있지만, 폰트 로드 후 시스템 폰트가 교체되는 현상(FOUT, Flash Of Unstyled Text)이 발생하므로, 다음과 같이 설치한 폰트를 가져와 미리로드 경로로 지정할 수 있습니다.

/// message-box --icon=warning
다른 로딩 프로세스가 차단되어 초기 로드가 매우 느려질 수 있으니, 페이지에서 사용하는 주요 폰트만 미리로드하세요!
///

```svelte --path=/src/+layout.svelte
<script lang="ts">
  import pretendard from '$lib/font/PretendardVariable.woff2'
  import '$lib/font/pretendardvariable.css'
</script>

<link
  rel="preload"
  href={pretendard}
  as="font"
  type="font/woff2"
  crossorigin="anonymous" />
```

폰트 사용을 잊지 마세요!

```css --path=/src/app.css
body {
  font-family: 'Pretendard Variable', Pretendard, -apple-system, BlinkMacSystemFont, system-ui,
    Roboto, 'Helvetica Neue', 'Segoe UI', 'Apple SD Gothic Neo', 'Noto Sans KR', 'Malgun Gothic',
    'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', sans-serif;
}
```

## 링크 옵션

SvelteKit은 `<Link>` 같은 별도의 컴포넌트가 아닌 HTML `<a>`를 경로 탐색 요소로 사용합니다.
요소 자신이나 부모 요소에 다음의 링크 옵션을 적용할 수 있습니다.

```html
<a data-sveltekit-preload-data="hover" href="/path">To Path!</a>
```

옵션 | 설명 | 값
---|---|---
`data-sveltekit-preload-data` | 페이지 데이터 미리로드 | `hover`, `tap`
`data-sveltekit-preload-code` | 페이지 코드만 미리로드 | `eager`, `viewport`, `hover`, `tap`
`data-sveltekit-reload` | 패이지 다시로드 | 
`data-sveltekit-replacestate` | 탐색 히스토리를 대체 |
`data-sveltekit-keepfocus` | 탐색 후에도 포커스 유지 |
`data-sveltekit-noscroll` | 스크롤 초기화 비활성화 |

## 페이지의 데이터 로드 및 전달

페이지(`+page.svelte`)를 렌더링하기 전에 필요한 데이터를 로드하는 방법으로 `load` 함수를 내보내는 `+page.server.ts`와 `+page.ts` 파일을 사용할 수 있습니다.
각 파일은 `+page.server.ts`, `+page.ts`, `+page.svelte` 순으로 실행되며, 만약 모두 사용하는 경우 다음과 같이 `+page.server.ts`에서 `+page.ts` 파일로 데이터를 전달해야 합니다.

/// message-box --icon=info
`+page.server.ts` 파일은 서버에서만 실행되며, `+page.ts` 파일은 서버와 클라이언트에서 모두 실행됩니다.
///

```ts --path=/src/routes/hello/+page.server.ts --caption=1. 서버에서만 실행
export async function load() {
  return {
    pageServerData: 'Hello, Server Data!'
  }
}
```

```ts --path=/src/routes/hello/+page.server.ts --caption=2. 서버와 클라이언트에서 모두 실행
export async function load({ data }) {
  return {
    ...data, // pageServerData: 'Hello, Server Data!'
    pageData: 'Hello, Hydration Data!'
  }
}
```

```svelte --path=/src/routes/hello/+page.svelte --caption=3. 페이지 렌더링
<script lang="ts">
  import type { PageData } from './$types'

  export let data: PageData
  const { pageServerData, pageData } = data

  console.log(pageServerData) // 'Hello, Server Data!'
  console.log(pageData) // 'Hello, Hydration Data!'
</script>
```

## TanStack Query 사용

루트 레이아웃의 `load` 함수에서 쿼리 클라이언트를 생성해 반환합니다.
그리고 서버에서 불필요하게 실행되지 않도록 클라이언트(브라우저)에서만 쿼리를 활성화합니다.

```ts --path=/src/routes/+layout.ts
import { browser } from '$app/environment'
import { QueryClient } from '@tanstack/svelte-query'

export async function load() {
  const queryClient = new QueryClient({
    defaultOptions: {
      queries: {
        enabled: browser // 브라우저에서만 활성화
      }
    }
  })
  return { queryClient }
}
```

생성한 쿼리 클라이언트를 가져와 연결합니다.

```svelte --path=/src/routes/+layout.svelte
<script lang="ts">
  import { QueryClientProvider } from '@tanstack/svelte-query'
  import type { LayoutData } from './$types'

  export let data: LayoutData
</script>

<QueryClientProvider client={data.queryClient}>
  <slot />
</QueryClientProvider>
```

각 페이지에 접근할 때, `prefetchQuery` 메소드로 사용할 데이터를 미리 가져옵니다.
페이지에 다시 방문해도 캐시 데이터를 사용할 수 있습니다.

```ts --path=/src/routes/posts/[postId]/+page.ts
export async function load({ parent, fetch, params }) {
  const { queryClient } = await parent() // 상위 레이아웃(+layout.ts)에서 반환하는 데이터 접근
  const { postId } = params

  await queryClient.prefetchQuery({
    queryKey: ['analytics', postId],
    queryFn: async () => (await fetch(`/api/posts/${postId}`)).json(),
    staleTime: 1000 * 60 * 60 * 24 // 24시간!
  })
}
```

각 페이지 컴포넌트에서 `createQuery` 함수를 사용해 쿼리를 생성합니다.
`createQuery` 함수는 Svelte 스토어 객체를 반환합니다.

```svelte --path=/src/routes/posts/[postId]/+page.svelte
<script lang="ts">
  import { createQuery } from '@tanstack/svelte-query'
  import { browser } from '$app/environment'
  import { page } from '$app/stores'
	
  const { postId } = $page.params
  const query = createQuery<ResponseValue>({
    queryKey: ['analytics', postId],
    queryFn: async () => (await fetch(`/api/posts/${postId}`)).json(),
    staleTime: 1000 * 60 * 60 * 24 // 24시간!
  })
  
  query.subscribe(async ({ isFetching, data }) => {
    // 브라우저가 아니거나 데이터를 가져오는 중이면 실행하지 않음
    if (!browser || isFetching) return
    console.log(data)
  })
</script>

<div>
  <div>{$query.isLoading ? '로딩 중..' : $query.data}</div>
</div>
```
